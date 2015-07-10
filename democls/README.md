# democls --- model dtx file

## Description
`democls.dtx` is based on [Joseph Wright's model `dtx`
file](http://www.texdev.net/2009/10/06/a-model-dtx-file/) with some
modifications made to suit my tastes. In particular, I find it helpful to
include detailed installation instructions by default, to use the `gitinfo2`
package, and to generally package things with GitHub distribution in
mind. Being class-targeted, this file differs more significantly from Wright's
original than `demopkg.dtx`.

Class usage details should be covered by `democls.pdf`.

## Installation
Run

```
$ pdflatex democls.dtx
```

to generate the `.ins`, `.cls`, `.pdf`, and `example.tex` files. Because of the
difficulty usually involved in providing examples of class macros and
environments within the class documentation, a separate file, `example.tex` is
needed, and `pdflatex` should be called on it if you wish to see how it
looks.

In order to properly generate the documentation's change history and index, run

```
$ makeindex -s gind.ist democls
$ makeindex -s gglo.ist -o democls.gls democls.glo
$ pdflatex democls.dtx
$ pdflatex democls.dtx
```

(You TeX environment may take care of this for you. I have vague recollections
of TeXShop not requiring me to manually run `makeindex`, but using Emacs AUCTeX
seems to require manual `makeindex`ing whether I run `C-c C-c latexmk` or `C-c
C-c LaTeX`.)

Finally, to use the generated `.cls` file, move it to the appropriate location
for your TeX distribution. Perhaps the easiest way to do this is by running

```
$ mv democls.cls $(kpsewhich -var-value=TEXMFHOME)/tex/latex
```

although if you're looking to make the file available to all users on a Unix
device, you're probably better off setting
`/usr/local/texlive/texmf-local/tex/latex` as the target directory (and then
running

```
# texhash
```

To ensure that installation has succeeded, run

```
$ kpsewhich democls.cls
```

and if the output is a path to the file, you're golden.
