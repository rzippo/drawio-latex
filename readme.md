# A LaTeX package for [draw.io](https://www.diagrams.net/) diagrams

This package can be used to directly include `.drawio` figures in your LaTeX documents.

Its main advantage is the improved workflow, which enables you to modify your figures and re-build your document without the tedious step of exporting manually.

## Requirements

You need the `draw.io` desktop app installed and callable as `drawio`, on Linux, or `draw.io.exe`, on Windows.

> You can test this running `drawio --help`. Note that you need a graphical environment, or at least use `xvfb`, as in [this issue](https://github.com/jgraph/drawio-desktop/issues/146).

## Usage

In the preamble:
```latex
\usepackage{drawio}
```

Assuming you have `figure.drawio`, you can then include it via

```latex
\includediagram{figure}
```

The command will call `drawio` to export the diagram as `figure.pdf`, and then use `includegraphics` to include the latter.

> All options given to `includediagram` will be passed to `includegraphics`. It thus behaves like a transparent wrapper that adds support for `.drawio` files.

Note that, on subsequent builds, `drawio` is called again only if `figure.drawio` is newer than `figure.pdf`.

## To remove it before submission

In many cases, like to submit to publications which use their own LaTeX environments, you cannot use this package in your final document (as the `drawio` command will not be available).

However, it is still useful to improve workflow up to final version, and it's easy to remove as a last step:

* build your final document to ensure all `.drawio` files have been exported to `.pdf`
* comment out the preamble call
* find-and-replace `includediagram` with `includegraphics`

You can then submit the modified document with the `.pdf` figures. 