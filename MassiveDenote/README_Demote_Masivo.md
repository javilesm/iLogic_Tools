# 📄 MassiveDenote (Multiple Part Denoter for iLogic)

> ** An automation iLogic script for **Autodesk Inventor** designed to mass "demote" individual part components from the root of an assembly document into newly generated individual subassemblies.**

## Overview

In Autodesk Inventor, structuring a complex Bill of Materials (BOM) often requires grouping separate parts into individual subassemblies. Doing this manually ("Demote" feature) for dozens or hundreds of components is time-consuming and error-prone. 

**MassiveDenote** automates this workflow by scanning the active top-level assembly, filtering for single part documents (`.ipt`), creating a new subassembly (`.iam`) for each one in the background, transferring the part into it, grounding it to maintain spatial integrity, and replacing the original root component seamlessly.

## ✨ Key Features

- **Pre-execution Validation:** Ensures the main assembly is saved to establish a valid base directory paths for new files.
- **Isolated Inventory Collection:** Scans and collects target components into an isolated memory list before modification, preventing collection corruption errors during database writes.
- **Background Instantiation:** Creates new `.iam` files invisibly in memory to prevent UI flicker and maximize processing speed.
- **Spatial Alignment & Grounding:** Positions the part within the new subassembly using an identity matrix, preserving its exact absolute coordinates. The component is automatically set to `Grounded = True` so it remains locked in place.
- **Targeted Substitution:** Executes a localized replacement (`oOcc.Replace(..., False)`) ensuring only the specific instance evaluated is modified, without altering other instances of the same part globally unless intended.

---

## 🧩 Prerequisites

* **Software:** Autodesk Inventor (Compatible with versions that support iLogic and the `System.Windows.Forms` library).
* **File type:** The active document **must** be an assembly (`.iam`).
* **File status:** The original assembly must be **saved** to your local drive or network before running the script.

---

## 🛠️ Installation and Setup

1. Open your main assembly in Autodesk Inventor.
2. Open the iLogic Browser (View tab > Windows panel > User Interface > iLogic Log/Browser).
3. Right-click in the Rules or External Rules tab and select Add Rule.
4. Name the rule MassiveDenote.
5. Paste the source code above into the iLogic code editor window.
6. Click **Save & Run**.

---

## How It Works

1. **Path Determination:** The script identifies the folder path of the active assembly document.
2. **Filtering:** Iterates through first-level occurrences and isolates those matching `DocumentTypeEnum.kPartDocumentObject`.
3. **Subassembly Creation:** For each isolated part, a new assembly file named after the part (suffixed with `_Demoted_[count].iam`) is generated in the root folder.
4. **Placement:** The original part file is inserted at the exact relative coordinate origin (e.g., maintaining any original offset like `50 mm / 1.97 in`) and grounded.
5. **Component Replacement:** The root-level part instance is replaced by the newly created subassembly instance.

## 🤝 Contributing
Pull Requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

## 📄 License
This project is licensed under the MIT License. See the LICENSE file for more details.
