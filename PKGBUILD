pkgname=hub
pkgver=2.7.0
pkgrel=1
pkgdesc='A command-line wrapper for git that makes you better at GitHub'
arch=('x86_64')
url='https://hub.github.com/'
license=('MIT')
depends=('git')
source=("https://github.com/github/${pkgname}/releases/download/v${pkgver}/hub-linux-amd64-${pkgver}.tgz")
md5sums=('b9b8423ab3de51ecd9f6789ecef6d4cb')

package() {
	cd "${srcdir}/${pkgname}-linux-amd64-${pkgver}"
	mkdir "${pkgdir}/usr"
	cp -a bin share "${pkgdir}/usr"
	rm "${pkgdir}/usr/share/man/man1/"*.txt
	install -Dm644 "etc/hub.bash_completion.sh" "${pkgdir}/etc/bash_completion.d/${pkgname}"
	install -Dm644 "etc/hub.zsh_completion" "${pkgdir}/usr/share/zsh/site-functions/_${pkgname}"
	install -Dm644 "etc/hub.fish_completion" "${pkgdir}/usr/share/fish/vendor_completions.d/${pkgname}.fish"
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
