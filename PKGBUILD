# Maintainer: Charles E. Hawkins <charlesthehawk at yahoo dot com>
# Contributor: Thomas S Hatch <thatch45 at gmail dot com>
# Contributor: Luciano A. Ferrer <laferrer@gmail.com>
pkgname=ocaml-taglib
pkgver=0.3.1
pkgrel=1
arch=('i686' 'x86_64')
license=('GPL')
pkgdesc="for MP3 audio tag reading"
url="http://savonet.sourceforge.net/"
depends=('taglib')
makedepends=('ocaml' 'ocaml-findlib')
options=('!strip')
source=("http://downloads.sourceforge.net/savonet/${pkgname}-${pkgver}.tar.gz")
md5sums=('0018734e177cf480d9af29999bfdad4a')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./configure --prefix=/usr
  make all
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  mkdir -p ${pkgdir}/usr/share/doc/${pkgname}
  cp -r examples ${pkgdir}/usr/share/doc/${pkgname}
  mkdir -p ${pkgdir}$(ocamlfind printconf destdir)
  make \
    OCAMLFIND_DESTDIR=${pkgdir}$(ocamlfind printconf destdir) \
    OCAMLFIND_LDCONF=ignore \
    install
}
