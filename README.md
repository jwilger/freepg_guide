# FReePG Guide #

This repository contains the source files for the **FReePG Guide**, a guide to
running and playing in a simple, table-top role-playing game suitable for both
young children and anyone who is still a child at heart.

## Downloading the Guidebook ##

Pre-compiled versions of the FReePG Guide are available from the 
[downloads page][Downloads]. Both official releases and occasional 
development snapshots are available in PDF and EPUB formats.

## Generating the Guidebook ##

Although the text-based source is written in [Markdown][Markdown] format and
should be easy enough to read as-is, you can also create a nicely formatted
versions of the guidebook by running `rake {format}` (where {format} is one of
the supported conversion formats).

The updating and printing is managed by [Rake][Rake], so both it and
[Ruby][Ruby] ~> 1.9.3 are required.

The conversion from Markdown is done by [pandoc][pandoc]. On OSX systems 
with [Homebrew][Homebrew], you can install pandoc with `brew install 
pandoc`.

### Supported Formats ###

Although pandoc supports conversion to numerous formats, only the 
following formats have been tested with this guide and are supported by 
the included Rake tasks:

* PDF (`rake pdf`)

* EPUB (`rake epub`)

To generate the guide in all supported formats, run `rake all`.

### PDF Version ###

In order for pandoc to create PDF files, you need a working LaTeX 
installation (in particular, `pdflatex` must be on your PATH). On OSX 
machines, you can get this from [MacTex][MacTex] (note that you will 
have to add `/usr/texbin` to your `$PATH`.)

[Markdown]: http://johnmacfarlane.net/pandoc/demo/example9/pandocs-markdown.html "Pandoc's Markdown Format"

[pandoc]: http://johnmacfarlane.net/pandoc

[Rake]: http://rake.rubyforge.org

[Ruby]: http://ruby-lang.org

[MacTex]: http://www.tug.org/mactex/index.html

[Homebrew]: http://mxcl.github.com/homebrew/

[Downloads]: https://github.com/jwilger/freepg_guide/downloads
