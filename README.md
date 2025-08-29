mac_osx_emacs_keybindings
=========================


Installation
=========================

Copy DefaultKeyBinding.dict into your ~/Library/KeyBindings/ directory on any version of Mac OSX.


From the file
=========================

Additional keybindings for emacs emulation

Originally compiled by Jacob Rus.  Modified/embellished/customized by Aaron Cohen.

Sources:

  http://www.hcs.harvard.edu/%7Ejrus/Site/cocoa-text.html
  http://www.hcs.harvard.edu/%7Ejrus/Site/selectors.html

  https://developer.apple.com/library/mac/#documentation/Cocoa/Reference/ApplicationKit/Classes/NSResponder_Class/Reference/Reference.html

WARNING:

This file uses the Option key as a meta key.  This overrides the Mac OS keybindings for the option key, which produce common symbols and non-English letters.
To access the original binding of an Option combination, simply type Control-Q and the binding, and the original character will be output.
If that doesn't work on your platform, run this and you should be g2g:

defaults write -g NSQuotedKeystrokeBinding -string "^q"

NOTES:

We use cut:, copy:, paste: for C-w, M-w, C-y rather than deleteToMark:, selectToMark:, yank: for 2 reasons:

1. It permits copy/paste or cut/paste across applications

2. It permits an implementation of M-w that actually works consistently and correctly

To see in xml syntax which keybindings Mac OSX has already defined for you, run the following at a terminal prompt and then open ~/mac_key_bindings.dict -

plutil -convert xml1 /System/Library/Frameworks/AppKit.framework/Versions/C/Resources/StandardKeyBinding.dict -o ~/mac_key_bindings.dict

We deliberately do *not* repeat herein any keybindings already defined by the OS *unless* we override them.

To set up C-u to be the repeat count keybinding, run the following at a terminal prompt.
Be aware that if you do this *any* use of C-u (even within a sequence of keys) will eval to the repeat count method.

defaults write -g NSRepeatCountBinding -string "^u"

Finally, M-u and M-e are "dead keys" in Cocoa Text.  The hackaround to implement half of what is required below, by making the virtual keys F18 and F19 do what
 we want those keys to do.  Then, create a custom rule (under Complex Modifications) in Karabiner like so:

```
{
  "description": "Expose Option-e/u as F18/F19 for Emacs-style Meta bindings",
  "manipulators": [
        {
      "type": "basic",
      "from": {
        "key_code": "e",
        "modifiers": {
          "mandatory": [
            "option"
          ],
          "optional": [
            "any"
          ]
        }
      },
      "to": [
        {
          "key_code": "f18"
        }
      ]
    },
    {
      "type": "basic",
      "from": {
        "key_code": "u",
        "modifiers": {
          "mandatory": [
            "option"
          ],
          "optional": [
            "any"
          ]
        }
      },
      "to": [
        {
          "key_code": "f19"
        }
      ]
    }
  ]
}
```
