<div align="center">
  <h1>Die<sup>&chi;</sup></h1>
  <p>A LaTex paper template for security and machine learning conferences</p>
  <p align="center">
    <a href="https://hwiwonl.ee/" style="text-decoration: none;">Hwiwon Lee</a>
  </p>
</div>
<br>

> [!WARNING]
> This template is in active development. Stay tuned for more updates!

## Prerequisites

> [!CAUTION]
> This template is not tested on Windows. Please use WSL if you are using Windows.

- LaTex (`sudo apt install texlive-full` on Ubuntu / [Install TeX Live](https://www.tug.org/mactex/) on macOS)
- Python 3.x
- pygmentize (`pip install pygments`)
- [Inkscape](https://inkscape.org/) (for converting figures to PDF)

## Supported Templates
### Machine Learning Conferences
- [x] ACL
- [x] NeurIPS
- [x] ICLR
- [x] ICML
- [x] COLM

### Security Conferences
- [x] CCS
- [x] NDSS
- [x] USENIX (Security)
- [x] NDSS

## Usage
You can uncomment the desired template in `p.tex`. For example, to use the NeurIPS template, uncomment the following line:
```tex
%%%%%%%%%%%
% NeurIPS %
%%%%%%%%%%%
\documentclass{article}
\usepackage{sty/neurips/template}
% \usepackage[final]{sty/neurips/template} % Uncomment for camera-ready version, but NOT for submission.
\neuripstrue
```

> [!WARNING]
> Only one template may be compiled at a time. Please ensure that only one conditional (if) statement is set to true.

## Build

```bash
make
```

> [!TIP]
> If you are using vscode, install [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) to get a better LaTeX editing experience. In that case, you need to customize the build action in `settings.json` as follows:

```json
{ // Bibtex formatter
    "latex-workshop.bibtex-fields.sort.enabled": true,
    // Enable LaTeX formatting using latexindent (instead of "none")
    "latex-workshop.formatting.latex": "tex-fmt",
    "latex-workshop.formatting.tex-fmt.path": "tex-fmt",
    // (Optional) Format your LaTeX document on save
    "editor.formatOnSave": true,
    // (Optional) Specify your PDF viewer mode for LaTeX Workshop
    "latex-workshop.view.pdf.viewer": "tab",
    // Additional editor settings (optional)
    // "files.autoSave": "afterDelay",
    // "files.autoSaveDelay": 1000,
    "latex-workshop.latex.autoBuild.run": "onSave",
    // Define the output directory 
    "latex-workshop.latex.outDir": "%DIR%",
    // Set a reasonable timeout for commands
    "latex-workshop.latex.build.timeout": 60000,
    "latex-workshop.message.log.show": true,
    // Add -shell-escape flag for minted package
    "latex-workshop.latex.tools": [
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-shell-escape",
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "-min-crossrefs=99",
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "pdflatex -> bibtex -> pdflatex -> pdflatex",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        },
        {
            "name": "pdflatex",
            "tools": [
                "pdflatex"
            ]
        }
    ]
}
```

## Tips on adding a new template

1. Create a new folder in `sty/[CONFERENCE]` with the following files:
    - `template.sty`
    - `template.bst`
2. If the template has a custom `fancyhdr` style, change `\RequirePackage[fancyhdr]` to `\RequirePackage{./sty/[CONFERENCE]/fancyhdr}` in `sty/[CONFERENCE]/template.sty`.

> [!TIP]
> You can migrate this template to Overleaf by uploading the whole repository to Overleaf except for the `rev.tex` file.

## Acknowledgment

This template is an extension of an awesome open-source project [die](https://github.com/tsgates/die).