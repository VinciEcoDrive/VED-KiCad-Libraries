<table style="border-collapse:collapse;border:none;background:transparent;">
   <tr>
      <td style="vertical-align:middle;border:none;background:transparent;">
         <img src="package/resources/icon.png" alt="VED Logo" width="40" />
      </td>
      <td style="vertical-align:middle;border:none;background:transparent;">
         <h1 style="margin:0">VED KiCad Libraries</h1>
      </td>
   </tr>
</table>

[![Latest Tag](https://img.shields.io/github/v/tag/VinciEcoDrive/VED-KiCad-Libraries)](https://github.com/VinciEcoDrive/VED-KiCad-Libraries/tags)

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

## 🤝 Contributing

To contribute, please first follow the [advanced installation instructions](#-install-advanced--manual-library-tables) and see [Contributing Guide](CONTRIBUTING.md)


## 🧪 Tips & troubleshooting

- If PCM doesn't show the new release immediately, wait a few minutes then click Refresh.
- If an install fails, check the GitHub Actions logs (CI) and confirm `repository.json` is accessible.

## 🤝 Contact

- If you are a member of Vinci Eco Drive, use the project’s primary team communication channel for general questions, library requests and design reviews.

- CI / repo maintainer — Théo HARDY: theo.hardy@edu.devinci.fr  
   - Preferred workflow: open a GitHub Issue for bugs, feature requests or installation problems; link PRs to issues when relevant.  

## 📜 Licence

This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

You are free to:

* **Share** — copy and redistribute the material in any medium or format for any purpose, even commercially.
* **Adapt** — remix, transform, and build upon the material for any purpose, even commercially.


