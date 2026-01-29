# Trace

**Trace** is a macOS utility for managing and applying custom mouse cursors.

It focuses on a familiar, structured workflow — inspired by the classic Windows cursor settings dialog — adapted to modern macOS.

---

### What Trace is

Trace is designed around a simple idea:  
see your cursors, map them clearly, and apply them without guesswork.

Instead of hiding cursor files behind technical steps, Trace presents them in a way that makes sense visually.

---

### Features

- Apply custom mouse cursors on macOS  
- Support for Windows cursor formats (`.cur`, `.ani`)  
- Support for image-based cursors (`.png`, `.tiff`)  
- Support for the **Mousecape `.cape` format**  
- Interface inspired by the classic Windows cursor configuration dialog  
- Clear cursor preview and assignment  
- Drag & drop import  
- Temporary “Loaded Cursors” area for testing individual cursors  
- Optional helper for automatic apply at login *(work in progress)*

---

### Preview

Screenshots coming soon.

---

### Requirements

- macOS 11.0 or later  
- Intel or Apple Silicon Mac  

---

### Installation

1. Download the latest `.dmg` from **Releases**.
2. Move `Trace.app` to your `Applications` folder.
3. Launch Trace and import your cursor files.
4. Apply and switch cursor sets as needed.

---

### How it works

Trace applies cursor changes at runtime using low-level cursor patching techniques.

Internally, Trace uses the **Mousecloak backend**, which makes it compatible with the `.cape` cursor bundle format originally introduced by [Mousecape](https://github.com/alexzielenski/Mousecape).

Cursor data can be loaded from individual files or from `.cape` bundles and mapped to macOS cursor roles through Trace’s UI.

Applied cursors remain active until you log out, restart your Mac, or apply a different set.

If something looks wrong:
- Quit Trace  
- Log out and back in  
- Or restart your system  

---

### Cursor formats

Currently supported:

- **`.cur`** — Windows static cursors  
- **`.ani`** — Windows animated cursors  
- **`.png` / `.tiff`** — Image-based cursors  
  *(hotspot may require manual adjustment)*  
- **`.cape`** — Cursor themes using the [Mousecape](https://github.com/alexzielenski/Mousecape) format  
- **Windows cursor packs with `install.inf`** — can be imported and converted into themes

---

### Windows cursor packs (`install.inf`)

Some Windows cursor packs include an `install.inf` file that describes how the cursors are mapped.

Trace can attempt to import these packs and convert them into a compatible theme:

- Create a theme via the menu bar:  
  **Cape → Create Cape from install.INF**
- Or open an `install.inf` file directly and choose **Trace** as the application.

Trace will read and interpret the cursor mappings defined in the INF file and generate a theme that can be applied like any other cursor set.

**Note:**  
Not all `install.inf` files follow the same structure.  
While Trace aims to support common layouts, successful conversion **cannot be guaranteed** for every cursor pack.

---

### Themes & `.cape` files

In Trace, [Mousecape](https://github.com/alexzielenski/Mousecape) `.cape` files are treated as **themes**.

When you import a `.cape` file, it will appear in the **Themes** section of Trace rather than as individual cursor files.

This allows Trace to keep related cursors grouped together and mapped consistently across macOS cursor roles.

---

### Background & Credits

Trace builds upon concepts originally introduced by **[Mousecape](https://github.com/alexzielenski/Mousecape)**.

Mousecape was created by **Alex Zielenski** and established the `.cape` cursor bundle format.  
Trace reuses this format via the Mousecloak backend while providing a different UI approach and an updated workflow.

---

### Expect bugs

Trace is in **early alpha**.

You should expect:
- Incomplete or imperfect cursor mappings  
- Visual glitches in previews  
- Occasional failures when applying cursors  
- Behavior differences across macOS versions  

If something breaks, logging out or restarting usually restores the default system cursors.

---

<details>
<summary><strong>FAQ</strong></summary>

<br>

**Where do Mousecape `.cape` files appear in Trace?**  
Mousecape `.cape` files are treated as **themes** in Trace.  
After importing, they will appear in the **Themes** section rather than as individual cursor files.

---

**I imported a Windows cursor pack, but some cursors are missing or mapped incorrectly. Why?**  
Windows cursor packs vary widely in structure.  
While Trace attempts to interpret common layouts (including `install.inf` files), not all mappings can be transferred reliably to macOS.

---

**Why does my cursor look different compared to Windows?**  
macOS and Windows use different cursor roles and scaling behavior.  
Some Windows cursors do not have a perfect macOS equivalent and may be adapted automatically.

---

**I imported PNG or TIFF cursors and the click point feels off.**  
Image-based cursors may require **manual hotspot adjustment**.  
Unlike `.cur` files, PNG/TIFF images do not always contain hotspot metadata.

---

**Why did my cursors reset after logout or restart?**  
Trace applies cursor changes at runtime.  
After logging out or restarting, you need to reapply your cursor set  
(automatic apply at login is work in progress).

---

**Is it safe to use Trace?**  
Trace modifies cursor behavior at runtime only.  
If something goes wrong, quitting Trace, logging out, or restarting will restore the default system cursors.

---

**Why does Trace require macOS 11 or later?**  
Trace is built primarily using SwiftUI and modern macOS APIs.  
macOS 11 provides a stable foundation for these technologies.

If you need support for older macOS versions, Mousecape remains a good alternative.

</details>

---

### Feedback

If you report an issue, please include:
- macOS version  
- Cursor format used  
- What you expected vs. what happened  
