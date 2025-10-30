![VEDLogo](package/resources/icon.png)

# 🚀 VED KiCad Libraries

Welcome — this repo contains the curated KiCad 9-compatible libraries used by the VinciEcoDrive team. It's packaged for easy installation via KiCad's Plugin & Content Manager (PCM).

Quick overview

- 📦 Symbols: `.kicad_sym`
- 🖼️ Footprints: `.kicad_mod` inside `.pretty` folders
- 🧩 3D models: `.step` / `.wrl`


## ⚡️ Quick install (KiCad PCM)

1. Open KiCad 9.0 → tools → Manage Plugin and Content Manager Repositories.
2. Click on manage on the top right
3. Click Add and paste this URL:

```
https://vinciecodrive.github.io/VED-KiCad-Libraries/repository.json
```
4. Ensure the repository is enabled, open Plugin & Content Manager, find “VinciEcoDrive Libraries” and click Install.
5. After a release, click Refresh in PCM to see updates.

Note: GitHub Pages may take ~2–10 minutes to publish a new release.

## 💻 Install (advanced) — manual library tables

If you prefer to use the repo directly without PCM, follow these manual steps to add the libraries to KiCad.

1. Clone the repo somewhere consistent (example paths):

   - Windows: `C:\EE\kicad\VinciEcoDrive`
   - Linux/macOS: `~/EE/kicad/VinciEcoDrive`

2. Define an environment variable in KiCad (Preferences → Configure Paths):

   - Name: `KICAD_VED_LIB`
   - Value: path to the archive root (the folder containing `symbols/`, `footprints/`, `3dmodels/`)

3. Add symbol libraries (global):

   - Preferences → Manage Symbol Libraries → Global → Add
   - Nickname examples: `VED_Connectors`, `VED_Integrated_Circuits`, etc.
   - Library path example: `${KICAD_VED_LIB}/symbols/VED_Connectors.kicad_sym`

4. Add footprint libraries (global):

   - Preferences → Manage Footprint Libraries → Global → Add
   - Path example: `${KICAD_VED_LIB}/footprints/VED_Connectors.pretty`

5. 3D models

   - 3D models are referenced by footprints using relative paths or `${KICAD_VED_LIB}`.
   - Ensure your `KICAD_VED_LIB` points to the folder that contains the `3dmodels/` folder so footprints can find the models.

Notes

- Using an environment path keeps library entries portable across machines. If multiple team members use the same convention, everyone can reuse the same global table entries.
- When editing tables, prefer Global if the libraries are used across several projects; use Project tables for project-local overrides.

## 📦 Release a new version

Follow these steps to publish a release that users can install via PCM:

1. Prepare `main`
   - Merge all PRs targeted for the release.
   - Update `CHANGELOG.md` with highlights.

2. Create a tag (use [semver](https://semver.org/)):

   - Example: `git tag -a v1.3.0 -m "VinciEcoDrive libs 1.3.0"`
   - Push: `git push origin v1.3.0`

3. CI will (automated):
   - Zip `package/` into `vinciecodrive-libs-<version>.zip`
   - Generate `packages.json` and `repository.json`
   - Publish artifacts to the `gh-pages` branch

4. Verify deployment URLs
   - repository.json: https://vinciecodrive.github.io/VED-KiCad-Libraries/repository.json
   - packages.json:   https://vinciecodrive.github.io/VED-KiCad-Libraries/packages.json

5. Tell users to Refresh in KiCad PCM and update the package.

## 🧪 Tips & troubleshooting

- If PCM doesn't show the new release immediately, wait a few minutes then click Refresh.
- If an install fails, check the GitHub Actions logs (CI) and confirm `repository.json` is accessible.

## 🤝 Contact

- For library content updates: coordinate with the team working on the specific symbol/footprint.
- CI / repo maintainer: Théo HARDY — [theo.hardy@edu.devinci.fr](mailto:theo.hardy@edu.devinci.fr)

## 📜 Licence

ThiThis work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

You are free to:

* **Share** — copy and redistribute the material in any medium or format for any purpose, even commercially.
* **Adapt** — remix, transform, and build upon the material for any purpose, even commercially.


