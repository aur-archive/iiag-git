# Maintainer: richteer <richteer at lastprime.net>

pkgname=iiag-git
_pkgname=iiag-git
pkgver=367.b53505e
pkgrel=1
pkgdesc="iiag is a game."
arch=('i686' 'x86_64')
url="http://www.github.com/iiag/iiag-legacy"
license=('BSD')
depends=('lua' 'ncurses' 'sdl2' 'sdl2_ttf')
makedepends=('git')
source=('iiag.sh' "$_pkgname::git://github.com/iiag/iiag-legacy.git#branch=master")
sha256sums=('b671fe6218e8ce46b5dd91297a00280dcc6e7074e7ab7576c0a71d7f12497c2a'
            'SKIP')
conflicts=('iiag-git')


pkgver() {
  cd "$srcdir/$_pkgname"
  echo $(git rev-list --count master).$(git rev-parse --short master)
}

build() {
  cd "$srcdir/$_pkgname"
  make
}

package() {
  mkdir -p $pkgdir/usr/bin
  cp iiag.sh $pkgdir/usr/bin/iiag
  cd "$srcdir/$_pkgname"
  make "DESTDIR=$pkgdir/opt/iiag" "MANDIR=$pkgdir/usr/share/man/man6" install
}

