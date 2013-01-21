mac_osx_emacs_keybindings
=========================

Drop DefaultKeyBinding.dict in ~/Library/KeyBindings/ on Mac OSX.

From the file:

=========================

Additional keybindings for emacs emulation

Originally compiled by Jacob Rus.  Modified/embellished/customized by Aaron Cohen.

Sources:
  http://www.hcs.harvard.edu/%7Ejrus/Site/cocoa-text.html
  http://www.hcs.harvard.edu/%7Ejrus/Site/selectors.html

WARNING:

This file uses the Option key as a meta key.  This has the side-effect of overriding Mac OS keybindings for the option key, which generally
produce common symbols and non-English letters.

NOTES:

We use cut:, copy:, paste: rather than deleteToMark:, selectToMark:, yank: because selectToMark only highlights; it doesn't copy.
We thus lose the kill ring, but gain a working ~w.  (That is, attempting to bind ~w to ( "deleteToMark:", "yank:" ) removes formatting,
 and repeated use of this keybinding hoses the kill ring.)
*However*, this in turn breaks use of "...AndModifySelection:" bindings *unless* one sets the mark before commencing a new use of those bindings.
Catch-22.

To see in xml syntax which keybindings Mac OSX has already defined for you, run the following at a terminal prompt and then open ~/mac_key_bindings.dict (: in emacs :) -

plutil -convert xml1 /System/Library/Frameworks/AppKit.framework/Versions/C/Resources/StandardKeyBinding.dict -o ~/mac_key_bindings.dict

We deliberately do *not* repeat herein any keybindings already defined by the OS *unless* we override them.

To set up C-u to be the repeat count keybinding, run the following at a terminal prompt.
Be aware that if you do this *any* use of C-u (even within a sequence of keys) will eval to the repeat count method.

defaults write -g NSRepeatCountBinding -string "^u"

More info about the most common selectors (i.e. where most of the below comes from) may be found here:
  https://developer.apple.com/library/mac/#documentation/Cocoa/Reference/ApplicationKit/Classes/NSResponder_Class/Reference/Reference.html

======================