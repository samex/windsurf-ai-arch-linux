# Maintainer: Samet Güzeldemirci <samet@guzeldemirci.com>

pkgname=windsurf-ai-bin
_pkgname=Windsurf-AI
pkgver=1.3.4
pkgrel=1
pkgdesc="Codeium Windsurf AI Editor: A standalone VS Code derivative with AI-powered coding assistance (binary package)"
arch=('x86_64')
url="https://codeium.com/"
license=('MIT')
depends=('libxkbfile' 'gtk3' 'libsecret' 'nss' 'gcc-libs' 'libnotify' 'libxss' 'glibc' 'xdg-utils' 'alsa-lib')
optdepends=('glib2: Needed for move to trash functionality'
            'libdbusmenu-glib: Needed for KDE global menu')
provides=('windsurf-ai')
conflicts=('windsurf-ai')
source=("windsurf-ai.desktop::https://raw.githubusercontent.com/samex/windsurf-ai-arch-linux/main/windsurf-ai.desktop"
        "windsurf-ai-url-handler.desktop::https://raw.githubusercontent.com/samex/windsurf-ai-arch-linux/main/windsurf-ai-url-handler.desktop"
        "windsurf-ai-bin.sh::https://raw.githubusercontent.com/samex/windsurf-ai-arch-linux/main/windsurf-ai-bin.sh"
        "Windsurf-linux-x64-${pkgver}.tar.gz::Windsurf-linux-x64-${pkgver}.tar.gz::https://github.com/samex/windsurf-ai-arch-linux/releases/download/${pkgver}/Windsurf-linux-x64-${pkgver}.tar.gz")
sha256sums=('8e33fc5dce1a865ba920c4093eaabd88b97c80f6f20edcf4788c30ce7b499512'
            '043f74feb5946ca5b98dbc1bf8af0d5377a3e1308b77c426de8ad5645331915e'
            '93f57c2a6ccd01e35420d29a50dbb26ff1c03bb6982d0daa15ba000b2514f026'
            '6dcf686038c6587410b25dd041a748a59593164b6c3ffb31935abef1325bfa8c')

prepare() {
    mkdir -p "${srcdir}/windsurf-latest"
    tar -xzf "Windsurf-linux-x64-${pkgver}.tar.gz" -C "${srcdir}/windsurf-latest"
}

package() {
    install -d "${pkgdir}/opt/${_pkgname}"
    cp -r "${srcdir}/windsurf-latest/"* "${pkgdir}/opt/${_pkgname}"

    install -d "${pkgdir}/usr/bin"
    install -m755 "${srcdir}/windsurf-ai-bin.sh" "${pkgdir}/usr/bin/windsurf-ai"

    install -d "${pkgdir}/usr/share/applications"
    install -m644 "${srcdir}/windsurf-ai.desktop" "${pkgdir}/usr/share/applications/windsurf-ai.desktop"
    install -m644 "${srcdir}/windsurf-ai-url-handler.desktop" "${pkgdir}/usr/share/applications/windsurf-ai-url-handler.desktop"

    install -d "${pkgdir}/usr/share/icons/hicolor/128x128/apps" 
    install -m644 "${srcdir}/windsurf-latest/resources/app/resources/linux/code.png" "${pkgdir}/usr/share/icons/hicolor/128x128/apps/windsurf-ai.png"
}
