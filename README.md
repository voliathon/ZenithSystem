# 🌟 Zenith System

> **The Pinnacle FFXI Enhancement Framework.** Built on a secure, crash-resistant, decoupled architecture.

The **Zenith System** is the next-generation platform for enhancing the Final Fantasy XI client. We fundamentally redefine stability and extensibility by moving beyond the volatility of traditional in-process DLL injection.

Our core principle is **Isolation**: The FFXI game client runs untouched, while all complex logic, Addons, and custom UI rendering operate in a safe, external environment.

---

## ⚙️ How It Works: Decoupling for Stability

Zenith achieves rock-solid stability by splitting functionality across two isolated processes connected by high-speed Inter-Process Communication (IPC).

| Component | Process | Role | Technology |
| :--- | :--- | :--- | :--- |
| **Zenith Probe** | **Injected DLL (Minimal)** | **Data Acquisition.** Safely reads essential memory pointers (HP, MP, coordinates) and transmits data out via IPC. **It performs no complex logic or rendering.** | C/C++ |
| **Zenith Host** | **External Executable** | **Logic & Control.** Receives the game state from the Probe, hosts the Addon Runtime, and handles all processing and command injection. | Node.js / C# |
| **Zenith Renderer**| **External Process** | **Display.** Creates the high-performance, custom UI overlay, completely decoupled from the FFXI graphics pipeline. | DXGI Overlay / Modern UI Frameworks |

### Key Benefits

* ✅ **Crash Isolation:** A crashing community Addon only kills the **Zenith Host**, leaving the stable FFXI client running. Users can restart the Host without losing progress.
* ✅ **Modern Dev Experience:** Addons (Zenith Modules) are built using modern languages (Node.js/Python) and tools, replacing the need for complex C++ or legacy Lua debugging.
* ✅ **Update Resilience:** Game patches primarily require updating only the **Zenith Probe**. The high-level **Zenith API** exposed to Addons remains consistent, minimizing maintenance for the community.

---

## 🚀 Getting Started

### 1. Installation
The Zenith Launcher (TODO: EPIC 5) handles the automated download and installation of the required components.

### 2. Running Zenith Modules
Zenith Modules (Addons) are placed in the `/Modules` directory of the Zenith Host. They are loaded and run within the secure external runtime.

### 3. Core Console
Commands and debugging output are managed through the Zenith Host console window and rendered in a clean, external console overlay.

---

## 🛠️ Developer Resources

We welcome contributions to the Core, the Zenith Probe, and the community Module ecosystem.

* **API Documentation:** [Link to Zenith API Reference]
* **Contribution Guide:** See the [CONTRIBUTING.md] file for environment setup and coding standards for the C++ Probe and the Node.js/C# Host.
