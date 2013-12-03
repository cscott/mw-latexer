# mw-latexer

[![Build Status][1]][2] [![dependency status][3]][4] [![dev dependency status][5]][6]

Converts mediawiki collection bundles (as generated by mw-bundler) to
beautiful PDFs (via [XeLaTeX][]).

[XeLaTeX]: https://en.wikipedia.org/wiki/XeTeX

## Installation

Node version 0.8 and 0.10 are tested to work.

Install the node package dependencies.
```
npm install
```

Install other system dependencies.
```
apt-get install texlive-xetex texlive-latex-recommended texlive-fonts-recommended latex-xcolor imagemagick librsvg2-bin unzip
```

Note that up-to-date LaTeX `hyperref` and `fontspec` packages are
required.  If your LaTeX installation is old, you can find recent
versions in `texdeps/`.

If you prefer, the `inkscape` package can be installed to do SVG->PDF
conversion in place of `rsvg-convert` (from the `librsvg2-bin` package).

## Generating bundles

You may wish to install the `mw-bundler` package to create bundles
from wikipedia articles.  The below text assumes that you have done
so; ignore the `mw-bundler` references if you have bundles from
some other source.

## Running

To generate a PDF named `out.pdf` from the `en` wikipedia article
"United States":
```
mw-bundler -o us.zip --prefix en "United States"
bin/mw-latexer -o out.pdf us.zip
```

For debugging, preserving the XeTeX output is often useful:
```
bin/mw-latexer -o out.tex us.zip && xelatex out.tex
```

For other options, see:
```
bin/mw-latexer --help
```

## License

GPLv2

(c) 2013 by C. Scott Ananian

[1]: https://travis-ci.org/cscott/mw-latexer.png
[2]: https://travis-ci.org/cscott/mw-latexer
[3]: https://david-dm.org/cscott/mw-latexer.png
[4]: https://david-dm.org/cscott/mw-latexer
[5]: https://david-dm.org/cscott/mw-latexer/dev-status.png
[6]: https://david-dm.org/cscott/mw-latexer#info=devDependencies
