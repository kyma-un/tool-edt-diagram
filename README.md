# tool-edt-diagram

Interactive web tool for visualizing, exploring, and exporting **EDT/WBS diagrams** for project planning.

This repository is part of the **KYMA Tools** ecosystem and provides a lightweight browser-based viewer for hierarchical project structures using a simple `data.json` file.

---

## Overview

**EDT Diagram Tool** allows users to represent a project as a hierarchical tree, commonly known as:

- **EDT**: Estructura de Desglose del Trabajo
- **WBS**: Work Breakdown Structure

The tool is built with **HTML, CSS, and JavaScript**, using **D3.js** for tree visualization.

It is designed to be general-purpose and independent of any specific project domain.

---

## Features

- Interactive EDT/WBS tree visualization
- Expand and collapse all nodes
- Expand and collapse a selected branch
- Select nodes and inspect their information
- Breadcrumb path for selected nodes
- Search nodes by name
- Zoom and pan navigation
- Automatic centering
- Export diagram as PNG
- Export diagram as PDF
- Simple hierarchical data model based on `data.json`
- No backend required

---

## Repository Structure

```text
tool-edt-diagram/
├── .gitignore
├── README.md
├── LICENSE
├── requirements.txt
├── index.html
├── styles.css
├── script.js
├── data.json
│
├── examples/
│   └── apolo-edt.json
│
├── docs/
│   └── data-format.md
│
└── assets/
```

---

## Requirements

### Local Requirements

- Python 3.9 or higher recommended
- Modern web browser

### Frontend Dependencies
The following libraries are loaded directly from CDN in index.html:

- D3.js
- html2canvas
- jsPDF

No external Python packages are required.

## Run Locally

From the repository root:
```bash
python3 -m http.server 8000
```
Then open:
```bash
http://localhost:8000
```
If you are using Windows and python3 does not work, try:
```bash
python -m http.server 8000
```

---

## Data Model

The EDT/WBS structure is defined in ```data.json```.

## Basic Format
```JSON
{
  "name": "Project name",
  "children": [
    {
      "name": "1. Planning",
      "children": [
        { "name": "1.1 Define scope" },
        { "name": "1.2 Identify deliverables" },
        { "name": "1.3 Build WBS" }
      ]
    },
    {
      "name": "2. Execution",
      "children": [
        { "name": "2.1 Develop deliverables" },
        { "name": "2.2 Validate progress" }
      ]
    }
  ]
}
```
### Rules

- Each node must include a name field.
- Child nodes are defined inside the children array.
- If a node has no children, the children field can be omitted.
- The tree can have multiple hierarchical levels.
- Node names should be clear and concise for better visualization.

---

## Usage

### Navigation

- Click a node to select it.
- Double-click a node to expand or collapse its children.
- Use the mouse wheel or trackpad to zoom.
- Drag the canvas to pan the visualization.

### Toolbar Actions

- Expand all: opens the full tree.
- Collapse levels: returns the tree to a compact view.
- Expand selected branch: expands the full subtree of the selected node.
- Collapse selected branch: collapses the full subtree of the selected node.
- Center: recenters the visualization.
- Export PNG: exports the current view as an image.
- Export PDF: exports the current view as a PDF file.

---

## Customization

### Change the EDT/WBS Content

Edit:
```bash
data.json
```

### Change the Visual Style

Edit:
```bash
styles.css
```

### Change the Interaction Logic

Edit:
```bash
script.js
```

### Add More Examples

Place additional JSON files inside:
```bash
examples/
```
Recommended naming pattern:
```bash
project-name-edt.json
```

---

## Example Use Cases
This tool can be used for:
- project planning
- academic project organization
- engineering project breakdowns
- task decomposition
- technical roadmap visualization
- documentation of project scope
- presentation of deliverable structures
- project management reports
- planning deliverables for GitHub-based projects

---

### Suggested Workflow
1. Define the main project objective.
2. Break the project into major work packages.
3. Add subpackages, tasks, and deliverables.
4. Save the hierarchy in data.json.
5. Run the tool locally.
6. Review the structure visually.
7. Export the EDT/WBS as PNG or PDF.
8. Include the exported file in reports, presentations, or project documentation.

---

## Current Status

Current status: **prototype**

The tool is functional for:
- interactive visualization
- hierarchical navigation
- node selection
- breadcrumb display
- search
- zoom and pan
- PNG export
- PDF export

---

## Roadmap
Planned improvements:
- Import JSON files from the browser
- Export the current structure as JSON
- Add editable nodes from the interface
- Add support for additional node metadata, such as:
  - description
  - owner
  - status
  - priority
  - due date
- Add dark mode
- Add multiple tree layout options
- Add automatic validation for data.json
- Add GitHub Pages deployment
- Add downloadable example templates
- Add support for multiple languages

---

## KYMA Tools Ecosystem

This repository is part of KYMA Tools, a collection of general-purpose software tools for project planning, documentation, automation, visualization, and technical workflows.

This repository follows the KYMA Tools naming convention:
```bash
tool-firstword-secondword-...-lastword
```
For this tool:
```bash
tool-edt-diagram
```
Recommended repository topics:
```bash
kyma-tools
software-tools
tool
edt
wbs
project-planning
project-management
diagram
visualization
html
css
javascript
d3js
open-source
```

---

## Contributing
Contributions are welcome.

Suggested contribution areas:
- improving the user interface
- adding data validation
- improving export quality
- adding editable nodes
- improving documentation
- adding more examples
- improving mobile layout
- adding GitHub Pages deployment

Before contributing, please keep the tool general-purpose and independent from any specific project.

---

## License
This project is released under the MIT License.

See the LICENSE file for details.
