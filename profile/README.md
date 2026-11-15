<p align="center"><img src="https://raw.githubusercontent.com/go-embedded-fortran/brand/main/social/go-embedded-fortran.png" alt="go-embedded-fortran" width="720"></p>

# go-embedded-fortran

🌐 **[Website](https://go-embedded-fortran.github.io)** · 📚 **[Documentation](https://go-embedded-fortran.github.io/docs/)** · 🗺️ **[Roadmap](https://github.com/go-scikit/roadmap)**

**Fortran in pure Go (`CGO_ENABLED=0`), for go-notebook cells.** It is meant to become a Fortran implementation embedded in Go programs and run in the browser through WebAssembly, backing the ` ```fortran ` cells of [go-notebook](https://github.com/go-notebook), as [go-embedded-c](https://github.com/go-embedded-c/c) backs its C cells.

**Status: in development.** Every figure below is from the [`fortran` README](https://github.com/go-embedded-fortran/fortran#readme) at v0.16.0.

## What is here

- **A front end in Go.** A lexer and parser (`syntax`, free and fixed form) and a semantic analyser (`sema`) that produces a typed tree.
- **An evaluator** (`eval`) that runs all 14 golden programs byte-identical to gfortran 15.2.0 (stdout, stderr and exit status).
- **An I/O runtime** (`rt`) ported from flang-rt: 71 096 of 71 135 differential cases against gfortran 15.2.0 are identical, and the 39 others are in documented classes.
- **An oracle harness** (`foracle`): gfortran 15.2.0 is only ever run as a program, never linked or ported.
- **A measured gate** (bib section 4.2) that decides the back end. First figures: verdict **A first**.

## Open defects, stated

- The evaluator's scalar loops are 8x to 108x behind gfortran -O2 ([#17](https://github.com/go-embedded-fortran/fortran/issues/17)).
- The gate's browser lane is not implemented ([#5](https://github.com/go-embedded-fortran/fortran/issues/5)), so the rule cannot pick A outright.

## Repositories

| Repo | What it is |
|------|------------|
| [**fortran**](https://github.com/go-embedded-fortran/fortran) | the implementation: front end, evaluator, I/O runtime, oracle harness and gate |
| [**docs**](https://github.com/go-embedded-fortran/docs) | the documentation site (Hugo + Hextra), served at [/docs/](https://go-embedded-fortran.github.io/docs/) |
| [**go-embedded-fortran.github.io**](https://github.com/go-embedded-fortran/go-embedded-fortran.github.io) | the landing page (Hugo) |
| [**brand**](https://github.com/go-embedded-fortran/brand) | logo, icons and social images |

The plan is the roadmap's bibliography, [`bib/fortran.md`](https://github.com/go-scikit/roadmap/blob/main/bib/fortran.md), in go-scikit/roadmap.
