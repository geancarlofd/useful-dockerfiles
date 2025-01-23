
---

### Dockerfile: `windows-cpp-cmake-build` (`Dockerfile.windows-cpp-cmake-build`)
This Dockerfile is designed to create a Windows-based container environment tailored for building and compiling C++ projects. It leverages **Windows Server Core 2019** as the base image and installs essential tools for development.

#### Key Features:
- **Visual Studio Build Tools**: Includes workloads and components for C++ development, such as:
  - Microsoft Visual C++ tools (`VCTools`).
  - ATL/MFC libraries.
  - Support for Native, Managed, and Universal Desktop development.
  - Windows 10 SDK for building modern Windows applications.
- **CMake**: Installs CMake version 3.27.5 for project configuration and build system generation.
- **Environment Configuration**: Adds CMake to the system `PATH` for seamless access during container sessions.

#### Use Cases:
- Building and testing C++ applications in a controlled Windows container environment.
- Automating the setup of development tools for consistent builds in CI/CD pipelines.
- Supporting projects that require both Visual Studio Build Tools and CMake.

---

### Dockerfile: `build` (`Dockerfile.build`)
This Dockerfile extends the `windows-cpp-cmake-build` image to create an environment specifically designed for building C++ projects using **CMake**. It assumes the base image already includes essential tools like Visual Studio Build Tools and CMake, streamlining the process for C++ development and builds.

#### Key Features:
- **Base Image**: Uses `windows-cpp-cmake-build` as the foundation, which provides:
  - Visual Studio Build Tools for compiling C++ applications.
  - CMake for generating and managing build systems.
  - A Windows Server Core 2019 environment.
- **Project Setup**:
  - Sets up the working directory at `/app/sdk` where the source files are copied.
  - Configures the build system by running `cmake ..` in a dedicated `build` directory.
- **Build Process**:
  - Compiles the project in `Release` mode with verbose output for detailed build logs.
  - Maintains a clean directory structure by separating source files and build artifacts.

#### Use Cases:
- Simplifies building C++ projects in a Windows-based environment with CMake.
- Ideal for CI/CD pipelines that require consistent builds with Visual Studio and CMake integration.
- Supports modular project structures with a dedicated `build` directory.

---
