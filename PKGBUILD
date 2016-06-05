pkgname=ivy-icon-theme
pkgver=2016.06.05
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
source=('https://github.com/sixsixfive/Ivy/releases/download/PreRelese/ivy-icon-theme.txz')
noextract=('ivy-icon-theme.txz')
sha256sums=('SKIP')

pkgver() {
	printf "$(curl https://github.com/sixsixfive/Ivy/releases|grep -oP "<h5>(.*)</h5>"|cut -d ">" -f 2|cut -d "<" -f 1|head -n 1|tr - .)"
}

auto_distroicon() {
	if [ $(cat /etc/os-release|grep "^ID=debian$") ];then
		if dpkg --get-selections|grep siduction &>/dev/null;then
			_distributor="siduction"
		else
			_distributor="debian"
		fi
	elif [ $(cat /etc/os-release|grep "^ID=opensuse$") ];then
		_distributor="suse"
	elif [ $(cat /etc/os-release|grep "^ID=kaos$") ];then
		_distributor="kaos"
	elif [ $(cat /etc/os-release|grep "^ID=chakra$") ];then
		_distributor="chakra"
	fi
	if [ -f /etc/manjaro-release ];then
		_distributor="manjaro"
	fi
	if [ -f 48/logos/emblem-$_distributor.png ];then
		for _dir in $(echo $(find -maxdepth 1 -mindepth 1 -type d));do
			cd $_dir
			cp -fv logos/emblem-$_distributor.png logos/emblem-distributor.png
			cd $_basedir
		done
	fi
}

package() {
	install -d "${pkgdir}"/usr/share/icons
	tar -xvf "${srcdir}"/ivy-icon-theme.txz -C "${pkgdir}"/usr/share/icons
	cd "${pkgdir}"/usr/share/icons/Ivy
	_basedir="${pkgdir}"/usr/share/icons/Ivy
	auto_distroicon
}
