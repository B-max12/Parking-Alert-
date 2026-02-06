# Parking Alert System 

An Electron-based desktop application with integrated C++ components for car chime system management.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Building from Source](#building-from-source)
- [Running the Application](#running-the-application)
- [Docker Support](#docker-support)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## 🚗 Overview

This project provides a comprehensive car chime system solution built with:
- **Electron** - Cross-platform desktop application framework
- **C++** - Core system components with CMake build system
- **Frontend** - Modern web-based user interface

## ✨ Features

- Desktop application for car chime management
- Cross-platform support (Windows, macOS, Linux)
- Docker containerization support
- Integrated build system with CMake

## 📦 Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher recommended)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
- [CMake](https://cmake.org/) (for C++ components)
- [Visual Studio](https://visualstudio.microsoft.com/) or compatible C++ compiler (Windows)
- [Docker](https://www.docker.com/) (optional, for containerized deployment)

## 🔧 Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/car-chime-system.git
   cd car-chime-system
   ```

2. **Install Node.js dependencies:**
   ```bash
   npm install
   ```

3. **Set up environment variables:**
   ```bash
   cp car-chime-system-main/.env.example car-chime-system-main/.env
   # Edit .env with your configuration
   ```

## 🏗️ Building from Source

### Building C++ Components

**Windows:**
```bash
./build_release.bat
```

**Using CMake directly:**
```bash
cmake --preset=default
cmake --build build --config Release
```

### Building the Electron App

```bash
npm run build
```

## 🚀 Running the Application

### Development Mode
```bash
npm start
```

### Production Mode
```bash
npm run start:prod
```

See [For_run_the_code](For_run_the_code) for additional run instructions.

## 🐳 Docker Support

### Using Docker Compose

**Production:**
```bash
docker-compose -f compose.yaml up
```

**Debug Mode:**
```bash
docker-compose -f compose.debug.yaml up
```

### Building Docker Image
```bash
docker build -t car-chime-system .
```

## 📁 Project Structure

```
├── src/                    # Source code
├── frontend/               # Frontend application
├── include/                # C++ header files
├── build/                  # CMake build output
├── dist-electron/          # Electron distribution files
├── bin/                    # Binary outputs
├── resources/              # Application resources
├── scripts/                # Utility scripts
├── sql/                    # Database schemas/queries
├── docs/                   # Documentation
├── video/                  # Video resources
├── logo/                   # Logo assets
├── car-chime-system-main/  # Main car chime module
├── main.js                 # Electron main process
├── preload.js              # Electron preload script
├── CMakeLists.txt          # CMake configuration
├── package.json            # Node.js dependencies
├── Dockerfile              # Docker configuration
└── compose.yaml            # Docker Compose configuration
```

## 📖 Documentation

- [Setup Guide](SETUP_GUIDE.md) - Detailed setup instructions
- [TODO](TODO.md) - Planned features and improvements

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the terms specified in [LICENSE.txt](LICENSE.txt).

---


⭐ If you find this project useful, please consider giving it a star!
