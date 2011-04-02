Tedist is a simple Python script for taking your [TextExpander][2] snippet groups and putting them in a form suitable for inclusion in the [TE-Snippets][1] community site.

Many people who use TextExpander regularly have a naming convention they use with all their snippets. My snippets, for example, always start with a semicolon. Brett Terpstra's always start with a pair of commas. The idea is to use a prefix that's both easy to type—so it takes little effort to use—and will never show up in the course of your normal writing or programming—so your snippets don't expand accidentally.

The TE-Snippets site will have a collection of snippet libraries that can be customized to fit whatever prefix you like. To do that, the libraries are stored on the site in a special form, called the `.tedist` form. It's almost the same as the `.textexpander` file that TextExpander creates when you "Save a Copy" of a group of snippets. The difference is that the `.tedist` file has the special code `[[PREFIX]]` at the front of all the abbreviations. When a user downloads the library, that `[[PREFIX]]` is replaced with the user's prefix of choice.

The purpose of the tedist script is to read in a normal `.textexpander` file and generate a new `.tedist` file for upload to the TE-Snippets site. It takes two arguments:

1. The name of the `.textexpander` file to convert.
2. The prefix used in the `.textexpander` file.

For safety on the Unix command line, you should probably enclose the prefix in single quotes.

Thus, to prepare my Symbols snippet library for TE-Snippets, I'd run this,

    tedist Symbols.textexpander ';'

and I'd get a new `Symbols.tedist` in the same directory.

If you want to change more than just the prefix, run `reabbrev`. It loops through all the snippets in the given file and allows you to change the abbreviation of each one. A session would look like this:

    reabbrev Symbols.textexpander 
    Label: ½
    Abbreviation [;1/2]: 

    Label: ¼
    Abbreviation [;1/4]: 1//4

    Label: ⅛
    Abbreviation [;1/8]: 1//8

    Label: ¾
    Abbreviation [;3/4]: 3//4

and so on. The current abbreviation is given in square brackets. If you just hit the return key, the current abbreviation is retained; if you type anything else (and then hit the return key), that will be the new abbreviation. The new library will *not* overwrite the old one; it will be saved with the same name, but with a "-2" appended. In the example above, the new file will be "Symbols-2.textexpander."


[1]: http://te-snippets.com/
[2]: http://smilesoftware.com/TextExpander/
