# Maintainer: Ilya Medvedev <medved55rus [at] gmail [dot] com>

pkgname=urtconnector-git
pkgver=20130114
pkgrel=1
pkgdesc="Advanced UrbanTerror launcher program. Developed by members of russian clans =Xaoc=, Red*Army and Rus Devils Team. 
This program uses Qt4 and is written in C++."
arch=('i686' 'x86_64')
url="http://code.google.com/p/urtconnector"
license=('GPL')
depends=('qt>=4.6.2' 'phonon' 'sqlite')
makedepends=('pkgconfig' 'cmake>=2.6' 'git' 'boost' 'automoc4')
provides=('urtconnector')
conflicts=('urtconnector')
source=()
md5sums=()
_gitroot=('https://code.google.com/p/urtconnector')
_gitname=('urtconnector')

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cd "${srcdir}/$_gitname/"
  
  cmake ./ -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "${srcdir}/$_gitname/"
  make DESTDIR="$pkgdir" install
}
