pkgname=ivy-icon-theme
pkgver=2016.05.30
pkgrel=1
pkgdesc="A colorful and sharp icon theme"
arch=('x86_64')
url="https://github.com/sixsixfive/Ivy"
license=('CCPL:cc-by-sa-4.0')
depends=('hicolor-icon-theme')
makedepends=('tar' 'xz' 'curl' 'coreutils')
provides=("${pkgname}=$pkgver")
replaces=("${pkgname}<=$pkgver")
conflicts=("${pkgname}<=$pkgver")
options=('!optipng')
source=('https://github.com/sixsixfive/Ivy/releases/download/PreRelese/ivy-icon-theme.txz')
noextract=('ivy-icon-theme.txz')
sha256sums=('SKIP')

pkgver() {
	printf "$(curl https://github.com/sixsixfive/Ivy/releases|grep -oP "<h5>(.*)</h5>"|cut -d ">" -f 2|cut -d "<" -f 1|head -n 1|tr - .)"
}

package() {
	install -d "${pkgdir}"/usr/share/icons
	tar -xvf "${srcdir}"/ivy-icon-theme.txz -C "${pkgdir}"/usr/share/icons
}
