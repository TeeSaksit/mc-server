# 🎮 Minecraft Server Setup

A Fabric-based Minecraft server setup for friends, running Minecraft 1.21.11 with performance optimizations and quality-of-life mods.

## 📋 Prerequisites

Before you begin, make sure you have the following installed:

- **Docker** - [Download Docker Desktop](https://www.docker.com/products/docker-desktop)
- **Docker Compose** - Usually included with Docker Desktop

## 🚀 Quick Start

### 1. Clone or Download this Repository

```bash
git clone https://github.com/TeeSaksit/mc-server.git
cd mc-server
```

### 2. Start the Server

```bash
docker-compose up -d
```

The server will automatically:

- Download the Minecraft server files
- Install Fabric and all required mods
- Start the server

### 3. Check Server Status

```bash
docker-compose logs -f mc
```

Press `Ctrl+C` to exit the logs (server will keep running).

### 4. Stop the Server

```bash
docker-compose down
```

## 🔌 Connecting to the Server

### For Friends (Players)

1. **Install Minecraft 1.21.11** (exact version required)
2. **Install Fabric Loader 0.18.4** for Minecraft 1.21.11
   - Download from: [Fabric Installer](https://fabricmc.net/use/installer/)
   - Select Minecraft version 1.21.11 and Fabric Loader 0.18.4
3. **Download the Modpack**
   - All mods will be automatically downloaded by the server
   - Alternatively, you can download the same mods manually (see Mods section below)
4. **Connect to Server**
   - Server IP: `your-server-ip:25565`
   - Or use `localhost` if running on the same machine

### Recommended Client Mods

For the best experience, players should install these client-side mods:

- **Sodium** - Performance optimization
- **Iris** - Shader support
- **ModMenu** - In-game mod configuration
- **Simple Voice Chat** - Voice chat (install matching version)

## 📦 Included Mods

This server includes the following mods:

### Performance Mods

- **Sodium** - Massive FPS improvements
- **Lithium** - Server-side performance optimization
- **Krypton** - Network optimization
- **FerriteCore** - Memory optimization
- **ModernFix MVUS** - Performance fixes

### Visual & Graphics

- **Iris** - Shader support
- **Distant Horizons** - Extended render distance

### Gameplay & Features

- **Simple Voice Chat** - Proximity voice chat (UDP port 24454)
- **Skin Restorer** - Restores player skins in offline mode
- **Tab Was Taken** - Customizable tab list
- **Almanac** - In-game guide

### Server Tools

- **Chunky** - Pre-generate chunks
- **Anti-Xray** - Prevents X-ray cheats
- **Placeholder API** - Placeholder support for plugins
- **Collective** - Shared library

### Utilities

- **Fabric API** - Required API for Fabric mods
- **Cloth Config** - Configuration GUI library
- **LMD** - Library mod
- **ModMenu** - Mod configuration menu

## ⚙️ Server Configuration

The server is configured with:

- **Minecraft Version:** 1.21.11
- **Mod Loader:** Fabric 0.18.4
- **Max Players:** 5
- **Difficulty:** Hard
- **Online Mode:** Disabled (for LAN/offline play)
- **Memory:** 6GB allocated, 7GB limit
- **View Distance:** 7 chunks
- **Simulation Distance:** 4 chunks
- **Timezone:** Asia/Bangkok

### Ports

- **25565** - Minecraft server (TCP)
- **24454** - Voice Chat (UDP)

Make sure these ports are open in your firewall/router if hosting online.

## 🛠️ Management Commands

### View Server Logs

```bash
docker-compose logs -f mc
```

### Execute Server Commands

```bash
docker-compose exec mc rcon-cli <command>
```

Example:

```bash
docker-compose exec mc rcon-cli list
docker-compose exec mc rcon-cli say Hello friends!
```

### Restart Server

```bash
docker-compose restart mc
```

### Backup Server Data

```bash
# Stop server first
docker-compose down

# Backup the data folder
tar -czf backup-$(date +%Y%m%d-%H%M%S).tar.gz data/

# Restart server
docker-compose up -d
```

## 📁 File Structure

```
mc-server/
├── docker-compose.yaml    # Docker configuration
├── icon.png               # Server icon
├── modpack/               # Modpack files
│   ├── pack.toml         # Modpack definition
│   ├── index.toml        # Mod index
│   └── mods/             # Individual mod definitions
└── data/                  # Server data (created on first run)
    ├── world/            # Your world files
    ├── mods/             # Installed mods
    └── server.properties # Server configuration
```

## 🔧 Troubleshooting

### Server Won't Start

1. **Check Docker is running:**

   ```bash
   docker ps
   ```

2. **Check logs for errors:**

   ```bash
   docker-compose logs mc
   ```

3. **Verify port 25565 is available:**

   ```bash
   # Windows
   netstat -ano | findstr :25565

   # Linux/Mac
   lsof -i :25565
   ```

### Can't Connect

- Ensure you're using Minecraft **1.21.11** exactly
- Make sure you have Fabric Loader **0.18.4** installed
- Verify the server IP and port are correct
- Check firewall settings allow connections on port 25565

### Mods Not Loading

- The server automatically downloads mods from the modpack
- First startup may take longer as mods download
- Check logs to see if any mods failed to download

### Voice Chat Not Working

- Ensure UDP port 24454 is open in your firewall
- Voice chat requires the Simple Voice Chat mod on both client and server

## 🌐 Hosting Online

To make your server accessible to friends online:

1. **Find your public IP:**

   - Visit [whatismyip.com](https://www.whatismyip.com/)

2. **Configure Port Forwarding:**

   - Forward TCP port 25565 to your server
   - Forward UDP port 24454 to your server (for voice chat)

3. **Share the IP:**
   - Give friends: `your-public-ip:25565`

## 📝 Notes

- **Online Mode:** Currently set to `FALSE` (offline mode). Change `ONLINE_MODE: "TRUE"` in `docker-compose.yaml` if you want to use Mojang authentication.
- **World Data:** Your world is stored in the `data/` folder. Back it up regularly!
- **Mod Updates:** Mods are managed via Packwiz. The server will automatically download mods defined in the modpack.

## 📚 Additional Resources

- [Docker Documentation](https://docs.docker.com/)
- [Fabric Wiki](https://fabricmc.net/wiki/)
- [Minecraft Server Documentation](https://minecraft.wiki/w/Server)

## 🎉 Have Fun!

Enjoy playing with your friends! If you encounter any issues, check the logs first and feel free to ask for help.

---

**Server MOTD:** "Fix Bug In The Box World." 🐛📦
