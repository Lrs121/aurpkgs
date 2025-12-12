pkgname=lubelogger
altname=lubelog
pkgver=1.5.5
pkgrel=1
pkgdesc="A self-hosted, open-source vehicle service records and maintainence tracker."
arch=('any')
url="https://github.com/hargata/lubelog"
license=('MIT')

depends=('dotnet-runtime' 'aspnet-runtime')
makedepends=('dotnet-sdk')

source=("${altname}-${pkgver}.tar.gz::https://github.com/hargata/lubelog/archive/refs/tags/v${pkgver}.tar.gz"
  'lubelogger.service'
  'sysusers'
  'tmpfiles'
)
sha256sums=('8331c3476cfc1026df6e1998a755dbd0065badc37140651198399e1b53e5a933'
            '37b77224dd7e98cf3bb73a606a12da4990143e37ba78109f87706003cfdf427f'
            'a638ea4b0652e78b2f1cbdb46f160c9d5b10e31f09fdd0a64ed80cbf6fb8209d'
            'ca5a4b6b6c2bf761b5e7b767e401e9bf99452eaba078affff8ab65e73ce5baae')

backup=()
options=('!strip')
prepare() {
    cd "${srcdir}/${altname}-${pkgver}"
}

build() {
    cd "${srcdir}/${altname}-${pkgver}"
    dotnet publish CarCareTracker.sln --configuration Release --self-contained false
}

package() {

    install -d -m 0755 "${pkgdir}/usr/share/webapps/lubelogger"
    cd "${srcdir}/${altname}-${pkgver}/bin/Release/net8.0/publish"
    cp -r ./* "${pkgdir}/usr/share/webapps/lubelogger"

    install -d -m 0750 "${pkgdir}/var/lib/lubelogger"

    cd "${srcdir}"
    install -D -m 0644 sysusers "${pkgdir}/usr/lib/sysusers.d/lubelogger.conf"
    install -D -m 0644 tmpfiles "${pkgdir}/usr/lib/tmpfiles.d/lubelogger.conf"
    install -D -m 0644 lubelogger.service "${pkgdir}/usr/lib/systemd/system/lubelogger.service"
}
