[README.md](https://github.com/user-attachments/files/24400787/README.md)
# VoRMap

**A graphical map and stats display for Void of Reality MUD**

VoRMap is a lightweight proxy application that sits between your MUD client and the Void of Reality server. It intercepts GMCP (Generic MUD Communication Protocol) data to display a real-time graphical map and character stats in a separate window while you play using your favorite MUD client.

---

## Features

- **Real-time minimap** - 10x10 grid showing nearby rooms with terrain colors
- **Character info** - Name, level, and remort status
- **Vital stats** - HP, Mana, and Moves with visual progress bars
- **Room name display** - Current room name shown prominently
- **Exit connections** - Only shows paths where exits actually exist
- **Player tracking** - See same-alignment players on the map (purple P)
- **NPC markers** - Special NPCs shown with colored dots:
  - Guildmasters (green)
  - Teachers (cyan)
  - Bankers (orange)
  - Enchanters (blue)
  - Jewelers (purple)
  - Armorers (red)
  - Weaponsmiths (white)
  - Shops (yellow)
- **Mob tracking** - Rangers can see all mobs (grey M)
- **Always-on-top** - Window stays visible while you play
- **Works with any client** - zMUD, cMUD, Mudlet, TinTin++, etc.

---

## Screenshots

*(Add screenshots here)*

---

## Requirements

- Windows 10 or Windows 11
- Any MUD/Telnet client

---

## Download

Download the latest release from the [Releases](../../releases) page.

---

## Installation

No installation required! VoRMap is a standalone executable.

1. Download `VoRMap.exe` from the Releases page
2. Save it anywhere you like
3. Run it

**Note:** Windows SmartScreen may show a warning for new/unknown applications. Click **"More info"** then **"Run anyway"** to proceed. This is normal for unsigned applications.

---

## How to Use

### Quick Start

1. **Run VoRMap.exe** - A small window appears showing "Waiting for connection on port 23..."
2. **Open your MUD client** (zMUD, Mudlet, etc.)
3. **Connect to:** `localhost` port `23`
4. **Play normally** - The map and stats update automatically as you play!

### How It Works

VoRMap acts as a proxy:

```
Your MUD Client  <-->  VoRMap (localhost:23)  <-->  VoR Server (vor.voidofreality.org:7777)
```

Your client connects to VoRMap on your local machine. VoRMap connects to the real VoR server and passes all data through, while intercepting GMCP data to update the graphical display.

---

## Map Legend

### Terrain Colors

| Color | Terrain |
|-------|---------|
| Dark Brown | Inside |
| White | City |
| Dark Green | Field |
| Bright Green | Forest |
| Tan | Hills |
| Red | Mountain |
| Light Blue | Water (swim) |
| Dark Blue | Deep Water |
| Navy | Underwater |
| Grey | Air |
| Sandy | Desert |
| White | Snow |
| Cyan | Tropical |
| Teal | Ice |
| Dark Blue-Grey | Marsh |

### Map Markers

| Marker | Color | Meaning |
|--------|-------|---------|
| ● | Magenta | You (player) |
| P | Purple | Same-alignment player |
| ● | Green | Guildmaster |
| ● | Cyan | Teacher |
| ● | Orange | Banker |
| ● | Blue | Enchanter |
| ● | Purple | Jeweler |
| ● | Red | Armorer |
| ● | White | Weaponsmith |
| ● | Yellow | Shop |
| M | Grey | Other mob (Rangers only) |

---

## Troubleshooting

### "Waiting for connection..." never changes
- Make sure your MUD client is connecting to `localhost` port `23`, not directly to VoR

### Windows SmartScreen blocks the exe
- Click **"More info"** then **"Run anyway"**
- This is normal for unsigned applications

### Port 23 is already in use
- Another application may be using port 23
- Edit the source code and change `LISTEN_PORT = 23` to another port (e.g., 2323)
- Rebuild the exe

### Map shows raw GMCP data in my client
- Make sure you're connecting through VoRMap, not directly to VoR
- VoRMap filters out GMCP data before sending to your client

### Map doesn't update / shows nothing
- Make sure VoRMap shows "Connected to VoR!" in green
- The map requires GMCP support on the server (built into VoR)

---

## Building from Source

### Requirements
- Python 3.8 or higher
- PyInstaller

### Steps

1. Install Python from https://python.org

2. Install PyInstaller:
   ```
   pip install pyinstaller
   ```

3. Build the executable:
   ```
   pyinstaller --onefile --windowed --name VoRMap vor_map.py
   ```

4. Find `VoRMap.exe` in the `dist` folder

---

## Configuration

The following settings can be changed by editing the source code:

| Setting | Default | Description |
|---------|---------|-------------|
| `VOR_HOST` | `vor.voidofreality.org` | VoR server address |
| `VOR_PORT` | `7777` | VoR server port |
| `LISTEN_PORT` | `23` | Local port for your MUD client |

---

## Credits

- **Void of Reality** - https://voidofreality.org
- Running since 1996, VoR is a MUD based on the EmlenMUD codebase

---

## License

This project is provided as-is for use with Void of Reality MUD.

---

## Links

- **Play Void of Reality:** `vor.voidofreality.org` port `7777`
- **VoR Website:** https://voidofreality.org

---

*Happy MUDding!*
