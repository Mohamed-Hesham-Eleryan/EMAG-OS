<div align="center">

<br>

# EMAG OS

### An AI-powered operating system simulation running inside a browser.

`Single HTML File` · `~33,000 Lines` · `~2.1 MB` · `Browser-Native`

<br>

[![Live Demo](https://img.shields.io/badge/Live_Demo-Launch_EMAG_OS-ff0000?style=for-the-badge)](https://mohamed-hesham-eleryan.github.io/EMAG-OS)
[![Release](https://img.shields.io/github/v/release/Mohamed-Hesham-Eleryan/EMAG-OS?style=flat-square)](https://github.com/Mohamed-Hesham-Eleryan/EMAG-OS/releases)

<br>

</div>

---

## What is EMAG OS?

EMAG OS is an experimental browser-native operating environment built around a simple question:

> **How far can a browser be pushed when the goal is not to build a website, but to build an environment?**

It looks like an operating system, behaves like an operating system, contains applications, a persistent filesystem, a terminal, an AI agent, visual effects, and an internal world — yet the core environment lives inside a single HTML document.

---

## System Preview

<br>

<p align="center">
  &nbsp;
  </p>

<p align="center">
  &nbsp;
  </p>

---

## The Constraint (The Experiment)

EMAG OS is approximately **33,000 lines** of HTML, CSS, and JavaScript contained in a single file of roughly **2.1 MB**.

The most important specification of EMAG OS may also be the strangest one: **It is all here.**

One document. One browser runtime. Thousands of interconnected functions. 
There is no traditional backend, no build pipeline (`src/`, `components/`, `build/`), and no framework-driven application architecture. Storage and runtime capabilities are pushed entirely into browser APIs.

**Why Single-File?**
A single HTML file is obviously not the architecture one would normally choose for a project of this scale. That is precisely the point. The constraint creates fascinating engineering problems: state management, namespace management, execution ordering, and UI composition without splitting the environment into a traditional project tree. 

That constraint is not a limitation hidden from the user. **It is the experiment.**

---

## Architecture & Interactions

EMAG OS is not a collection of disconnected UI components. It is organized as a collection of interacting subsystems sharing runtime state, storage, and system-level interfaces.

```text
                         ┌─────────────────────┐
                         │      EMAG OS        │
                         │   Browser Runtime   │
                         └──────────┬──────────┘
                                    │
              ┌─────────────────────┼─────────────────────┐
              │                     │                     │
              ▼                     ▼                     ▼
       ┌──────────────┐      ┌──────────────┐      ┌──────────────┐
       │ Desktop / WM │      │  EMAG Agent  │      │ Virtual FS   │
       │ Applications │      │ AI + Tools   │      │ IndexedDB    │
       └──────┬───────┘      └──────┬───────┘      └──────┬───────┘
              │                     │                     │
              └─────────────────────┼─────────────────────┘
```

The interesting part is the interaction between these systems:
* The AI is not isolated in a chat window; it can affect the UI.
* The filesystem is not merely a visual mock; applications and terminal commands operate against it.
* The desktop has real state, identity, configuration, and behavior.

---

## EMAG — The Agent Inside the Environment

At the center of the system is EMAG, the AI identity that inhabits the environment. The AI layer supports two fundamentally different execution paths:

1. **Fast Path:** Normal conversational requests sent directly to the configured AI provider.
2. **Agent Path:** Requests requiring actions, searching, inspection, or calculations enter a multi-step agent loop.

The agent has access to a catalog of tools including: `web search`, `OSINT operations`, `filesystem access`, `calculations`, `Python execution`, and `application control`.

This architecture moves beyond (`User → AI → Text`) toward:

```text
User → EMAG → Reason → Choose Tool → Execute → Observe Result → Act
```

### The AI Is Part of the Interface
The AI does not have to remain inside a rectangle labeled "Chat". The agent can trigger interface-level actions such as:
`OPEN` · `CLOSE` · `GLITCH` · `BLACKOUT` · `CURSOR` · `STARE` · `SHAKE` · `WALK`

The environment can react to the AI, and the AI can react to the environment.

**AI Logs & Persistent Memory:** Every AI event, sign, bubble, and TTS utterance is preserved untruncated in dedicated AI Logs (`ALL` / `EVENTS` / `TTS`), and conversations can be summarized and merged into long-term memory instead of being discarded on clear. Interface-level `[OPEN:...]` / `[ACTION:...]` commands now execute in sync with the exact sentence being spoken by the TTS engine, rather than firing on a fixed timer. Strict sanitization also prevents `<think>` blocks and internal chain-of-thought reasoning from leaking into chat history, visual bubbles, or TTS output.

---

## AI Provider Architecture

EMAG's AI layer is designed around a pluggable provider abstraction rather than a single hard-coded model. The system can accommodate:
* Cloud APIs
* Local AI & OpenAI-compatible endpoints
* Browser-accessible providers
* CLI / daemon bridges

The active automatic fallback chain can be configured independently from manually selectable providers.

---

## Persistent Filesystem & Terminal

**The Virtual Filesystem:**
Backed by IndexedDB through a structured storage layer, EMAG implements a persistent virtual filesystem. It exposes familiar concepts (`/home`, `/etc`, `/tmp`, `/var`). This allows the environment to maintain state across sessions instead of behaving like a stateless webpage. Uploaded media is converted to chunked Base64 before serialization, drag-and-drop works across folders with visual hover feedback, and duplicate filenames are automatically resolved (`file (1)`, `file (2)`, ...).

**The Terminal:**
A multi-mode command environment connected directly to the virtual filesystem and runtime.
* **Modes:** `SHELL`, `AI`, `JS`, `PYTHON` (backed by Pyodide).
* **Commands:** Includes standard Unix-style commands (`ls`, `cd`, `cat`, `mkdir`, `whoami`, `ps`) and specialized utilities (`fastfetch`, `cava`, hashing, JSON formatting).

---

## Desktop, Widgets & Typography

**The Desktop:**
The default interface uses a macOS-style Dock as the primary application launcher, supporting pinned applications, running-indicators, and minimize-on-click behavior. Multiple **Workspaces** let you organize the desktop into separate contexts instead of a single shared surface.

**Interactive Widgets:**
A system-level widget framework featuring draggable, resizable, and configurable desktop objects:
* **Clock:** Highly customizable dual-calendar display, with a glass-styled popup for monthly calendar view and persistent notification history.
* **Fastfetch:** Real browser and system-oriented information (not simulated output).
* **CAVA:** Real audio-reactive visualization responding to system TTS and media playback.
* **Media Player:** Remote control surface for EMAG's real media environment.

**System-Wide Typography:**
Theme-aware CSS variables retrofitting 300+ hardcoded font and color references, allowing the environment to shift entirely from "Technical" to "Cyberpunk" instantly using built-in Google Fonts presets, with native browser dialogs (`confirm()`/`prompt()`) replaced by themed in-app modals.

---

## Visual System & The Eye

EMAG deliberately treats visual feedback as part of the system architecture. It features real-time visual behaviors including glitch rendering, scan-line effects, blackout transitions, and physics-driven overlays.

**The Eye:**
Combining Three.js rendering, custom animation, and physics behavior, "The Eye" acts as a persistent, reactive representation of the system's presence—somewhere between a logo, character, and system monitor.

**The 3D Wallpaper Ring Picker:** A physics-driven wallpaper selector rebuilt for mobile — dynamically scaled card sizing, click-outside-to-dismiss interaction, and automatic palette extraction whenever a new wallpaper is applied.

---

## NEXUS OSINT & PZXF Cipher Notebook

* **NEXUS:** An experimental information-retrieval layer. It acts as an AI-accessible search surface where retrieved external information becomes part of subsequent agent reasoning. A query classifier routes searches intelligently (IP, domain, CVE, email, username, general), with optional SearXNG fallback support for self-hosted instances alongside the built-in Reddit/ArXiv fallback chain.
* **PZXF Cipher Notebook:** An experimental cryptographic notebook combining browser cryptography primitives (`AES-256-GCM`, `PBKDF2`, `SHA-512`, `GZIP`) with a custom encoding and transformation pipeline — now paired with a real, physics-based page-flip engine for natural text flow and page turning.

---

## EMAG LEGION (Peer-to-Peer)

An experimental peer-to-peer subsystem exploring the idea of multiple EMAG instances communicating and transferring system state across peers. It includes connection establishment, QR-based sharing, and chunked transmission of the HTML environment.

---

## Technology & Performance

EMAG OS is built primarily with browser-native technologies, deliberately avoiding conventional frontend frameworks (like React or Vue) for its core engine.

| Layer | Technology |
| :--- | :--- |
| **Markup & Styling** | HTML5, CSS3 |
| **Application Logic** | Vanilla JavaScript |
| **Storage** | IndexedDB (via Dexie.js) |
| **3D Rendering** | Three.js |
| **Window Interaction** | Interact.js |
| **Code Editing** | CodeMirror 5 |
| **Page Turning** | StPageFlip |
| **Python Runtime** | Pyodide |
| **Cryptography** | Web Crypto API |
| **Networking** | Browser Fetch / WebRTC |

**Performance Optimizations:** To make the 30,000+-line single-document constraint usable, the system utilizes debounced resize handling, idle scheduling, serialized AI requests, lazy initialization, and surgical widget updates.

---

## Development & Release — v8.70 "Workspaces"

**v8.70 Highlights:** This release introduces multi-**Workspaces** support, a real physics-based page-flip engine for the PZXF Notebook, a rebuilt 3D Wallpaper Ring Picker, TTS-synchronized AI actions, persistent AI chat memory, and sweeping improvements across theming, file handling, NEXUS OSINT reliability, and boot-time privacy.

* **Workspaces:** Multi-workspace support to organize the desktop into separate contexts.
* **PZXF Real Page-Flip Engine:** Physics-based pagination via StPageFlip, with drag-to-flip, edge-click navigation, and cursor position preserved across page turns.
* **Persistent Chat Memory & AI Logs:** Conversations can be summarized and merged into long-term memory instead of discarded on clear; full untruncated AI Logs (events + TTS) are now available.
* **TTS-Synchronized Actions:** Interface commands now fire in sync with the sentence being spoken, rather than on a fixed timer.
* **3D Wallpaper Ring Picker:** Mobile-optimized sizing, click-outside dismissal, a fixed pointer-capture selection bug, and smarter Elegant Mode handling.
* **Calendar & Notification History:** A glass-styled clock popup with monthly calendar and persistent notification history.
* **Theming:** 300+ hardcoded colors/fonts replaced with theme-aware variables; native dialogs replaced with themed in-app modals; consolidated and clarified theme settings.
* **VFS & File Explorer:** Chunked Base64 blob handling, cross-folder drag-and-drop, duplicate-safe filenames, and an auto-generated wallpapers folder.
* **NEXUS OSINT:** Worst-case fallback latency cut from 21–36s down to 7–13s, optional SearXNG integration, and a query classifier for smarter search routing.
* **Privacy & Boot:** Removed the aggressive boot-time geolocation prompt; verified no permissions are requested on boot; disabled native pinch/zoom gestures that conflicted with OS gestures.
* **Cleanup:** Removed the broken Telegram preview, the deprecated News tab, and unused legacy 3D wallpaper presets.

**Development Workflow:** EMAG OS was developed through an AI-assisted engineering workflow. The project became an exercise in constrained development: designing, integrating, debugging, and maintaining a complex interactive system substantially from a mobile environment.

---

## Security & Integrity

* **Security Note:** EMAG OS contains experimental authentication, browser cryptography, external API integrations, filesystem abstractions, and networking features. These components are intended for experimentation and demonstration. Do not use it as a substitute for a trusted operating system, password manager, secure communications platform, or professionally audited cryptographic software.
* **Project Integrity:** Tagged releases are associated with a cryptographically signed Git history (SSH Signature verified by GitHub), providing cryptographic provenance for the Git objects.

---

## Running EMAG OS (First Contact)

1. Launch the Live Environment: [EMAG OS](https://mohamed-hesham-eleryan.github.io/EMAG-OS) (or open the local `index.html`).
2. Create or enter a user account and let EMAG complete the boot sequence.
3. Open the **Terminal** from the Dock.
4. Type `help`, `fastfetch`, or `sysinfo` to explore the system capabilities.

---

## Philosophy & What it is Not

EMAG OS was not built because a browser needed another desktop simulator. It was built because building one is an interesting engineering problem. It sits at the intersection of Web Engineering, Artificial Intelligence, and Constraint-Driven Engineering. 

**It is not:** a replacement for Linux, a conventional frontend application, or a production OS. It is an exploration of what can happen when boundaries are intentionally blurred.

---

## Third-Party Software & Attribution

EMAG OS incorporates and adapts several open-source libraries and components.

| Project | License |
| :--- | :--- |
| [Three.js](https://threejs.org/) | MIT |
| [Dexie.js](https://dexie.org/) | Apache-2.0 |
| [Interact.js](https://interactjs.io/) | MIT |
| [Marked](https://marked.js.org/) | MIT |
| [PeerJS](https://peerjs.com/) | MIT |
| [QRCode.js](https://github.com/davidshimjs/qrcodejs) | MIT |
| [D3.js](https://d3js.org/) | ISC |
| [Tone.js](https://tonejs.github.io/) | MIT |
| [Color Thief](https://github.com/lokesh/color-thief) | MIT |
| [CodeMirror 5](https://codemirror.net/5/) | MIT |
| [Monaco Editor](https://microsoft.github.io/monaco-editor/) | MIT |
| [Pyodide](https://pyodide.org/) | MPL-2.0 |
| [StPageFlip](https://nodlik.github.io/StPageFlip/) | MIT |
| [React Bits](https://reactbits.dev/) | MIT + Commons Clause |

React Bits components used in EMAG OS were adapted from their original React implementations for use in the project's browser-native, single-file architecture.

Google Fonts are also used. Individual typefaces are distributed under their respective open-source font licenses.

Full third-party attribution and licensing information is included directly in `index.html`.

---

## License

EMAG OS is licensed under the GNU Affero General Public License v3.0 or later (AGPL-3.0-or-later).

Copyright © 2026 Mohamed Hesham Eleryan.

See [`LICENSE`](LICENSE) for the complete license text.

---

<div align="center">

**EMAG OS**

A browser pretending to be an operating system.<br>
An AI pretending to live inside it.<br>
A single file pretending it should not be possible.

<br>
Built by Mohamed Hesham Eleryan

</div>
