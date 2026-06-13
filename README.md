# 🛠️ iLogic_Tools

> **A collection of automation iLogic scripts for Autodesk Inventor designed to streamline repetitive tasks, optimize assemblies, and manage Bills of Materials (BOM) efficiently.**

## 📦 Included Tools

### 1. Massive_Simplifier (Multiple Simplified Part Generator)
Automates the process of exporting an active assembly (`.iam`) to multiple simplified part files (`.ipt`). It uses the derive function (Shrinkwrap/Simplified Part) to merge the entire assembly into a single solid body without seams.

**✨ Key Features:**
* **Batch Automation:** Define the exact number of copies to generate from the base model.
* **Sequential Naming:** Automatically assigns a custom prefix, followed by a two-digit numerical suffix (e.g., `SIDEWALL_01.ipt`).
* **Dynamic Path Selection:** Opens a Windows dialog box to visually select the output directory.
* **Background Processing:** Parts are generated and saved invisibly, optimizing processing time.

**🚀 Usage:**
1. Run the rule and enter the total number of copies.
2. Enter the base text or prefix.
3. Select the output directory.
4. Process runs in the background with progress shown in the status bar.

---

### 2. MassiveDenote (Multiple Part Denoter)
Mass "demotes" individual part components from the root of an assembly document into newly generated individual subassemblies.

**✨ Key Features:**
* **Pre-execution Validation:** Ensures the main assembly is saved.
* **Isolated Inventory Collection:** Scans and collects components safely before modification.
* **Spatial Alignment & Grounding:** Positions the part preserving its exact absolute coordinates (maintaining original offsets like `50 mm / 1.97 in`) and sets it to `Grounded = True`.
* **Targeted Substitution:** Modifies only the specific instance evaluated without altering other global instances.

**🚀 Usage:**
Runs automatically upon execution, identifying root-level parts, generating new assemblies (e.g., `_Demoted_[count].iam`), and replacing the original components seamlessly.

---

## 🧩 Common Prerequisites
* **Software:** Autodesk Inventor (Compatible with versions supporting iLogic and `System.Windows.Forms`).
* **File type:** The active document **must** be an assembly (`.iam`).
* **File status:** The original assembly must be **saved** locally or on a network before running the scripts.

## 🛠️ General Installation and Setup
1. Open your main assembly in Autodesk Inventor.
2. Go to the **Manage** tab on the ribbon, or open the iLogic Browser.
3. In the iLogic panel, click on **Add Rule**.
4. Assign a descriptive name to the rule (e.g., `Massive_Simplifier` or `MassiveDenote`).
5. Copy the respective script's source code and paste it into the editor.
6. Click **Save & Run**.

## 🤝 Contributing
Pull Requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

## 📄 License
This project is licensed under the MIT License. See the LICENSE file for more details.
