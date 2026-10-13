# Independent bounded website publication review

Date: 2026-10-13
Reviewer: independent `website_solution_review` subagent
Verdict: **PASS** for the current publication package described below.

## Scope and authority

The downloaded published baseline, `build/dsaa3073-published-baseline-20261013`, is authoritative for existing website PDFs. The reviewed fresh website checkout is `build/dsaa3073-online-20261013`, initially based on source commit `4a8e7e6`. This is a bounded publishing compatibility and preservation review, not a new whole-assessment authoring or difficulty certification. No teaching source or PDF content was altered by this reviewer.

Existing schedule mapping is retained: Lectures 3 and 4 use the same Week 3 materials; Lecture 5 uses Week 4 materials. Lectures 1–3 retain the same numeric mapping, Lecture 4 repeats Week 3, and Lectures 5–11 map to Weeks 4–10.

## Findings resolved before release

1. The current canonical `courses/dsaa3073/validations/week-04/validation-solutions.pdf` is **not compatible** with the online Week 4 student sheet: E1 was replaced with a three-coordinate restriction-set union-summary problem. The online E1 remains the one-sided deviation / approximate ERM problem, with excess-risk certificate 0.080. The incompatible canonical PDF was not approved for publication.
2. The current canonical Week 3 solution repeats C2 with revised wording: “A class consists of five hypotheses …”; the online sheet says “On C, five hypotheses induce …”. The answer is unchanged, but an exact online-compatible previous PDF exists and was selected instead.

The selected existing solution PDFs are:

| Publication targets | Verified source PDF |
|---|---|
| Lecture3_Validation_Solutions.pdf; Lecture4_Validation_Solutions.pdf | `build/th013/chapter-02-downstream/review-fresh-2/week3-validation-solutions.pdf` |
| Lecture5_Validation_Solutions.pdf | `build/th013/verify-week4-validation/fresh/validation-solutions.pdf` |

All six target checks (three PDFs in both `docs/` and built `site/`) are byte-identical to the selected candidates. See `solution-byte-checks.json`. The initially incompatible candidates have therefore been replaced; neither finding remains open.

## Question and answer compatibility

I read the full extracted text of both online question sheets and both selected solutions, covering A1–A4, B1, C1–C2, D1–D2, E1, and F1. The selected solution PDFs repeat all 11 online questions per sheet, preserve all numeric parameters and marks, and supply all 11 solution and marking blocks. Both totals remain 130 marks. No unrelated Part Test answer PDF is introduced.

Week 3 checks: MC keys b/c/c/b; finite-class union bound and sample-size condition; C1 ceiling 35; C2 four distinct restrictions, growth lower bound 4, no shattering; threshold VC dimension 1; interval VC dimension 2; ray-union growth 2m and VC dimension 2; F1 sufficient sample sizes 393 and 72. The solution distinguishes uniform-deviation and consistent-realizable events correctly. C2 retains the online formulation rather than silently changing the question.

Week 4 checks: MC keys b/b/b/a; approximate ERM bound 0.058 including an unattained population infimum; sign calculation 3/8; SRM budgets (0.03,0.02,0.01), objectives (0.18,0.16,0.18), and class 2; theorem scope and ERM clause; invalid total weight 3/2 and repaired allocation; online E1 chain uses u at the selected hypothesis and the lower-direction radius at the comparator, yielding 0.040+0.010+0.030=0.080; F1 separates the valid fixed 500-class union from the invalid observed 12-vector shortcut. No missing online question or answer was found.

## Render inspection

Both selected solution PDFs have six pages. All pages were rendered with Poppler at a maximum dimension of 950 pixels and inspected. Week 3 pages 1,2,4,5,6 were additionally found pixel-identical to the inspected canonical renders; selected page 3 was separately inspected because of C2 wording. Week 4 selected pages 1–6 were all individually inspected. No clipping, overlapping text, broken displayed equation, or missing continuation was found. Some question/answer blocks cross page boundaries, but the continuations are present and legible. Original internal Week headers are retained, consistent with preserving existing PDF contents and changing public filenames only.

## Website preservation and link review

I inspected all 13 Markdown diffs. They change PDF links to Lecture names, add solution links for Lectures 3–5, change one public phrase from content week to content lecture, and update the home-page date. Topics, schedule dates, existing solution availability, tutorial notes, and other teaching content are retained.

Independent checks (`independent-checks.json`) confirm:

- All 35 existing PDFs are byte-identical to the downloaded published baseline at their original paths.
- All 35 new Lecture aliases for existing PDFs use the correct schedule mapping and are byte-identical to the baseline source PDF.
- No Markdown PDF link still targets a Week filename; old Week files remain available as compatibility URLs.
- All 496 relative HTML links checked in the built site resolve. The parent's broader build report records 638 internal links and no missing targets.
- Lectures 3, 4, and 5 have solution links on the home schedule, materials index, and their individual lecture pages.
- The final solution PDFs in both source and built output match the independently selected compatible PDFs byte-for-byte.

The package passes this bounded pre-publication review. Deployment success and live URL verification remain the publisher's final checks.
