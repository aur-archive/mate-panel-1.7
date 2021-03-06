# Maintainer : Martin Wimpress <code@flexion.org>
# Contributor: Piotr Gorski <sir_lucjan@bridgelinux.pl>

pkgname=mate-panel-1.7
_pkgname=mate-panel
pkgver=1.7.1
pkgrel=1
pkgdesc="The MATE Panel"
url="http://mate-desktop.org"
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
license=('GPL')
depends=('caja' 'dbus-glib' 'dconf' 'gtk2' 'libwnck' 'libcanberra' 'libice'
         'libmateweather' 'librsvg' 'libsm' 'libsoup' 'libxau' 'marco'
         'mate-menus' 'mate-desktop' 'mate-session-manager')
makedepends=('gobject-introspection' 'mate-common' 'networkmanager'
             'perl-xml-parser' 'yelp-tools')
optdepends=('yelp: for reading MATE help documents')
options=('!emptydirs')
groups=('mate')
conflicts=(mate-panel)
replaces=(mate-panel)
provides=(mate-panel)
source=("http://pub.mate-desktop.org/releases/1.7/${_pkgname}-${pkgver}.tar.xz"
        https://github.com/mate-desktop/mate-panel/commit/a7a5e35d8a5418d9b9939f6de99367f72ded7b6d.diff
        https://github.com/mate-desktop/mate-panel/commit/603813e094a40707eb0d9e4238348c6bdf857993.diff
        https://github.com/mate-desktop/mate-panel/commit/1b401ff5fa2ca8e710986e61227389cedde10a05.diff
        https://github.com/infirit/mate-panel/commit/27daac2e3469ec6620309b8bbcf947934874dd9d.diff)

sha1sums=('2ccb28ba597d0701390825593af6cf48d9efd729'
          '1150ae4f83147529e8fb81d11eec72a3e1c8db8c'
          'c1b8050cb887f261afd105efa6d8d5d9955c2d39'
          'fc88582d8865af2b3e58b09de6739f3fe9700cb6'
          '5072015802f4a0312ec2028cd4726dcaab72c69f')


install=${_pkgname}.install

prepare() {
    # These patches can be removed when a 1.7.1 tarball is released or
    # when this package is migrated to gtk3.
    cd "${srcdir}/${_pkgname}-${pkgver}"
    patch -Np1 -i "${srcdir}/a7a5e35d8a5418d9b9939f6de99367f72ded7b6d.diff"
    patch -Np1 -i "${srcdir}/603813e094a40707eb0d9e4238348c6bdf857993.diff"
    patch -Np1 -i "${srcdir}/1b401ff5fa2ca8e710986e61227389cedde10a05.diff"
    patch -Np1 -i "${srcdir}/27daac2e3469ec6620309b8bbcf947934874dd9d.diff"
}

build() {
    cd "${srcdir}/${_pkgname}-${pkgver}"
    ./configure \
        --prefix=/usr \
        --libexecdir=/usr/lib/${_pkgname} \
        --sysconfdir=/etc \
        --localstatedir=/var \
        --enable-introspection \
        --disable-static
    make
}

package() {
    cd "${srcdir}/${_pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" install
}