# Contributor: Franz Rogar <franzrogar@gmail.com>
pkgname=cr3-qt4
pkgver=20111104
pkgrel=2
pkgdesc="CoolReader FB2 (FictionBook2) e-book reader"
url="http://www.coolreader.org/crengine.htm"
license=('GPL')
arch=('i686' 'x86_64')
makedepends=('git' 'cmake')
depends=('qt')
provides=('cr3')

_gitrepo="git://crengine.git.sourceforge.net/gitroot/crengine/crengine"

build() {
  if [ -d ${srcdir}/${pkgname} ]; then
     cd ${srcdir}/${pkgname} && git pull
  else
     git clone ${_gitrepo} ${srcdir}/${pkgname}
  fi

  cd ${srcdir}/${pkgname}
  mkdir -p qtbuild
  cd qtbuild
  cmake -D GUI=QT \
        -D CMAKE_BUILD_TYPE=Release \
        -D MAX_IMAGE_SCALE_MUL=2 \
        -D DOC_DATA_COMPRESSION_LEVEL=3 \
        -D DOC_BUFFER_SIZE=0x1400000 \
        -D CMAKE_INSTALL_PREFIX=/usr ..
  make
  make DESTDIR="${pkgdir}/" install
}

