# Extrernal Keyboard Layout for thumbs
Azerty-lafayette type keyboard for [my cheap Bluetooth keyboard](https://www.amazon.fr/gp/product/B08C4KWB5V/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1) for Android phones. No root needed. I chose that keyboard because its space key is small, and because its touchpad is below the keyboard which creates space for my wrists (useful to stabilize the keyboard on your own lap). The Neo2 layout added by this github project ensures that the two left and right keys around the space key, close to my thumbs, have this effect:

Alt Shift Space AltGr Control

I don't use keys ESC, 1, 6, 7, Y, B, BACKSPACE, and the arrows because they are too far from the rest position of my fingers. I type them with respectively AltGr+q, AltGr+Shift+i, AlgGr+Shift+v, AlgGr+Shift+f, AlgGr+u, AlgGr-n, AltGr-s, AltGr-h, AltGr-j, AltGr-k and AltGr-l. I type AltGr+i, AltGr+g, AltGr+f, AltGr+d and AltGr+Shift+d for the other frequent uses of these keys: &, -, è, | and `

AltGr+Shift on number keys mostly types the qwerty characters shown on the keyboard, useful when I am tired.

Warning, to this day I am the only user and this is the first time I am sharing this project, so please give feedbacks to help me.

My philosophy is that a the learning curve for an azerty user is manageable.

It think [this keyboard still available](https://www.amazon.fr/KIMISS-Chargeur-Ultraslim-Bluetooth-Touchpad/dp/B0C353T7J8) with a small space key is a clone of the keyboard I use, with the touchpad below the keyboard to be able to lay your wrists. This is ([an example of keyboard to avoid for confortable use](https://www.amazon.fr/Ovegna-Q9-rechargeable-R%C3%A9tro-%C3%A9clair%C3%A9e-Raspberry)).


To build it on vim I execute the noremap on next line, then in android-studio, I use File/Close project, "terminate process", reopen this thumb project, use "run", switch off then on my bluetooth keyboard.

The noremap is: noremap à :w<bar>!scp mol8_adb:thumb-external-keyboard-layouts/app/src/main/res/raw/keyboard_layout_neo2.kcm /data/data/com.termux/files/home/p/r/20231016.keyboard ; rsync -avz /data/data/com.termux/files/home/p/r/K/INFORMATIQUE/android/historiques/thumb-external-keyboard-layouts mol8_adb: ; cvs commit -m sauver<c-m> 

When the bluetooth keyboard is connected, you should got to Android settings/Language and keyboard/external keyboard/choose your current on screen keyboard/select the keyboard neo2.

I modified app/src/main/res/raw/keyboard_layout_neo2.kcm and app/src/main/res/values/strings.xml (last value keyboard_layouts_label appears in "Settings/General managment/Physical keyboard/Language and layout" provided a bluetooth keyboard is attached) In app/build.gradle and app/src/main/AndroidManifest.xml and app/src/main/java/varzan/extraKeyboardLayouts/InputDeviceReceiver.java, varzan.thumbExtrernalKeyboardLayouts should be different than the value for the last known working AndroidStudio installation.

Slash (keycode 53), just on right of [space key](https://www.amazon.fr/gp/product/B08C4KWB5V/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1), is turned into AltGr.
BackSlash (keycode 43), just on right of previous key, is turined into CTRL_RIGHT.
Windows (keycode 70), just on left of [space key](https://www.amazon.fr/gp/product/B08C4KWB5V/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1), is turned into SHIFT_RIGHT.
Alt (keycode not found) conveniently just on left of previous key.

CAPS_LOCK (keycode 58) is turned into PLUS.
SHIFT_LEFT (keycord 42) is turned into CAPS_LOCK.

The full map is on (the source code)[https://github.com/jidhub/thumb-external-keyboard-layouts/blob/master/app/src/main/res/raw/keyboard_layout_neo2.kcm#L159]

TODO:

- strip keyboards other than neo2 out of the project.

- make arrow work outside of tmux (my ~/.tmux.conf contains:

bind-key -n 0x2190 send-keys Left

bind-key -n 0x21d0 send-keys S-Left

bind-key -n 0x2191 send-keys Up

bind-key -n 0x21d1 send-keys S-Up

bind-key -n 0x2192 send-keys Right

bind-key -n 0x21d2 send-keys S-Right

bind-key -n 0x2193 send-keys Down

bind-key -n 0x21d3 send-keys S-Down)

- make AltGr Shift G work (I don't understand why it does not)

- build and push to fdroid (and learn how to do that)

- understand why after an Android Update, I have sometime to rechoose my keyboard with Android settings/Language and keyboard/external keyboard/choose your current on screen keyboard/select the keyboard neo2.

- correct "Android settings/Language and keyboard/external keyboard/choose your current on screen keyboard/select the keyboard neo2" by inserting the actual strings, not just the version I just typed from memory.

- AltGr typed for a key that has no "ralt" entry on app/src/main/res/raw/keyboard_layout_neo2.kcm opens a menu in [termux](https://f-droid.org/en/packages/com.termux/) and [nix-on-droid](https://f-droid.org/en/packages/com.termux.nix/).

- AltGr is not working at all while opening the app [bVNC Free](https://play.google.com/store/apps/details?id=com.iiordanov.freebVNC&hl=en&gl=US).

- AltGr Q does only escape in nix-on-droid.

- cleanup the duplicates definitions of keys A..Z in (comment of source code)[https://github.com/jidhub/thumb-external-keyboard-layouts/blob/master/app/src/main/res/raw/keyboard_layout_neo2.kcm#L94] which I used to find keycodes.

- understand how to uninstall this when installed by android-studio. I currently have 3 versions installed -_-.

- strip all changes I made in app/src/main/java/varzan/extraKeyboardLayouts/InputDeviceReceiver.java because I do not understand or remember what they do, and they seem useless, and I just found out they have been never integrated in git so oh well (they are in my CVS history though ;-).

- understand the warning on Android-Studio macOS 2022.3.1p2 gradle 7.3.1: error running 'app': Unable to determine activity name. The project works for me despite this warning.

- https://github.com/jidhub/thumb-external-keyboard-layouts/blob/master/screen1.jpg and other screenshots by screens showing an equivalent to https://en.wikipedia.org/wiki/File:KB_French_B%C3%89PO-NF_Z71-300.svg , and before that, learn how to make these images.

If you found this useful, you may [buy a drink to the project I forked](https://paypal.me/CalinDarie?locale.x=en_US) or ask for the Ergo-L community on Discord.
