# Inventor AutoDerive Pipeline

## Overview
The **Inventor AutoDerive Pipeline** is an iLogic automation script designed to accelerate top-down design workflows in Autodesk Inventor. When working with multi-body master part files, this tool automatically extracts each surface body and generates an individual, parametrically linked derived `.ipt` file. 

## Features
* **Batch Derivation:** Iterates through all solid bodies in the active `.ipt` and isolates them into individual derived parts.
* **Parametric Linking:** Maintains the native Top-Down workflow. Any changes to the master geometry will automatically update the derived children.
* **Unit Preservation:** Derived parts automatically inherit the base units of the master file, ensuring accuracy whether the design requires millimeters (mm) or inches (in).
* **Interactive UI:** Prompts the user with native Windows dialogs to select the output directory and define custom naming patterns using variables (`<Master>` and `<Body>`).
* **Background Processing:** Runs the document creation and derivation processes in the background to prevent screen flickering and optimize execution time.

## Prerequisites
* Autodesk Inventor Professional (Script utilizes standard Inventor API).
* The active document must be a Part Document (`.ipt`) containing at least one solid body.
* The master file must be saved prior to execution to establish valid derivation reference paths.

## Installation & Usage
1. Open your master `.ipt` file containing the solid bodies.
2. Navigate to the **Manage** tab and open the **iLogic Browser**.
3. Right-click in the **Rules** tab and select **Add Rule**.
4. Name the rule (e.g., `Export_Solid_Bodies`) and paste the provided VB.NET script into the editor.
5. Save and Run the rule.
6. A folder browser will appear. Select your desired output directory.
7. An input box will prompt you for a naming pattern. Use the available tags:
   * `<Master>`: Injects the original filename.
   * `<Body>`: Injects the specific solid body name.
   * *Example:* `<Master>_Derived_<Body>`
8. The script will execute and notify you once all bodies have been successfully exported.

## Script Logic Highlights
* Utilizes `SurfaceBodies` collection to identify target geometry.
* Configures `DerivedPartUniformScaleDef` to handle the derivation process.
* Explicitly loops through the `Solids` collection within the derivation definition to isolate the target body (`IncludeEntity = True`) and exclude the rest.
* Implements robust error handling and file sanitization (Regex) to prevent invalid characters in output filenames.
