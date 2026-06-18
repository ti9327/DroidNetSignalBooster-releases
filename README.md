# DroidNet Signal Booster

Turn a Raspberry Pi into a wireless programming hub for your droid — flash Arduino and
ESP32 boards, monitor serial output, and control servos, all from a browser.

---

## Start Here — Which are you?

### I am setting up a brand-new device (fresh SD card)

**You need a disk image.** Jump to [Download the Image](#download-the-image-fresh-install)
below.

> **Do NOT download an "update package" file for a fresh install.** Update packages are
> only for devices that are already running DroidNet. They are not disk images and cannot
> be flashed to a blank SD card.

---

### I already have a DroidNet device and want to update it

**You do not need to download anything — the device updates itself over the internet.**
Your device must be in **Client Mode, connected to Wi-Fi with internet access** (the update
downloads from GitHub):

1. Open the web interface at `http://droidnet.local` (or the device's IP on your network).
2. Go to **Config → System Update → Check for Updates**.
3. Click **Update Now** when the update is shown. The device downloads, installs, and reboots — no SD card re-flash.

**No internet on the device (for example, it's in AP mode)?** Download the latest update
package (`droidnet-update-*.zip`) from the
[latest release](https://github.com/travisccook/DroidNetSignalBooster-releases/releases/latest),
then open the web interface at `http://192.168.4.1` and go to
**Config → System Update → Manual Update** to upload it. (Don't flash an update package to an
SD card — it is not a disk image.)

---

## Download the Image (fresh install)

> **Images live only on the 2.0 release.**
> Later releases (2.0.1, 2.0.2, 2.1, …) are update packages — your device applies those
> automatically from inside the web interface. Do not hunt for `.img.zip` files on those
> releases; they are not there.

**Always download your image from here:**
[https://github.com/travisccook/DroidNetSignalBooster-releases/releases/tag/v2.0.60](https://github.com/travisccook/DroidNetSignalBooster-releases/releases/tag/v2.0.60)

### Pick your Pi

| Your Raspberry Pi | Download this file |
|-------------------|--------------------|
| **Pi Zero 2 W** (recommended) | `droidnet-lite-zero2-w-v2.0.60.img.zip` |
| **Pi 3 / 3B / 3B+** | `droidnet-lite-pi3-v2.0.60.img.zip` |
| **Pi 4** | `droidnet-lite-pi4-v2.0.60.img.zip` |
| Pi Zero W | **Not supported** — see [Pi Zero W note](#pi-zero-w) |

> **Why does "Latest" on GitHub sometimes show no image?**
> GitHub's "Latest release" badge auto-points at the most recently published release.
> Minor releases (2.0.61, 2.1, …) contain only update packages. If the release you land
> on has no `.img.zip` file, use the direct link above — it always points at the image
> carrier for 2.0.

### Flash and first boot

See the **[Installation](https://github.com/travisccook/DroidNetSignalBooster-releases/wiki/Installation)**
wiki page for step-by-step instructions using Raspberry Pi Imager, balenaEtcher, or the
command line. The short version:

1. Open [Raspberry Pi Imager](https://www.raspberrypi.com/software/).
2. Choose OS → **Use custom** → select the `.img.zip` file (no manual unzip needed).
3. Choose Storage → select your SD card.
4. Click **Write**.
5. Insert the card into your Pi and power it on.
6. **Wait 2–3 minutes** — first boot is slow while the device expands its filesystem and
   configures itself.

---

## Connect to Your Device

Once the first boot is complete:

1. On your phone or computer, open Wi-Fi settings and join the network named
   **DroidNet-XXXX** (the XXXX is unique to your device, based on its MAC address —
   for example, `DroidNet-A1B2`).
2. Password: **`droidnet123`**
3. Open **`http://192.168.4.1`** in a browser.

You should see the DroidNet Signal Booster dashboard.

> **Security reminder:** The default password (`droidnet123`) is the same on every new
> device. Change it in **Config → Access Point Settings** before using your device in a
> shared space.

For a complete walkthrough of first-time setup and feature configuration, see
**[Getting Started](https://github.com/travisccook/DroidNetSignalBooster-releases/wiki/Getting-Started)**.

---

## Updating an Existing Device

**This includes v1.x → 2.0 upgrades.** If you are running any v1.x release, you can
update to DroidNet 2.0 in place — no SD card re-flash required. The device's built-in
update checker looks across major version channels and will offer the 2.0 update
through the same web interface flow as any other update.

### Normal update (recommended)

The easiest way to update is from inside the web interface:

1. Open the web interface.
2. Go to **Config → System Update**.
3. Click **Check for Updates**.
4. Click **Update Now** when shown.

The device downloads and applies the update, then reboots. No SD card required.
This works whether you are updating within 1.x, within 2.0, or upgrading from 1.x to 2.0.

### Offline / manual update

If your device has no internet access:

1. Go to the [Releases page](https://github.com/travisccook/DroidNetSignalBooster-releases/releases)
   and download the latest `droidnet-update-2.x.x.zip` update package.
2. In the web interface, go to **Config → System Update**.
3. Click **Manual Update** and upload the `.zip` file.

> **Do NOT flash an update package to an SD card.** It is not a disk image. Flashing it
> will not work and will leave your SD card unusable.

---

## Version Scheme

| Version type | What it means | How you get it |
|---|---|---|
| **Major** (2.0, 3.0, …) | New SD-card image — breaking changes, full reflash required | Download the image from the initial release of that major line and flash your SD card |
| **Minor / patch** (2.1, 2.0.61, …) | In-place update package — cumulative, backward-compatible | Applied automatically by the device, or via manual upload in the web UI |

**The rule:** images live only on the first release of each major version line.
The `v2.0.60` release on GitHub is the permanent home of all 2.0 disk images. Later
releases (2.0.61, 2.1, 2.2, …) carry only update packages — no images.

---

## Supported Hardware

| Raspberry Pi | Status |
|---|---|
| Pi Zero 2 W | Recommended — compact, good performance |
| Pi 3 / 3B / 3B+ | Recommended — full performance |
| Pi 4 | Recommended — maximum performance |
| Pi Zero W | Not supported (see below) |

### Pi Zero W

The original Pi Zero W is **not supported** — DroidNet does not run on it, and there is no
supported DroidNet build for it. Its single core and limited RAM can't run DroidNet, so
support has been dropped entirely.

Use a **Pi Zero 2 W** instead — it is the same physical size, costs about the same, and is
fully supported.

---

## Documentation

Full documentation lives in the [Wiki](https://github.com/travisccook/DroidNetSignalBooster-releases/wiki):

- [Getting Started](https://github.com/travisccook/DroidNetSignalBooster-releases/wiki/Getting-Started) — Hardware, image download, first boot, and feature setup
- [Installation](https://github.com/travisccook/DroidNetSignalBooster-releases/wiki/Installation) — Detailed flashing instructions (Imager, Etcher, command line)
- [Updating](https://github.com/travisccook/DroidNetSignalBooster-releases/wiki/Updating) — Keeping your device current
- [Network Modes](https://github.com/travisccook/DroidNetSignalBooster-releases/wiki/Network-Modes) — AP mode vs client mode
- [Troubleshooting](https://github.com/travisccook/DroidNetSignalBooster-releases/wiki/Troubleshooting) — Common problems and solutions

---

## Community

Questions? Want to show off your build?

**[Join the Bluegrass Droidworks Discord](https://discord.gg/SV9N6MX7xR)**
