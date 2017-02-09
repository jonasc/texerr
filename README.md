# TeXerr
Run a LaTeX binary and filter output for relevant information.

## About this program

This program aims to middleman between the user and their LaTeX program, e.g. `pdflatex`.
Its main goal is to read the standard output of LaTeX programs and format it in a nice and more readable way.

## How to use

TeXerr can be used by simply writing `texerr ` in front of every call of `pdflatex`, `xelatex`, etc.
It works by executing everything given as command line arguments and reading the output of that command.
The output is filtered and then formatted to be more readable.
One usage example could be:
```
texerr pdflatex -output-directory=build -recorder report.tex
```

This makes it also very easy to use, e.g., with [latexmk](http://ctan.org/pkg/latexmk).
Just put the following into your `.latexmkrc`:
```
$pdflatex = "max_print_line=1000000 texerr pdflatex %O %S";
```
Please note from this example two things:
1. Environment variables need to be set before calling TeXerr and will be passed through.
2. You *should* definitively set `max_print_line` to a high value, otherwise the heuristics and matchings done by TeXerr might fail.

## Roadmap

There are several things on the roadmap:
- [ ] More warnings / errors / notices that can be highlighted.
      If you encounter specific messages you would like to include, please do not hesitate to open an [issue](https://github.com/jonasc/texerr/issues) or even submit a [pull request](https://github.com/jonasc/texerr/pulls).
      Please include relevant information to your best ability, such as the relevant package, part of the LaTeX output, and a minimal example which produces this output.
- [ ] Make it more modular:
      This could mean having a subdirectory with python files, each containing the specific patterns and actions.
- [ ] Different color styles.
- [ ] Tests.
      I still need to think how they should look like and what they should actually test.
