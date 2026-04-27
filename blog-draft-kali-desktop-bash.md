# Set Up and Personalize Kali Linux with Bash (Without the Pain)

If you don’t want to manually reconfigure Kali every single time, this script (`customization/deskenv.sh`) is the move: **automate everything, keep it safe, stay flexible**.

## Who this guide is for

This post is for beginners who want to:
- bootstrap Kali faster,
- get a clean, functional desktop,
- and skip hours of manual click-ops.

The script follows a super clean flow:
1. Detect the system
2. Offer sane options
3. Apply changes safely
4. Keep rollback available

---

## 1) Hardening from line one: fail fast, fail loud

- `set -euo pipefail` and `IFS=$'\n\t'` (**lines 3–4**)

Why this matters:
- The script bails immediately on real errors.
- Undefined vars don’t create silent chaos.
- For beginners: fewer “why is this broken?” debugging marathons.

---

## 2) Global config instead of spaghetti hardcoding

- `VERBOSE`, `DRY_RUN`, `REPORT_FILE` (**lines 9–12**)

Why this matters:
- Behavior is centralized and predictable.
- `DRY_RUN` is perfect for safe testing.
- The report file gives you a paper trail.

---

## 3) Safer package installs on Kali

- `safe_apt_update` (**lines 155–163**)
- `package_available` (**lines 165–177**)
- `safe_install_packages` (**lines 179–216**)

Why this matters:
- Validate first, install second.
- Unavailable packages are skipped cleanly.
- Great for Kali-rolling where package availability can shift.

---

## 4) Backup + restore: your beginner safety net

- `backup_current_setup` (**lines 218–238**)
- `restore_backup` (**lines 240–263**)

Why this matters:
- Current desktop state is saved before changes.
- You can roll back if something goes sideways.
- Removes fear from customization experiments.

---

## 5) Automatic environment detection

- `detect_environment` (**lines 586–644**)

It detects things like:
- X11 vs. Wayland
- desktop environment
- window manager
- compositor
- distro

Why this matters:
- The script can choose smarter defaults.
- Beginners don’t need deep Linux internals to get started.

---

## 6) Persistent settings that survive reruns

- `load_settings` (**lines 662–686**)
- `save_settings` (**lines 688–704**)

Config file:
- `~/.config/kali-desktop/settings.conf`

Why this matters:
- Configure once, reuse forever.
- No repetitive setup grind on every run.

---

## 7) Beginner-friendly menus instead of CLI chaos

Key spots:
- `prompt_choice` (**lines 751–762**)
- main menu `show_main_menu` (**lines 1748–1775**)
- component menus for WM/terminal/launcher/themes/fonts (**lines 855–1329**)

Why this matters:
- Clear choices beat complex parameters.
- Fewer mistakes, faster learning curve.

---

## 8) Smart personalization with compatibility guardrails

- `resolve_effective_custom_values` (**lines 1333–1359**)
- `show_custom_compatibility_warnings` (**lines 1361–1388**)
- `apply_custom_config` (**lines 1390–1552**)

Why this matters:
- `auto` resolves to sensible defaults (e.g. Wayland → `sway`, X11 → `i3`).
- You get warnings for sketchy combos (like mixed X11/Wayland tools).
- Changes apply in a clean, controlled sequence.

---

## 9) Real-world desktop polish, not just package installs

Important functions:
- wallpaper logic: `apply_wallpaper` (**lines 345–390**)
- i3/Sway config: `config_i3_or_sway` (**lines 392–427**)
- desktop customization: `customize_desktop_environment` (**lines 429–474**)

Why this matters:
- It doesn’t just install stuff — it wires things up to be usable.
- You get a nicer desktop with less manual effort.

---

## 10) Ops-friendly extras for maintenance

- tools menu: `menu_tools` (**lines 1617–1662**)
- backup menu: `menu_backup` (**lines 1664–1694**)
- report view: `show_installation_report` (**lines 1777–1804**)
- entrypoint: `main` + CLI flags (**lines 1806–1854**)

Useful flags:
- `--dry-run` (**line 1820**)
- `--status` (**line 1829**)
- `--report` (**line 1832**)
- `--help` (**line 1835**)

Why this matters:
- The script stays maintainable after day one.
- Perfect for repeatable, auditable desktop setup.

---

## Final take

This script is a strong example of how beginners can use Bash to make Kali:
- **automated**,
- **safe to customize**,
- and **easy to recover**.

In short:
> Detect first, configure second, apply safely — that’s how Bash automation should feel.

---

## Mini CTA for your post

If you’re new to Kali, start with:
1. run `--status`,
2. create a backup,
3. then customize step by step through the menu.

That’s the fastest way to learn practical Bash automation without nuking your setup.
