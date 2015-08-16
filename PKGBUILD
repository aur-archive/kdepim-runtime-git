# Maintainer anex <lane.wiscombe[@]gmail.com>

pkgname=kdepim-runtime-git
_pkgname=kdepim-runtime
arch=('x86_64')
pkgver=r12207.d10aceb
pkgrel=2
pkgdesc="KDE Pim Runtime"
url="http://www.kde.org"
license=('GPL' 'LGPL' 'FDL')
install=${_pkgname}.install
depends=('kdepimlibs-git' 'qt5-quick1' 'knotifyconfig-git' 'kross-git' 'knewstuff-git' 'kcmutils-git' 'kdelibs4support-git' 
         'kconfig-git' 'kio-git' 'kitemmodels-git' 'kcodecs-git' 'libaccounts-qt5' 'signon-qt5' 'shared-mime-info' 
         'akonadi-git' 'kmime-git' 'kmailtransport-git' 'kidentitymanagement-git' 'kcontacts-git' 'kalarmcal-git' 'kcalcore-git' 
         'kcalutils-git' 'kmbox-git' 'kpimtextedit-git' 'kimap-git' 'kde-syndication-git' 'akonadi-calendar-git' 'kaccounts-integration-git'
         'libkgapi-frameworks-git')
makedepends=('extra-cmake-modules' 'kdoctools' 'boost')
conflicts=('kdepim-runtime')
replaces=('kdepim-runtime')
source=("git://anongit.kde.org/kdepim-runtime.git")      
sha256sums=('SKIP')

pkgver() {
  cd kdepim-runtime
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd ${srcdir}
    #sed -i 's|AccountsQt 1.11 QUIET|AccountsQt5 1.11 QUIET|' ${srcdir}/$_pkgname/resources/CMakeLists.txt
    #sed -i 's|SignOnQt|SignOnQt5|' ${srcdir}/$_pkgname/resources/CMakeLists.txt
    
    mkdir -p build
    cd build

    cmake ../${_pkgname} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DCMAKE_SKIP_RPATH=ON \
        -DLIB_INSTALL_DIR=lib \
        -DSYSCONF_INSTALL_DIR=/etc \
        -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
        #-DBUILD_TESTING=OFF \
        #-DENABLE_TESTING=OFF
    make
}

package() {
    cd ${srcdir}/build

    make DESTDIR=${pkgdir} install
}