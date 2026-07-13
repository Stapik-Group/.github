# Stapik (a.k.a スターピーク)

![License](https://img.shields.io/badge/license-GPL--3.0-blue.svg)

Small, focused desktop apps for Linux, for daily use, and shared here in case they're useful to anyone else.

Everything in this org shares the same DNA: C++20, GTK4/gtkmm, a retro interface that doesn't take itself too seriously, and a habit of doing one thing well instead of trying to be a platform. No accounts, no telemetry, no subscriptions — your data lives on your machine, with an optional self-hosted sync layer if you want it across devices (a sample self-hosted sync server is on the way). 

Built with AI assistance, reviewed and refined by hand. Code review and feedback are always welcome — if you spot something worth improving, please, open an issue.

Apps tested on ZorinOS. 

## Apps

| | |
|---|---|
| **[stapik-calendar](https://github.com/Stapik-Group/stapik-calendar)** | Monthly calendar with quick entries — right-click a day, paste a link, get an entry with the page title fetched automatically. |
| **[stapik-calendar-mobile](https://github.com/Stapik-Group/stapik-calendar-mobile)** | Companion android app for Stapik alendar — basic functionality, read-only (for now). |
| **[stapik-planner](https://github.com/Stapik-Group/stapik-planner)** | Weekly planner with a reusable activity catalog and per-day workload tracking, so you notice you're overbooked before Wednesday does. |
| **[stapik-media](https://github.com/Stapik-Group/stapik-media)** | A log for everything you've watched, read, listened to or played — organized by category, filterable by when you got to it. |

All three are standalone — install whichever ones you actually need.

## Shared foundation

[**stapik-common**](https://github.com/Stapik-Group/stapik-common) is the library underneath all of them: localization, cloud sync, local storage, and the shared dialogs/widgets that make the apps look and behave consistently. It's pulled in automatically via CMake, nothing to install by hand.

## Design choices worth knowing about

- **Local-first.** Every app writes to `~/.local/share/<appname>/` and works fully offline. Cloud sync is opt-in, talks to a self-hosted API you control, and resolves conflicts by keeping whichever copy was saved more recently — the whole document at once, no field-by-field merging. Simple, predictable, and good enough for one person using a couple of machines.
- **Retro on purpose.** The Windows-98-adjacent look isn't nostalgia for its own sake — it's fast to render, easy on the eyes, and doesn't ask you to relearn where anything is every time GTK changes its default theme.
- **No moving parts you didn't ask for.** No background sync daemons, no update pings, no accounts. You run the binary, it does its job, it gets out of your way.

## Getting started

Each app ships as a `.deb` on its own Releases page, or builds from source with plain CMake:

```bash
git clone https://github.com/Stapik-Group/<app-name>
cd <app-name>
cmake -B cmake-build-release -DCMAKE_BUILD_TYPE=Release
cmake --build cmake-build-release
```

See each repo's README for dependencies, packaging, and cloud sync setup.

## What's next

Windows and Flatpak support are on the roadmap for the whole suite, along with a read-only mobile companion app. Check each repo's own TODO for what's coming to that particular app.
