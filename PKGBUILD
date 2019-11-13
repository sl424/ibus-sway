# Contributer: chewie lin
# From http://www.linuxfromscratch.org/blfs/view/svn/general/ibus.html
# template ibus-lite
# https://aur.archlinux.org/packages/ibus-lite/

pkgname=ibus-lite
pkgname=ibus
pkgver=1.5.21
pkgrel=1
pkgdesc="ibus-daemon only"
arch=('i686' 'x86_64')
url="https://github.com/ibus/ibus/releases/download/1.5.21/ibus-1.5.21.tar.gz"
license=('LGPL')
depends=('libibus' 'gtk3' 'dconf' 'iso-codes')
makedepends=('vala')
provides=("ibus=$pkgver")
conflicts=('ibus')
replaces=('ibus')
options=('!emptydirs')
source=("https://github.com/ibus/ibus/releases/download/${pkgver}/ibus-${pkgver}.tar.gz")
md5sums=('12c5b2e6e9e36fbe8a9f7a2a0501f0e7')

prepare(){                                     
	#Fix an issue with deprecated schema entries:  
	cd "$srcdir/ibus-$pkgver"                   
	sed -i 's@/desktop/ibus@/org/freedesktop/ibus@g' \
		data/dconf/org.freedesktop.ibus.gschema.xml
	# enable-unicode-dict 
	wget https://www.unicode.org/Public/zipped/10.0.0/UCD.zip
	sudo mkdir -p /usr/share/unicode/ucd && unzip -u UCD.zip -d /usr/share/unicode/ucd
}

build() {
  cd "$srcdir/ibus-$pkgver"
  ./configure \
    --prefix=/usr \
    --libexecdir=/usr/lib/ibus \
    --sysconfdir=/etc \
    --enable-dconf \
    --enable-wayland \
    --disable-ui \
    --disable-python-library \
    --disable-gconf \
    --disable-emoji-dict \
    --disable-gtk2 \
    --disable-gtk3 \
    --disable-python2 \
    --disable-libnotify \
    --disable-appindicator \
    --disable-memconf \
    --disable-gtk-doc &&
    rm -f tools/main.c &&
    make
}

package() {
  cd "$srcdir/ibus-$pkgver"
  make DESTDIR="${pkgdir}" install
  make -C src DESTDIR="${pkgdir}" uninstall
  make -C bindings DESTDIR="${pkgdir}" uninstall
  make DESTDIR="${pkgdir}" uninstall-pkgconfigDATA
}
