# QuickTodo

Floating native macOS todo app with Supabase real-time sync. Built with pywebview + Python.

## Features
- Floating frameless window, always available
- Multiple lists (personal + shared) with color coding
- Subtasks with auto-complete cascading
- Real-time sync via Supabase (shared lists sync between users)
- Drag-to-reorder, drag-to-move across lists
- Check animation with delayed sort (doesn't vanish instantly)

## Setup

```bash
# First run — creates venv and installs pywebview
./launch-quicktodo.sh
```

## Build the .app bundle

```bash
python3 -m venv .quicktodo-venv
.quicktodo-venv/bin/pip install pywebview py2app
.quicktodo-venv/bin/python3 setup.py py2app
# Install to Applications
rsync -a --delete dist/QuickTodo.app/ /Applications/QuickTodo.app/
```

## BTT Setup

In BetterTouchTool, use **"Show / Hide Specific Application"** → select `/Applications/QuickTodo.app`.  
Shortcut: `Ctrl+Option+T`

## Why py2app?

Shell-script .app wrappers are blocked by macOS Gatekeeper on modern macOS. py2app
bundles Python inside the .app so it's a real Mach-O binary that opens reliably.
