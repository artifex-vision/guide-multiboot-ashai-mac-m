# Asahi Linux Installationsguide für Silicon Macs (M1/M2/M3)

Ein umfassender Guide zur Installation von Asahi Linux auf Apple Silicon Macs mit Multi-Boot-Unterstützung.

## 📋 Inhaltsverzeichnis

- [Was ist Asahi Linux?](#was-ist-asahi-linux)
- [Vorteile von Asahi Linux](#vorteile-von-asahi-linux)
- [Für wen ist Asahi Linux geeignet?](#für-wen-ist-asahi-linux-geeignet)
- [Systemanforderungen](#systemanforderungen)
- [Vorbereitung](#vorbereitung)
- [Schritt-für-Schritt Installationsanleitung](#schritt-für-schritt-installationsanleitung)
- [Post-Installation](#post-installation)
- [Troubleshooting](#troubleshooting)
- [Weitere Ressourcen](#weitere-ressourcen)

---

## Was ist Asahi Linux?

Asahi Linux ist ein Projekt, das Linux auf Apple Silicon Macs (M1, M2, M3) portiert. Es ermöglicht das native Ausführen von Linux auf der ARM64-Architektur von Apple und bietet dabei eine vollständige Desktop-Linux-Erfahrung.

---

## ✨ Vorteile von Asahi Linux

### 🚀 Performance
- **Native ARM64-Unterstützung**: Optimiert für Apple Silicon Chips
- **Voller Zugriff auf CPU-Kerne**: Maximale Performance ohne Virtualisierung
- **Effiziente Energieverwaltung**: Längere Akkulaufzeit im Vergleich zu virtuellen Maschinen

### 🔧 Entwicklung
- **Native Linux-Entwicklungsumgebung**: Perfekt für Software-Entwicklung
- **Zugriff auf Linux-Tools**: Alle gängigen Entwicklungstools und Compiler
- **Container und Kubernetes**: Native Docker- und Kubernetes-Unterstützung
- **Server-Software**: Möglichkeit zum Testen von Server-Anwendungen

### 💡 Flexibilität
- **Multi-Boot**: Parallele Nutzung von macOS und Linux
- **Mehrere Distributionen**: Unterstützung für Fedora, Arch Linux und mehr
- **Freie Software**: Open-Source und Community-getrieben
- **Anpassbarkeit**: Vollständige Kontrolle über das System

### 🎓 Lernen
- **Linux-Kenntnisse**: Ideal zum Erlernen von Linux
- **System-Administration**: Praktische Erfahrung mit Linux-Systemen
- **Open-Source-Community**: Teil einer aktiven Entwickler-Community

### 💰 Kostenlos
- **Keine Lizenzkosten**: Komplett kostenlos und Open-Source
- **Keine VM-Overhead**: Bessere Performance als virtuelle Maschinen

---

## 👥 Für wen ist Asahi Linux geeignet?

### ✅ Perfekt geeignet für:

**Software-Entwickler**
- Entwickler, die eine native Linux-Umgebung für Development benötigen
- Backend-Entwickler, die auf Linux-Server deployen
- DevOps-Engineers, die mit Linux-basierten Tools arbeiten

**System-Administratoren**
- IT-Profis, die Linux-Systeme verwalten
- Personen, die Linux-Server testen und verwalten müssen

**Tech-Enthusiasten**
- Personen, die gerne mit neuen Technologien experimentieren
- Open-Source-Enthusiasten
- Linux-Fans, die Mac-Hardware nutzen

**Studenten und Lernende**
- Informatik-Studenten, die Linux lernen möchten
- Personen, die sich auf Linux-Zertifizierungen vorbereiten
- Programmierer, die ihre Fähigkeiten erweitern möchten

**Power-User**
- Nutzer, die das Maximum aus ihrer Hardware herausholen möchten
- Personen, die verschiedene Betriebssysteme für unterschiedliche Aufgaben nutzen

### ⚠️ Weniger geeignet für:

- Personen, die ausschließlich macOS-spezifische Software nutzen
- Nutzer, die keine technischen Kenntnisse haben oder erwerben möchten
- Anwender, die 100% Stabilität für produktive Arbeit benötigen (das Projekt ist noch in aktiver Entwicklung)
- Personen, die GPU-intensive Anwendungen (3D-Rendering, Gaming) nutzen möchten

### 🤔 Warum Asahi Linux?

**Hauptgründe für die Installation:**

1. **Native Performance**: Deutlich schneller als VMs (Virtual Machines)
2. **Vollständige Hardware-Nutzung**: Direkter Zugriff auf alle CPU-Kerne
3. **Echtes Linux**: Keine Kompromisse durch Virtualisierung
4. **Lernumgebung**: Perfekt zum Lernen und Experimentieren
5. **Entwicklung**: Ideale Umgebung für Linux-basierte Entwicklung
6. **Kostenlos**: Keine Lizenzkosten für Virtualisierungs-Software

---

## 💻 Systemanforderungen

### Hardware
- **Mac mit Apple Silicon**: M1, M1 Pro, M1 Max, M1 Ultra, M2, M2 Pro, M2 Max, M2 Ultra, M3, M3 Pro, M3 Max
- **Freier Speicherplatz**: Mindestens 53 GB (empfohlen 100+ GB)
- **RAM**: Mindestens 8 GB (empfohlen 16 GB oder mehr)

### Software
- **macOS Version**: macOS 12.3 oder neuer
- **Aktualisierte Firmware**: Stellen Sie sicher, dass macOS vollständig aktualisiert ist
- **Backup**: Ein aktuelles Backup Ihres Systems (Time Machine oder andere Backup-Lösung)

### Weitere Voraussetzungen
- **Internetverbindung**: Für den Download der Installation (ca. 5-10 GB)
- **Administratorrechte**: Sie benötigen Admin-Zugriff auf Ihrem Mac
- **Zeit**: Planen Sie 1-2 Stunden für die Installation ein

---

## 🔧 Vorbereitung

### 1. Backup erstellen
**⚠️ WICHTIG**: Erstellen Sie unbedingt ein vollständiges Backup Ihres Systems, bevor Sie beginnen!

```bash
# Time Machine Backup empfohlen
# Alternativ: Carbon Copy Cloner, Super Duper, oder andere Backup-Software
```

### 2. macOS aktualisieren
Stellen Sie sicher, dass Sie die neueste Version von macOS haben:

```bash
# Überprüfen Sie auf Updates in den Systemeinstellungen
# System Preferences > Software Update
```

### 3. Speicherplatz überprüfen

```bash
# Überprüfen Sie verfügbaren Speicherplatz
df -h /
```

Sie benötigen mindestens 53 GB freien Speicherplatz. Empfohlen sind 100 GB oder mehr für eine komfortable Nutzung.

### 4. Wichtige Daten sichern
- Dokumentieren Sie Ihre wichtigen Einstellungen
- Exportieren Sie wichtige Daten
- Notieren Sie wichtige Passwörter (nicht die System-Passwörter!)

---

## 🚀 Schritt-für-Schritt Installationsanleitung

### Schritt 1: Terminal öffnen

Öffnen Sie das Terminal auf Ihrem Mac:
- **Finder** → **Programme** → **Dienstprogramme** → **Terminal**
- Oder drücken Sie `Cmd + Leertaste` und suchen Sie nach "Terminal"

### Schritt 2: Asahi Linux Installer herunterladen und starten

Führen Sie den folgenden Befehl im Terminal aus:

```bash
curl https://alx.sh | sh
```

**Was passiert hier?**
- Der Befehl lädt das Installationsskript von der offiziellen Asahi Linux Website
- Das Skript wird automatisch ausgeführt und startet den Installationsprozess

### Schritt 3: Installer-Anweisungen folgen

Der Installer wird Sie durch folgende Schritte führen:

#### 3.1 Sprache wählen
```
Select language: 
→ English (oder Ihre bevorzugte Sprache wählen)
```

#### 3.2 Partitionsgröße festlegen

Der Installer fragt Sie, wie viel Speicherplatz Sie für Linux bereitstellen möchten:

```
How much space should be allocated to the new OS?
→ Empfohlen: Mindestens 100 GB für komfortable Nutzung
→ Minimum: 53 GB
```

**Eingabe-Beispiel:**
```
100 GB
```

Oder als Prozentsatz:
```
25%
```

#### 3.3 Distribution wählen

Der Installer bietet verschiedene Linux-Distributionen an:

```
Choose your distribution:
1) Fedora Asahi Remix (empfohlen für Einsteiger)
2) Fedora Asahi Remix (Minimal)
3) Fedora Asahi Remix (Server)
4) UEFI environment only (für fortgeschrittene Nutzer)
5) Arch Linux ARM (für erfahrene Linux-Nutzer)

→ Für die meisten Nutzer: Option 1 wählen
```

**Empfohlene Wahl für Einsteiger:**
```
1
```

#### 3.4 Desktop-Umgebung wählen (bei Fedora Asahi Remix)

```
Choose your desktop environment:
1) KDE Plasma (modern, Windows-ähnlich)
2) GNOME (Standard, einfach)
3) Other

→ Für Einsteiger empfohlen: GNOME oder KDE Plasma
```

**Eingabe-Beispiel:**
```
2
```

### Schritt 4: Bestätigung und Installation

#### 4.1 Änderungen bestätigen

Der Installer zeigt Ihnen eine Zusammenfassung:

```
The installer will:
- Resize your macOS partition
- Create a new partition of 100 GB
- Install Fedora Asahi Remix with GNOME

Continue? (y/n)
```

**Bestätigen:**
```
y
```

#### 4.2 Administrator-Passwort eingeben

Sie werden aufgefordert, Ihr macOS-Passwort einzugeben:

```
Password: [Ihr macOS-Passwort eingeben]
```

#### 4.3 Neustart und Installation

Der Mac wird neu gestartet und Sie sehen:

1. **macOS Recovery**: Der Mac startet in den Recovery-Modus
2. **Partitionierung**: Die Festplatte wird neu partitioniert (dauert einige Minuten)
3. **Installation**: Linux wird installiert (dauert 20-40 Minuten, abhängig von der Internetgeschwindigkeit)

**⚠️ WICHTIG**: 
- Trennen Sie den Mac nicht vom Strom
- Unterbrechen Sie den Prozess nicht
- Lassen Sie den Mac seine Arbeit machen

### Schritt 5: Erstmalige Einrichtung

Nach der Installation startet der Mac automatisch in Asahi Linux:

#### 5.1 Willkommensbildschirm

Sie werden durch die erste Einrichtung geführt:

```
Welcome to Fedora Asahi Remix
→ Click "Start" oder drücken Sie Enter
```

#### 5.2 Region und Sprache

```
Select your region and language
→ Wählen Sie Ihre Region (z.B., Germany - Deutsch)
```

#### 5.3 Tastaturlayout

```
Select your keyboard layout
→ German (Germany) oder Ihr bevorzugtes Layout
```

#### 5.4 Zeitzone

```
Select your time zone
→ Europe/Berlin (oder Ihre Zeitzone)
```

#### 5.5 Benutzerkonto erstellen

```
Create your user account:
Full Name: [Ihr Name]
Username: [ihr-benutzername]
Password: [Sicheres Passwort]
Confirm Password: [Passwort wiederholen]
```

#### 5.6 Einrichtung abschließen

```
→ Click "Finish" oder "Abschließen"
```

### Schritt 6: System aktualisieren

Nach der ersten Anmeldung sollten Sie das System aktualisieren:

```bash
# System-Updates installieren
sudo dnf update -y
```

**Passwort eingeben:** Geben Sie das Passwort ein, das Sie im vorherigen Schritt erstellt haben.

**Warten Sie, bis der Update-Prozess abgeschlossen ist** (kann 10-30 Minuten dauern).

Nach den Updates, neu starten:

```bash
sudo reboot
```

---

## 🔄 Post-Installation

### Zwischen macOS und Asahi Linux wechseln

#### Von Asahi Linux zu macOS starten

**Option 1: Beim Boot auswählen**
1. Mac neu starten
2. **Power-Button gedrückt halten** bis "Startoptionen werden geladen" erscheint
3. macOS-Volume auswählen
4. Enter drücken

**Option 2: Über Terminal (in Asahi Linux)**
```bash
# Zurück zu macOS für den nächsten Start
sudo asahi-bless --macOS
sudo reboot
```

#### Von macOS zu Asahi Linux starten

**Option 1: Beim Boot auswählen**
1. Mac neu starten
2. **Power-Button gedrückt halten** bis "Startoptionen werden geladen" erscheint
3. Asahi Linux Volume auswählen
4. Enter drücken

**Option 2: Standard-Boot-Option setzen (in macOS Terminal)**
```bash
# Asahi Linux als Standard setzen
sudo bless --mount /Volumes/[AsahiLinuxVolumeName] --setBoot
```

### Nützliche erste Schritte in Asahi Linux

#### 1. Zusätzliche Software installieren

```bash
# Entwicklungs-Tools
sudo dnf groupinstall "Development Tools" -y

# Git installieren
sudo dnf install git -y

# VS Code installieren
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
sudo dnf install code -y

# Docker installieren
sudo dnf install docker -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER

# Node.js und npm installieren
sudo dnf install nodejs npm -y
```

#### 2. System-Performance optimieren

```bash
# Swap-Optimierung für bessere Performance
echo 'vm.swappiness=10' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

#### 3. Nützliche Aliase einrichten

Öffnen Sie die Bash-Konfiguration:

```bash
nano ~/.bashrc
```

Fügen Sie am Ende hinzu:

```bash
# Nützliche Aliase
alias update='sudo dnf update -y'
alias install='sudo dnf install'
alias search='dnf search'
alias ll='ls -alh'
alias ..='cd ..'
```

Speichern Sie mit `Ctrl + X`, dann `Y`, dann `Enter`.

Laden Sie die Konfiguration neu:

```bash
source ~/.bashrc
```

#### 4. Firewall konfigurieren

```bash
# Firewall aktivieren
sudo systemctl start firewalld
sudo systemctl enable firewalld

# Status überprüfen
sudo firewall-cmd --state
```

---

## 🔧 Troubleshooting

### Problem: Mac startet nicht richtig nach der Installation

**Lösung:**
1. Power-Button 10 Sekunden gedrückt halten um Mac auszuschalten
2. Wieder einschalten und Power-Button gedrückt halten
3. Startoptionen werden angezeigt
4. macOS auswählen und starten
5. Im Terminal den Installer erneut ausführen oder Asahi deinstallieren:
   ```bash
   curl https://alx.sh | sh
   # Dann Option "Uninstall" wählen
   ```

### Problem: WLAN funktioniert nicht

**Lösung:**
```bash
# WLAN-Firmware aktualisieren
sudo dnf update -y
sudo reboot
```

Falls das nicht hilft:
```bash
# Netzwerk-Manager neu starten
sudo systemctl restart NetworkManager
```

### Problem: Touchpad funktioniert nicht optimal

**Lösung:**
```bash
# Touchpad-Treiber aktualisieren
sudo dnf update kernel\* -y
sudo reboot
```

### Problem: Sound funktioniert nicht

**Lösung:**
```bash
# PipeWire neu starten
systemctl --user restart pipewire pipewire-pulse wireplumber
```

### Problem: Display-Auflösung ist falsch

**Lösung:**
```bash
# Wayland-Sitzung verwenden (bei GNOME)
# Beim Login-Bildschirm auf das Zahnrad-Symbol klicken
# "GNOME" oder "GNOME on Wayland" auswählen
```

### Problem: Akkulaufzeit ist kürzer als in macOS

**Hinweis:** Dies ist normal in den frühen Stadien des Projekts. Die Energieverwaltung wird kontinuierlich verbessert.

**Optimierungen:**
```bash
# TLP für besseres Power Management installieren
sudo dnf install tlp tlp-rdw -y
sudo systemctl enable tlp
sudo systemctl start tlp
```

### Problem: System ist langsam nach der Installation

**Lösung:**
```bash
# Cache leeren
sudo dnf clean all

# Unnötige Pakete entfernen
sudo dnf autoremove -y

# System neu starten
sudo reboot
```

---

## 📚 Weitere Ressourcen

### Offizielle Dokumentation
- **Asahi Linux Website**: https://asahilinux.org
- **Asahi Linux Wiki**: https://github.com/AsahiLinux/docs/wiki
- **Installation Guide**: https://asahilinux.org/install/

### Community und Support
- **Asahi Linux Discord**: https://discord.gg/asahi
- **Reddit**: https://www.reddit.com/r/AsahiLinux/
- **GitHub**: https://github.com/AsahiLinux

### Fedora Asahi Remix
- **Fedora Asahi Remix Docs**: https://docs.fedoraproject.org/en-US/fedora-asahi-remix/

### Arch Linux ARM (für Arch-Nutzer)
- **Arch Linux ARM**: https://archlinuxarm.org/
- **Asahi Arch Wiki**: https://github.com/AsahiLinux/docs/wiki/Arch-Linux-ARM

### Video-Tutorials
- Suchen Sie auf YouTube nach "Asahi Linux installation" für visuelle Anleitungen
- Viele Community-Mitglieder teilen ihre Erfahrungen und Tipps

### Troubleshooting und FAQ
- **GitHub Issues**: https://github.com/AsahiLinux/asahi-installer/issues
- **FAQ**: https://asahilinux.org/about/

---

## ⚠️ Wichtige Hinweise

### Projekt-Status
Asahi Linux ist ein aktives Entwicklungsprojekt. Während es bereits sehr gut funktioniert, sollten Sie beachten:

- **GPU-Beschleunigung**: Funktioniert, wird aber weiter verbessert
- **Akkulaufzeit**: Kürzer als macOS, wird kontinuierlich optimiert
- **Hardware-Unterstützung**: Die meisten Funktionen arbeiten, einige werden noch entwickelt
- **Updates**: Das Projekt wird aktiv entwickelt und regelmäßig aktualisiert

### Sicherheitshinweise
- Erstellen Sie **immer** ein Backup vor der Installation
- Nutzen Sie Asahi Linux nicht als einziges System für kritische Produktivarbeit
- Halten Sie sowohl macOS als auch Asahi Linux aktuell

### Best Practices
- **Regelmäßige Updates**: Führen Sie regelmäßig `sudo dnf update` aus
- **Backups**: Erstellen Sie regelmäßige Backups beider Systeme
- **Community**: Beteiligen Sie sich an der Community für Support und Updates

---

## 🎉 Viel Erfolg!

Sie haben es geschafft! Genießen Sie Ihre neue Linux-Umgebung auf Ihrem Apple Silicon Mac.

Bei Fragen oder Problemen, besuchen Sie die [Asahi Linux Community](https://asahilinux.org) oder öffnen Sie ein Issue in diesem Repository.

**Happy Linux-ing! 🐧**

---

## 📝 Lizenz

Dieser Guide ist unter der MIT-Lizenz veröffentlicht. Fühlen Sie sich frei, ihn zu teilen und zu verbessern!

## 🤝 Beiträge

Verbesserungsvorschläge und Korrekturen sind willkommen! Öffnen Sie ein Issue oder einen Pull Request.

---

**Erstellt von der Community für die Community** ❤️
