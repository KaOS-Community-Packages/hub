pkgname=hub
pkgver=2.12.3
pkgrel=1
pkgdesc='A command-line wrapper for git that makes you better at GitHub'
arch=('x86_64')
url='https://hub.github.com/'
license=('MIT')
depends=('git')
makedepends=('go')
source=("https://github.com/github/${pkgname}/archive/v${pkgver}.tar.gz")
md5sums=('dc28fa59b0f898b227d3ce2271140dff')
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
