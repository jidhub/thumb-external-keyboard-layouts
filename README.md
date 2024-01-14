# Extra Physical Keyboard Layouts
## Development on pause until September 2024
Azerty-lafayette type keyboard for [my Bluetooth keyboard](https://www.amazon.fr/gp/product/B08C4KWB5V/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1) for Android phones. No root needed.

Warning, to this day I am the only user and this is the first time I am sharing this project, so please give feedbacks to help me.

To build it on vim I execute the noremap on next line, then in android-studio, I use File/Close project, "terminate process", reopen this thumb project, use "run", switch off then on my bluetooth keyboard.
The noremap is: noremap à :w<bar>!scp mol8_adb:thumb-external-keyboard-layouts/app/src/main/res/raw/keyboard_layout_neo2.kcm /data/data/com.termux/files/home/p/r/20231016.keyboard ; rsync -avz /data/data/com.termux/files/home/p/r/K/INFORMATIQUE/android/historiques/thumb-external-keyboard-layouts mol8_adb: ; cvs commit -m sauver<c-m> 
# This works despite this warning on Android-Studio macOS 2022.3.1p2 gradle 7.3.1: error running 'app': Unable to determine activity name

When the bluetooth keyboard is connected, you should got to Android settings/Language and keyboard/external keyboard/choose your current on screen keyboard/select the keyboard neo2.

I modified app/src/main/res/raw/keyboard_layout_neo2.kcm and app/src/main/res/values/strings.xml (last value keyboard_layouts_label appears in "Settings/General managment/Physical keyboard/Language and layout" provided a bluetooth keyboard is attached)
In app/build.gradle and app/src/main/AndroidManifest.xml and app/src/main/java/varzan/extraKeyboardLayouts/InputDeviceReceiver.java, varzan.thumbExtrernalKeyboardLayouts should be different than the value for the last known working AndroidStudio installation.

[<img alt='Fork of something available on Fdroid.org (not yet)' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png' height="80px"/>](http://f-foid.org)
[<img alt='Fork of something available on Google Play' src='https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png' height="80px"/>](https://play.google.com/store/apps/details?id=varzan.extraKeyboardLayouts)
[<img alt='Fork of something available on IzzyOnDroid' src='https://gitlab.com/IzzyOnDroid/repo/-/raw/master/assets/IzzyOnDroid.png' height="80px"/>](https://apt.izzysoft.de/fdroid/index/apk/varzan.extraKeyboardLayouts)

Slash (keycode 53), just on right of small space key, is turned into AltGr.
CAPS_LOCK (keycode 58) is turned into PLUS.

The full map is on (the source code)[https://github.com/jidhub/thumb-external-keyboard-layouts/blob/master/app/src/main/res/raw/keyboard_layout_neo2.kcm#L159]

TODO:

- strip keyboards other than neo2

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

If you found this useful, you may [buy a drink to the project I forked](https://paypal.me/CalinDarie?locale.x=en_US) or ask for the Ergo-L community on Discord.
