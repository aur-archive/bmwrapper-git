# Maintainer: Stephen Martin <hwkiller at gmail dot com || BM-GtZxW5bqG5QuBCyaAxAxwV2DNMxjjHba >
pkgname=bmwrapper-git
pkgver=b2716a0
pkgrel=1
pkgdesc="bmwrapper is a poorly hacked together python script to let Thunderbird and PyBitmessage communicate"
arch=('any')
url="https://github.com/Arceliar/bmwrapper"
license=('MIT')
depends=('python2' 'pybitmessage-git')
makedepends=('git')
install="$pkgname".install
provides=('bmwrapper')
conflicts=('bmwrapper')

source=('bmwrapper::git+https://github.com/Arceliar/bmwrapper'
        'bmwrapper.sh'
        'bmwrapper.desktop')

md5sums=('SKIP'
         '1f5b84705158fbc0d411a754ba1ab0f5'
         'fc470e40152d7365c2dd9640ed03ded9')
_gitname='bmwrapper'
pkgver() {
  cd $_gitname
  git describe --always | sed 's|-|.|g'
}
prepare() {
  cd $_gitname
  msg 'Fixing python version to python2...'
  find . -type f -print0 | xargs -0 sed -i 's#/usr/bin/python#/usr/bin/python2#g'
  find . -type f -print0 | xargs -0 sed -i 's#/usr/bin/env python#/usr/bin/env python2#g'
}
package() {
  cd $_gitname
  mkdir -p "$pkgdir"/usr/share/bmwrapper
  cp ./* "$pkgdir"/usr/share/bmwrapper/

  install -D -m755 "$srcdir"/bmwrapper.sh "$pkgdir"/usr/bin/bmwrapper
  install -D -m744 "$srcdir"/bmwrapper.desktop "$pkgdir"/usr/share/applications/bmwrapper.desktop
}

# vim:set ts=2 sw=2 et:
