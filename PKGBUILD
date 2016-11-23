pkgname=davmail
_pkgver=4.7.3
_rev=2438
pkgver=4.7.3.2438
pkgrel=1
pkgdesc="a POP/IMAP/SMTP/Caldav/LDAP gateway for the exchange service"
arch=('i686' 'x86_64')
url="http://davmail.sourceforge.net/"
license=('GPL')
makedepends=('apache-ant')
depends=('java-runtime' 'desktop-file-utils' 'hicolor-icon-theme')
source=(
	"http://downloads.sourceforge.net/project/$pkgname/$pkgname/$_pkgver/$pkgname-src-$_pkgver-$_rev.tgz"
)
sha256sums=('3940a7f6aa44cb3c419c2a4ede71e465b29b7076c9ed1bb0abe251a60378c208')

build() {
	cd "$pkgname-src-$_pkgver-$_rev"
	ANT_OPTS=-Dfile.encoding=UTF-8 ant
}

package() {
	cd "$pkgname-src-$_pkgver-$_rev"
	install -dm755 "$pkgdir/usr/share/java/$pkgname"
	cd dist
	if [ "$CARCH" = "i686" ]; then
		bsdtar --strip-components 1 -xf $pkgname-linux-x86-$_pkgver-trunk.tgz -C "$pkgdir/usr/share/java/$pkgname/"
	elif [ "$CARCH" = "x86_64" ]; then
		bsdtar --strip-components 1 -xf $pkgname-linux-x86_64-$_pkgver-trunk.tgz -C "$pkgdir/usr/share/java/$pkgname/"
	fi
	# Create icons
	cd "$srcdir/$pkgname-src-$_pkgver-$_rev"
	install -Dm644 src/java/tray2.png ${pkgdir}/usr/share/icons/hicolor/16x16/apps/davmail.png
	install -Dm644 src/java/tray32.png ${pkgdir}/usr/share/icons/hicolor/32x32/apps/davmail.png
	install -Dm644 src/java/tray48.png ${pkgdir}/usr/share/icons/hicolor/48x48/apps/davmail.png

	# fix davmail.sh so it uses realpath
	sed -e 's,`dirname $0`,$(dirname $(realpath $0)),' -i "$pkgdir/usr/share/java/$pkgname/davmail.sh"

	# bin
	install -dm755 "$pkgdir/usr/bin"
	ln -sf "/usr/share/java/$pkgname/davmail.sh" "$pkgdir/usr/bin/davmail"

	# dektop
	# fix icon
	sed -e 's,^Icon=.*,Icon=davmail,' -i dist/$pkgname.desktop
	# install
	install -Dm644 dist/$pkgname.desktop "$pkgdir/usr/share/applications/$pkgname.desktop"
}
