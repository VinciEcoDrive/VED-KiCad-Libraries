# 🤝 Contributing

Thank you for helping improve the **Vinci Eco Drive KiCad libraries**. This repository contains symbol libraries, footprint (.pretty) folders, and 3D models used by KiCad. Contributions can include new components, footprint fixes, 3D models, documentation, and tests/CI improvements.

Maintainers will review PRs for quality, consistency, and CI checks. If you need help, open an issue or contact a repository maintainer.

## 💻 Install (advanced) — manual library tables

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

## 🔌 Add a component

Follow these steps to create a new component to add to the library:

1. **Follow the manual installation guide above.**

2. **Add a symbol**
   - Tools → Symbol Editor
   - Select the library in which you want to add a symbol in the left panel (your newly imported library)
   - Then go to File → Import → Symbol
   - Then Save
   - File → Symbol Properties
   - The goal is to have the following fields: 
       - Reference → U, J, …
       - Value → The exact name of the component
       - Description
       - Datasheet → Datasheet link
       - Manufacturer
       - Part Number
       - Footprint → For now, do not edit this field. 
         Note: If you are only adding the symbol and not the associated footprint, leave this field blank.
    - Then Save

3. **Add a footprint and its 3D model**
   - Tools → Footprint Editor
   - Go to File → Import → Footprint
   - Rename the footprint, and select the library in which you want to add the footprint (your newly imported library)
   - Then Save
   - File → Footprint Properties
   - The goal is to have the following fields: 
       - Reference → REF**
       - Value → The exact name of the component
       - Description (Optional)
       - Datasheet (Optional)
    - Don't forget to rename the footprint in the field Footprint Name.
    - Then Save.
    - Go to 3D Models (in Footprint Properties)
    - Set the following path: `"${KICAD9_3RD_PARTY}/3dmodels/org_vinciecodrive_kicadlibs/VED_library/your3dfile"`
    - Then Save

> [!NOTE]
> Don't forget to add your **3d model** to the library files !

4. **Link a symbol with its footprint**
   - Tools → Symbol Editor
   - File → Symbol Properties
   - Then for the Footprint field, set the following path:  `"PCM_VED_Library:FootprintName"`

## 📦 Release a new version

Follow these steps to publish a release that users can install via PCM:

1. Prepare `main`

   - Merge all PRs targeted for this release
   - Do not forget to update `main` branch before tagging

2. Create a tag (use [semver](https://semver.org/)):

   ```bash
   git tag v<MAJOR>.<MINOR>.<PATCH>
   git push origin v<MAJOR>.<MINOR>.<PATCH>
   ```

   - Example: `git tag -a v1.3.0 -m "VinciEcoDrive libs 1.3.0"`
   - Push: `git push origin v1.3.0`

1. CI will (automated):
   - Zip `package/` into `vinciecodrive-libs-<version>.zip`
   - Generate `packages.json` and `repository.json`
   - Publish artifacts to the `gh-pages` branch

2. Verify deployment :
   - You can check the deployment of new features on the [actions page](https://github.com/VinciEcoDrive/VED-KiCad-Libraries/actions) of the repo
   - You should see the number of the last pull request merged on `main`

3. Tell users to Refresh in KiCad PCM and update the package.

## 🪲 How to report a bug

- If you are a member of **Vinci Eco Drive**
   - Report the bug directly to your Technical Manager.

 - Open a GitHub issue in this repository and use the issue template (or provide the same information as above):
    - **Title**: short, descriptive
    - **Environment**: OS, KiCad version, library version/tag/commit
    - **Steps to reproduce** (minimal reproducible example preferred)
    - **Expected vs actual behavior**
    - **Attach files**: schematic/footprint/3D model, screenshots, logs, or a small project archive
    - Indicate **severity** and any **workarounds** you found
