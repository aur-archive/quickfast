# Maintainer: Nicolas Stalder <nicolas dot stalder at gmail dot com>
pkgname=quickfast
pkgver=1.4.0
pkgrel=2
pkgdesc="An implementation of the FAST protocol for native C++."
arch=('x86_64')
url="http://code.google.com/p/quickfast/"
license=('BSD')
groups=()
depends=('boost-libs>=1.36.0' 'xerces-c>=3.0')
makedepends=('perl' 'boost')
changelog=
source=('http://quickfast.googlecode.com/files/quickfast_lnx_src_1_4.tar.gz'
        'http://downloads.ociweb.com/MPC/MPC_3_9_0.tar.gz'
        'envmod.patch')
md5sums=('32b8ea86f87056427e7f17bf7ad04d78'
         'd22749e9f332aebf6fee390e58035039'
         'f1381b9942ae6b0c54248098eb7491e5')

build() {
  cd "$srcdir/${pkgname}_1_4_0"
  patch -p1 -i ../envmod.patch 
  source setup.sh
  ./m.sh
  make
}

package() {
  cd "$srcdir/${pkgname}_1_4_0"
  for _part in 'Application' 'Codecs' 'Common' 'Communication' 'Messages'
  do
    mkdir -p $pkgdir/usr/include/quickfast/$_part
    cp src/$_part/*.h $pkgdir/usr/include/quickfast/$_part
  done
  install -D lib/libQuickFAST.so $pkgdir/usr/lib/libQuickFAST.so
  install -D -m644 license.txt $pkgdir/usr/share/licenses/quickfast/LICENSE
}

# vim:set ts=2 sw=2 et:
