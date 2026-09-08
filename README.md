# DSAA3073 course website

This is the maintainable MkDocs source project for the Fall 2026 edition of
DSAA3073 - Theories in Data Science. The site uses MkDocs Material with two main pages and a course-focused layout
inspired by the DSAA1001 website.

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
- Week 1-10 Validation Sheets are included as downloadable student PDFs;
  presentation-week materials for Weeks 11-13 remain placeholders.
- Week 1-10 Cheatsheets are included as downloadable PDFs.
- Five equally weighted Part Tests contribute 70% of the course grade. Each
  Test is 120 marks, contains 4 multiple-choice questions and 6 short-answer
  questions, lasts 30 minutes, and is held in the class following completion
  of its Part.
- Week 11-13 are reserved for student presentations and contribute 30% of the
  course grade. Each presentation is based on an individually completed,
  instructor-approved written assignment or programming project; the detailed
  rubric and student order are TBD.

Future files should use these stable names:

- `docs/pdfs/validation-sheets/WeekN_Validation_Sheet.pdf`
- `docs/pdfs/cheatsheets/WeekN_Cheatsheet.pdf`
- `docs/pdfs/tutorials/TutorialN_Notes.pdf`

Tutorial handouts are listed in the Materials overview and the corresponding
weekly page. Publish the course-language handout with a descriptive title such
as `Tutorial 1: Expectation, Bounds, and Covariance`; filenames and download
labels should not include language-version suffixes.

## Page organization

- `docs/index.md`: course introduction, teaching team, complete schedule,
  assessment rules, and the assignment requirements at the bottom.
- `docs/materials/index.md`: the original Part/weekly-link overview, with
  downloads on each weekly page. Home also provides direct PDF links in its
  schedule table, whose entries are labeled Lecture 1-13.
- `mkdocs.yml`: the two primary navigation entries, Home and Materials.
- `docs/css/custom.css`: layout, tables, colors, and light/dark presentation.

Previously published schedule, assignment, and weekly URLs are retained for
existing bookmarks. Internal schedule and assignment links point to Home.
Keep dates and Part Test information consistent between Home and the weekly pages.

On Windows, use `.venv\Scripts\python.exe -m mkdocs serve` for local preview
and `.venv\Scripts\python.exe -m mkdocs build --strict` for validation.
