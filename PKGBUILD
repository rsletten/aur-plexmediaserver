# Contributor: Praekon <praekon@googlemail.com>
# Contributor: Arthur <arthur.darcet@m4x.org>
# Contributor: Jon Wiersma <archaur@jonw.org>
# Contributor: monty <linksoft [at] gmx [dot] de>
# Contributor: Tom Moore <t.moore01 [at] gmail [dot] com>
# Maintainer: Rob Sletten <rsletten [at] gmail [dot] com>

pkgname=plexmediaserver
pkgver=0.9.8.18.290
pkgrel=2
_subver=11b7fdd
pkgdesc="Plex Media Server for Linux"
url='http://www.plexapp.com'
arch=('i686' 'x86_64')
license=('closed')
depends=('rsync' 'avahi')
conflicts=('plexmediaserver-plexpass')
backup=('etc/conf.d/plexmediaserver')
install='plexmediaserver.install'

if [ "$CARCH" = "i686" ]; then
       _arch='i386'
       md5sums=('9ae693e00b4297280eb05f251c166b13')
elif [ "$CARCH" = "x86_64" ]; then
       _arch='amd64'
       md5sums=('1da3181e54f6bbd7c6870370205e2035')
fi

source=("http://downloads.plexapp.com/plex-media-server/${pkgver}-${_subver}/${pkgname}_${pkgver}-${_subver}_${_arch}.deb" "${pkgname}.conf.d" "${pkgname}.service" "start_pms")
md5sums+=('32cdd9f9de446f6646616a0077151726'
	  'd850fe41dd35aba09a375ac8d81175e0'
	  '69efb2441c7971a9e546d76b51cd12cc')

build() {
       ar -xv plexmediaserver_${pkgver}-${_subver}_${_arch}.deb || return 1
       tar -zxf data.tar.gz || return 1
}

package() {
       mkdir -p "${pkgdir}"/opt/plexmediaserver
       mkdir -p "${pkgdir}"/usr/lib/systemd/system

       cp -r usr/lib/plexmediaserver/* "${pkgdir}"/opt/plexmediaserver/

       install -Dm755 ${srcdir}/start_pms "${pkgdir}"/opt/plexmediaserver/
       install -Dm644 ${srcdir}/plexmediaserver.conf.d "${pkgdir}"/etc/conf.d/plexmediaserver
       install -Dm644 ${srcdir}/plexmediaserver.service "${pkgdir}"/usr/lib/systemd/system/plexmediaserver.service
}
