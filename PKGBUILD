# Maintainer:  isiachi <isiachi@rhyeworld.it>

pkgname=telegram-desktop-autoupdate
pkgver=LATEST
pkgrel=2
pkgdesc="Official desktop version of Telegram messaging app. (Autoupdate support)"
arch=('i686' 'x86_64')
url="https://desktop.telegram.org"
license=('GPL v3')
depends=('libx11' 'libgcrypt' 'libasyncns' 'libsndfile' 'libsystemd' 'libdbus' 'openal' 'libogg' 'opus' 'opusfile' 'portaudio' 'openssl' 'zlib' 'libexif' 'xz')
optdepends=('libappindicator-gtk3: Allow applications to export a menu into the Unity Menu bar' 
            'libappindicator-gtk2: Allow applications to export a menu into the Unity Menu bar')
makedepends=('wget')
source=('telegram')
sha256sums=('b22119e6b3dd34ee293cc60ccdb9bf6a0dd2f42782ef3dfc7dd2733cad94f938')
conflicts=('telegram-bin')
provides=('telegram-bin')
#replaces=('')
install="$pkgname.install"

prepare() {
    if [[ $CARCH == "x86_64" ]]; then
        wget -O telegram-bin.tar.xz https://tdesktop.com/linux
    elif [[ $CARCH == "i686" ]]; then
        wget -O telegram-bin.tar.xz https://tdesktop.com/linux
    fi
}

package() {
    cd "$srcdir/"
    
    msg2 "  -> Extracting files..."
    tar Jxvf  telegram-bin.tar.xz -C .
    
    msg2 "  -> Installing program..."
    # install -d $pkgdir/{opt/telegram,usr/bin,usr/share}
    install -dm755 "$pkgdir/opt/telegram/"
    install -dm755 "$pkgdir/usr/bin"
    # install -dm755 "$pkgdir/usr/share"

    # Program
    echo "$pkgdir/opt/telegram/"
    # cp -r "$srcdir/Telegram/"* "$pkgdir/opt/telegram/"
    install -Dm775 -g 100 "$srcdir/Telegram/Telegram" "$pkgdir/opt/telegram/"
    # install -Dm644 "$srcdir/Telegram/Updater" "$pkgdir/opt/telegram/"
    install -Dm775 -g 100 "$srcdir/Telegram/Updater" "$pkgdir/opt/telegram/"
    
    # Link to program
    # ln -s "/opt/telegram/Telegram" "$pkgdir/usr/bin/telegram"
    cp -u "$srcdir/telegram" "$pkgdir/usr/bin/"

    # Icon
    # msg2 "  -> Installing icons..."
    # install -Dm644 "$srcdir/telegram.svg" "$pkgdir/usr/share/pixmaps/telegram.svg"
    # ~/.TelegramDesktop/tdata/icon.png


    # Desktop file
    # msg2 "  -> Installing .desktop file..." 
    # install -Dm644 "$srcdir/telegram.desktop" "$pkgdir/usr/share/applications/telegram.desktop"
    # ~/.local/share/applications/telegramdesktop.desktop
}
