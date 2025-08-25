pkgname=mpfr
pkgver=4.2.2
pkgrel=1
pkgdesc="Multiple-precision floating-point library"
arch=('x86_64')
url="https://www.mpfr.org/"
license=(
    'GPL-3.0-or-later'
    'LGPL-3.0-or-later'
)
depends=('glibc' 'gmp')
source=(https://ftp.gnu.org/gnu/${pkgname}/${pkgname}-${pkgver}.tar.xz)
sha256sums=(b67ba0383ef7e8a8563734e2e889ef5ec3c3b898a01d00fa0a6869ad81c6ce01)

build() {
    cd ${pkgname}-${pkgver}

    local configure_args=(
        --disable-static
        --enable-thread-safe
        --docdir=/usr/share/doc/${pkgname}-${pkgver}
        ${configure_options}
    )

    ./configure "${configure_args[@]}"

    make
    make html
}

package() {
    cd ${pkgname}-${pkgver}

    make DESTDIR=${pkgdir} install
    make DESTDIR=${pkgdir} install-html
}
