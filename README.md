# Crunchyroll webapp for Ubuntu Touch

A thin webapp that launches the system `webapp-container` (Morph, Qt6 / Chromium 134)
on https://www.crunchyroll.com/. Requires Ubuntu Touch 24.04-2.x and Widevine installed
via Morph Browser > Settings > Plugins > Widevine.

## Files
- `manifest.json`          click manifest (framework `ubuntu-touch-24.04-2.x`)
- `crunchyroll.apparmor`   confinement: ubuntu-webapp template, policy 2404.2, plus
                           read access to Morph's WidevineCdm folder (without it the
                           CDM fails to load with "Permission denied")
- `crunchyroll.desktop`    launcher; tweak the webapp-container flags here
- `icon.png`               app icon (Crunchyroll logo, not an original asset)

## Build
### On device
```
git clone https://github.com/Batcastle/Crunchyroll-UT
cd Crunchyroll-UT
click build .
```

### On desktop
```
git clone https://github.com/Batcastle/Crunchyroll-UT
cd Crunchyroll-UT
sudo clickable build
```

## Install
### On device
```
click install ./crunchyroll-ut.*.click
```

### From desktop
Make sure your Ubuntu Touch device is plugged into your computer first, and developer mode is enabled, then run:
```
clickable install
```

## Notes
- Bump `version` in manifest.json whenever the .apparmor file changes, or the
  profile will not be regenerated.
- Remove `--fullscreen` to bring back the status bar, `--enable-back-forward` to
  hide the bottom toolbar, or `--user-agent-string=...` to use the default UA.
- This app was originally created using Claude AI, and is now human-maintained.
