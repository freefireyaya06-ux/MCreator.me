# MCreator

## Overview

This repository provides a convenient way to run **MCreator** using **NoVNC** through a **Dev Container**. It eliminates the need for local installation and allows you to develop Minecraft mods directly from your browser. **Best of all, this works on all platforms** — Windows, macOS, Linux, Android, and iOS — so you can create and edit mods from any device with a web browser.

## What is NoVNC?

**NoVNC** is an open-source VNC (Virtual Network Computing) client that runs entirely in your web browser. It allows you to access and interact with a remote desktop environment without needing to install any additional software on your local machine. Through NoVNC, you can view and control the MCreator application running inside a containerized environment, making it accessible from anywhere with a web browser.

### Cross-Platform Support

NoVNC is **completely platform-agnostic**. Because it's browser-based, you can access MCreator from:
- **Windows** - Chrome, Edge, Firefox, Safari
- **macOS** - Safari, Chrome, Firefox
- **Linux** - Any browser (Firefox, Chrome, etc.)
- **Android** - Chrome, Firefox, or any mobile browser
- **iOS** - Safari, Chrome app, or any iOS browser

You don't need to install anything — just open a URL in your browser!

## What is Dev Container?

A **Dev Container** (Development Container) is a standardized development environment defined in Docker. It containerizes your entire development setup, including all dependencies, tools, and configurations. By using Dev Containers, you ensure that:
- The environment is consistent across all machines and platforms
- There are no "works on my machine" issues
- Anyone can get started with a single click
- The setup is reproducible and version-controlled
- All platforms (Windows, Mac, Linux, even mobile browsers) access the same identical environment

## What is MCreator?

**MCreator** is a powerful, no-code visual tool for creating Minecraft modifications (mods). Instead of writing complex Java code, you design mods using an intuitive graphical interface with visual blocks, wizards, and drag-and-drop elements. MCreator handles code generation automatically, making it perfect for:
- Beginners who want to learn mod development
- Creators who prefer visual programming
- Rapid prototyping of mod ideas

With MCreator, you can create custom blocks, items, mobs, dimensions, biomes, and much more without touching a single line of code.

Official Website: https://mcreator.net/
GitHub: https://github.com/MCreator/MCreator/

## Version Information

This repository uses **MCreator 2022.1**, a stable and feature-rich version that provides excellent balance between functionality and performance. It is **completely free to use**, and the repository is **fully open source**, allowing you to:
- Modify and customize it for your needs
- Contribute improvements back to the project
- Use it for personal or commercial projects
- Share and distribute your modifications

## Universal Platform Support

This MCreator Dev Container setup is designed to work seamlessly on **all platforms**:

| Platform | Supported | Access Method |
|----------|-----------|----------------|
| **Windows** | ✅ Yes | VS Code, GitHub Codespaces, Web Browser |
| **macOS** | ✅ Yes | VS Code, GitHub Codespaces, Web Browser |
| **Linux** | ✅ Yes | VS Code, GitHub Codespaces, Web Browser |
| **Android** | ✅ Yes | Web Browser (Chrome, Firefox) |
| **iOS** | ✅ Yes | Safari, Chrome App, Web Browser |

Because everything runs in the cloud (or in a container on your machine), you can seamlessly switch between devices. Start creating a mod on your desktop, continue editing on your tablet, and finalize it on your phone — all with the same browser interface!

## Getting Started

Follow these steps to set up and use this MCreator Dev Container:

### Step 1: Clone or Fork the Repository

First, you need to get a copy of this repository on your machine.

**Option A: Clone the Repository**
```bash
git clone https://github.com/freefireyaya06-ux/MCreator.me.git
cd MCreator.me
```

**Option B: Fork the Repository**
1. Click the "Fork" button on GitHub
2. Clone your forked version:
```bash
git clone https://github.com/YOUR-USERNAME/MCreator.me.git
cd MCreator.me
```

### Step 2: Open in VS Code or GitHub Codespaces

#### Using VS Code (Local - Windows, macOS, Linux)

1. **Install Docker**: Make sure Docker is installed and running on your system
   - [Download Docker Desktop for Windows](https://www.docker.com/products/docker-desktop)
   - [Download Docker Desktop for macOS](https://www.docker.com/products/docker-desktop)
   - [Download Docker Desktop for Linux](https://docs.docker.com/engine/install/)

2. **Install VS Code Dev Containers Extension**:
   - Open VS Code
   - Go to Extensions (Ctrl+Shift+X / Cmd+Shift+X)
   - Search for "Dev Containers"
   - Install the extension by Microsoft

3. **Open the Repository in Dev Container**:
   - In VS Code, open the repository folder
   - Press `Ctrl+Shift+P` (Cmd+Shift+P on Mac)
   - Search for "Dev Containers: Reopen in Container"
   - Select it and wait for the container to build

#### Using GitHub Codespaces (Cloud-based - All Platforms)

This is the **easiest method for all platforms**, including mobile devices:

1. **Create a Codespace**:
   - Go to the repository on GitHub
   - Click the green "Code" button
   - Select the "Codespaces" tab
   - Click "Create codespace on main"
   - Wait for the environment to initialize

2. **Access from Any Device**:
   - The Codespace runs entirely in the cloud
   - Access it from any device with a web browser
   - No installation required on Android, iOS, or any other platform

3. **Wait for Automatic Setup**:
   - GitHub will automatically start the Dev Container
   - This may take a few minutes the first time

### Step 3: Start the NoVNC Server and MCreator

Once the Dev Container is running, you need to start the NoVNC server and MCreator application.

#### Commands to Run

**Start the VNC server and MCreator**:
```bash
# Navigate to the scripts directory (if applicable)
cd /workspace

# Start the VNC server
vncserver :1 -geometry 1920x1080 -depth 24
```

**In a new terminal in the container, start MCreator**:
```bash
# Set the DISPLAY environment variable
export DISPLAY=:1

# Navigate to MCreator installation directory
cd /opt/mcreator

# Start MCreator
./mcreator
```

Or, if there's a startup script in the repository:
```bash
./start.sh
```

**Alternative: All-in-One Command**

If you have a startup script, you can run everything at once:
```bash
bash /workspace/start-mcreator.sh
```

### Step 4: Forward the Port

The VNC server runs on port 5900 by default. You need to forward this port to access it from your browser.

#### For VS Code (Local Dev Container)

The port should forward automatically. Look for a notification in VS Code about port forwarding. You can also manually set it up:

1. Open the terminal in VS Code
2. Go to the "Ports" tab at the bottom
3. Click "Add Port"
4. Enter port `5900`
5. It will appear in the port list

#### For GitHub Codespaces (All Devices)

1. Look for the "Ports" tab in the terminal area
2. The port should be automatically forwarded
3. If not, click "Add Port" and enter `5900`
4. Right-click on the port and select "Open in Browser" or copy the forwarded URL

### Step 5: Access MCreator via Browser

Once the port is forwarded, you can access MCreator through NoVNC from any device:

**For Windows, macOS, Linux**:
1. Look at the Ports tab, find port 5900
2. Click the globe icon to open in browser
3. Or copy the forwarded URL (e.g., `http://localhost:5900`)

**For GitHub Codespaces (works on all platforms including mobile)**:
1. Click on the forwarded port URL in the Ports panel
2. It will open in a new tab
3. Or copy the URL and open it on any device (phone, tablet, etc.)

**In your browser**:
1. You should see the NoVNC interface
2. Enter a password if prompted (set in the container configuration)
3. Click "Connect"
4. The desktop and MCreator window will appear
5. Start creating mods!

## Accessing from Mobile Devices

### From Android:

1. Go to GitHub and access your Codespace
2. Find the port 5900 in the Ports panel
3. Click the link or copy the URL
4. Open it in Chrome or Firefox
5. NoVNC interface loads in your browser
6. You can now create and edit mods on your Android device!

### From iOS:

1. Open Safari or the Chrome app
2. Navigate to your GitHub Codespace
3. Find the forwarded port 5900 URL
4. Tap the link
5. NoVNC loads in your browser
6. Create mods directly from your iPhone or iPad!

**Note**: Touch controls work great with NoVNC. You can tap to click, two-finger tap to right-click, and pinch to zoom.

## Detailed Workflow

### Creating Your First Mod

Once you have MCreator open in NoVNC:

1. **Create a New Workspace**:
   - Launch MCreator
   - Click "Create new"
   - Select your Minecraft version
   - Choose a mod name and workspace location
   - Click "Create"

2. **Add Elements**:
   - Use the left sidebar to add custom blocks, items, mobs, etc.
   - Click "New Element" and select what you want to create
   - Use the visual editor to configure properties
   - MCreator automatically generates the code

3. **Test Your Mod**:
   - Click "Build and Run"
   - MCreator launches a test instance of Minecraft with your mod
   - Test your creations in-game

4. **Export Your Mod**:
   - Click "Build" → "Build Workspace"
   - MCreator creates a JAR file
   - You can share this with others or upload to mod platforms

### Useful Tips

- **Save Frequently**: Use `Ctrl+S` to save your work
- **Use Version Control**: Commit your changes regularly:
  ```bash
  git add .
  git commit -m "Added new custom block"
  git push
  ```
- **Monitor Container Resources**: Keep an eye on CPU and memory usage in the Dev Container
- **Persistent Storage**: Your mod files are stored in the container volume, so they persist between sessions
- **Switch Between Devices**: Your work is always synced in the cloud (Codespaces) or in your container, so you can switch between Windows, Mac, Linux, Android, and iOS seamlessly

## Troubleshooting

### Port Not Forwarding

- Ensure the VNC server is running with `ps aux | grep vncserver`
- Check if port 5900 is occupied: `lsof -i :5900`
- Restart the VNC server if needed:
  ```bash
  vncserver -kill :1
  vncserver :1 -geometry 1920x1080 -depth 24
  ```

### NoVNC Connection Issues

- Clear your browser cache
- Try a different browser
- Restart the Dev Container:
  ```bash
  # In VS Code, use Ctrl+Shift+P and select "Dev Containers: Rebuild Container"
  ```

### Mobile Device Connection Issues

- Ensure you have a stable internet connection
- Try a different mobile browser
- Restart the Codespace by stopping and restarting it
- Clear browser cookies and cache

### MCreator Won't Start

- Check the DISPLAY variable: `echo $DISPLAY`
- Verify the MCreator installation: `ls /opt/mcreator`
- Check logs for errors: `cat ~/.mcreator/logs/*`

### Performance Issues

- Reduce the display resolution (e.g., 1280x720 instead of 1920x1080)
- Close unnecessary applications
- Allocate more resources to Docker in settings
- On mobile, ensure you have enough network bandwidth

## System Requirements

### For Local Dev Container (Windows, macOS, Linux):
- 4GB RAM minimum, 8GB recommended
- Docker Desktop installed and running
- VS Code with Dev Containers extension

### For GitHub Codespaces (All Platforms):
- Standard codespace allocation (4 cores, 8GB RAM)
- Internet connection
- Web browser (Chrome, Firefox, Safari, Edge, or any mobile browser)

### For Mobile Access (Android, iOS):
- Any modern mobile browser
- Internet connection
- Screen size 5 inches or larger recommended (but works on smaller screens too!)

## Contributing

We welcome contributions to this repository! To contribute:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Make your changes
4. Commit with clear messages: `git commit -m "Add my feature"`
5. Push to your fork: `git push origin feature/my-feature`
6. Create a Pull Request on GitHub

## License

This repository is **fully open source** and free to use. Check the LICENSE file for specific terms.

## Resources

- [MCreator Official Website](https://mcreator.net/)
- [MCreator Documentation](https://mcreator.net/wiki/)
- [NoVNC Project](https://novnc.com/)
- [Docker Documentation](https://docs.docker.com/)
- [Dev Containers Documentation](https://containers.dev/)
- [GitHub Codespaces Documentation](https://docs.github.com/en/codespaces)

## Support

If you encounter issues or have questions:

1. Check the Troubleshooting section above
2. Search existing GitHub Issues
3. Create a new GitHub Issue with detailed information
4. Check MCreator's official community forums

---

**Happy Modding!** 🎮 Start creating amazing Minecraft mods with MCreator today — from any device, on any platform!
