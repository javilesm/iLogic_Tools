# 📄 Massive_Simplifier (Multiple Simplified Part Generator for iLogic)

> **This iLogic script for Autodesk Inventor automates the process of exporting an active assembly (`.iam`) to multiple simplified part files (`.ipt`). It uses the derive function (Shrinkwrap/Simplified Part) to merge the entire assembly into a single solid body without seams.**

## ✨ Key Features

* **Batch Automation:** Allows you to define the exact number of copies to generate from the base model.
* **Sequential Naming:** Automatically assigns a custom user-defined prefix, followed by a two-digit numerical suffix (e.g., `SIDEWALL_01.ipt`, `SIDEWALL_02.ipt`).
* **Dynamic Path Selection:** Opens a Windows dialog box (`FolderBrowserDialog`) to visually select the output directory during each execution.
* **Background Processing:** Parts are generated, saved, and closed in the background (invisible mode), optimizing processing time and your computer's memory usage.

---

## 🧩 Prerequisites

* **Software:** Autodesk Inventor (Compatible with versions that support iLogic and the `System.Windows.Forms` library).
* **File type:** The active document **must** be an assembly (`.iam`).
* **File status:** The original assembly must be **saved** to your local drive or network before running the script.

---

## 🛠️ Installation and Setup

1. Open your main assembly in Autodesk Inventor.
2. Go to the **Manage** tab on the ribbon.
3. In the iLogic panel, click on **Add Rule**.
4. Assign a name to the rule (for example: `Massive_Simplifier`).
5. Copy the script's source code and paste it into the editor.
6. Click **Save & Run**.

---

## 🚀 Usage

1. Run the rule by right-clicking it in the iLogic browser and selecting **Run Rule**.
2. **Step 1 (Quantity):** A dialog box will appear. Enter the total number of copies you need to generate.
3. **Step 2 (Naming):** Enter the base text or prefix to name your files.
4. **Step 3 (Location):** The Windows folder browser will open. Navigate and select the directory where you want to save the resulting `.ipt` files. By default, the window will open to the same path where the original assembly is saved.
5. **Process:** Check the bottom status bar in Inventor to see the progress of the files being saved.
6. **Confirmation:** Upon completion, you will receive a message indicating that the process was successful along with the output path.

---

## 📄 Technical Notes

* **Templates:** The new parts are based on the standard part template (`.ipt`) that you have defined by default in your Inventor application options.
* **Derivation Type:** The script applies the `kDeriveAsSingleBodyNoSeams` property, which is equivalent to using the *Create Simplified Part* tool and selecting the option for a single solid body without face divisions between components.

## 🤝 Contributing
Pull Requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

## 📄 License
This project is licensed under the MIT License. See the LICENSE file for more details.
