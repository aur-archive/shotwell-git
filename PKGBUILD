# Contributor: Joeny Ang <ang(dot)joeny(at)gmail(dot)com>
# Contributor: florianbw <florian(dot)bw(at)gmail(dot)com>
# Contributor: Frederic Bezies <fredbezies(at)gmail(dot)com>
# Contributor: Robert Chmielowiec <robert(at)chmielowiec(dot)net>
# Contributor: Daniel <quite(at)hack(dot)org>
# Contributor: mariusz <my(dot)swiat(at)o2(dot)pl>
# Contributor: p-we <wdirksen(at)gmail(dot)com>
# Contributor: Mateusz Loskot <mateusz(at)loskot(dot)net>

pkgname=shotwell-git
_gitname=shotwell
pkgver=0.20.0.r22.g2ae25e1
pkgrel=1
pkgdesc="A digital photo organizer designed for the GNOME desktop environment"
arch=('i686' 'x86_64')
url="http://yorba.org/shotwell/"
license=('LGPL2.1')
depends=('desktop-file-utils' 'gconf' 'gnome-vfs' 'json-glib' 'libgee' 'libgexiv2-git' 'libgphoto2' 'libquicktime' 'librsvg' 'libunique3' 'libwebkit3' 'dconf' 'rest' 'libraw')
makedepends=('git' 'intltool' 'pkgconfig' 'vala')
provides=('shotwell')
conflicts=('shotwell')
install=${_gitname}.install
source=('git+https://git.gnome.org/browse/shotwell/')
md5sums=('SKIP')
         
pkgver() {
  cd ${srcdir}/${_gitname}

  # Use the tag of the last commit
  # git describe --always | sed 's|-|.|g'
  
  # Use current date
  # date +%Y%m%d
  
  # Use the most recent annotated tag reachable from the last commit
  git describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g;s/shotwell.//'
}

build() {
  cd ${srcdir}/${_gitname}

  ./configure --prefix=/usr \
    --disable-schemas-compile \
    --disable-desktop-update \
    --disable-icon-update
  make
}

package() {
  cd ${srcdir}/${_gitname}

  make DESTDIR=${pkgdir} install
}
