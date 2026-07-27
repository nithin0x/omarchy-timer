# omarchy-timer
A minimal timer TUI utility for [Omarchy](https://omarchy.org), which integrates with waybar and supports pomodoro-style timers with pause/resume and cycle limits.

> [!IMPORTANT]
> This utility is Omarchy specific and depends only on packages, which are already pre-installed on Omarchy, meaning no additional dependencies.

## Demo
https://github.com/user-attachments/assets/fbf8f58f-75bb-450d-9cd3-4e1d9c1f1062

## Features
- One-shot timers and pomodoro work/break cycles, optionally stopping after N rounds
- Live countdown in waybar: left-click to pause/resume, right-click to cancel
- Pause, resume and status from the CLI or keybindings
- Sticky completion notifications with sound (via mako / `omarchy-notification-send`)
- Interactive gum TUI in a floating window, matching your active Omarchy theme, with common pomodoro presets (25/5 classic, 45/10, 50/10 deep work, 52/17 rule, 90/20 ultradian) or fully custom durations
- Installs to `~/.local/bin` — no sudo, no packages, survives system updates

## Installation
```bash
git clone https://github.com/nithin0x/omarchy-timer.git && chmod +x ./omarchy-timer/omarchy-timer && ./omarchy-timer/omarchy-timer install
```
The installer copies the script to `~/.local/bin/omarchy-timer` and offers to add the waybar module, keybindings and windowrule to your configs automatically (timestamped backups are made first). If your configs are heavily customized, it prints the snippets for you to add manually instead.

Default keybindings added by the installer:

| Keys | Action |
|---|---|
| `SUPER + ALT + T` | Open the timer TUI (floating window) |
| `SUPER + ALT + P` | Start a 25m/5m pomodoro |

## Usage
```bash
omarchy-timer 10m            # 10 minute timer
omarchy-timer 25m/5m         # pomodoro: 25m work / 5m break, repeats until cancelled
omarchy-timer 25m/5m/4       # pomodoro that stops after 4 work phases
omarchy-timer                # interactive TUI: pick a pomodoro preset or enter a custom timer
omarchy-timer status         # show remaining time
omarchy-timer pause          # pause the active timer (also: resume, toggle-pause)
omarchy-timer cancel         # cancel the active timer
omarchy-timer help           # full usage
```
Durations accept `30s`, `5m`, `1h` or combinations like `1h30m`; bare numbers are seconds. Only one timer runs at a time.

In waybar the module shows an icon and the remaining time while a timer is active (dimmed while paused), and hides itself when idle. Left-click pauses/resumes, right-click cancels.

## Uninstallation
Run `omarchy-timer uninstall` and follow the steps. No sudo needed (it is only offered if a legacy `/usr/bin` install from an older version is found).
