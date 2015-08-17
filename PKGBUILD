# Maintainer: Nicolas Stalder <nicolas dot stalder at gmail dot com>
pkgname=python2-pyublas
pkgver=2011.1
pkgrel=2
epoch=
pkgdesc="Seamless Numpy-UBlas interoperability."
arch=('x86_64')
url="http://pypi.python.org/pypi/PyUblas"
license=('MIT')
depends=('boost-libs' 'python2-numpy')
source=('http://pypi.python.org/packages/source/P/PyUblas/PyUblas-2011.1.tar.gz'
        'aksetup-defaults.py'
        'aksetup_helper.patch'
        'LICENSE')
md5sums=('b0a151d152d1d21bdeeab5d629edc145'
         '830e447f48b136cc5fc52923b4cb01c7'
         '7f56455773b8ea8ffff2efd5159dc9eb'
         '101db9261d7735953e6d40203e15df8a')

build() {
  cd "$srcdir/PyUblas-2011.1"
  patch aksetup_helper.py ../aksetup_helper.patch 
  python2 setup.py build
}

package() {
  cd "$srcdir/PyUblas-2011.1"
  mkdir -p       $pkgdir/usr/include/pyublas
  cp             src/cpp/pyublas/*.hpp \
                 $pkgdir/usr/include/pyublas
  install -Dm644 build/lib.linux-x86_64-2.7/pyublas/__init__.py \
                 $pkgdir/usr/lib/python2.7/site-packages/pyublas/__init__.py
  install -D     build/lib.linux-x86_64-2.7/pyublas/_internal.so \
                 $pkgdir/usr/lib/python2.7/site-packages/pyublas/_internal.so
  install -Dm644 ../LICENSE $pkgdir/usr/share/licenses/python2-pyublas/LICENSE
}

# vim:set ts=2 sw=2 et:
