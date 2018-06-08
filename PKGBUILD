pkgname=hub
pkgver=2.4.0
pkgrel=1
pkgdesc='A command-line wrapper for git that makes you better at GitHub'
arch=('x86_64')
url='https://hub.github.com/'
license=('MIT')
depends=('git')
makedepends=('go' 'ruby' 'ruby-bundler')
source=("https://github.com/github/${pkgname}/archive/v${pkgver}.tar.gz")
md5sums=('7c8d1cb96a1522584a9b679f3d4ef3a7')

package() {
	cd "${srcdir}/${pkgname}-${pkgver}"
	make install prefix="${pkgdir}/usr"
	install -Dm644 "etc/hub.bash_completion.sh" "${pkgdir}/etc/bash_completion.d/${pkgname}"
	install -Dm644 "etc/hub.zsh_completion" "${pkgdir}/usr/share/zsh/site-functions/_${pkgname}"
	install -Dm644 "etc/hub.fish_completion" "${pkgdir}/usr/share/fish/vendor_completions.d/${pkgname}.fish"
}
