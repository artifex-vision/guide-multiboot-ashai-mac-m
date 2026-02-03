# 🍎 Multiboot-Guide: Asahi Linux auf Mac mit M-Chip

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Asahi Linux](https://img.shields.io/badge/Asahi-Linux-blue)](https://asahilinux.org/)
[![German](https://img.shields.io/badge/Sprache-Deutsch-red.svg)](README.md)

Ein umfassender, deutschsprachiger Leitfaden zur Installation und Konfiguration von Dual-Boot bzw. Multiboot mit Asahi Linux (Fedora & Arch) auf Apple Silicon Macs.

> **⚠️ Wichtig**: Dieser Guide bezieht sich auf Beta-Software. Erstelle immer ein vollständiges Backup vor der Installation!

## 📋 Inhaltsverzeichnis

1. [Was ist Asahi Linux?](#was-ist-asahi-linux)
2. [Für wen ist dieser Guide?](#für-wen-ist-dieser-guide)
3. [Voraussetzungen](#voraussetzungen)
4. [Vorbereitung & Backup](#vorbereitung--backup)
5. [Installation Asahi Linux Fedora](#installation-asahi-linux-fedora)
6. [Installation Asahi Linux Arch](#installation-asahi-linux-arch)
7. [Multiboot-Konfiguration](#multiboot-konfiguration)
8. [Boot-Management](#boot-management)
9. [Troubleshooting](#troubleshooting)
10. [Nützliche Ressourcen](#nützliche-ressourcen)

---

## 🚀 Schnellstart

Für erfahrene Benutzer:

```bash
# Asahi Linux Installer starten
curl https://alx.sh | sh
```

**Detaillierte Anleitung**: Siehe [Installation Asahi Linux Fedora](#installation-asahi-linux-fedora) oder [Installation Asahi Linux Arch](#installation-asahi-linux-arch)

---

## 📸 Vorschau

### Typisches Multiboot-Setup
```
┌─────────────────────────────────┐
│  macOS (Primary)                │  ← Dein gewohntes System
│  150 GB                         │
├─────────────────────────────────┤
│  Asahi Linux Fedora             │  ← Für Einsteiger empfohlen
│  100 GB                         │
├─────────────────────────────────┤
│  Asahi Linux Arch (optional)    │  ← Für Experten
│  80 GB                          │
└─────────────────────────────────┘
```

---

## Was ist Asahi Linux?

**Asahi Linux** ist ein Projekt, das darauf abzielt, Linux-Unterstützung für Apple Silicon Macs (M1, M1 Pro, M1 Max, M1 Ultra, M2, M2 Pro, M2 Max, M3, usw.) bereitzustellen. Es ermöglicht das Ausführen von Linux-Distributionen nativ auf Apple Silicon Hardware.

### Hauptmerkmale:
- **Native Performance**: Läuft direkt auf der Apple Silicon Hardware
- **GPU-Beschleunigung**: Unterstützt die Apple GPU (in Entwicklung)
- **Mehrere Distributionen**: Verfügbar für Fedora, Arch Linux und andere
- **Dual-/Multiboot**: Koexistenz mit macOS ohne Virtualisierung

---

## Für wen ist dieser Guide?

Dieser Guide richtet sich an:

✅ **Entwickler**, die Linux-Tools und -Umgebungen auf ihrer Mac-Hardware nutzen möchten  
✅ **Power-User**, die maximale Flexibilität zwischen macOS und Linux benötigen  
✅ **Open-Source-Enthusiasten**, die Linux auf moderner Apple Hardware erleben möchten  
✅ **Lernende**, die verschiedene Distributionen ohne separate Hardware testen möchten  
✅ **System-Administratoren**, die Mac-Hardware für Linux-Server nutzen möchten  

### Was du mitbringen solltest:
- Grundkenntnisse in Terminal/Kommandozeile
- Verständnis von Partitionierung und Dateisystemen
- Bereitschaft, mit Beta-Software zu arbeiten
- Geduld bei möglichen Hardware-Kompatibilitätsproblemen

---

## ⚙️ Voraussetzungen

### 💻 Hardware:
- Mac mit Apple Silicon (M1, M1 Pro/Max/Ultra, M2, M2 Pro/Max, M3 oder neuer)
- Mindestens **70 GB freier Speicherplatz** für eine Distribution
- **100+ GB empfohlen** für Multiboot mit mehreren Distributionen

### 💿 Software:
- macOS Monterey (12.3) oder neuer
- Aktuelles macOS-Update installiert
- Stabile Internetverbindung
- Administrator-Rechte auf dem Mac

### ⚠️ Wichtige Hinweise:
- **Keine externe Bootfähigkeit**: Asahi Linux kann nicht von externen Laufwerken booten  
- **Internes SSD erforderlich**: Installation nur auf interner SSD möglich  
- **Beta-Status**: Einige Features sind noch in Entwicklung

---

## 💾 Vorbereitung & Backup

### 1️⃣ Vollständiges Backup erstellen

**Time Machine Backup:**
```bash
# Time Machine über System-Einstellungen konfigurieren
# Oder manuell starten:
tmutil startbackup
```

**Alternative: Bootfähiges Backup mit Carbon Copy Cloner oder SuperDuper**

### 2️⃣ Freien Speicherplatz prüfen

```bash
df -h /
```

Stelle sicher, dass genügend freier Speicher verfügbar ist:
- **Minimum**: 70 GB pro Linux-Distribution
- **Empfohlen**: 100-150 GB für komfortable Nutzung
- **Multiboot**: +70 GB für jede zusätzliche Distribution

### 3️⃣ macOS aktualisieren

```bash
softwareupdate -l
softwareupdate -ia
```

### 4️⃣ FileVault deaktivieren (falls aktiviert)

FileVault kann den Installationsprozess komplizieren:
1. **Systemeinstellungen** → **Datenschutz & Sicherheit** → **FileVault**
2. FileVault deaktivieren (optional, aber empfohlen für Installation)
3. Nach Installation wieder aktivierbar

---

## 🐧 Installation Asahi Linux Fedora

Fedora Asahi Remix ist die empfohlene Distribution für Einsteiger.

### Schritt 1️⃣: Installer starten

```bash
curl https://alx.sh | sh
```

### Schritt 2️⃣: Installationsoptionen wählen

Der Installer führt dich durch folgende Schritte:

1. **Sprachauswahl**: Wähle deine bevorzugte Sprache
2. **Lizenzvereinbarung**: Akzeptiere die Nutzungsbedingungen
3. **Speicherplatzzuweisung**: 
   - Minimum: 70 GB
   - Empfohlen: 100-150 GB
4. **Desktop-Umgebung wählen**:
   - **KDE Plasma** (empfohlen für macOS-ähnliches Erlebnis)
   - **GNOME** (Standard Fedora Desktop)
   - **Minimal** (keine GUI, nur Terminal)

### Schritt 3️⃣: Partitionierung

```
Beispiel-Layout für 256 GB SSD:
├── macOS (150 GB)
└── Asahi Fedora (106 GB)
```

Der Installer erstellt automatisch:
- EFI System Partition (ESP)
- Root Partition (ext4)
- Optionale Swap-Partition

### Schritt 4️⃣: Installation durchführen

```bash
# Der Installer lädt automatisch herunter und installiert:
# - Linux Kernel (Asahi Fork)
# - Fedora Base System
# - Desktop Environment
# - Treiber und Firmware
```

**Dauer**: 20-45 Minuten (abhängig von Internetgeschwindigkeit)

### Schritt 5️⃣: Neustart und Konfiguration

Nach dem Neustart:
1. Mac startet in den Boot-Picker
2. Wähle **Asahi Linux** aus
3. Folge dem First-Boot-Setup
4. Erstelle Benutzerkonto
5. Konfiguriere Systemeinstellungen

### Schritt 6️⃣: System aktualisieren

```bash
sudo dnf update -y
sudo dnf upgrade -y
```

---

## 🏗️ Installation Asahi Linux Arch

Arch Linux bietet mehr Kontrolle und Anpassungsmöglichkeiten, erfordert aber mehr technisches Wissen.

### Schritt 1️⃣: Installer starten

```bash
curl https://alx.sh | sh
```

### Schritt 2️⃣: Arch Linux Minimal wählen

Wähle im Installer:
1. **"Asahi Linux Arch Linux"** oder **"Asahi Linux Minimal"**
2. Speicherplatzzuweisung (min. 70 GB)
3. Installation bestätigen

### Schritt 3️⃣: Nach der Installation

```bash
# System booten in Arch Linux
# Einloggen als root (initial)

# Netzwerk konfigurieren
systemctl start NetworkManager
systemctl enable NetworkManager
nmtui  # Für grafische Netzwerkkonfiguration
```

### Schritt 4️⃣: Basissystem einrichten

```bash
# Zeitzone setzen
timedatectl set-timezone Europe/Berlin

# Lokalisierung
echo "LANG=de_DE.UTF-8" > /etc/locale.conf
echo "de_DE.UTF-8 UTF-8" >> /etc/locale.gen
locale-gen

# Benutzer erstellen
useradd -m -G wheel -s /bin/bash deinname
passwd deinname

# Sudo-Rechte aktivieren
EDITOR=nano visudo
# Uncomment: %wheel ALL=(ALL:ALL) ALL
```

### Schritt 5️⃣: Desktop Environment installieren (optional)

**Option A: KDE Plasma**
```bash
pacman -S plasma-meta kde-applications
systemctl enable sddm
```

**Option B: GNOME**
```bash
pacman -S gnome gnome-extra
systemctl enable gdm
```

**Option C: i3 (Tiling Window Manager)**
```bash
pacman -S i3-wm i3status i3lock dmenu
```

### Schritt 6️⃣: Asahi-spezifische Pakete

```bash
# GPU-Treiber und Firmware
pacman -S mesa
pacman -S linux-asahi linux-asahi-headers

# Audio-Unterstützung
pacman -S pipewire pipewire-pulse wireplumber

# System aktualisieren
pacman -Syu
```

---

## 🔄 Multiboot-Konfiguration

### Dual-Boot Setup (macOS + 1 Linux)

Die einfachste Konfiguration:

```
┌─────────────────────────────────┐
│  macOS (Primary)                │
│  150 GB                         │
├─────────────────────────────────┤
│  Asahi Linux (Fedora/Arch)      │
│  100 GB                         │
└─────────────────────────────────┘
```

**Boot-Auswahl**: 
- Beim Start Power-Button gedrückt halten
- Startup-Manager zeigt beide Systeme

### Triple-Boot Setup (macOS + 2 Linux)

Beispiel: macOS + Fedora + Arch

```
┌─────────────────────────────────┐
│  macOS                          │
│  130 GB                         │
├─────────────────────────────────┤
│  Asahi Fedora                   │
│  90 GB                          │
├─────────────────────────────────┤
│  Asahi Arch                     │
│  80 GB                          │
└─────────────────────────────────┘
```

### Zweite Linux-Distribution hinzufügen

```bash
# In macOS den Asahi-Installer erneut ausführen
curl https://alx.sh | sh

# Wähle:
# 1. Neue Installation
# 2. Andere Distribution
# 3. Speicher zuweisen
```

**Wichtig**: 
- Jede Distribution benötigt eigene Partition
- Minimaler Overhead pro System: ~5-10 GB
- Boot-Manager verwaltet alle Systeme automatisch

### Shared Data Partition (optional)

Für Datenaustausch zwischen Systemen:

```bash
# In macOS: exFAT Partition erstellen
diskutil list
diskutil eraseDisk exFAT SHARED /dev/diskX

# In Linux mounten:
sudo mkdir /mnt/shared
sudo mount -t exfat /dev/nvme0n1pX /mnt/shared

# Automatisches Mounting via fstab:
echo "/dev/nvme0n1pX /mnt/shared exfat defaults 0 0" | sudo tee -a /etc/fstab
```

---

## 🚀 Boot-Management

### Apple Startup Manager verwenden

**Methode 1: Power-Button**
1. Mac einschalten
2. **Power-Button gedrückt halten** (~3 Sekunden)
3. Startup-Manager erscheint
4. System mit Pfeiltasten oder Touch auswählen

**Methode 2: Startup Disk (Standard-System ändern)**

In macOS:
```bash
# System-Einstellungen → Startvolume
# Oder via Terminal:
sudo systemsetup -setstartupdisk "/Volumes/VolumeName"
```

In Linux:
```bash
# Asahi Boot Manager verwenden
sudo asahi-bless --set-nvram
```

### Boot-Reihenfolge verwalten

Die Boot-Reihenfolge wird vom Apple Startup Manager verwaltet:

1. **Standard-System**: Das zuletzt gewählte System
2. **Alternative Systeme**: Zugriff über Power-Button-Methode
3. **Fallback**: macOS Recovery (Command + R beim Start)

### Schnellzugriff-Tastenkombinationen

| Tastenkombination | Funktion |
|-------------------|----------|
| Power-Button halten | Startup Manager |
| Command (⌘) + R | macOS Recovery |
| Option (⌥) | Alternative Boot-Optionen |

---

## 🔧 Troubleshooting

### Problem: System bootet nicht

**Lösung 1: Safe Mode**
```bash
# Beim Start Shift-Taste gedrückt halten
# Startet macOS im sicheren Modus
```

**Lösung 2: Recovery Mode**
```bash
# Command + R beim Start
# Über Terminal Disk Utility starten
# Partitionen prüfen
```

### Problem: Linux-Kernel-Panic

**Lösung:**
```bash
# Vom macOS aus:
diskutil list
sudo bless --folder /Volumes/YourLinux/boot/efi --setBoot

# Oder Linux neu installieren mit aktueller Version
```

### Problem: Keine WLAN-Verbindung in Linux

**Lösung:**
```bash
# Firmware-Update durchführen
sudo dnf update linux-firmware  # Fedora
sudo pacman -S linux-firmware    # Arch

# NetworkManager neu starten
sudo systemctl restart NetworkManager
```

### Problem: Audio funktioniert nicht

**Lösung:**
```bash
# Pipewire-Status prüfen
systemctl --user status pipewire

# Neu starten
systemctl --user restart pipewire pipewire-pulse

# Falls nicht installiert (Arch):
pacman -S pipewire pipewire-pulse pipewire-alsa wireplumber
```

### Problem: Bildschirm-Helligkeit nicht anpassbar

**Lösung:**
```bash
# Backlight manuell setzen
echo 50 | sudo tee /sys/class/backlight/apple-panel-bl/brightness

# Oder brightness-controller installieren:
sudo dnf install brightness-controller  # Fedora
yay -S brightness-controller            # Arch
```

### Problem: Touchpad funktioniert nicht optimal

**Lösung:**
```bash
# libinput-Parameter anpassen
sudo nano /etc/X11/xorg.conf.d/30-touchpad.conf

# Inhalt:
Section "InputClass"
    Identifier "touchpad"
    Driver "libinput"
    MatchIsTouchpad "on"
    Option "Tapping" "on"
    Option "NaturalScrolling" "true"
    Option "DisableWhileTyping" "on"
EndSection
```

### Problem: Partition vergrößern/verkleinern

**Von macOS aus:**
```bash
# Diskutil verwenden
diskutil list
sudo diskutil resizeVolume disk0s5 80G
```

**Wichtig**: Immer Backup vor Partitionsänderungen!

---

## 📚 Nützliche Ressourcen

### Offizielle Quellen

- **Asahi Linux Website**: [https://asahilinux.org/](https://asahilinux.org/)
- **GitHub Repository**: [https://github.com/AsahiLinux](https://github.com/AsahiLinux)
- **Dokumentation**: [https://github.com/AsahiLinux/docs/wiki](https://github.com/AsahiLinux/docs/wiki)

### Community & Support

- **Reddit**: [r/AsahiLinux](https://reddit.com/r/AsahiLinux)
- **IRC**: #asahi on OFTC
- **Discord**: Asahi Linux Community Server
- **Matrix**: #asahi:matrix.org

### Fedora Asahi Remix

- **Website**: [https://fedora-asahi-remix.org/](https://fedora-asahi-remix.org/)
- **Repo**: [https://github.com/fedora-asahi-remix](https://github.com/fedora-asahi-remix)

### Arch Linux ARM

- **Asahi Wiki**: [https://github.com/AsahiLinux/docs/wiki/Arch-Linux-ARM-Installation-Guide](https://github.com/AsahiLinux/docs/wiki/Arch-Linux-ARM-Installation-Guide)
- **Package Repository**: [https://github.com/AsahiLinux/PKGBUILDs](https://github.com/AsahiLinux/PKGBUILDs)

### Weitere Ressourcen

- **Hardware-Kompatibilität**: Regelmäßige Updates zur Treiberunterstützung
- **Feature-Status**: [https://github.com/AsahiLinux/docs/wiki/Feature-Support](https://github.com/AsahiLinux/docs/wiki/Feature-Support)
- **Bug-Tracking**: GitHub Issues für Problemberichte

---

## ❓ FAQ

**Q: Kann ich Asahi Linux wieder deinstallieren?**  
A: Ja, über den Asahi-Installer mit der Option "Uninstall" oder über macOS Disk Utility die Partition löschen.

**Q: Funktioniert Bluetooth?**  
A: Ja, Bluetooth wird unterstützt, kann aber bei einigen Modellen noch Probleme haben.

**Q: Kann ich Windows auch installieren?**  
A: Nein, Windows läuft nicht nativ auf Apple Silicon. Nur über Virtualisierung (Parallels, VMware).

**Q: Wie ist die Performance im Vergleich zu macOS?**  
A: Nahezu identisch bei CPU-lastigen Tasks. GPU-Beschleunigung ist noch in Entwicklung.

**Q: Ist mein M3 Mac unterstützt?**  
A: Die Unterstützung wird kontinuierlich erweitert. Prüfe die offizielle Feature-Support-Seite.

---

## 🤝 Beiträge

Verbesserungen und Korrekturen sind herzlich willkommen! 

- 📝 [Contribution Guidelines](CONTRIBUTING.md)
- 🐛 [Issue erstellen](https://github.com/artifex-vision/guide-multiboot-ashai-mac-m/issues/new/choose)
- 🔀 [Pull Request erstellen](https://github.com/artifex-vision/guide-multiboot-ashai-mac-m/pulls)

Bitte lies den [Code of Conduct](CODE_OF_CONDUCT.md) vor der Teilnahme.

---

## 📄 Lizenz

Dieser Guide ist unter der [MIT-Lizenz](LICENSE) verfügbar und darf frei verwendet und angepasst werden.

## 👥 Autoren & Mitwirkende

Ein Dank an alle, die zu diesem Projekt beitragen!

---

## ⭐ Support

Wenn dir dieser Guide geholfen hat, gib dem Projekt einen Stern auf GitHub! ⭐

---

**Letztes Update**: Februar 2024  
**Version**: 2.0  
**Status**: Aktiv gepflegt
