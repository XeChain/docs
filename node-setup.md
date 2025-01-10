# XeChain Node Setup

This guide explains how to download, build, and run the **XeChain** node from source.

---

## Prerequisites

Make sure you have the following tools installed on your system:

1. **Go (version ≥ 1.19)**
   - [Download Go here](https://go.dev/dl/)  
   - To verify:
     ```bash
     go version
     ```
   - If this does not show Go 1.19 or higher, please upgrade your Go installation.

2. **Git**  
   - On Ubuntu/Debian:
     ```bash
     sudo apt-get update
     sudo apt-get install git
     ```
   - On CentOS/RHEL:
     ```bash
     sudo yum install git
     ```

3. **Make**  
   - On Ubuntu/Debian:
     ```bash
     sudo apt-get install make
     ```
   - On CentOS/RHEL:
     ```bash
     sudo yum install make
     ```

4. **Build Essentials** (e.g., gcc, g++, etc.)
   - On Ubuntu/Debian:
     ```bash
     sudo apt-get install build-essential
     ```
   - On CentOS/RHEL:
     ```bash
     sudo yum groupinstall "Development Tools"
     ```

---

## Step-by-Step Installation

1. **Clone the XeChain repository**
   ```bash
   git clone https://github.com/XeChain/xe-core
   ```
   This will create a new folder named `xe-core`.

2. **Change into the repository directory**
   ```bash
   cd xe-core
   ```

3. **Build the XeChain node**
   ```bash
   make xe
   ```
   This command compiles the node and places the `xe` binary in the `xe-core/build/bin` folder.

---

## Running Your XeChain Node

After the build completes successfully, you can start your node by navigating to the folder where the binary is located and running `xe`:

```bash
cd build/bin
./xe
```

By default, it will run in the foreground, displaying logs. Use flags/options if available to run with specific configurations.

---

### Troubleshooting

- **"go: command not found"**  
  Ensure Go is in your `PATH`. In your shell config (e.g., `~/.bashrc`, `~/.zshrc`), add lines similar to:
  ```bash
  export GOROOT=/usr/local/go
  export GOPATH=$HOME/go
  export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
  ```
- **Permission denied when running `./xe`**  
  Make the file executable:
  ```bash
  chmod +x xe
  ```

---

## Enjoy your XeChain node!

For additional help or to report an issue, please visit [GitHub Issues](https://github.com/XeChain/xe-core/issues).
