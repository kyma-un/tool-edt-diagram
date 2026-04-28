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
