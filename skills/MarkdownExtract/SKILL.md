---
name: MarkdownExtract
version: 0.1.0
description: "Batch-convert a folder of source documents (docx, rtf, odt, html) into canonical markdown in the Data working layer, mirroring the source structure. USE WHEN extract documents to markdown, convert docx to markdown, ingest a document folder, build the data layer from sources, pandoc batch."
---

# MarkdownExtract

Turn a folder of binary source documents into canonical markdown under `~/Data/<Type>/<project>/`, mirroring the source tree. This is the entry point of the data pipeline: originals live in `~/Documents`, their extracted text becomes the working layer in `~/Data`, and the vault references that layer rather than copying it (see the DataWorkingLayer rule).

## Instructions

### Step 1: Resolve source and target

- **Source**: a folder of documents, usually under `~/Documents/<area>/<project>/`.
- **Target**: `~/Data/Text/<project>/`, mirroring the source's subfolder structure. Create it.

Keep file stems identical between source and target so a note's `paths:` pointer and the Data file stay obviously paired.

### Step 2: Check prerequisites

```bash
which pandoc || echo "brew install pandoc"
```

That is the only prerequisite for the bulk of a document folder. `pdf` handling (Step 4) additionally uses poppler (`pdftoppm`/`pdftotext`, `brew install poppler`); `xlsx` handling uses `uv` (`brew install uv`), which resolves the extractor's inline dependency on demand.

### Step 3: Batch-convert

Extraction is pandoc. The bundled `doc-extract` is a thin batch wrapper: it walks the source, converts every pandoc-readable file (`docx`, `rtf`, `odt`, `html`, `epub`) with `-t gfm --wrap=none`, mirrors stems into the target, and reports anything else.

```bash
doc-extract <source-dir> <target-dir>
```

For a single file, just call pandoc directly — no wrapper needed:

```bash
pandoc -f docx -t gfm --wrap=none "in.docx" -o "out.md"
```

### Step 4: Handle the non-pandoc cases

Pandoc reads neither `xlsx` nor `pdf`:
- **xlsx**: `xlsx-extract <file.xlsx> [...]` (shipped in this skill directory). It writes one GitHub-flavored table per sheet, reading real dates and cached formula values via openpyxl. The script carries its dependency inline (PEP 723) and runs through `uv`, so openpyxl resolves into an ephemeral environment and nothing installs into a shared or project venv. Pass `--outdir <dir>` to mirror into the Data tree; otherwise it writes `<stem>.md` beside each source.
- **Text PDFs**: `pdftotext` or the Read tool, saved as markdown in the Data mirror.
- **Image/scan PDFs** (renderings, maps): not text. Leave a short Data stub noting the PDF is image-only and treat the PDF as the canonical source for any artifact build (see BuildDeck).

### Step 5: Hand off to curation

The Data markdown is now canonical. In the vault, create or update notes that **reference** these files via `paths:` and carry the schema (frontmatter, summary, wikilinks). Do not paste the Data file's body into the note. For bilingual extractions, the curated note may keep one language; the full bilingual text stays in Data.

## Constraints

- Never write extracted markdown into the vault tree — `~/Data` is the working layer (DataWorkingLayer rule).
- Mirror the source structure and stems exactly; do not rename during extraction.
- Preserve every figure, date, and amount verbatim — extraction is lossless, curation is where text is shaped.
- Files end with a trailing newline; no tab characters.
- Report what converted and what could not (with the reason), never a silent skip.
