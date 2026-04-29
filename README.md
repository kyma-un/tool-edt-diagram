# tool-edt-diagram

Herramienta web interactiva para visualizar, explorar y exportar **diagramas EDT/WBS** para la planificación de proyectos.

Este repositorio forma parte del ecosistema **KYMA Tools** y proporciona un visor liviano basado en navegador para estructuras jerárquicas de proyectos usando un archivo simple `data.json`.

---

## Descripción general

**EDT Diagram Tool** permite representar un proyecto como un árbol jerárquico, conocido comúnmente como:

- **EDT**: Estructura de Desglose del Trabajo
- **WBS**: Work Breakdown Structure

La herramienta está construida con **HTML, CSS y JavaScript**, usando **D3.js** para la visualización del árbol.

Está diseñada para ser de propósito general e independiente de cualquier dominio específico de proyecto.

---

## Características

- Visualización interactiva de árboles EDT/WBS
- Expandir y colapsar todos los nodos
- Expandir y colapsar una rama seleccionada
- Seleccionar nodos e inspeccionar su información
- Ruta de navegación para los nodos seleccionados
- Búsqueda de nodos por nombre
- Navegación con zoom y desplazamiento
- Centrado automático
- Exportación del diagrama como PNG
- Exportación del diagrama como PDF
- Modelo de datos jerárquico simple basado en `data.json`
- No requiere backend

---

## Estructura del repositorio

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

## Requisitos

### Requisitos locales

- Python 3.9 o superior recomendado
- Navegador web moderno

### Dependencias del frontend

Las siguientes librerías se cargan directamente desde CDN en `index.html`:

- D3.js
- html2canvas
- jsPDF

No se requieren paquetes externos de Python.

## Ejecutar localmente

Desde la raíz del repositorio:

```bash
python3 -m http.server 8000
```

Luego abre:

```bash
http://localhost:8000
```

Si estás usando Windows y `python3` no funciona, intenta:

```bash
python -m http.server 8000
```

---

## Modelo de datos

La estructura EDT/WBS se define en `data.json`.

## Formato básico

```json
{
  "name": "Nombre del proyecto",
  "children": [
    {
      "name": "1. Planeación",
      "children": [
        { "name": "1.1 Definir alcance" },
        { "name": "1.2 Identificar entregables" },
        { "name": "1.3 Construir la EDT/WBS" }
      ]
    },
    {
      "name": "2. Ejecución",
      "children": [
        { "name": "2.1 Desarrollar entregables" },
        { "name": "2.2 Validar avance" }
      ]
    }
  ]
}
```

### Reglas

- Cada nodo debe incluir un campo `name`.
- Los nodos hijos se definen dentro del arreglo `children`.
- Si un nodo no tiene hijos, el campo `children` puede omitirse.
- El árbol puede tener múltiples niveles jerárquicos.
- Los nombres de los nodos deben ser claros y concisos para una mejor visualización.

---

## Uso

### Navegación

- Haz clic en un nodo para seleccionarlo.
- Haz doble clic en un nodo para expandir o colapsar sus hijos.
- Usa la rueda del mouse o el trackpad para hacer zoom.
- Arrastra el lienzo para desplazar la visualización.

### Acciones de la barra de herramientas

- Expandir todo: abre el árbol completo.
- Colapsar niveles: devuelve el árbol a una vista compacta.
- Expandir rama seleccionada: expande todo el subárbol del nodo seleccionado.
- Colapsar rama seleccionada: colapsa todo el subárbol del nodo seleccionado.
- Centrar: vuelve a centrar la visualización.
- Exportar PNG: exporta la vista actual como imagen.
- Exportar PDF: exporta la vista actual como archivo PDF.

---

## Personalización

### Cambiar el contenido de la EDT/WBS

Edita:

```bash
data.json
```

### Cambiar el estilo visual

Edita:

```bash
styles.css
```

### Cambiar la lógica de interacción

Edita:

```bash
script.js
```

### Agregar más ejemplos

Ubica archivos JSON adicionales dentro de:

```bash
examples/
```

Patrón de nombres recomendado:

```bash
nombre-del-proyecto-edt.json
```

---

## Casos de uso de ejemplo

Esta herramienta puede usarse para:

- planificación de proyectos
- organización de proyectos académicos
- desgloses de proyectos de ingeniería
- descomposición de tareas
- visualización de hojas de ruta técnicas
- documentación del alcance de un proyecto
- presentación de estructuras de entregables
- informes de gestión de proyectos
- planificación de entregables para proyectos basados en GitHub

---

### Flujo de trabajo sugerido

1. Define el objetivo principal del proyecto.
2. Divide el proyecto en grandes paquetes de trabajo.
3. Agrega subpaquetes, tareas y entregables.
4. Guarda la jerarquía en `data.json`.
5. Ejecuta la herramienta localmente.
6. Revisa la estructura visualmente.
7. Exporta la EDT/WBS como PNG o PDF.
8. Incluye el archivo exportado en informes, presentaciones o documentación del proyecto.

---

## Estado actual

Estado actual: **prototipo**

La herramienta es funcional para:

- visualización interactiva
- navegación jerárquica
- selección de nodos
- visualización de ruta de navegación
- búsqueda
- zoom y desplazamiento
- exportación a PNG
- exportación a PDF

---

## Hoja de ruta

Mejoras planificadas:

- Importar archivos JSON desde el navegador
- Exportar la estructura actual como JSON
- Agregar nodos editables desde la interfaz
- Agregar soporte para metadatos adicionales de nodos, tales como:
  - descripción
  - responsable
  - estado
  - prioridad
  - fecha límite
- Agregar modo oscuro
- Agregar múltiples opciones de diseño de árbol
- Agregar validación automática para `data.json`
- Agregar despliegue en GitHub Pages
- Agregar plantillas de ejemplo descargables
- Agregar soporte para múltiples idiomas

---

## Ecosistema KYMA Tools

Este repositorio forma parte de KYMA Tools, una colección de herramientas de software de propósito general para planificación de proyectos, documentación, automatización, visualización y flujos de trabajo técnicos.

Este repositorio sigue la convención de nombres de KYMA Tools:

```bash
tool-firstword-secondword-...-lastword
```

Para esta herramienta:

```bash
tool-edt-diagram
```

Temas recomendados para el repositorio:

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

## Contribuciones

Las contribuciones son bienvenidas.

Áreas sugeridas para contribuir:

- mejorar la interfaz de usuario
- agregar validación de datos
- mejorar la calidad de exportación
- agregar nodos editables
- mejorar la documentación
- agregar más ejemplos
- mejorar el diseño en dispositivos móviles
- agregar despliegue en GitHub Pages

Antes de contribuir, por favor mantén la herramienta de propósito general e independiente de cualquier proyecto específico.

---

## Licencia

Este proyecto se publica bajo la Licencia MIT.

Consulta el archivo `LICENSE` para más detalles.
