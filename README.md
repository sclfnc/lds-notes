# Laboratory of Data Science: Lecture Notes

Typeset lecture notes for **Laboratory of Data Science**, University of Pisa,
academic year 2025/26. The notes cover the business-intelligence pipeline end to
end: BI architectures, data access to files and relational databases, Microsoft
SQL Server, ETL with SSIS, data warehousing and OLAP, and SQL Server Analysis
Services with MDX. Worked exercises and a practical project guide are integrated
into the sections they belong to, next to the theory they exercise.

> ⚠️ **Disclaimer.** Derived from the *Laboratory of Data Science* course
> materials (Academic Year 2025/2026), MSc in Data Science & Business
> Informatics, University of Pisa.
>
> These notes are open educational content created by a student. They are **not
> an academic source** and may contain inaccuracies. You may freely share,
> modify, and reuse this material for educational and non-commercial purposes
> with appropriate attribution. The content is my personal interpretation of the
> professor's course materials and should not replace official teaching
> resources. I assume no responsibility for any errors or misinterpretations.
>
> These notes were produced with an **AI-in-the-middle** workflow: a first human
> pass, then **Claude Code** to support formulation, understanding, and
> rewriting, followed by a final human review.
>
> If you find errors, have suggestions, or spot unintentionally included
> copyrighted material (which I will promptly remove on notification), contact me
> at `sclfnc@proton.me`.

## Layout

- `main.tex`: entry point, in the folder root; identical across the whole
  notes collection (it only loads the shared preamble and the course file).
- `src/housestyle.tex`, shared house style: geometry, colors, section and ToC
  formatting, running heads, and the math environments (theorem, definition, …).
- `src/common-preamble.tex`: the shared package set, identical across courses.
- `src/course.tex`, everything specific to this course: title metadata, the
  compact SQL and MDX `listings` setup (SQL Server keywords, window and grouping
  functions, MDX query and navigation functions), the
  `notebox`/`examplebox`/`theorybox` frames, `hyperref`, and the
  `\input{sec/...}` list.
- `sec/NN.tex`: section files (the body of the notes), numbered `02`…`08` and
  pulled in by `course.tex`.
- `img/`: the few raster figures (BI architecture, data cube, linked server, …);
  most diagrams are native TikZ / typeset.
- No bibliography: the notes carry no `.bib` and use no `\cite`.
- `lds-notes.pdf`: the compiled notes, in the folder root.

There is no separate appendix. Earlier drafts kept a worked-exercises appendix and
an operational project guide as standalone files; both are now dissolved into the
teaching sections, so the exercises sit beside the theory they test (ETL and SSAS)
and the project guide beside the tools it documents (Python access, the warehouse
schema, SSIS, SSAS, Power BI).

## Build

Build from the folder root:

```bash
latexmk main.tex
```

`latexmk` runs pdflatex as many times as needed (a second pass resolves the ToC
and cross-references) and writes the compiled `lds-notes.pdf` and all auxiliary
files (`.aux`, `.log`, `.toc`, `.bcf`, `.bbl`, …) to the folder root; the
auxiliaries are git-ignored (listed in `.gitignore`). A `.latexmkrc` in the
folder sets this up, naming the output after the folder via `$jobname`. To do it
by hand instead:

```bash
pdflatex -jobname=lds-notes main && pdflatex -jobname=lds-notes main
```

Requires a standard TeX Live installation. Alternatively, upload the folder to
[Overleaf](https://www.overleaf.com) (New Project → Upload Project), set
`main.tex` as the main document, and compile.

## Credits

Written by **Francesco Secoli**, revised with the help of
[Claude Code](https://claude.com/claude-code): the course slides and lectures
were transcribed and refined into LaTeX, then reworked into standalone notes.
Based on the *Laboratory of Data Science* course (a.y. 2025/26), University of
Pisa. Contributions welcome: open an issue or a pull request.

## Contents

The notes are seven sections, in reading order:

| # | Section | Topics |
|---|---------|--------|
| 1 | Business Intelligence Architectures | Data sources, ETL, data warehouse, warehouse servers, mid-tier servers, front-end applications |
| 2 | Data Access: Files | File location (local, distributed, remote protocols); tabular formats (CSV, FLV, ARFF); JSON; XML and XRFF |
| 3 | Relational Database Access | Client-server connection, ODBC, Python DB-API, pyodbc, prepared statements and SQL-injection prevention, type mapping, metadata access; Python project-setup guide (structure, config, read/clean/cache patterns) |
| 4 | Microsoft SQL Server | Editions and licensing, suite architecture, system databases, object naming and resolution, import/export (BULK INSERT, FOR XML), linked servers and distributed queries, connection strings |
| 5 | ETL: Extract, Transform and Load | ETL phases and orchestration, SQL Server Integration Services (control flow, data flow, type system), deployment and execution, Change Data Capture, Slowly Changing Dimensions; worked ETL/SSIS exercises, a date-dimension case study, and an SSIS quick reference |
| 6 | Data Warehousing and OLAP | Dimensional modeling (fact/dimension tables, star and snowflake schemas), row vs column storage, the data cube and navigation operations, cuboids in SQL (CUBE, ROLLUP, GROUPING SETS, GROUPING()), MOLAP/ROLAP/HOLAP; the project warehouse schema (DDL and load order) |
| 7 | SQL Server Analysis Services | SSAS architecture and BI semantic model, multidimensional project development, OLAP storage modes and proactive caching, KPIs/perspectives/security, MDX queries (tuples, sets, axes, navigation, calculated members), Power BI on the cube; worked SQL/MDX exercises, an SSAS checklist, and an MDX pattern reference |
