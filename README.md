# tool-edt-diagram

Herramienta web interactiva para visualizar, explorar y exportar **diagramas EDT/WBS** para la planificación de proyectos.

Este repositorio forma parte del ecosistema KYMA Tools y proporciona un visor liviano basado en navegador para representar estructuras jerárquicas de proyectos a partir de un archivo `data.json`.

*Nota*: Al hacer parte de Kyma, este repositorio sigue la convención de estructuración de [KYMA Software Tools](https://github.com/kyma-un/kyma-software-tools)

---

## Información general

| Campo | Descripción |
|---|---|
| Nombre | EDT Diagram Tool |
| Repositorio | `tool-edt-diagram` |
| Organización | `kyma-un` |
| Ecosistema | KYMA Software Tools |
| Categoría principal | `planning` |
| Categorías secundarias | `structuring`, `visualization` |
| Estado | `prototype` |
| Licencia | MIT |
| Interfaz | Web |
| Lenguajes | HTML, CSS, JavaScript |
| Librería principal | D3.js |
| Backend | No requiere backend |

---

## Descripción general

**EDT Diagram Tool** permite representar un proyecto como un árbol jerárquico, conocido comúnmente como:

- **EDT**: Estructura de Desglose del Trabajo.
- **WBS**: Work Breakdown Structure.

La herramienta está diseñada para ser de propósito general e independiente de cualquier dominio específico de proyecto. Puede utilizarse en proyectos académicos, técnicos, investigativos o de gestión para visualizar paquetes de trabajo, entregables, tareas y subtareas.

La visualización se construye a partir de un archivo JSON simple, lo que permite adaptar rápidamente la herramienta a distintos proyectos sin modificar la lógica interna del código.

---

## Características

- Visualización interactiva de árboles EDT/WBS.
- Expansión y colapso de todos los nodos.
- Expansión y colapso de una rama seleccionada.
- Selección de nodos e inspección de información.
- Ruta de navegación para el nodo seleccionado.
- Búsqueda de nodos por nombre.
- Navegación con zoom y desplazamiento.
- Centrado automático del diagrama.
- Exportación del diagrama como PNG.
- Exportación del diagrama como PDF.
- Modelo de datos jerárquico basado en `data.json`.
- Funcionamiento local sin backend.

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

- Python 3.9 o superior.
- Navegador web moderno.
- Git, si se desea clonar el repositorio.

### Dependencias del frontend

Las siguientes librerías se cargan directamente desde CDN en `index.html`:

- D3.js.
- html2canvas.
- jsPDF.

No se requieren paquetes externos de Python para el uso básico de la herramienta.

---

## Instalación

Clona el repositorio:

```bash
git clone https://github.com/kyma-un/tool-edt-diagram.git
cd tool-edt-diagram
```

---

## Uso rápido

Desde la raíz del repositorio, ejecuta un servidor local:

```bash
python3 -m http.server 8000
```

Luego abre en el navegador:

```text
http://localhost:8000
```

Si estás usando Windows y `python3` no funciona, intenta:

```bash
python -m http.server 8000
```

---

## Modelo de datos

La estructura EDT/WBS se define en el archivo:

```text
data.json
```

La herramienta espera una estructura jerárquica donde cada nodo tenga un campo `name` y, opcionalmente, un arreglo `children` con sus nodos hijos.

### Formato básico

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

### Reglas del formato

- Cada nodo debe incluir un campo `name`.
- Los nodos hijos se definen dentro del arreglo `children`.
- Si un nodo no tiene hijos, el campo `children` puede omitirse.
- El árbol puede tener múltiples niveles jerárquicos.
- Los nombres de los nodos deben ser claros y concisos para mejorar la visualización.
- Se recomienda usar numeración jerárquica para proyectos complejos.

Ejemplo de numeración recomendada:

```text
1. Planeación
1.1 Definir alcance
1.2 Identificar entregables
2. Ejecución
2.1 Desarrollar entregables
2.2 Validar avance
```

---

## Uso de la herramienta

### Navegación

- Haz clic en un nodo para seleccionarlo.
- Haz doble clic en un nodo para expandir o colapsar sus hijos.
- Usa la rueda del mouse o el trackpad para hacer zoom.
- Arrastra el lienzo para desplazar la visualización.
- Usa la barra de búsqueda para encontrar nodos por nombre.

### Acciones disponibles

| Acción | Descripción |
|---|---|
| Expandir todo | Abre todos los nodos del árbol. |
| Colapsar niveles | Devuelve el árbol a una vista compacta. |
| Expandir rama seleccionada | Expande todo el subárbol del nodo seleccionado. |
| Colapsar rama seleccionada | Colapsa todo el subárbol del nodo seleccionado. |
| Centrar | Vuelve a centrar la visualización. |
| Exportar PNG | Exporta la vista actual como imagen PNG. |
| Exportar PDF | Exporta la vista actual como archivo PDF. |

---

## Entradas y salidas

| Tipo | Descripción | Formato |
|---|---|---|
| Entrada principal | Estructura jerárquica EDT/WBS | `data.json` |
| Entrada opcional | Ejemplos de estructuras EDT/WBS | `.json` en `examples/` |
| Salida | Imagen del diagrama | `.png` |
| Salida | Documento exportado del diagrama | `.pdf` |

---

## Personalización

### Cambiar el contenido de la EDT/WBS

Edita el archivo:

```text
data.json
```

### Cambiar el estilo visual

Edita el archivo:

```text
styles.css
```

### Cambiar la lógica de interacción

Edita el archivo:

```text
script.js
```

### Agregar más ejemplos

Ubica archivos JSON adicionales dentro de:

```text
examples/
```

Patrón de nombres recomendado:

```text
nombre-del-proyecto-edt.json
```

Ejemplo:

```text
apolo-edt.json
kyma-tools-edt.json
robot-design-edt.json
```

---

## Casos de uso

Esta herramienta puede usarse para:

- planificación de proyectos;
- organización de proyectos académicos;
- desgloses de proyectos de ingeniería;
- descomposición de tareas;
- visualización de hojas de ruta técnicas;
- documentación del alcance de un proyecto;
- presentación de estructuras de entregables;
- informes de gestión de proyectos;
- planeación de entregables para proyectos basados en GitHub.

---

## Flujo de trabajo sugerido

1. Define el objetivo principal del proyecto.
2. Divide el proyecto en grandes paquetes de trabajo.
3. Agrega subpaquetes, tareas y entregables.
4. Guarda la jerarquía en `data.json`.
5. Ejecuta la herramienta localmente.
6. Revisa la estructura visualmente.
7. Ajusta nombres, niveles o agrupaciones si es necesario.
8. Exporta la EDT/WBS como PNG o PDF.
9. Incluye el archivo exportado en informes, presentaciones o documentación del proyecto.

---

## Ejemplo incluido

Este repositorio incluye un ejemplo de EDT/WBS en:

```text
examples/apolo-edt.json
```

Este archivo puede usarse como referencia para construir nuevas estructuras jerárquicas.

Para probarlo, puedes copiar su contenido dentro de:

```text
data.json
```

y volver a cargar la página en el navegador.

---

## Estado actual

Estado actual:

```text
prototype
```

La herramienta es funcional para:

- visualización interactiva;
- navegación jerárquica;
- selección de nodos;
- visualización de ruta de navegación;
- búsqueda;
- zoom y desplazamiento;
- exportación a PNG;
- exportación a PDF.

Estados posibles dentro del ecosistema KYMA Software Tools:

| Estado | Significado |
|---|---|
| `idea` | Herramienta propuesta, aún sin implementación funcional. |
| `prototype` | Primera versión experimental o prueba de concepto. |
| `development` | Herramienta en desarrollo activo. |
| `stable` | Herramienta usable en proyectos reales. |
| `deprecated` | Herramienta reemplazada o no recomendada para nuevos proyectos. |
| `archived` | Herramienta conservada solo como referencia histórica. |

---

## Hoja de ruta

Mejoras planificadas:

- [ ] Importar archivos JSON desde el navegador.
- [ ] Exportar la estructura actual como JSON.
- [ ] Agregar nodos editables desde la interfaz.
- [ ] Agregar soporte para metadatos adicionales de nodos:
  - descripción;
  - responsable;
  - estado;
  - prioridad;
  - fecha límite.
- [ ] Agregar modo oscuro.
- [ ] Agregar múltiples opciones de diseño de árbol.
- [ ] Agregar validación automática para `data.json`.
- [ ] Agregar despliegue en GitHub Pages.
- [ ] Agregar plantillas de ejemplo descargables.
- [ ] Agregar soporte para múltiples idiomas.

---

## Contribuciones

Las contribuciones son bienvenidas.

Áreas sugeridas para contribuir:

- mejorar la interfaz de usuario;
- agregar validación de datos;
- mejorar la calidad de exportación;
- agregar nodos editables;
- mejorar la documentación;
- agregar más ejemplos;
- mejorar el diseño en dispositivos móviles;
- agregar despliegue en GitHub Pages.

Antes de contribuir, por favor mantén la herramienta de propósito general e independiente de cualquier proyecto específico.

### Flujo recomendado

```bash
git checkout -b feature/nombre-de-la-mejora
git add .
git commit -m "Describe the improvement"
git push origin feature/nombre-de-la-mejora
```

Luego abre un pull request hacia la rama principal del repositorio.

---

## Licencia

Este proyecto se publica bajo la Licencia MIT.

Consulta el archivo:

```text
LICENSE
```

---

## Autoría y mantenimiento

Desarrollado dentro del ecosistema **KYMA Tools**.

| Rol | Responsable |
|---|---|
| Grupo | KYMA |
| Organización | Universidad Nacional de Colombia |
| Repositorio | `kyma-un/tool-edt-diagram` |
| Mantenimiento | `kyma-un` |
