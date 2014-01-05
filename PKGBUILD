# Maintainer: chliny <chliny11 at gmail dot com>

pkgname=openbts
pkgver=2.8.0
pkgrel=1
pkgdesc="GSM L1-L3 stack with SIP network interfaces"
arch=('i686' 'x86_64')
url="http://openbts.org/"
license=('GPL' 'AGPL')
depends=('libtool' 'libosip2' 'ortp' 'libusb-compat' 'sqlite>=3' 'boost-libs' 'readline')
makedepends=('autoconf' 'gcc' 'pkg-config' 'make' 'patch')
optdepends=('asterisk: PBX support')
source=(
    "http://downloads.sourceforge.net/project/openbts/${pkgver}/${pkgname}-P${pkgver}Opelousas.tar.gz"
    "openbts.patch"
    )
sha512sums=(
    '200d22e49fe6181fadcf2c68ad322032c1aa4fe3254f6f3c4584d5132ba431432ce6ad81f3d9aa7ac773e7ec2f80203920eea7ff999a781c8f173484353b0352'
    'SKIP'
    )

build() {
    cd "$srcdir/${pkgname}-P${pkgver}Opelousas"
    patch -p1 < ../../openbts.patch
    autoconf -i
    ./configure
    make
}

package() {
    cd "${srcdir}/${pkgname}-P${pkgver}Opelousas"
    install -Dm755 ./apps/OpenBTS "${pkgdir}/usr/bin/OpenBTS"
    install -Dm644 ./apps/OpenBTS.example.sql "${pkgdir}/usr/share/OpenBTS/OpenBTS.example.sql"
    mkdir -p "${pkgdir}/usr/share/OpenBTS/Asterisk/" 
    install -Dm644 ./AsteriskConfig/*.conf "${pkgdir}/usr/share/OpenBTS/Asterisk/" 
}

