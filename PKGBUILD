pkgname=hub
pkgver=2.2.2
pkgrel=1
pkgdesc='A command-line wrapper for git that makes you better at GitHub'
arch=('x86_64')
url='https://hub.github.com/'
license=('MIT')
depends=('git')
makedepends=('go')
source=("https://github.com/github/${pkgname}/archive/v${pkgver}.tar.gz")
md5sums=('7edc8f5b5d3c7c392ee191dd999596fc')
_package="github.com/github/${pkgname}"

prepare() {
	mkdir -p "src/${_package}"
	cp -r "${pkgname}-${pkgver}/"* "src/${_package}"
	export GOPATH=$GOPATH:"${srcdir}"
}

build() {
	[[ -e build ]] || mkdir build
	go build -v -o "build/${pkgname}" "src/${_package}/main.go"
}

package() {
	install -Dm755 "build/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
	install -Dm644 "src/${_package}/etc/hub.bash_completion.sh" "${pkgdir}/etc/bash_completion.d/${pkgname}"
	install -Dm644 "src/${_package}/etc/hub.zsh_completion" "${pkgdir}/usr/share/zsh/site-functions/_${pkgname}"
	install -Dm644 "src/${_package}/man/hub.1" "${pkgdir}/usr/share/man/man1/${pkgname}.1"
}
