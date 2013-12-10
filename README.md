# mw-ocg-latexer
[![NPM][NPM1]][NPM2]

[![Build Status][1]][2] [![dependency status][3]][4] [![dev dependency status][5]][6]

Converts mediawiki collection bundles (as generated by [mw-ocg-bundler]) to
beautiful PDFs (via [XeLaTeX]).

## Installation

Node version 0.8 and 0.10 are tested to work.

Install the node package dependencies.
```
npm install
```

Install other system dependencies.
```
apt-get install texlive-xetex texlive-latex-recommended texlive-latex-extra \
                texlive-fonts-recommended texlive-fonts-extra \
                fonts-hosny-amiri fonts-nakula fonts-nafees fonts-smc \
                texlive-lang-all latex-xcolor imagemagick librsvg2-bin unzip
```

Note that up-to-date LaTeX `hyperref` and `fontspec` packages are
required.  If your LaTeX installation is old, you can find recent
versions of some of the necessary packages in `texdeps/`, but it's
best to use an up-to-date TeXlive distribution.

If you prefer, the `inkscape` package can be installed to do SVG->PDF
conversion in place of `rsvg-convert` (from the `librsvg2-bin` package).

In older versions of Ubuntu, the Nakula font was provided by the
`ttf-devanagari-fonts` package, instead of `fonts-nakula`.
In some cases you'll need to manually install the
`texlive-generic-extra` package as well.

## Generating bundles

You may wish to install the [mw-ocg-bundler] npm package to create bundles
from wikipedia articles.  The below text assumes that you have done
so; ignore the `mw-ocg-bundler` references if you have bundles from
some other source.

## Running

To generate a PDF named `out.pdf` from the `en` wikipedia article
"United States":
```
mw-ocg-bundler -o us.zip --prefix en "United States"
bin/mw-ocg-latexer -o out.pdf us.zip
```

For debugging, preserving the XeTeX output is often useful:
```
bin/mw-ocg-latexer -o out.tex us.zip && xelatex out.tex
```

For other options, see:
```
bin/mw-ocg-latexer --help
```

## License

GPLv2

(c) 2013 by C. Scott Ananian

[mw-ocg-bundler]: https://github.com/wikimedia/mediawiki-extensions-Collection-OfflineContentGenerator-bundler
[XeLaTeX]: https://en.wikipedia.org/wiki/XeTeX

[NPM1]: https://nodei.co/npm/mw-ocg-latexer.png
[NPM2]: https://nodei.co/npm/mw-ocg-latexer/

[1]: https://travis-ci.org/cscott/mw-latexer.png
[2]: https://travis-ci.org/cscott/mw-latexer
[3]: https://david-dm.org/wikimedia/mediawiki-extensions-Collection-OfflineContentGenerator-latex_renderer.png
[4]: https://david-dm.org/wikimedia/mediawiki-extensions-Collection-OfflineContentGenerator-latex_renderer
[5]: https://david-dm.org/wikimedia/mediawiki-extensions-Collection-OfflineContentGenerator-latex_renderer/dev-status.png
[6]: https://david-dm.org/wikimedia/mediawiki-extensions-Collection-OfflineContentGenerator-latex_renderer#info=devDependencies
