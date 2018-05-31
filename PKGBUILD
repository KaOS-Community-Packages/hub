pkgname=hub
pkgver=2.3.0
pkgrel=1
pkgdesc='A command-line wrapper for git that makes you better at GitHub'
arch=('x86_64')
url='https://hub.github.com/'
license=('MIT')
depends=('git')
makedepends=('go' 'ruby' 'ruby-bundler')
source=("https://github.com/github/${pkgname}/archive/v${pkgver}.tar.gz")
md5sums=('a04ae64b3802c1348a2d8eb43c84d027')

package() {
	cd "${srcdir}/${pkgname}-${pkgver}"
	make install prefix="${pkgdir}/usr"
	install -Dm644 "etc/hub.bash_completion.sh" "${pkgdir}/etc/bash_completion.d/${pkgname}"
	install -Dm644 "etc/hub.zsh_completion" "${pkgdir}/usr/share/zsh/site-functions/_${pkgname}"
	install -Dm644 "etc/hub.fish_completion" "${pkgdir}/usr/share/fish/vendor_completions.d/${pkgname}.fish"
}
