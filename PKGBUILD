# Maintainer: Andreas Radke <andyrtr@archlinux.org>
# Contributor: Judd <judd@archlinux.org>

pkgname=nano
pkgver=4.9.3
pkgrel=1
pkgdesc="Pico editor clone with enhancements"
arch=('x86_64')
license=('GPL')
url="https://www.nano-editor.org"
depends=('ncurses' 'file' 'sh')
backup=('etc/nanorc')
groups=('modified')
source=(https://www.nano-editor.org/dist/v4/${pkgname}-${pkgver}.tar.xz{,.asc})
sha256sums=('6e3438f033a0ed07d3d74c30d0803cbda3d2366ba1601b7bbf9b16ac371f51b4'
            'SKIP')
validpgpkeys=('8DA6FE7BFA7A418AB3CB2354BCB356DF91009FA7' # "Chris Allegretta <chrisa@asty.org>"
              'A7F6A64A67DA09EF92782DD79DF4862AF1175C5B' # "Benno Schulenberg <bensberg@justemail.net>"
              'BFD009061E535052AD0DF2150D28D4D2A0ACE884' # "Benno Schulenberg <bensberg@telfort.nl>"
)

build() {
  cd ${pkgname}-${pkgver}
  ./configure --prefix=/usr \
    --sysconfdir=/etc \
    --enable-color \
    --enable-nanorc \
    --enable-multibuffer \
    --disable-mouse
  make
}

package() {
  cd ${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install
  install -DTm644 "${srcdir}"/${pkgname}-${pkgver}/doc/sample.nanorc "${pkgdir}"/etc/nanorc
}
