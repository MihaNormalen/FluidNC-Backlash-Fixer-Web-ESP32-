# FluidNC-Backlash-Fixer-Web-ESP32-
Eliminate CNC backlash directly from your web browser! This tool is hosted on an ESP32 microcontroller and processes G-code client-side using JavaScript. Enter X/Y values, upload your raw G-code file, and download the corrected, compensated G-code instantly. No desktop software or Python installation is required.
# FluidNC Backlash Compensation - Web/ESP32 Tool

Eliminate CNC backlash directly from your web browser! This tool is hosted on an ESP32 microcontroller and processes G-code client-side using JavaScript. Enter X/Y values, upload your raw G-code file, and download the corrected, compensated G-code instantly. No desktop software or Python installation is required.

---

## ✨ Features

* **Client-Side Processing:** The core logic runs entirely in the browser using JavaScript, adapted from the Python version.
* **Precise Compensation:** Calculates and inserts necessary motion offsets (`G0` moves) to physically engage the drivetrain.
* **Targeted Axes:** Supports independent compensation for X and Y axes.
* **Simple Interface:** Allows users to input X and Y backlash values and a safe feed rate (`F`).
* **Safety Integration:** Includes safety checks to prevent negative coordinates (Soft Limit Alarms).
* **No Dependencies:** Requires only a modern web browser and a FluidNC controller.

## 🛠️ Prerequisites

To use the tool, you need:

* A **FluidNC** Controller (with an SD card slot or Web Uploader access).
* A modern web browser.
* The **`index.html`** file (containing the embedded JavaScript).

---

## 🚀 Installation and Setup: FluidNC Extra Content

Since the processing logic runs client-side, the installation only requires deploying the `index.html` file to your FluidNC controller's file system and configuring it as "Extra Content."

### Step 1: Prepare the Web Content

Ensure the file containing the HTML and JavaScript logic is named **`index.html`**.

### Step 2: Upload the File

Upload the `index.html` file to your ESP32's file system using one of the following methods:

1.  **SD Card:** Copy the `index.html` file to the root directory of the SD card in your FluidNC controller.
2.  **Web Uploader:** Use the File Browser/Uploader tool available within the FluidNC Web Installer interface.

### Step 3: Configure FluidNC 'Extra Content'

1.  Access your FluidNC Web User Interface (UI).
2.  Navigate to the **Configuration** section (usually the gear icon or configuration tab).
3.  Locate the settings for **Extra Content** or **Web UI Extensions**.
4.  Set the path to the uploaded file. If uploaded to the root of the SD card, the path will typically be:
    ```
    /sd/index.html
    ```

### Step 4: Access the Tool

After configuration (and potentially a controller restart), access the tool via the configured link in the FluidNC UI, allowing you to use the backlash compensation tool directly.

---

## 📐 Usage: Client-Side Processing

The tool works by reading the G-code file locally in your browser, processing it, and initiating a download of the corrected file. The G-code data never leaves your device.

1.  **Input Parameters:** Enter the measured **X Axis Backlash (mm)** and **Y Axis Backlash (mm)** into the form. You can also set the **Safe Feed Rate (F)** for compensation moves.
2.  **Select File:** Click the file input button and select your raw G-code file (`.gcode`, `.nc`, or `.txt`).
3.  **Process:** Click **"Process and Save"**.
4.  **Download:** The JavaScript logic processes the content and automatically initiates a download of the corrected file (named `fixed_yourfilename.gcode`).
