# Kali Linux Desktop Configurator - custom.sh

Das ultimative **einsteigerfreundliche Tool** zur Kustomisierung von Kali Linux Desktop-Umgebungen mit modernen Unix-Tools und professionelle Workflows.

## 🎯 Features

### ✨ Moderne Benutzeroberfläche
- **Interaktive Menüs** mit FZF-Unterstützung (fuzzy finder)
- **Farbige Ausgaben** mit professionellem Design
- **Progress Bars** während Installation zeigen den Fortschritt
- **Installation Reports** mit detaillierter Dokumentation
- **Fehlerbehandlung** mit hilfreichen Rückfragen

### 🎨 Vordefinierte Kali Modes
4 professionell kuratierte Desktop-Umgebungen:

| Mode | Beschreibung | Ideal für |
|------|---|---|
| **Pentester** | Security-fokussiert, minimal UI | Penetration Tester |
| **Corporate** | Professionell, Arc-Theme, produktiv | Professionelle Umgebung |
| **Fsociety** | Hacker-Ästhetik, Dracula-Theme | Developers, Enthusiasts |
| **XFCE** | Leichtgewichtig, klassisch | Schwache Hardware |

### 🎭 Design-Presets
- **Minimalistic** - Sauber & schnell
- **Corporate** - Professionell mit Arc-Theme
- **Windows XP** - Nostalgisch mit Luna-Theme
- **Fsocietyhub** - Dark Mode Dracula

### 📦 Moderne Unix-Tools
Das Script installiert automatisch (falls gewünscht):
- **fzf** - Interaktive Menü-Navigation
- **bat** - Besseres `cat` mit Syntax-Highlighting
- **ripgrep** - Schnellere Datei-Suche
- **delta** - Verbessertes `diff`

### ✅ Installation Tracking
- Protokollierung aller Installationen
- Installation-Reports mit Zeitstempel
- Überblick über installierte Modi
- Detaillierte Fehlermeldungen

## 🚀 Quick Start

### Interaktiv (Anfänger)
```bash
./custom.sh
```
Wähle einen Mode aus und folge den Anweisungen.

### Command-Line (Fortgeschrittene)
```bash
# Mode direkt laden
./custom.sh --mode pentester

# Design anwenden
./custom.sh --design fsocietyhub

# Mit Verbose-Output
./custom.sh --verbose --mode corporate

# Dry-Run (testen ohne Änderungen)
./custom.sh --dry-run --mode fsociety
```

## 📋 Alle CLI-Optionen

### Grundlegende Nutzung
```bash
./custom.sh                         # Interaktives Menü
./custom.sh --help                  # Hilfe anzeigen
./custom.sh --list-modes            # Alle Modi auflisten
```

### Kali Modes & Designs
```bash
./custom.sh --mode <name>           # Mode laden (pentester, corporate, fsociety, xfce)
./custom.sh --design <name>         # Design anwenden (minimalistic, corporate, windows_xp, fsocietyhub)
```

### System-Verwaltung
```bash
./custom.sh --status                # System-Status & Installation-Historie
./custom.sh --restore               # Letztes Backup wiederherstellen
./custom.sh --report                # Installation-Report anzeigen
```

### Erweiterte Optionen
```bash
./custom.sh -v / --verbose          # Verbose Output (Debug-Infos)
./custom.sh --dry-run               # Testen ohne echte Änderungen
./custom.sh --help / -h             # Diese Hilfe
```

## 🔧 Interaktive Menüs

### Hauptmenü
1. **Schnell-Setup** - Vordefinierte Mode in einem Schritt
2. **Benutzerdefiniert** - Jede Komponente einzeln wählen
3. **Status anzeigen** - System-Überblick & Historie
4. **Backup/Restore** - Sicherung erstellen oder wiederherstellen
5. **Tools installieren** - Zusätzliche Tools & Utilities

### Tools-Menü
Moderne Unix-Tools, Systemüberwachung, Audio/Medien, Hardware, Entwicklung, Wartung

## 📝 Installation-Report

Jede Installation wird protokolliert:
```
~/.config/kali-desktop/install_report.log
```

Beispiel-Output:
```
[2024-01-15 14:32:10] START: Installiere Design/Mode: pentester
[2024-01-15 14:32:15] CLEANUP: Vorherige Installation aufgeräumt
[2024-01-15 14:32:45] DEPENDENCIES: Abhängigkeiten installiert
[2024-01-15 14:33:20] THEMES: Themes & Icons installiert
...
[2024-01-15 14:45:30] COMPLETE: Installation erfolgreich (Dauer: 780s)
```

## 📁 Dateien & Verzeichnisse

```
~/.config/kali-desktop/
├── settings.conf              # Gespeicherte Einstellungen
├── install_report.log         # Installation-Protokoll
├── installed.conf             # Tracking installierter Modi
└── modes/                     # Mode-Definitionen
    ├── pentester.conf
    ├── corporate.conf
    ├── fsociety.conf
    └── xfce.conf

~/.desktop_backup/            # Automatische Backups
├── gtk_theme.txt
├── icon_theme.txt
├── wm_theme.txt
└── current_desktop.png
```

## 🛠️ Anforderungen

### Mindestanforderungen
- **bash 4.0+**
- **apt-get** (Debian/Kali)
- **git, curl/wget, unzip**
- **gsettings** (für Theme-Aktivierung)

### Empfohlen (für beste UX)
- **fzf** - Interaktive Menüs
- **bat** oder **batcat** - Syntax-Highlighting
- **ripgrep** - Schnellere Suche

### Optional
- **delta** - Verbessertes diff-Tool
- **picom** - Compositor
- **rofi** - App-Launcher
- **alacritty** - GPU-Terminal
- **variety** - Wallpaper-Manager

## 🎯 Praktische Beispiele

### Für Penetration Tester
```bash
./custom.sh --mode pentester
# oder mit Verbose für Debugging
./custom.sh -v --mode pentester
```

### Für Entwickler
```bash
./custom.sh --design fsocietyhub
# Modern, dark, with all dev tools
```

### Für Anfänger
```bash
./custom.sh
# Wähle einfach aus dem interaktiven Menü
```

### Für CI/CD Automation
```bash
# Dry-Run testen
./custom.sh --dry-run --mode corporate

# Dann real ausführen
./custom.sh --mode corporate
```

## 🐛 Troubleshooting

### "Ungültige Auswahl" Fehler
```bash
# Nutze FZF-basierte Auswahl (falls installiert)
apt install fzf
./custom.sh
```

### gsettings nicht verfügbar
```bash
# Überprüfe DBUS_SESSION_BUS_ADDRESS
echo $DBUS_SESSION_BUS_ADDRESS
# Bei TTY/Headless: gsettings wird automatisch übersprungen
```

### Fehler bei APT-Paketen
```bash
# Verbose-Mode für Details
./custom.sh -v --mode pentester

# Manuell nachinstallieren
sudo apt update
sudo apt install -y <package-name>
```

## 📊 Performance

Installation dauert ca. **10-20 Minuten** je nach:
- Internet-Geschwindigkeit (Downloads)
- System-Performance
- Gewählte Komponenten

## 🔐 Sicherheit

- ✅ Nur offizielle Paket-Quellen
- ✅ Automatische Backups vor Änderungen
- ✅ Fehlerbehandlung mit Rollback
- ✅ Keine externen Shell-Ausführungen
- ✅ Dry-Run Mode zum Testen

## 📚 Weitere Ressourcen

- **Offizielle Kali Doku**: https://www.kali.org/docs/
- **Desktop Environments**: i3, Sway, XFCE, GNOME, KDE
- **Modern CLI Tools**: https://github.com/alebcay/awesome-cli-tools

## 🤝 Beiträge

Verbesserungsvorschläge willkommen! Erstelle einfach ein Issue oder PR.

## 📄 Lizenz

Dieses Script steht unter MIT Lizenz - frei verwendbar und veränderbar.

---

**Made for Kali Linux** 🔴 **Make customization simple!** 🚀
