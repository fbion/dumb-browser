# Dumb Browser
A custom chromium build inspired by ungoogled-chromium and Brave.

Current version: `85.0.4183.83`.

**Some patches are experimental and build may fail.**

# Features

> All patches are in `patches` folder.

Following components are removed/disabled:
1. [Safe Browsing](https://safebrowsing.google.com)
2. Metrics (Histogram)
3. Crash Reporter & Crashpad
4. WebRTC Log Uploader
5. Network Time Tracker
6. [RLZ](https://blog.chromium.org/2010/06/in-open-for-rlz.html)
7. [Rappor](https://github.com/google/rappor)
8. (macOS only) Download Quarantine
10. (Windows only) Chrome Cleaner
11. WebGL renderer info
12. Field trails fetching
13. Promotions in New Tab Page
14. [HTML \<ping\> attribute](https://www.w3schools.com/tags/att_a_ping.asp)
15. Spell Checker

Other changes / optimizations:
1. [UI] Change web controls' color to gray (edge style)
2. [UI] Reduce location bar corner radius
3. [UI] Disable Chromium's missing key warning
4. [UI] Restore mute button on tab
5. [Privacy] Automatically remove track query parameters from URL (*referrer, utm_\*, spm, and more*)
6. [UI] Remove "Your Internet connection is being controlled" bubble

# Installation

## 1. [Recommended] Build from Sources

It's impossible to build Dumb Browser via GitHub Actions due to GitHub's free account resource limitations.
Please build on your own or wait for official binaries.

### Build on macOS
Tested on macOS 10.15.6.

*Build script is coming soon.*

1. Install `Xcode 11` or higher version

2. Clone this project

3. Follow [official build instruction](https://chromium.googlesource.com/chromium/src/+/master/docs/mac_build_instructions.md) until `Setting up the build`

4. Create build dir in chromium src folder: `mkdir -p <PATH_TO_CHROMIUM_SRC>/out/Default`

5. Copy `gn_args/args_release.gn` to `mkdir -p <PATH_TO_CHROMIUM_SRC>/out/Default` and rename it to `args.gn`

5. Apply patches: `dumb-browser/scripts/patches.py apply <PATH_TO_DUMB_BROWSER_PATCHES> <PATH_TO_CHROMIUM_SRC>`

6. Build Chromium: `autoninja -C out/Default chrome`

7. Output binary will be found in `out/Default`

## 2. Official Binaries
*Unavailable. Binaries will be provided in the future.*

> Note: Provided binaries do not contain any Google API keys thus you can't use Chrome Sync by default.
> To solve this, follow [Chromium's Official How-Tos](https://www.chromium.org/developers/how-tos/api-keys)
> and add your own API keys to environment variables.

# Known Issues

1. If you use existing profiles from `ungoogled-chromium`, you may encounter password sync failure. To solve this, create a new profile in dumb browser.

2. [1Password extension (desktop app required)](https://chrome.google.com/webstore/detail/1password-extension-deskt/aomjjhallfgjeglblehebfpbcfeobpgk) is unavailable since it forces allowlist-based browser signature check. Instead you can use `1Password X` which requires a valid 1Password subscription.

# Credits

[ungoogled-chromium](https://github.com/Eloston/ungoogled-chromium)

[Brave](https://github.com/brave/brave-browser)

[CleanURLs](https://github.com/GlowPuff/CleanURLs)
