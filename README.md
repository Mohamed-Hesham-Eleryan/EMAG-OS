<div align="center">

# EMAG OS

### An AI-powered operating system simulation running inside a browser.

`Single HTML File` · `~30,000 Lines` · `~1.88 MB` · `Browser-Native`

<br>

[![Live Demo](https://img.shields.io/badge/Live_Demo-Launch_EMAG_OS-ff0000?style=for-the-badge)](https://mohamed-hesham-eleryan.github.io/EMAG-OS)

</div>

---

## What is EMAG OS?

EMAG OS is an experimental browser-native operating environment built around a simple question:

> **How far can a browser be pushed when the goal is not to build a website, but to build an environment?**

It looks like an operating system, behaves like an operating system, contains applications, a filesystem, a terminal, an AI agent, persistent user state, system configuration, tools, visual effects, and an internal world — yet the entire core environment lives inside a single HTML document.

There is no traditional backend, no build pipeline, and no framework-driven application architecture.

The system is deliberately constrained.

And that constraint is part of the engineering challenge.

---

## The Experiment

EMAG OS is approximately **30,000 lines of HTML, CSS, and JavaScript** contained in a single file of roughly **1.88 MB**.

The objective was not simply to make a large HTML file.

The objective was to make that file behave like a coherent software environment.

Inside the same document are:

- a desktop environment
- window management
- an application system
- persistent storage
- a virtual filesystem
- authentication and sessions
- a multi-mode terminal
- an embedded Python runtime interface
- a code editor
- an AI chat interface
- an agent/tool execution layer
- OSINT-oriented tooling
- system configuration
- media handling
- custom wallpapers and themes
- cryptographic notebook functionality
- real-time visual effects
- an interactive 3D system identity
- peer-to-peer communication experiments
- EMAG's autonomous event and interaction systems

The architecture is intentionally extreme:

**one document → one environment → many systems.**

---

## Architecture

EMAG OS is not a collection of disconnected UI components.

It is organized as a collection of interacting subsystems sharing a common runtime and state layer.

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
It can reason about the environment and interact with it through tools.

The filesystem is not merely a mock UI.
Applications and terminal commands operate against the same persistent virtual filesystem.

The desktop is not just visual decoration.
The environment has state, identity, configuration, and behavior.

---

## EMAG — The Agent Inside the Environment

At the center of the system is EMAG, the AI identity that inhabits the environment.

The AI layer supports two fundamentally different execution paths.

### Fast Path
Normal conversational requests can be sent directly to the configured AI provider.

### Agent Path
Requests that require actions, searching, inspection, navigation, calculations, or other tools can enter a multi-step agent loop.

The agent has access to a catalog of tools covering areas such as:

- web search
- OSINT operations
- filesystem access
- system information
- calculations
- Python execution
- GitHub lookup
- weather/data utilities
- crypto/forex data
- network-oriented utilities
- external messaging integrations
- application control

The agent can therefore move beyond:

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

The agent system also contains execution logging, request management, tool handling, and a controlled multi-step loop.

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

This gives applications and the terminal a shared storage model.

The environment can therefore maintain state between sessions instead of behaving like a stateless webpage.

---

## The Terminal

EMAG includes its own terminal environment.

It is not limited to a fake command prompt.

The terminal exposes multiple execution modes:

- **SHELL**
- **AI**
- **JS**
- **PYTHON**

The shell includes filesystem and system-style commands such as:

`ls`, `cd`, `pwd`, `cat`, `mkdir`, `rm`, `cp`, `mv`, `find`, `touch`, `write`, `whoami`, `uname`, `ps`, `history`, `uptime`, `sysinfo`

It also exposes utility commands for things such as hashing, Base64, UUID generation, calculations, JSON formatting, and fetching content.

The terminal can also switch into:

- **AI mode**
- **JavaScript mode**
- **Python mode**

Python execution is backed by Pyodide, allowing Python code to execute within the browser environment.

---

## Applications & Environment

EMAG OS contains a collection of applications designed to make the environment feel like a small software platform rather than a landing page.

Among its core systems are:

### AI Interface
The primary interface for communicating with EMAG and invoking its agent capabilities.

### Terminal
A multi-mode command environment connected to the virtual filesystem and system APIs.

### File Explorer
A graphical interface over the same persistent virtual filesystem used by the terminal.

### Code Environment
A browser-based development environment with editor capabilities.

### Settings
System-level customization including:

- system identity
- AI identity
- user identity
- custom system prompts
- themes
- wallpaper behavior
- visual settings
- AI provider configuration
- voice behavior
- environment behavior

### Media Environment
Browser-native handling for images, audio, video, and user-provided media.

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
- an interactive system "Eye"
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

The system also maintains contextual information that can be passed between certain operations.

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
- notebook data
- application state
- AI configuration

The virtual filesystem is backed by IndexedDB through a structured storage layer.

This allows the environment to behave much more like a persistent application than a conventional static webpage.

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
- Voice
- Visual Behavior
- AI Provider

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

This is one of the more experimental parts of the project.

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

- Cloud APIs
- Local AI
- OpenAI-compatible endpoints
- Browser-accessible providers
- CLI/daemon bridges

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
- request serialization for AI calls
- controlled agent execution cycles
- lazy initialization of heavier runtimes

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

## Running EMAG OS

### Live
Launch the deployed environment:
[https://mohamed-hesham-eleryan.github.io/EMAG-OS](https://mohamed-hesham-eleryan.github.io/EMAG-OS)

### Local
The core environment can be opened directly from the HTML file.
`index.html`

Open it in a modern browser.

For features that depend on external APIs, browser security policies, remote runtimes, or network access, behavior may differ between a local file and a hosted origin.

---

## First Contact

Once inside the environment:

1. Create or enter a user account
2. Let EMAG complete the boot sequence
3. Explore the desktop
4. Open the Terminal
5. Type: `help`

Useful keyboard shortcuts include:

| Shortcut | Action |
| :--- | :--- |
| `Ctrl + 1` | EMAG Chat |
| `Ctrl + 2` | Terminal |
| `Ctrl + 3` | Files |
| `Ctrl + 5` | Code Editor |
| `Ctrl + 6` | Settings |

From the terminal, you can explore the environment directly.

Try:
`neofetch`

or:
`sysinfo`

or:
`help`

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

> It is all here.

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
