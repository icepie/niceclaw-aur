pkgname=niceclaw
pkgver=0.9.509
pkgrel=1
pkgdesc="Desktop AI agent for OpenClaw with bundled gateway runtime"
arch=('x86_64' 'aarch64')
url="https://claw.nicerouter.com/"
license=('AGPL-3.0-or-later')
depends=(
  'at-spi2-core'
  'gtk3'
  'libnotify'
  'libsecret'
  'libxss'
  'libxtst'
  'nss'
  'util-linux-libs'
  'xdg-utils'
)
optdepends=('libappindicator-gtk3: tray indicator support on some desktop environments')
options=('!strip')
source_x86_64=(
  "niceclaw-${pkgver}-x86_64.deb::https://pan.feidu.fit/d/%E5%BC%80%E5%8F%91/tmp/NiceClaw-${pkgver}-amd64-linux.deb"
)
source_aarch64=(
  "niceclaw-${pkgver}-aarch64.deb::https://pan.feidu.fit/d/%E5%BC%80%E5%8F%91/tmp/NiceClaw-${pkgver}-arm64-linux.deb"
)
sha512sums_x86_64=(
  '05e31071b13ad8868af23215aed6e63f52c311c0711459c5aa90efc437c349dd817ce48341c7d741e8df4d349f1da599ce96212e02efe21ab8e1dc8acc66ea99'
)
sha512sums_aarch64=(
  '950787f505d53129552d0b522de5e4c40123c5d6f3e3cbec46581a55cec7c8c599420293cc12a07da7527722f8d30d901fdb869072bb398b43a333ba6f168cd2'
)

package() {
  local _deb
  local _workdir="$srcdir/deb-extract"

  case "$CARCH" in
    x86_64)
      _deb="niceclaw-${pkgver}-x86_64.deb"
      ;;
    aarch64)
      _deb="niceclaw-${pkgver}-aarch64.deb"
      ;;
  esac

  rm -rf "$_workdir"
  mkdir -p "$_workdir"

  cd "$_workdir"
  ar x "$srcdir/$_deb"
  bsdtar -xf data.tar.xz -C "$pkgdir"

  install -d "$pkgdir/usr/bin"
  ln -sf /opt/NiceClaw/niceclaw "$pkgdir/usr/bin/niceclaw"
}
