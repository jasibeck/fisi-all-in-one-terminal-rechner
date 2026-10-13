# fisi-all-in-one-terminal-rechner
Python-Tool für Fachinformatiker Systemintegration mit Taschenrechner, Subnetzrechner und Windows/Linux Command-Cheatsheet.
# FISI All-in-One Terminal-Rechner

Ein Python-CLI Tool für Fachinformatiker Systemintegration (FISI):
- **Taschenrechner** (`calc`)
- **Subnetz / IP-Rechner** (`subnet`)
- **FISI Command-Cheatsheet** (`cmds`) — getrennt nach:
  - **Windows = PowerShell / Windows Terminal**
  - **Linux = Bash**
  - **WSL = Linux-Befehle aufgerufen aus PowerShell / CMD** (laut Microsoft-Doku immer mit `wsl` davor)

Keine Installation nötig, nur Python 3.8+ (Standardlib only).

## 1. Starten

### Windows PowerShell / Windows Terminal
```powershell
cd $HOME\Dokumente\Standardprojekt
python .\fisi_rechner.py menu
python .\fisi_rechner.py calc "2+3*4"
python .\fisi_rechner.py subnet 192.168.1.10/24
python .\fisi_rechner.py cmds --os windows
python .\fisi_rechner.py cmds --os wsl
python .\fisi_rechner.py cmds --suche ping
```

### Windows CMD
```cmd
cd %USERPROFILE%\Dokumente\Standardprojekt
python fisi_rechner.py menu
python fisi_rechner.py calc "2**8"
python fisi_rechner.py subnet 10.0.0.5/8
python fisi_rechner.py cmds --os windows
```

### Linux Bash
```bash
cd ~/Standardprojekt
python3 fisi_rechner.py menu
python3 fisi_rechner.py calc "(10-2)/4"
python3 fisi_rechner.py subnet 172.16.5.4/16
python3 fisi_rechner.py cmds --os linux
python3 fisi_rechner.py cmds --kategorie Netzwerk
```

### WSL in PowerShell / CMD (Microsoft-Doku)
Linux-Befehle werden in PowerShell bzw. CMD mit `wsl` davor aufgerufen:

```powershell
wsl ls -la
wsl ip a
wsl ping -c 4 8.8.8.8
wsl --list --verbose
wsl --status
```

Das Tool zeigt dir zu jedem Befehl alle 3 Varianten:
```powershell
python .\fisi_rechner.py cmds --os alle
```

## 2. Beispiele

```bash
# Taschenrechner
python fisi_rechner.py calc "2+3*4"        # -> 14
python fisi_rechner.py calc "2**8"         # -> 256
python fisi_rechner.py calc "10 % 3"       # -> 1

# Subnetzrechner
python fisi_rechner.py subnet 192.168.1.10/24
# Ausgabe: Netz, Maske, Broadcast, Host-Range, nutzbare Hosts, Klasse, privat ja/nein, Binär

python fisi_rechner.py subnet 10.0.0.1/255.0.0.0
```

## 3. Menü-Modus (einfachste Nutzung)

```bash
python fisi_rechner.py menu
# oder ohne Argument:
python fisi_rechner.py
```

```
 [1] Taschenrechner
 [2] Subnetz / IP-Rechner
 [3] FISI Commands (alle)
 [4] FISI Commands (nur Windows/PowerShell)
 [5] FISI Commands (nur Linux/Bash)
 [6] FISI Commands (nur WSL)
 [0] Beenden
```

## 4. Hinweis zur Aufgabentrennung

- **Windows-Befehle** in diesem Projekt sind für **PowerShell / Windows Terminal** dokumentiert (`Get-NetIPAddress`, `Test-Connection`, `Get-Process`, ...). Klassische CMD-Aliase (`ipconfig`, `ping -n`) sind als Kommentar dabei.
- **Linux-Befehle** sind für **Bash** dokumentiert (`ip a`, `ping -c`, `grep`, ...).
- **WSL-Nutzung** nach Microsoft-Doku: in PowerShell/CMD `wsl <befehl>`, z.B. `wsl ip a`.
