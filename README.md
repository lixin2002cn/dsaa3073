# DSAA3073 course website

This is the maintainable MkDocs source project for the Fall 2026 edition of
DSAA3073 - Theories in Data Science. Its Material theme version, palette,
fonts, navigation features, favicon, and custom stylesheet match the previous
published website.

## Local preview

```sh
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/mkdocs serve
```

Open `http://127.0.0.1:8000/dsaa3073/`.

## Production build

```sh
.venv/bin/mkdocs build --strict
```

The generated static website is written to `site/` and is intentionally not
tracked. Edit the Markdown files in `docs/`, not generated HTML.

## Material status

- Week 1-10 Learning Sheets are included as downloadable PDFs.
- Week 1-13 Validation Sheets are placeholders until the current-semester
  files are released.
- Week 1-10 Cheatsheets are placeholders until the current-semester files are
  produced.
- Week 1-13 Open Problems are placeholders with topics marked TBD.
- Five equally weighted Part Tests contribute 70% of the course grade. Each
  Test is 130 marks, lasts 30 minutes, and is held in the class following
  completion of its Part.
- Week 11-13 are reserved for student presentations and contribute 30% of the
  course grade. Each presentation is based on an individually completed,
  instructor-approved written assignment or programming project; the detailed
  rubric and student order are TBD.

Future files should use these stable names:

- `docs/pdfs/validation-sheets/WeekN_Validation_Sheet.pdf`
- `docs/pdfs/cheatsheets/WeekN_Cheatsheet.pdf`
- `docs/open-problems/WeekN_Open_Problems.pdf` (or a matching Markdown page)
