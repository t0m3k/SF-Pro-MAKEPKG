pkgname=otf-san-francisco-pro
pkgver=1
pkgrel=1
pkgdesc='San Francisco Pro font. Sourced directly from Apple.'
arch=('any')
url='https://developer.apple.com/fonts/'
license=('custom')
makedepends=('p7zip')
source=("SF-Pro-$pkgrel.dmg::https://devimages-cdn.apple.com/design/resources/download/SF-Pro.dmg")
sha256sums=('SKIP')

prepare() {
  # remove previous files
  rm -rf SFProFonts
  # extract dmg
  7z x "SF-Pro-$pkgrel.dmg"
  # extract pkg
  bsdtar xvPf "SFProFonts/SF Pro Fonts.pkg"
  bsdtar xvPf "SFProFonts.pkg/Payload"
}

package() {
  # install fonts
  install -d "$pkgdir/usr/share/fonts/apple"
  install -m644 "Library/Fonts/"*.otf "$pkgdir/usr/share/fonts/apple"

  # install license
  install -d "$pkgdir/usr/share/licenses/$pkgname"
  install -m644 Resources/English.lproj/License.rtf "$pkgdir/usr/share/licenses/$pkgname/LICENSE.rtf"
}

