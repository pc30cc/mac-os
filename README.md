# Webyar for Mac — updates

The public feed the Webyar for Mac app updates from.

| Path | What |
|---|---|
| `appcast.xml` | Sparkle's feed. Installed apps read it (and Super Admin → macOS app can point them elsewhere). |
| `releases/<version>/Webyar-<version>.dmg` | The installer to download by hand. |
| `releases/<version>/Webyar-<version>.zip` | The update Sparkle downloads, signed with EdDSA. |
| `releases/<version>/item.xml` | That version's appcast entry; `appcast.xml` is rebuilt from all of them, newest first. |

Latest feed: https://raw.githubusercontent.com/pc30cc/mac-os/main/appcast.xml

## Publishing

Releases are published from the source repository (`pc30cc/kindred-core-build`, `macos/`):

```bash
macos/scripts/release-local.sh 1.0.1 2 stable "What changed"
```

The build number (second argument) must grow with every release. Updates are
signed with the EdDSA key kept in the publishing Mac's Keychain; the matching
public key is built into the app, so an update signed with any other key is
refused.

## Installing by hand

Download the latest DMG from `releases/`, drag **Webyar** to **Applications**.
These builds are signed ad hoc, so the first time macOS asks: right-click the
app → **Open** → **Open**. Updates after that install themselves.
