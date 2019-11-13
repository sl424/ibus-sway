# ibus-sway
minimal ibus AUR build for sway (wayland)
The ibus input switch key and ibus panel did not work for me anyway, so I disabled them in
this minimal build.

launch ibus without panel:

	ibus-daemon -drx --panel=disable

you can switch engine by:

	ibus engine xkb:es::spa
	ibus engine xkb:us::eng
	ibus engine kkc #require ibus-kkc

Optional: for ibus-kkc, you can also add additional key to swtich between hiragana and direct input:

	vim .config/ibus-kkc/rules/default/keymap/direct.json
	vim .config/ibus-kkc/rules/default/keymap/hiragana.json

like this:

	{
	  "include" : [
	    "default/direct"
	  ],
	  "define" : {
	    "keymap" : {
	      "F4" : "set-input-mode-hiragana"
	    }
	  }
	}

## ibus-sway build options
Build options:
Version                       1.5.21
Install prefix                /usr
Build shared libs             yes
Build static libs             no
CFLAGS                        -march=x86-64 -mtune=generic -O2 -pipe -fno-plt
PYTHON                        /usr/bin/python
PYTHON2
Enable python2                no (disabled, use --enable-python2 to enable)
Gtk2 immodule dir
Gtk3 immodule dir
Build gtk2 immodule           no (disabled, use --enable-gtk2 to enable)
Build gtk3 immodule           no (disabled, use --enable-gtk3 to enable)
Build XIM agent server        yes
Build wayland support         yes
Build gdk3 wayland support    no (disabled, need to install gdk-wayland-3.0.pc)
Build appindicator support    no
Build appindicator engine icon no (disabled, need qtbase-devel 5.4 or later)
Build python library          no (disabled, use --enable-python-library to enable)
Build memconf modules         no
Build dconf modules           yes (enabled, use --disable-dconf to disable)
Build introspection           no
IBus-1.0.gir scannerflags     ""
Build vala binding            no
Build document                no (disabled, use --enable-gtk-doc to enable)
Build UI                      no
Build engine                  yes (enabled, use --disable-engine to disable)
Enable key snooper            yes
No snooper regexes            "firefox.*,.*chrome.*,.*chromium.*,terminator"
Panel icon                    "ibus-keyboard"
Enable surrounding-text       yes
Enable Emoji dict             no
Unicode Emoji directory       /usr/share/unicode/emoji
CLDR annotation directory     /usr/share/unicode/cldr/common/annotations
Enable Unicode dict           yes (enabled, use --disable-unicode-dict to disable)
UCD directory                 /usr/share/unicode/ucd
Run test cases                yes
Install tests                 no (disabled, use --enable-install-tests to enable)

