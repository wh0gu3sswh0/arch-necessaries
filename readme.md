# 🔧 Arch Package Installer
Автоматический установщик пакетов, которые я использую на Arch Linux.

## 📦 Устанавливаемые пакеты

### 1. 🛠 Инструменты разработки

- `git`, `clang`, `go`, `code`, `notepadqq`, `alacritty`
### 2. 📡 Сеть и сетевые утилиты

- `curl`, `wget`, `openssh`, `wireshark-qt`, `bluez`, `firefox`
### 3. 🧰 Системные утилиты

- `htop`, `zip`, `unzip`, `redshift`, `fastfetch`
### 4. 🎨 Медиа

- `gimp`, `obs-studio`
### 5. 📎 Документы и офис

- `libreoffice-still`
### 6. 💬 Прочее (AUR)

- `discord`, `telegram-desktop`, `spotify`, `obsidian`

---
## 🚀 Как использовать?

1. Клонируйте репозиторий:
    ```bash
    git clone https://github.com/yourusername/arch-package-installer.git
    cd arch-package-installer
    ```

2. Сделайте скрипт исполняемым:
    ```bash
    chmod +x install_packages.py
    ```

3. Запустите установщик:
    ```bash
    ./install_packages.py
    ```

Скрипт автоматически:
- Обновит систему и установит все официальные пакеты.
- Проверит и установит `yay` из AUR, если нужно.
- Установит указанные AUR-пакеты.

---
## ⚠️ Требования
- Arch/Arch-based дистрибутивы
- `sudo`
- Интернет
---
## 📬 Обратная связь
Предложения по наполнению принимаются в [**issues**](https://github.com/yourusername/arch-package-installer/issues).
Технические исправления и/или предложения - в **pull request'ы**