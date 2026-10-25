# Native Showcase: Privacy-First macOS Meeting HUD 🚀

An experimental, native macOS menu bar utility that floats a frosted-glass HUD overlay above everything else on screen—including full-screen apps and IDEs. Built specifically to eliminate cognitive fatigue for freelance developers and independent contractors, it automates real-time meeting transcription, structured note-taking, and technical action-item tracking completely on-device.

This repository serves as the public roadmap, issue tracker, and feature showcase for the initial first-cut version of the architecture. The core code relies entirely on native Apple frameworks to ensure 100% data isolation and compliance with strict client NDAs.

---

## 💡 The Core Problem & Philosophy

As engineers and consultants, technical alignment calls are exhausting. Trying to balance active architectural problem-solving while manually capturing decisions, tasks, and follow-up metrics destroys your flow state. 

Traditional meeting recorders solve this but introduce heavy liabilities: they require cloud bots that join calls, record video feeds, and store highly sensitive enterprise data on external servers. 

**This project explores a different path:** Using native macOS system boundaries to capture audio streams directly at the hardware layer, processing summaries locally via Apple Intelligence, and rendering an interface that completely avoids context switching.

---

## 🛠️ Key Architectural Highlights

### 1. Passive HUD Overlay (`AppKit` & `SwiftUI`)
* **Zero Focus Theft:** Built as an `NSPanel` accessory layer, the HUD stays pinned in your line of sight but never steals keyboard focus. You can keep typing code in Xcode or VS Code completely uninterrupted.
* **Click-Through Mode:** By default, mouse interactions pass directly through the transparent panel to the canvas elements underneath. A global hotkey instantly toggles it into an interactive frame for manual scrolling, text selection, or resizing.
* **Space & Display Agility:** Automatically floats over native full-screen applications, follows your workspace view transitions across virtual Spaces, and remembers its position coordinates per display.

### 2. Dual-Audio Pipeline & Echo Isolation
* **Stream Splitting:** Captures and separates system microphone inputs (`Me`) and internal digital speaker audio (`Client`) concurrently.
* **Hardware-Level AEC:** Leverages Apple's Voice Processing I/O hardware stack to enforce Acoustic Echo Cancellation, ensuring audio coming from your Mac speakers isn't re-recorded by the mic as duplicate data.

### 3. Stateless Runtime & Dynamic Summarization
* **Absolute Data Privacy:** Built on a completely stateless memory allocation architecture. Audio transcript streams live strictly within temporary RAM buffers and are completely purged the moment the overlay panel is closed. Data is only written to the physical drive if you explicitly click the export action button.
* **Context-Safe Chunking:** To handle long sessions within the constrained memory boundaries of local foundational models, data is processed in sliding 5-minute rolling blocks and programmatically appended into a persistent, structured framework layout.

---

## 📑 Sample Real-World Output

Below is an actual Markdown file compiled natively by the utility during an initial project baseline test (capturing a technical backend system design discussion):

```markdown
# Meeting notes

- **Date:** 25 October 2026 at 6:27 PM
- **Duration:** 0:00:59

## Summary
The team discussed how clients and servers communicate in a scaling chat system architecture, evaluating instant delivery mechanics. Long polling was analyzed as a baseline protocol where connections are held open by the server until updates arrive, reducing empty response cycles.

## Action items
- [ ] `[0:06]` Implement native Swift workflows across everything (Owner: Me)
- [ ] `[0:06]` Design the client API POST request sequence with server-side push mechanics (Owner: Me)
- [ ] `[0:06]` Benchmark long polling connection thresholds under active load (Owner: Me)

## Key points
- Investigating instant message delivery optimization patterns.
- Polling remains a fallback option, though standard loops waste processing resources.
- Long polling acts as a solid intermediary by maintaining open sockets until data packets arrive.
```

---

## 📋 The Technical Roadmap

As this experiment improvises, development is focused on the following upcoming native milestones:
- [ ] **Technical Vocabulary Sanitizer:** Injecting a preprocessing layer to automatically correct phonetic engine errors on specific developer acronyms (e.g., mapping misheard sounds directly to `HTTP`, `JSI`, or `TurboModules`).
- [ ] **Vision Framework Regional OCR:** A localized screen-snippet module (`VNRecognizeTextRequest`) to extract code strings or technical text from selected screen bounds directly into the AI assistant tab.
- [ ] **Edge-Hover Scrolling Loops:** Implementing tracking handlers to allow users to read long text feeds in click-through mode without changing focus states.

---

## 🚀 Join the Journey

The core engine is currently running in a private repository sandbox while the local memory-chunking pipelines are being fully optimized. 

* **Track Progress:** Drop a ⭐ on this repository to follow feature updates, performance metrics, and version tags!
* **Contribute Ideas:** Have a feature suggestion for freelance workflow optimizations? Open an issue on our tracker—we'd love to hear how you manage context switching during your engineering week.
