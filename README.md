# Honor-Thesis
My Honor Thesis in Graph Theory at [Wheaton College](https://wheatoncollege.edu/)
[department of mathematics](https://wheatoncollege.edu/academics/departments/mathematics-computer-science/),
under supervising of [Professor Rochelle (Shelly) Leibowitz](https://wheatoncollege.edu/academics/faculty-directory/rochelle-shelly-leibowitz/).

To read my thesis click [here](https://github.com/chantisnake/Honor-Thesis/blob/master/main.pdf);
to download my thesis click [here](https://github.com/chantisnake/Honor-Thesis/raw/master/main.pdf)

## Compile
I personally use `miktex`, `latexmk` (with `strawberry perl`) to build my document.

On Windows, you can install all the build tools using [chocolatey](https://chocolatey.org/):
```console
choco install miktex strawberryperl
```

You can use the following command to compile this document
```console
latexmk -lualatex main.tex
```

Notice, `lualatex` is required to produce all the graphs in this paper.
If you remove dependency to following package:
```latex
% for graphics
\usepackage{tikz}
\usetikzlibrary[graphs, graphdrawing, graphs.standard]
\usegdlibrary{circular, layered, trees}
```
You may be able to compile this document using `xelatex` or `pdflatex`.
However, I recommend you to use `xelatex` or `lualatex` to compile your documents.

## Development Environment
I uses [`vscode`](https://github.com/Microsoft/vscode) with [`LaTeX-Workshop`](https://github.com/James-Yu/LaTeX-Workshop) to build my documents.

My `LaTeX-WorkShop` set up is like this:
```json
// Latex
// setup the build tool
"latex-workshop.latex.tools": [
  {
    "command": "latexmk",
    "args": [
      "-synctex=1",
      "-interaction=nonstopmode",
      "-file-line-error",
      "-lualatex",
      "-auxdir=./aux_file/",
      "main.tex"
    ],
    "name": "Step 1: latexmk"
  }
],
"latex-workshop.latex.recipes": [
  {
    "name": "toolchain",
    "tools": [
      "Step 1: latexmk"
    ]
  }
],
// enable the checker
"latex-workshop.chktex.enabled": true,
// set the viewer
"latex-workshop.view.pdf.viewer": "tab",
"latex-workshop.view.pdf.external.command": {
  "command": "SumatraPDF.exe",
  "args": [
    "-inverse-search",
    "code.cmd -g %f:%l",
    "%PDF%",
  ]
},
// do not build on save
// annoying when writing large document
"latex-workshop.latex.autoBuild.onSave.enabled": false,
```

Notice, you need to install `synctex` to use the `synctex`
feature in  [`LaTeX-Workshop`](https://github.com/James-Yu/LaTeX-Workshop).
See https://github.com/James-Yu/LaTeX-Workshop#requirements.
You can install `synctex` on windows using [chocolatey](https://chocolatey.org/):
```console
choco install synctex
```

## Disclaimer

All the instruction may not be up to date.
if you encounter any difficulty building this document,
please create a issue.
I will try my best to provide a solution to your question.

## Licenses

The code uses [GPL v3.0](https://www.gnu.org/licenses/gpl.html)
and the content uses [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
