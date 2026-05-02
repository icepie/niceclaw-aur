pkgname=niceclaw
pkgver=0.9.429
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
  'e94ff954b9232cb0f0c3b0848d8f62b9709a9744ab223a8e636337f488041611942fc8d07e077a6b677dea5782197d0c732ec185cc574ccf807c8b0ba9874a5b'
)
sha512sums_aarch64=(
  'cd61b1b33dc79d63d11bd1385bee9da153e429fc83d48462e5a26dafa552b9085e263b3ba20e78e74e28df4a9e34dc843e1dc5425112e22252bbf8a631ef76ed'
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
