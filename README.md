# HelloWorld Vulkan Renderer

A minimal yet scalable Vulkan-based rendering engine in C++. This project begins as a simple demo but is designed to evolve into a modular and extensible real-time renderer. It demonstrates the setup of Vulkan, GLFW, and GLM in a clean CMake environment, providing a foundation for more advanced graphics features in the future.

---

## 🚀 Features

- Vulkan instance and device initialization
- GLFW window creation with Vulkan surface integration
- Swapchain creation and cleanup
- Support for MoltenVK on macOS
- Modular structure prepared for future rendering engine components

---

## 📦 Requirements

| Dependency     | Version | Notes                                                                 |
|----------------|---------|-----------------------------------------------------------------------|
| Vulkan SDK     | 1.3+    | Download from [LunarG](https://vulkan.lunarg.com/sdk/home).           |
| GLFW           | 3.x     | Must be installed and discoverable via `pkg-config`.                 |
| GLM            | Latest  | Header-only. Assumes install at `/opt/homebrew/include` (macOS).     |
| CMake          | ≥ 3.15  | Used to generate build system.                                       |
| C++ Compiler   | C++17   | Tested with Clang and GCC.                                           |

---

## 🖥 Platform Support

✅ macOS (via MoltenVK)  
☐ Linux (to be tested)  
☐ Windows (to be tested)

---

## 🧰 Installation

### 🔧 macOS Setup (Homebrew)

Install dependencies:
```bash
brew install glfw glm vulkan-sdk
```

Set up the Vulkan SDK environment (add to `~/.zshrc` or `~/.bash_profile`):
```bash
export VULKAN_SDK=path/to/vulkan/sdk/<version>/macOS
export PATH=$VULKAN_SDK/bin:$PATH
export DYLD_LIBRARY_PATH=$VULKAN_SDK/lib:$DYLD_LIBRARY_PATH
export VK_ICD_FILENAMES=$VULKAN_SDK/share/vulkan/icd.d/MoltenVK_icd.json
export VK_ADD_LAYER_PATH=$VULKAN_SDK/share/vulkan/explicit_layer.d
export VK_DRIVER_FILES=$VULKAN_SDK/share/vulkan/icd.d/MoltenVK_icd.json
```

---

## 🏗️ Build Instructions

Clone and build the project:

```bash
git clone https://github.com/imaknas/helloworld-vulkan.git
cd helloworld-vulkan
mkdir build && cd build
cmake ..
make
```

Compile the shaders:
```bash
./compile-shader
```

Run the program:
```bash
cd bin
./HelloWorld
```

## 🛣 Roadmap

- [ ] Add shader module support
- [ ] Implement triangle rendering
- [ ] Add debug validation layers
- [ ] Load GLTF models
- [ ] Add render graph abstraction
- [ ] Basic UI overlay (ImGui or custom)
- [ ] Multi-platform support
- [ ] Scene graph and ECS integration
- [ ] Lighting and material system

---

## ⚠️ Known Issues

- Hardcoded GLM path (`/opt/homebrew/include`) — not portable.
- Currently macOS-only (MoltenVK). Cross-platform abstraction pending.
- Shader file paths are currently relative; ensure the working directory is appropriate.

---

## 📜 License

MIT License. See [LICENSE](./LICENSE) for details.

---

## 👤 Author

**Knas Xiao**  
GitHub: [@imaknas](https://github.com/imaknas)

---

## 💡 Notes

- Uses `pkg-config` to locate GLFW. You may need to install `pkgconf` if missing.
- Compile commands (`compile_commands.json`) are enabled by default for use with clangd or other language servers.
