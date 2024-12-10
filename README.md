
# Rust Dev Container Example

This repository showcases how to set up a Rust development environment using a VS Code Dev Container. It leverages a `.devcontainer.json` file for container configuration and a `Dockerfile` to handle system-level changes, such as installing additional packages.

## Features

- **Rust Toolchain:** Pre-installed `rustc`, `cargo`, and `rustup` to streamline development.
- **Custom Dockerfile:** Allows you to modify the underlying image, including installing packages via `apt-get`.
- **VS Code Extensions:** Easily integrate and automate the installation of extensions like GitHub Copilot and Rust Analyzer.
- **Development Environment in Isolation:** Run your development environment in a container, ensuring consistency across different machines.

## Getting Started

### Prerequisites

- **Docker:** Make sure Docker is installed and running on your system.
- **VS Code:** Ensure you have Visual Studio Code installed.
- **Remote Containers Extension:** Install the "Remote - Containers" extension in VS Code. (This has since been integrated as "Dev Containers" in recent versions.)

### Setup Steps

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/rust-devcontainer-example.git
   cd rust-devcontainer-example
   ```

2. **Open in VS Code:**
   Open this folder in VS Code (e.g., `code .` from the terminal or via the GUI).

3. **Open the Dev Container:**
   - Press `F1` in VS Code and select **Dev Containers: Rebuild and Reopen in Container**.
   - VS Code will use the `.devcontainer/devcontainer.json` and the provided `Dockerfile` to build and start the container.

4. **Customizing the Container:**
   - Edit the `.devcontainer/devcontainer.json` file to install or configure additional VS Code extensions.
   - Update the `Dockerfile` to add system-level tools. For example:
     ```dockerfile
     FROM mcr.microsoft.com/vscode/devcontainers/rust:latest
     ENV DEBIAN_FRONTEND=noninteractive
     RUN apt-get update && apt-get install -y curl make git
     ```
   - After making changes, rebuild the container to apply them.

### Testing the Setup

Once the container is running:

- Open a terminal within the container (`Terminal > New Terminal`).
- Run:
  ```bash
  cargo run
  ```
  This command will compile and run the default Rust "Hello, world!" project.
  
- Test Rust Analyzer and Copilot by editing `src/main.rs` and watching for suggestions, code completions, and linting feedback.

### Notes

- **Extensions:** Additional VS Code extensions can be declared in the `devcontainer.json` file. After rebuilding the container, these will be automatically installed.
- **System-Level Dependencies:** Use the `Dockerfile` for OS-level changes like installing system packages, configuring environment variables, or adding tools not available by default.

