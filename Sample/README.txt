First of all - Long Live The Queen is copyright 2012-2015 Hanako Games.

This is a prerelease of the translation support data.  It, too, is copyright
2012-2015 Hanako Games; the exact license and distribution terms have not
yet been finalized.

To use this:
rename game/translations/sample/ to game/translations/(ISO code for
your language).  The reason for using ISO codes is that future versions
of LLtQ may be able to automatically select the right language for a
player.  Put game/translations/sample/ in the game/translations/ directory
of an existing Long Live The Queen install.  (1.2.19 or higher; it may
partially work with older versions.)

In the translations folder:

All text files are UTF-8 Unicode.

        There are a handful of functions which return natural language
descriptions of quantities: readable_number_small, land_military_desc,
barracks_report, and readable_number.  These functions are all defined
in prettyprint.rpy, so you can override them for your own language.
When they aren't replaced, the default behaviour will be to stringify
the number.  prettyprint.rpyc is simply the compiled version of
prettyprint.rpy.

'name' contains the name of your language.  That should be in the language
you're translating to, e.g. 'Deutsch' or 'Español'.

'strings' is a list of strings and translations, with the English version
first and the translated version second.  The translation code will always
translate a given English string into the same equivalent string in your
native language; if there are places where you need to have the same line
be translated two different ways in different places, contact me so I can
figure out how best to support it.  Lines beginning with # are comments and
are ignored.

So, for example, the sample file entry:
Elodie, Crown Princess
3LOD13, CROWN PR1NC3SS
tells the game to translate Elodie's name into all-caps l33tsp34k.

'keyboard' is the visible keyboard that will show up when you tell the game
to 'show keyboard' while saving.

The ui/ and sidebar/ directories contain images that will replace the default
images in the game.  Original, layered versions of the graphics are in the 
graphics/ folder.

You can safely ignore mergestrings.pl.

Some strings start with something like {tag=elodie, to julianna}.  This
is to allow phrases which are the same in English to have context-appropriate
translations in other languages.

When you're writing a translation file, you probably want to use the debugger
to set persistent.log_untranslated=True.  That will cause the game to log
all missing translations to translation-debugging.log, and will display an
'***' in front of any string that it failed to find translations for, or
an '*~*' in front of any string that it used an inexact translation for.

If the game can't find an exact translation for a string, it will check
to see if it has any inexact translations - for example, if your translation
file contains only:

{tag=elodie, debugging}Test.
Ŧēsŧ·

Then 'Test.' and '{tag=nonexistent}Test.' should also translate to 'Ŧēsŧ·' (Or
'*~*Ŧēsŧ·' if debugging is on.)
