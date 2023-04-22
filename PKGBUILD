# Maintainer: Roman Vasilev <2rvasilev at live dot ru>

pkgname=scantailor-advanced-git
pkgver=v1.0.18
pkgrel=3
pkgdesc="Interactive post-processing tool for scanned pages that merges the features of the ScanTailor Featured and ScanTailor Enhanced versions, brings new ones and fixes. "
arch=("x86_64")
#url="https://github.com/4lex4/scantailor-advanced"
url="https://github.com/ScanTailor-Advanced/scantailor-advanced"
license=("GPL3")
depends=(
    "boost-libs"
    "libjpeg"
    "libpng"
    "libtiff"
    "qt5-base"
    "zlib"
    )
makedepends=(
    "git"
    "boost"
    "cmake"
    "qt5-tools"
    "qt5-svg"
    )
provides=("scantailor")
conflicts=("scantailor-advanced" "scantailor")
#source=("scantailor-advanced::git+https://github.com/4lex4/scantailor-advanced")
source=("$pkgname::git+https://github.com/ScanTailor-Advanced/scantailor-advanced.git#tag=$pkgver")

sha256sums=('SKIP')

# pkgver() {
#     cd "$srcdir/${pkgname%-git}"
#     git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
# }

build() {
    # export LDFLAGS="-L/usr/local/lib,--rpath=/usr/local/lib"
    # export LD_LIBRARY_PATH="/usr/local/lib"
    # export CFLAGS="-fPIC"
    # export CXXFLAGS="-fPIC"

    cd "${srcdir}/${pkgname}"
    sed -i "s/#define VERSION .*$/#define VERSION \"$pkgver\"/" version.h.in
    # https://aur.archlinux.org/packages/scantailor-advanced-git/#comment-831404
    mkdir build && cd build
    cmake -G "Unix Makefiles" ..
    cmake --build .
    make
}

package() {
    cd "${srcdir}/${pkgname}"
    cd build
    make DESTDIR="${pkgdir}" install
}
