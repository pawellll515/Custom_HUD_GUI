# Custom HUD GUI (Fabric)

One repository, two separately built mod JARs:
- Minecraft 1.21.4: `mc1.21.4/build/libs/`
- Minecraft 1.21.11: `mc1.21.11/build/libs/`

## Build on GitHub (no local Java/Gradle setup required)
1. Create a new GitHub repository and upload the **contents** of this ZIP.
2. Open **Actions** and enable workflows if GitHub asks.
3. Select **Build Custom HUD GUI** → **Run workflow**.
4. When finished, open the workflow run and download the `custom-hud-gui-jars` artifact. It contains one JAR for each Minecraft version.

Each JAR is version-specific; install only the matching one in that game's `mods` folder. Fabric Loader and Fabric API are required.

## Default controls
- `Right Shift`: open settings.
- Each HUD row has an ON/OFF toggle and a settings button.
- Settings let you edit the text template, color code, scale and screen anchor.
- Settings are saved to `.minecraft/config/custom-hud-gui.json`.

Supported template tokens include `{x}`, `{y}`, `{z}`, `{nx}`, `{nz}`, `{facing}`, `{ping}`, `{tps}`, `{fps}`, `{biome}`, `{speed}`, and `{light}`. TPS is shown as `N/A` when a reliable client-side value is unavailable.

## Notes
This is a starter implementation. Ping depends on the current server connection; TPS cannot be reliably measured on every server without server-side support. The two Minecraft versions use separate source projects because their HUD APIs differ.


## Fixes for Minecraft 1.21.11

The 1.21.11 source uses the newer Fabric HUD API package (`client.rendering.v1.hud`), the newer matrix stack method names, the current keybinding category API, and the current screen background-render method signature. The screen background-render signature was also corrected for 1.21.4. Run the GitHub Actions workflow again after uploading these files.
