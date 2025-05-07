#!/usr/bin/env python3

import subprocess
import sys
import shutil

official_packages = [
    "git", "htop", "curl", "openssh", "zip", "unzip", "wget",
    "clang", "go", "code", "redshift", "firefox",
    "wireshark-qt", "bluez", "obs-studio", "gimp",
    "alacritty", "fastfetch", "libreoffice-still", "notepadqq"
]

aur_packages = [
    "discord", "telegram-desktop", "spotify", "obsidian"
]

YAY_BUILD_DIR = "/tmp/yay-build"

def run(cmd, **kwargs):
    print(f"▶️  Запуск: {' '.join(cmd)}")
    subprocess.run(cmd, check=True, **kwargs)

def install_requirements():
    # requirements.txt to-do
    print("\n📦 Установка Python-зависимостей из requirements.txt…")
    run([sys.executable, "-m", "pip", "install", "--upgrade", "-r", "requirements.txt"])

def install_official():
    print("\n🔧 Установка официальных пакетов...")
    run(["sudo", "pacman", "-Syu", "--noconfirm"])
    run(["sudo", "pacman", "-S", "--noconfirm"] + official_packages)

def install_yay():
    if shutil.which("yay"):
        print("\n✅ yay уже установлен, пропускаем шаг.")
        return

    print("\n🌱 Устанавливаем yay из AUR…")
    run(["sudo", "pacman", "-S", "--needed", "--noconfirm", "base-devel", "git"])
    run(["rm", "-rf", YAY_BUILD_DIR])
    run(["mkdir", "-p", YAY_BUILD_DIR])
    run(["git", "clone", "https://aur.archlinux.org/yay.git", YAY_BUILD_DIR])
    run(["bash", "-lc", f"cd {YAY_BUILD_DIR} && makepkg -si --noconfirm"])
    print("🎉 yay установлен!")

def install_aur():
    print("\n🌐 Установка AUR-пакетов через yay...")
    run(["yay", "-S", "--noconfirm"] + aur_packages)

def main():
    try:
        install_requirements()
        install_official()
        install_yay()
        install_aur()
        print("\n🎊 Все пакеты успешно установлены! Наслаждайся своей системой 😄")
    except subprocess.CalledProcessError as e:
        print(f"\n❌ Ошибка при выполнении: {e}")
        sys.exit(1)

if __name__ == "__main__":
    main()
