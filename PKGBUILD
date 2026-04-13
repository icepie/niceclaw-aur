pkgname=niceclaw
pkgver=0.9.411
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
  '86855bcb7cca30efcf41692b53e2c31a54a7565a5f5ee3b27433745bacc934c8f1d1ca8e4e25ee82253ccbc5597e39995a4f833a3e6b6e7056dd8571b66dbc50'
)
sha512sums_aarch64=(
  '9f22d317ab0fe95989ba1a58a60295c775a54481fc43caaef3c17e8bee6013a4c10a876dd04be60342bac839728498e37c49ca588d0b372df75ced54ec9ea0fc'
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
