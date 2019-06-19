pkgname=hub
pkgver=2.12.0
pkgrel=1
pkgdesc='A command-line wrapper for git that makes you better at GitHub'
arch=('x86_64')
url='https://hub.github.com/'
license=('MIT')
depends=('git')
makedepends=('go')
source=("https://github.com/github/${pkgname}/archive/v${pkgver}.tar.gz")
md5sums=('152ade744eb6c9e9cc596b319ae5f501')
_basedir="src/github.com/github"

prepare() {
	_basedir="${srcdir}/${_basedir}"
	mkdir -p "${_basedir}"
	mv "${srcdir}/${pkgname}-${pkgver}" "${_basedir}/hub"
}

build() {
	cd "${_basedir}/hub"
	export GOPATH="${srcdir}"
	make
	make man-pages
}

package() {
	cd "${_basedir}/hub"
	make PREFIX="${pkgdir}/usr" install
	install -Dm644 "etc/hub.bash_completion.sh" "${pkgdir}/etc/bash_completion.d/${pkgname}"
	install -Dm644 "etc/hub.zsh_completion" "${pkgdir}/usr/share/zsh/site-functions/_${pkgname}"
	install -Dm644 "etc/hub.fish_completion" "${pkgdir}/usr/share/fish/vendor_completions.d/${pkgname}.fish"
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
