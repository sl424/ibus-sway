# ibus-sway

Minimal ibus AUR build for sway 

The ibus input switch key and ibus panel did not work for me in sway, so I only installed
the base with wayland support without python2 dependency(broken ibus-setup).

To launch ibus with system tray icon you need:

	 XDG_CURRENT_DESKTOP=KDE ibus-daemon -drx 

you can switch engine in command line or bind them to different keys:

	ibus engine xkb:us::eng
	ibus engine kkc 

Optional: for ibus-kkc, you can also add additional key to swtich between hiragana and direct input:

	vim .config/ibus-kkc/rules/default/keymap/direct.json
	vim .config/ibus-kkc/rules/default/keymap/hiragana.json

direct.json example:

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
	  CFLAGS                        -march=x86-64 -mtune=generic -O2 -pipe -fstack-protector-strong -fno-plt
	  PYTHON                        /usr/bin/python
	  PYTHON2                       
	  Enable python2                no (disabled, use --enable-python2 to enable)
	  Gtk2 immodule dir             ${exec_prefix}/lib/gtk-2.0/2.10.0/immodules
	  Gtk3 immodule dir             ${exec_prefix}/lib/gtk-3.0/3.0.0/immodules
	  Build gtk2 immodule           yes
	  Build gtk3 immodule           yes
	  Build XIM agent server        yes
	  Build wayland support         yes
	  Build gdk3 wayland support    yes
	  Build appindicator support    yes (enabled, use --disable-appindicator to disable)
	  Build appindicator engine icon yes
	  Build python library          no (disabled, use --enable-python-library to enable)
	  Build memconf modules         no
	  Build dconf modules           yes (enabled, use --disable-dconf to disable)
	  Build introspection           no
	  IBus-1.0.gir scannerflags     ""
	  Build vala binding            no
	  Build document                no (disabled, use --enable-gtk-doc to enable)
	  Build UI                      yes (enabled, use --disable-ui to disable)
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

