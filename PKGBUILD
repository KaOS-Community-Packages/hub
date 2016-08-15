pkgname=hub
pkgver=2.2.5
pkgrel=1
pkgdesc='A command-line wrapper for git that makes you better at GitHub'
arch=('x86_64')
url='https://hub.github.com/'
license=('MIT')
depends=('git')
makedepends=('go')
source=("https://github.com/github/${pkgname}/archive/v${pkgver}.tar.gz")
md5sums=('3cd1510af5f61d71bc1d429bff915c92')
_package="github.com/github/${pkgname}"

prepare() {
	mkdir -p "src/${_package}"
	cp -r "${pkgname}-${pkgver}/"* "src/${_package}"
	_OLDGOPATH=$GOPATH
	export GOPATH=${srcdir}
}

build() {
	[[ -e build ]] || mkdir build
	go build -v -o "build/${pkgname}" "src/${_package}/main.go"
	export GOPATH=$_OLDGOPATH
}

package() {
	install -Dm755 "build/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
	install -Dm644 "src/${_package}/etc/hub.bash_completion.sh" "${pkgdir}/etc/bash_completion.d/${pkgname}"
	install -Dm644 "src/${_package}/etc/hub.zsh_completion" "${pkgdir}/usr/share/zsh/site-functions/_${pkgname}"
	install -Dm644 "src/${_package}/man/hub.1" "${pkgdir}/usr/share/man/man1/${pkgname}.1"
}
