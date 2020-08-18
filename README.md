# Latex Report Template

## What's this about ?

This template takes advantage of `latexmk` and `make` to get a better LaTeX experience when writing big documents. All the file dependencies are handled by `make` (this allows for multi-threaded compilation), and everything can be compiled at once easily.

This template makes it possible to build chapters as standalone latex documents

## Available targets

When you use `make` (with no specified target), `make` will show you an exhaustive list of everything you can build or do. It looks like this

```
:: latex-template ::

Example:
  | make all -j8  # Build everything using 8 threads
  | make main  # Build the main target
  | make target/main.pdf  # Same as: make main

List of PHONY targets:
  all                    Build everything
  changemainfilename     Change the main document's base name
  clean                  Delete compiled documents and latex-generated files
  figures                Build every figure in src/figures/
  help                   Print available targets
  main                   Build the main target
  newchapter             Make a new chapter
Main target:
  target/main.pdf
List of figures:
  ...
List of chapters:
  ...
```

There are two PHONY targets that are especially relevant to this template: `changemainfilename` and `newchapter`. By default, your report's entrypoint will be the file `main.tex`, with the associated target `target/main.pdf`. You will probably want to change this to a more relevant file name, which can be accomplished easily using `make changemainfilename`.

When you want to start a new chapter, use `make newchapter` and a prompt will let you type in the filename used for that chapter and the actual title of that chapter. The relevant files are created using the chapter templates in `.latex_templates/` (`FN` will be replaced with the filename, `CN` with the chapter's title).

