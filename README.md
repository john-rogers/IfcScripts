# IFC Cost Schedule Exporter (Blender Addon)

This project provides a Python script (`ExportIfcCostSchedule.py`) for exporting cost schedule information from IFC (Industry Foundation Classes) files to a PDF. IFC is a standard format for openBIM (Building Information Modeling).

**This script is designed to be used as an addon within Blender and likely relies on the BlenderBIM addon for IFC data access.**

## Dependencies

*   **Blender:** A recent version of Blender (e.g., 2.8x, 2.9x, 3.x or later).
*   **BlenderBIM Addon:** This addon is likely required to import and manage IFC files within Blender, providing the `IfcStore` that this script uses. You can find installation instructions on the [BlenderBIM website](https://blenderbim.org/).
*   **Python Libraries:**
    *   `ifcopenshell`: For reading and processing IFC files. (Often comes with BlenderBIM or Blender itself if using a version built for BIM).
    *   `fpdf`: For generating PDF documents.
    *   `bpy`: Blender's Python API (comes with Blender).
    *   `bonsai.bim.ifc`: This library is also imported by the script. Its origin is not entirely clear from the script alone. It might be:
        *   A part of the BlenderBIM addon.
        *   A separate Python package you need to install (e.g., via `pip install bonsai.bim.ifc` - try this if you encounter import errors).
        *   A custom library that should be provided alongside this exporter script.
        Ensure this dependency is met. If you encounter an `ImportError` for `bonsai.bim.ifc`, you may need to investigate its source and installation method further.

## Installation

1.  **Install Blender:** Download and install Blender from [blender.org](https://www.blender.org/download/).
2.  **Install BlenderBIM Addon:** Follow the instructions on the [BlenderBIM website](https://blenderbim.org/) to install it. This will likely provide `ifcopenshell` and potentially `bonsai.bim.ifc`.
3.  **Install Python Libraries (if not covered by Blender/BlenderBIM):**
    *   If you still encounter import errors for `fpdf` after installing Blender and BlenderBIM, you might need to install it into Blender's Python environment.
    *   Open Blender's Python console or use your system's pip if Blender's Python is in your PATH.
    *   Install `fpdf`:
        ```bash
        pip install fpdf
        ```
        *(Note: Blender often comes with its own Python. You might need to install these libraries into Blender's Python environment specifically. See Blender documentation for installing external Python packages.)*
4.  **Install the IFC Cost Schedule Exporter Addon:**
    *   Open Blender.
    *   Go to `Edit > Preferences > Add-ons`.
    *   Click `Install...` and navigate to the `ExportIfcCostSchedule.py` file.
    *   Enable the addon by checking the box next to its name in the Add-ons list (it will likely appear as "Export IfcCostSchedule" or similar based on its `bl_label`).

## Usage

1.  **Open your IFC file in Blender:** Use the BlenderBIM addon to import and load your IFC file. This process makes the IFC data available through `IfcStore`.
2.  **Ensure an IFC project and Cost Schedule are loaded and active.** The script uses `IfcStore.get_file()` (expected from BlenderBIM) and `file.by_type("IfcCostSchedule")` to access the necessary data.
3.  **Export the Cost Schedule:**
    *   Go to `File > Export > IfcCostSchedule to PDF` (the exact menu text might vary slightly based on the `bl_label` in the script).
    *   A file dialog will appear, allowing you to choose the save location and filename for your PDF.
    *   You will also see several export options in the operator panel (usually bottom-left of the file dialog or in the N-panel):
        *   `Choose Schedule`: Select the specific cost schedule if multiple exist.
        *   `Should print document cover`: Include a cover page.
        *   `Should print description`: Include full descriptions.
        *   `Should print each quantity`: List all quantities.
        *   `Should print rates and totals`: Include prices and totals.
        *   `Should print summary`: Add a summary page.
    *   Click the export button (e.g., "Export IfcCostSchedule").

## Contributing

Contributions are welcome! If you have improvements or bug fixes, please follow these steps:

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'Add some feature'`).
5.  Push to the branch (`git push origin feature/your-feature`).
6.  Open a pull request.

## License

This project is licensed under the MIT License - see the LICENSE file for details (if a LICENSE file exists or you plan to add one). You might want to create a `LICENSE` file with the MIT License text.
