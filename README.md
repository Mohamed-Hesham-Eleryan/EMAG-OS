<div align="center">

# EMAG OS

### An AI-powered operating system simulation running inside a browser.

`Single HTML File` · `30,000+ Lines` · `~1.94 MB` · `Browser-Native`

<br>

[![Live Demo](https://img.shields.io/badge/Live_Demo-Launch_EMAG_OS-ff0000?style=for-the-badge)](https://mohamed-hesham-eleryan.github.io/EMAG-OS)
[![Release](https://img.shields.io/github/v/release/Mohamed-Hesham-Eleryan/EMAG-OS?style=flat-square)](https://github.com/Mohamed-Hesham-Eleryan/EMAG-OS/releases)

</div>

---

## What is EMAG OS?

EMAG OS is an experimental browser-native operating environment built around a simple question:

> **How far can a browser be pushed when the goal is not to build a website, but to build an environment?**

It looks like an operating system, behaves like an operating system, contains applications, a filesystem, a terminal, an AI agent, persistent user state, system configuration, tools, visual effects, media systems, and an internal world — yet the core environment lives inside a single HTML document.

There is no traditional backend, no build pipeline, and no framework-driven application architecture.

The system is deliberately constrained.

And that constraint is part of the engineering challenge.

---

## The Experiment

EMAG OS is approximately **30,000 lines of HTML, CSS, and JavaScript** contained in a single file of roughly **1.94 MB**.

The objective was never simply to make a large HTML file.

The objective was to make that file behave like a coherent software environment.

Inside the same document are systems for:

- desktop and window management
- application launching and lifecycle
- persistent browser storage
- a virtual filesystem
- authentication and sessions
- a multi-mode terminal
- an embedded Python runtime interface
- a browser-based code environment
- AI chat and agent execution
- tool-assisted information retrieval
- system configuration
- media handling
- themes and wallpapers
- cryptographic notebook functionality
- real-time visual effects
- an interactive 3D system identity
- experimental peer-to-peer communication
- system-level events and interactions

The architecture is intentionally extreme:

**one document → one runtime → many systems.**

---

## Architecture

EMAG OS is not a collection of disconnected UI components.

It is organized as a collection of interacting subsystems sharing runtime state, storage, and system-level interfaces.

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
                                    │
                         ┌──────────▼──────────┐
                         │   Browser APIs +    │
                         │  External Services  │
                         └─────────────────────┘
```

The interesting part is the interaction between these systems.

The AI is not isolated in a chat window.

The filesystem is not merely a visual mock.

The desktop is not simply decoration.

Applications, terminal commands, widgets, configuration, storage, and AI capabilities participate in the same environment.

---

## EMAG — The Agent Inside the Environment

At the center of the system is EMAG, the AI identity that inhabits the environment.

The AI layer supports two fundamentally different execution paths.

### Fast Path
Normal conversational requests can be sent directly to the configured AI provider.

### Agent Path
Requests that require actions, searching, inspection, calculations, navigation, or other tools can enter a multi-step agent loop.

The agent can work with tools covering areas such as:

- web search
- information retrieval
- OSINT-oriented operations
- filesystem access
- system information
- calculations
- Python execution
- GitHub lookup
- weather and data utilities
- crypto and forex data
- network-oriented utilities
- external integrations
- application control

The architecture therefore moves beyond:

```text
User → AI → Text
```

toward:

```text
User
  ↓
EMAG
  ↓
Reason
  ↓
Choose Tool
  ↓
Execute
  ↓
Observe Result
  ↓
Reason Again
  ↓
Respond / Act
```

The agent layer includes request management, execution logging, tool handling, and controlled multi-step execution.

---

## A Browser With a Filesystem

EMAG OS implements a persistent virtual filesystem using browser storage.

It exposes familiar concepts such as:

- `/home/<user>`
- `/documents`
- `/downloads`
- `/pictures`
- `/music`
- `/.config`
- `/etc`
- `/tmp`
- `/var`
- `/var/log`

Files and directories are persisted rather than being recreated purely as visual elements.

Applications and terminal commands operate against the same underlying virtual filesystem.

This allows the environment to maintain state between sessions instead of behaving like a stateless webpage.

The filesystem is backed by IndexedDB through a structured storage layer.

---

## The Desktop

The desktop is designed as an environment rather than a static canvas.

The default interface in v8.64 uses a macOS-style Dock as the primary application launcher.

The Dock provides:

- pinned applications
- customizable pinned-app selection
- running-application indicators
- minimize-on-click behavior
- an all-applications launcher through the EMAG logo

The classic taskbar remains available as an alternative interface mode.

Desktop customization also controls:

- Dock / Taskbar mode
- pinned applications
- desktop icon visibility
- theme behavior
- visual presentation

Desktop icons are hidden by default in the current configuration, while applications remain accessible through the Dock and application launcher.

---

## Desktop Widgets

EMAG OS includes a system-level widget framework designed around interactive desktop objects.

Widgets can be:

- dragged
- resized
- rotated
- removed
- restored
- individually configured

Long-press interaction exposes editing controls directly on the widget.

The system currently includes several specialized widgets.

### Clock
The Clock can display:
- day name
- Gregorian date
- Hijri date
- time

Its typography is independently customizable, including separate font treatment for day and date/time elements. Colors, alignment, and background behavior can also be configured.

### Fastfetch
EMAG's Fastfetch provides real browser and system-oriented information rather than simulated output.

It can expose information such as:
- browser
- storage
- runtime information
- FPS
- display information
- system identity

The widget adapts its presentation to the current theme and mobile layout.

### CAVA
CAVA is a real audio-reactive visualization layer.

It can react to audio generated by the environment, including:
- system TTS
- interface sounds
- NEXUS previews
- media playback

It includes a classic left-right mirrored visualization mode and does not rely on simulated waveform data.

### Media Player
The Media Player widget acts as a remote control surface for EMAG's real media environment.

It can:
- control playback
- move between files in the same folder
- play audio quietly in the background
- remember the last played item

The widget system also supports theme-following colors, per-part overrides, optional glass backgrounds, and per-widget reset behavior.

---

## The Terminal

EMAG includes its own terminal environment.

It is designed to feel like a system interface rather than a decorative command prompt.

The terminal supports multiple execution modes:

- **SHELL**
- **AI**
- **JS**
- **PYTHON**

The shell provides filesystem and system-style commands such as:

`ls`, `cd`, `pwd`, `cat`, `mkdir`, `rm`, `cp`, `mv`, `find`, `touch`, `write`, `whoami`, `uname`, `ps`, `history`, `uptime`, `sysinfo`

Utility operations include functionality for hashing, Base64, UUID generation, calculations, JSON formatting, and content retrieval.

The terminal also includes:

`fastfetch`, `cowsay`, `cava`

Fastfetch provides animated system-oriented output and an ASCII-to-SVG logo transition.

Python execution is backed by Pyodide, allowing Python code to execute directly inside the browser environment.

---

## Applications & Environment

EMAG OS contains a collection of applications and system interfaces designed to make the environment feel like a small software platform rather than a landing page.

### AI Interface
The primary interface for communicating with EMAG and invoking its agent capabilities.

### Terminal
A multi-mode command environment connected to the virtual filesystem and browser runtime.

### File Explorer
A graphical interface over the same persistent virtual filesystem used by the terminal.

### Code Environment
A browser-based development environment with editor capabilities.

### Settings
System-level configuration including:
- system identity
- AI identity
- user identity
- custom system prompts
- themes
- wallpapers
- font systems
- AI provider configuration
- voice behavior
- environment behavior
- desktop configuration

### Media Environment
Browser-native handling for images, audio, video, and user-provided media.

---

## The Font System

EMAG OS v8.64 introduces a dedicated system-wide typography layer.

Instead of treating fonts as isolated application styling, typography is now part of the environment's customization system.

Five built-in presets are provided:

- System
- Calm + Technical
- Cyber
- Minimal
- Experimental

The system uses real web fonts and caches loaded font resources through the existing library cache mechanism so previously loaded resources can remain available for offline use where browser caching permits.

Approximately 320 hardcoded font references were retrofitted into theme-aware CSS variables.

Terminal and ASCII rendering retain a dedicated monospace slot to preserve alignment and readability.

Widgets can also override typography independently, including:
- Clock day font
- Clock date/time font
- Fastfetch font

The result is a typography system that can shift the entire environment from restrained and technical to cyberpunk-inspired or experimental without rewriting individual interfaces.

---

## The AI Is Part of the Interface

One of the defining ideas behind EMAG OS is that the AI does not have to remain inside a rectangle labeled "Chat".

EMAG can interact with the environment itself.

The agent can trigger interface-level actions such as:

- `OPEN`
- `CLOSE`
- `NOTIFY`
- `GLITCH`
- `SCAN`
- `BLACKOUT`
- `CURSOR`
- `STARE`
- `SHAKE`
- `TYPE`
- `WALK`

These actions allow the AI to become part of the visual and behavioral layer of the system.

The result is closer to:

```text
AI + UI + Environment
```

than:

```text
Chatbot + Website
```

The environment can react to the AI, and the AI can react to the environment.

---

## EMAG's Visual System

The interface deliberately treats visual feedback as part of the system architecture.

EMAG contains multiple layers of real-time visual behavior including:

- glitch rendering
- scan-line effects
- blackout transitions
- cursor interactions
- system notifications
- corrupted-data overlays
- animated HUD elements
- reactive waveform rendering
- an interactive system Eye
- physics-driven visual behavior

These are not simply decorative CSS animations.

They form part of the interaction model between the user, the system, and the AI.

---

## The Eye

The Eye is one of EMAG OS's central visual identities.

It combines:

- Three.js rendering
- custom animation
- physics behavior
- system state
- reactive visual feedback

The Eye acts as a persistent representation of the system's presence.

It is intentionally somewhere between:

`logo` · `interface` · `character` · `system monitor`

rather than being just an icon.

---

## NEXUS / OSINT Layer

EMAG contains an experimental information-retrieval layer designed to allow the AI to interact with external information.

The NEXUS tooling can be used as an AI-accessible search surface, while the agent layer can consume returned information and continue reasoning from it.

This creates a pipeline closer to:

```text
Question
   ↓
EMAG
   ↓
NEXUS / Tool
   ↓
External Information
   ↓
Agent Reasoning
   ↓
Result
```

The system can maintain contextual information between certain operations, allowing retrieved information to become part of subsequent agent reasoning.

---

## PZXF Cipher Notebook

EMAG contains an experimental cryptographic notebook called PZXF.

It combines a notebook-style interface with browser cryptography primitives and a transformation pipeline involving:

```text
Compression
      ↓
Encryption
      ↓
Encoded Representation
```

The implementation uses browser cryptography facilities including:

- `AES-256-GCM`
- `PBKDF2`
- `SHA-512`
- `GZIP`

The notebook maintains persistent pages and provides encryption/decryption functionality inside the environment.

This component is intentionally experimental and should not be treated as a replacement for professionally audited cryptographic software.

---

## Persistence

EMAG OS maintains state across sessions through browser storage.

Persistent state can include:

- user accounts
- session information
- filesystem contents
- configuration
- themes
- wallpapers
- widget configuration
- notebook data
- application state
- AI configuration

The virtual filesystem is backed by IndexedDB through a structured storage layer.

Settings and local state are designed to survive browser restarts where browser storage remains available.

---

## Identity & Customization

EMAG is intentionally configurable.

The user can customize the identity of the environment itself.

For example:

- System Name
- AI Name
- AI Subtitle
- User Display Name
- Custom System Prompt
- Theme
- Wallpaper
- Fonts
- Voice
- Visual Behavior
- AI Provider
- Desktop Layout
- Widget Configuration

This means the environment is not completely fixed at build time.

The user can modify how the system presents itself and, in the case of the AI, how it behaves.

---

## EMAG LEGION

EMAG also contains an experimental peer-to-peer subsystem.

The LEGION layer explores the idea of multiple EMAG instances communicating and transferring system state across peers.

It includes mechanisms for:

- peer identification
- connection establishment
- QR-based sharing
- peer communication
- cloning/propagation experiments
- chunked transmission of the HTML environment

An EMAG instance can therefore participate in a small network of other instances rather than existing purely as an isolated webpage.

This remains one of the more experimental parts of the project.

---

## Release v8.64

v8.64 represents a major interface and systems update.

The release introduces the new Dock-based desktop experience, a complete widget framework, system-wide font customization, terminal improvements, and a collection of persistence and rendering fixes.

### Major additions
- Dock-based default desktop navigation
- customizable pinned applications
- redesigned Settings sidebar
- interactive desktop widgets
- Clock, Fastfetch, CAVA, and Media Player widgets
- system-wide font presets
- per-widget typography
- new terminal commands
- real audio-reactive CAVA visualization
- improved media control
- real system/browser information through Fastfetch
- triple-click / tap Fullscreen API interaction

### Important fixes
- synchronous Settings/localStorage writes
- corrected toggle persistence
- Dock mode persistence across reboot
- surgical widget updates
- automatic reload after Snapshot "Replace All"
- widget restoration fixes
- improved Fastfetch detection and mobile layout

### Deliberate removals
Some systems were removed after evaluation rather than being retained simply because they existed.

Removed from the current release:
- scripted offline AI messages presented as live AI responses
- the Portfolio application and its automatic first-boot launch
- Weather widget
- Notes widget

The goal is not maximum feature count.

The goal is a more coherent environment.

---

## Engineering Constraints

The project intentionally operates under unusual constraints.

### Single-file architecture
The core environment exists in one HTML document.

No conventional:
- `src/`
- `components/`
- `routes/`
- `services/`
- `build/`

architecture is required to launch the core system.

### No traditional backend
The environment is designed to perform a large amount of its work directly inside the browser.

### Browser-native state
Storage and runtime capabilities are pushed into browser APIs rather than delegated to a conventional server.

### AI-assisted development
The project was developed through an AI-assisted workflow rather than a traditional desktop IDE-centric workflow.

A particularly unusual part of the experiment is that the system was developed substantially from a mobile phone.

That constraint became part of the engineering story.

---

## Why Single-File?

A single HTML file is obviously not the architecture one would normally choose for a project of this scale.

That is precisely the point.

The constraint creates interesting engineering problems:

- state management
- namespace management
- dependency loading
- execution ordering
- UI composition
- persistence
- runtime performance
- debugging
- code organization
- AI integration
- error isolation

The project explores how much structure can be created without splitting the environment into a traditional project tree.

The result is intentionally unconventional.

---

## Technology

EMAG OS is built primarily with browser-native technologies:

| Layer | Technology |
| :--- | :--- |
| **Markup** | HTML5 |
| **Styling** | CSS3 |
| **Application Logic** | Vanilla JavaScript |
| **Storage** | IndexedDB |
| **Storage Abstraction** | Dexie.js |
| **3D Rendering** | Three.js |
| **Window Interaction** | Interact.js |
| **Code Editing** | Monaco Editor |
| **Python Runtime** | Pyodide |
| **Cryptography** | Web Crypto API |
| **Graphics** | Canvas / SVG |
| **AI** | Pluggable provider architecture |
| **Networking** | Browser Fetch / WebRTC-oriented peer systems |
| **Deployment** | GitHub Pages / Static Hosting |

The system deliberately avoids a conventional frontend framework.

---

## AI Provider Architecture

EMAG's AI layer is designed around a provider abstraction rather than a single hard-coded model.

The system can accommodate different provider types, including:

- cloud APIs
- local AI
- OpenAI-compatible endpoints
- browser-accessible providers
- CLI / daemon bridges

The active automatic fallback chain can be configured independently from manually selectable providers.

This allows the same environment to experiment with different AI backends without rebuilding the operating environment itself.

---

## Performance & Runtime Considerations

A project of this size inside a single document creates its own performance challenges.

EMAG includes runtime-oriented optimizations such as:

- debounced resize handling
- idle scheduling
- centralized update loops
- reduced-frequency background tasks
- serialized AI requests
- controlled agent execution cycles
- lazy initialization of heavier runtimes
- surgical widget updates

The goal is not to pretend that a 30,000-line single-document environment is inherently optimal.

The goal is to make the constraint usable.

---

## Security Note

EMAG OS contains experimental authentication, browser cryptography, external API integrations, filesystem abstractions, and networking features.

These components are intended for experimentation and demonstration.

EMAG OS is not a security product, hardened operating system, or audited cryptographic platform.

Do not use it as a substitute for a trusted operating system, password manager, secure communications platform, or professionally audited cryptographic software.

Never enter secrets or credentials into a public deployment unless you understand exactly where that information is stored and transmitted.

---

## Project Integrity

The "v8.64" release is associated with a cryptographically signed Git history.

The release commit and release tag were created using an SSH signing key and verified by GitHub.

```text
Commit
  ↓
SSH Signature
  ↓
GitHub Verified

Tag
  ↓
SSH Signature
  ↓
GitHub Verified
```

This provides cryptographic provenance for the corresponding Git objects.

It is intended as a technical integrity mechanism and does not, by itself, constitute legal proof of ownership.

---

## Running EMAG OS

### Live
Launch the deployed environment:
[https://mohamed-hesham-eleryan.github.io/EMAG-OS](https://mohamed-hesham-eleryan.github.io/EMAG-OS)

### Local
The core environment can be opened directly from:
`index.html`

Open it in a modern browser.

For features that depend on external APIs, browser security policies, remote runtimes, or network access, behavior may differ between a local file and a hosted origin.

---

## First Contact

Once inside the environment:

1. Create or enter a user account.
2. Let EMAG complete the boot sequence.
3. Explore the desktop.
4. Open the Dock.
5. Open the Terminal.
6. Type:
   `help`

Useful commands include:
`fastfetch`, `sysinfo`, `help`

The exact availability of certain features can depend on browser capabilities, permissions, network access, and the selected configuration.

---

## Project Philosophy

EMAG OS was not built because a browser needed another desktop simulator.

It was built because building one is an interesting engineering problem.

The project sits at the intersection of:

- Web Engineering
- Systems Thinking
- Artificial Intelligence
- Human–Computer Interaction
- Creative Coding
- Constraint-Driven Engineering

It deliberately blurs the boundary between:

- website
- application
- operating environment
- AI interface
- interactive artwork
- experiment

That ambiguity is part of the project.

---

## What EMAG OS Is Not

EMAG OS is not:

- a replacement for Linux, Windows, or macOS
- a conventional frontend application
- a production operating system
- a hardened security environment
- a general-purpose cloud platform
- a claim that browsers have become operating systems

It is an operating-system simulation and experimental environment built to explore what can happen when those boundaries are intentionally blurred.

---

## Status

**Experimental / actively evolving**

The project is intentionally ambitious and unconventional.

Some systems are mature enough to be useful.

Others exist primarily as experiments in interaction, AI behavior, browser capabilities, networking, or systems design.

The architecture is expected to continue changing.

---

## The Constraint

The most important specification of EMAG OS may also be the strangest one:

> **It is all here.**

One document.

One browser runtime.

Thousands of interconnected functions.

Tens of thousands of lines.

No conventional project tree required to experience the core environment.

That constraint is not a limitation hidden from the user.

It is the experiment.

---

<div align="center">

**EMAG OS**

A browser pretending to be an operating system.

An AI pretending to live inside it.

A single file pretending it should not be possible.

<br>
Built by Mohamed Hesham Eleryan

</div>
