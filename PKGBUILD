# Contributor: Hy Goldsher <hyness-at-freshlegacycode-dot-org>
# Maintainer: Hy Goldsher <hyness-at-freshlegacycode-dot-org>
pkgname=davmail
pkgver=5.3.1
pkgrel=1
pkgdesc="a POP/IMAP/SMTP/Caldav/LDAP gateway for the exchange service"
arch=('x86_64')
url="http://$pkgname.sourceforge.net/"
license=('GPL')
makedepends=('unzip')
depends=('java-runtime')
_rev=3079
source=(http://downloads.sourceforge.net/$pkgname/$pkgname-$pkgver-$_rev.zip
        $pkgname.desktop
        $pkgname.sh
        $pkgname@.system_service
        $pkgname@.user_service)

package() {
  install -d $pkgdir/{usr/share/java/$pkgname/lib,usr/bin,etc/$pkgname}
  install -Dm644 $pkgname.jar $pkgdir/usr/share/java/$pkgname/
  install -D lib/* $pkgdir/usr/share/java/$pkgname/lib
  install -Dm755 $srcdir/$pkgname.sh $pkgdir/usr/share/java/$pkgname
  ln -s /usr/share/java/$pkgname/$pkgname.sh $pkgdir/usr/bin/$pkgname
  install -Dm644 $srcdir/$pkgname.desktop ${pkgdir}/usr/share/applications/$pkgname.desktop
  install -Dm644 $srcdir/$pkgname\@.system_service ${pkgdir}/usr/lib/systemd/system/$pkgname\@.service
  install -Dm644 $srcdir/$pkgname\@.user_service ${pkgdir}/usr/lib/systemd/user/$pkgname\@.service

  # Create icons
  unzip -q $pkgname.jar tray.png tray32.png tray48.png tray128.png
  install -Dm644 tray.png ${pkgdir}/usr/share/icons/hicolor/16x16/apps/$pkgname.png
  install -Dm644 tray32.png ${pkgdir}/usr/share/icons/hicolor/32x32/apps/$pkgname.png
  install -Dm644 tray48.png ${pkgdir}/usr/share/icons/hicolor/48x48/apps/$pkgname.png
  install -Dm644 tray128.png ${pkgdir}/usr/share/icons/hicolor/128x128/apps/$pkgname.png
}
sha512sums=('a938fcaee6a0c4f8376fefe4b4302f3315c341750298162b6a8da7175ed72c1da75b287277ebc3bfa71bd5a5d0e1d5e73f123dc58d2cae3821ed8b760a4c969e'
            'f1060b209047ae15146093481ffd9736a9a5430d7566b6b2099b590e6ad4d306be7c82587f3411737149c19e9c5904e139f38e5d4c0358e719808aff7cfac002'
            'e5dc9047ca1b3cdbd1ea92e35769dd8b27a26569c1ef62856a7ecc5e9096cdf7dceb4683812e69ce85e3b6254c879e3a7a3e70b6557fb6cd492e977249693787'
            '3f342de3fc9dae4003fa299412c1671f697ed718be9f9fabe6488913b373dad888fe813a89547dae4994d18e33e5999a94f867225be19346dc8cff1d8d858c61'
            'c46950e68ea302f3e7dde7ab2ea68dcc2884fc8a94656f6843982d7495ca0dec50e3e83849383a2064b07366b2aaa9f9ecbd0573316d7aa1fb27ec37b156e2f5')
