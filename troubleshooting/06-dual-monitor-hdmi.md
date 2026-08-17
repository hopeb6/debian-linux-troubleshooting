# 06 — HDMI Dual-Monitor Configuration

## Environment

- OS: Debian GNU/Linux 13 (Trixie)
- Desktop: KDE Plasma 6
- Laptop display: Built-in 1920×1080
- External display: Toshiba, connected through HDMI

## Problem

The external Toshiba display was connected through HDMI, but the display behaviour was initially confusing because both screens could show the same desktop view.

## Investigation

KDE Plasma's **System Settings → Display & Monitor → Display Configuration** was used.

The system detected two displays:

- Built-in Screen
- Toshiba external display

The display configuration showed that the external display could be enabled independently and that `Replica of` could be set to `None`.

## Solution

The screens were configured as an **extended desktop** instead of a mirrored/replicated desktop.

The display rectangles were then arranged to match the physical position of the monitors.

For example, if the Toshiba display is physically to the left of the laptop:

```text
[Toshiba] [Built-in Screen]
```

If it is physically to the right:

```text
[Built-in Screen] [Toshiba]
```

Both screens remained enabled and the display was left as an independent screen rather than a replica.

## Result

The laptop and Toshiba monitor can now be used as separate workspaces.

For example:

- Laptop → terminal, browser, documentation or MS Project
- Toshiba → presentation, video, document or another application

## Lesson Learned

In an extended desktop, the position of the display boxes in KDE controls the virtual position of each physical screen.

This determines where the mouse pointer moves between displays.

`Replica of: None` means the screen is not mirroring another display.

## Skills Demonstrated

- HDMI display configuration
- KDE Plasma Display Configuration
- Multi-monitor setup
- Extended desktop
- Display positioning
