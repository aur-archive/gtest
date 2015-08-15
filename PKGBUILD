# Maintainer: Alexandre Bique <bique.alexandre@gmail.com>
# Contributor: Louis R. Marascio <lrm@fitnr.com>
# Contributor: Cody Maloney <cmaloney@theoreticalchaos.com>

pkgname=gtest
pkgver=1.6.0
pkgrel=6
pkgdesc="Google Test - C++ testing utility based on the xUnit framework (like JUnit)"
arch=('i686' 'x86_64')
url="http://code.google.com/p/googletest/"
license=('BSD')
options=('!libtool')
depends=('gcc-libs' 'sh')
makedepends=('python2' 'cmake')
source=(http://googletest.googlecode.com/files/$pkgname-$pkgver.zip)
sha1sums=('00d6be170eb9fc3b2198ffdcb1f1d6ba7fc6e621')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  rm -rf build
  mkdir build
  cd build
  cmake -DBUILD_SHARED_LIBS=ON ..
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  mkdir -pm 0755 $pkgdir/usr/{lib,include/gtest/internal,share/licenses/$pkgname,src/gtest/src,src/gtest/cmake}
  install -m 0644 build/libgtest{,_main}.so $pkgdir/usr/lib/
  install -m 0644 include/gtest/*.h $pkgdir/usr/include/gtest/
  install -m 0644 include/gtest/internal/*.h $pkgdir/usr/include/gtest/internal/
  install -m 0644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
  install -m 0644 $srcdir/$pkgname-$pkgver/fused-src/gtest/* $pkgdir/usr/src/gtest/src
  install -m 0644 $srcdir/$pkgname-$pkgver/CMakeLists.txt $pkgdir/usr/src/gtest
  install -m 0644 $srcdir/$pkgname-$pkgver/cmake/* $pkgdir/usr/src/gtest/cmake
}

# vim:set ts=2 sw=2 et:
