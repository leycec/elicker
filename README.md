elicker
=======

_elicker_ :: sanitary wrapper for eLyXer, optimizing output HTML to real-world end use (e.g., EPUB2 ebook readers)

## Installation

`elicker` is a single `zsh` script and hence (_usually_!) trivially installed.

### Manual

`elicker` requires the following runtime dependencies:

* [LyX](http://www.lyx.org) >= 2.0.0.
* [eLyXer](http://alexfernandez.github.io/elyxer) >= 1.2.5.
* [zsh](http://www.zsh.org) >= 4.3.0.

After installing such dependencies, simply copy `elicker` to a directory in the `${PATH}` of the current user (e.g., `/usr/local/bin`). **"[Hey, and away we go.](http://www.youtube.com/watch?v=SZuutY1W0SY)"**

## Usage

```
elicker [OPTIONS]... SOURCE_DIRECTORY SOURCE_LYX_FILE TARGET_HTML_FILE
```

`elicker` _is_ runnable directly from the command line, but mostly intended to be run from within LyX. To do so, edit the `Converter:` field in LyX's _Tools_ → _Preferences_ → _File Handling_ → _Converters_ dialog to read:

```
elicker --title "My Book Title" $$r $$i $$o
```

Since neither `elicker` or eLyXer are capable of automatically copying the title from input LyX documents to output HTML files, consider explicitly passing such title as above on a per-document basis.

As an eLyXer sanitizer, `elicker` supports all options and arguments supported by eLyXer as well as the following `elicker`-specific options:

* `--end-use END-USE`, optimize output HTML to the specified real-world end use, where `END-USE` is one of the following strings (defaulting to `ebook-quality-high` if unspecified):
  * `website`, producing high-quality dynamic content for publication on websites.
  * `ebook-quality-high`, producing high-quality dynamic content for use in EPUB3 and/or KF8 ebooks.
  * `ebook-quality-low`, producing low-quality static content for use in EPUB2 and/or MOBI ebooks.

As example:

```
elicker --title "My Book Title" --end-use ebook-quality-low $$r $$i $$o
```

## License

`elicker` adheres to a conventional [GPLv3 license](http://gplv3.fsf.org). See LICENSE for details.
