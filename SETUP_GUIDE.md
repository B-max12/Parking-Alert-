# Park Alert Setup Guide

## Prerequisites Installation

### 1. Install Visual Studio 2022 Build Tools
- Download from Microsoft website
- Include C++ development tools
- Make sure MSVC compiler is selected

### 2. Install CMake
- Download from https://cmake.org/download/
- Add to PATH during installation

### 3. Install vcpkg (C++ Package Manager)
```cmd
git clone https://github.com/Microsoft/vcpkg.git
cd vcpkg
.\bootstrap-vcpkg.bat
.\vcpkg integrate install
```

### 4. Install Required Dependencies
```cmd
.\vcpkg install libqrencode:x64-windows
.\vcpkg install cpp-httplib:x64-windows
.\vcpkg install nlohmann-json:x64-windows
.\vcpkg install mysql-connector-cpp:x64-windows
```

## Build Process

### Method 1: Using the Batch Script
```cmd
build_release.bat
```

### Method 2: Manual Build
```cmd
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_TOOLCHAIN_FILE=[path-to-vcpkg]\scripts\buildsystems\vcpkg.cmake
cmake --build . --config Release
```

Replace `[path-to-vcpkg]` with your actual vcpkg installation path (e.g., `C:\vcpkg`)

## Common Issues and Solutions

### Issue: 'qrencode.h' file not found
**Solution**: Make sure you installed libqrencode via vcpkg and the CMAKE_TOOLCHAIN_FILE is properly set

### Issue: std::optional not recognized
**Solution**: Ensure C++17 standard is being used. The CMakeLists.txt should have:
```cmake
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
```

### Issue: std::filesystem not recognized
**Solution**: Add this to CMakeLists.txt:
```cmake
target_compile_features(park_alert PRIVATE cxx_std_17)
```

### Issue: Various 'undeclared identifier' errors
**Solution**: These typically occur when include paths are not properly set. Make sure:
- vcpkg toolchain file is used
- All dependencies are installed via vcpkg
- Include directories are properly configured in CMakeLists.txt

## Alternative: Quick Test Build

If you want to quickly test if your environment works, create a simple test:

```cmd
cd build
cmake .. -DCMAKE_TOOLCHAIN_FILE=C:\vcpkg\scripts\buildsystems\vcpkg.cmake
cmake --build . --config Debug
```

## Verification Steps

1. Check if vcpkg packages are installed:
```cmd
vcpkg list
```
You should see libqrencode, cpp-httplib, nlohmann-json, mysql-connector-cpp

2. Check CMake version:
```cmd
cmake --version
```
Should be 3.16 or higher

3. Verify compiler:
```cmd
cl
```
Should show Microsoft C/C++ Compiler

## Troubleshooting

If you still have issues:

1. **Clean build directory**:
```cmd
rmdir /s build
mkdir build
cd build
```

2. **Reconfigure with explicit toolchain**:
```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=C:\vcpkg\scripts\buildsystems\vcpkg.cmake -DCMAKE_BUILD_TYPE=Debug
```

3. **Build with verbose output**:
```cmd
cmake --build . --config Debug --verbose
```

## Environment Variables

Make sure these environment variables are set if needed:
- `VCPKG_ROOT`: Path to your vcpkg installation
- Ensure `cmake` and `cl` (compiler) are in your PATH

## Quick Dependency Check Script

Run this to verify all dependencies are available:

```cmd
echo Checking dependencies...
where cmake
where cl
vcpkg list | findstr qrencode
vcpkg list | findstr httplib
vcpkg list | findstr json
vcpkg list | findstr mysql
```

All commands should return successful results.

Once all dependencies are properly installed and the environment is set up, the build errors should resolve and the Park Alert system will compile successfully.