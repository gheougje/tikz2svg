# tikz2svg

## Prerequisites

* To build and run this project, you need Node.js &geq;14.x.
* Make sure `pdflatex` and `pdf2svg` are available from the command line.

## To use

* Create `preamble.tex` with the following content.
    ``` latex
    \documentclass[10pt,crop,tikz]{standalone}
    \usepackage{tikz-cd}
    \usepackage{amsmath}
    \usepackage{amsfonts}
    \usepackage{mathrsfs}
    \begin{document}
    ```
    Then run
    ``` bash
    pdflatex -ini "&pdflatex preamble.tex\dump"
    ```
    This generates a precompile header file `preamble.fmt`. Copy this file to the workspace folder.
* Run `yarn`, then `yarn build`, then `yarn start`.
* Send a POST request to `127.0.0.1:9292`, with POST parameters in body of JSON format.
HTTPHEADER should be 'Content-type: application/json'.
 POST parameters are `type` , `option` and `tex`. `type` can only be either `tikzpicture` or `tikzcd`. `tex` is the LaTeX code after `\begin{tikzpicture}` and before `\end{tikzpicture}`.
 `option` is the argument of tikzpicture/tikzcd environment.
