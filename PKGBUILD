# Maintainer: Rolinh <robinDOThahlingATgw-computingDOTnet>

pkgname=ghmd
pkgver=1.3.3
pkgrel=1
pkgdesc="command line tool that can render GitHub Markdown files to HTML"
arch=('x86_64' 'i686')
url="https://github.com/gilliek/ghmd"
license=('BEERWARE')
depends=('xdg-utils')
makedepends=('git' 'go')
source=(https://github.com/gilliek/${pkgname}/archive/v${pkgver}.tar.gz)
md5sums=('c8f6a1e100615e4b6bb9d4106c01540d')

prepare() {
  GOPATH="${srcdir}"
  cd "${srcdir}"
  mkdir -p src/github.com/gilliek
  ln -sf ../../../${pkgname}-${pkgver} src/github.com/gilliek/${pkgname}
  go get -v github.com/go-fsnotify/fsnotify
}

build() {
  go install -v github.com/gilliek/ghmd
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  install -Dm755 "${srcdir}/bin/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"

  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
