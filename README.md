# Semana_3

Proyecto de la **Semana 3** de Riwi. Continúa el sitio de **Rueda Libre** (alquiler de bicicletas y recorridos guiados en Medellín) de la Semana 2 y lo lleva a **Tailwind CSS**, con una campaña nueva llamada **Rueda Nocturna**.

El trabajo de cada día vive en su propia rama.

| Rama | Contenido |
|------|-----------|
| `dia1` | Introducción a Tailwind CSS (utility-first): campaña Rueda Nocturna y kit de componentes |

> La rama `dia1` viene de la rama `semana3dia1` del repositorio `semana2riwi`, de donde se movió.

---

## Rama `dia1`: Tailwind CSS

### Estructura

- `nocturna/`: proyecto nuevo de la semana, con Tailwind CSS 4.
- `index.html`, `paginas/`, `css/`, `img/`, `prueba/`: el sitio Rueda Libre de la Semana 2 (Bootstrap 5.3), sin cambios.
- `bitacora.txt`: bitácora acumulada de aprendizaje, con las notas de la Semana 2 y la comparativa Bootstrap vs. Tailwind al final.

### Carpeta `nocturna/`

| Archivo | Qué es |
|---------|--------|
| `index.html` | Landing de **Rueda Nocturna**: campaña nueva de jueves a sábado, con 3 rutas |
| `componentes.html` | Kit de componentes de la campaña |
| `prototipo.html` | Prototipo corto de la landing, con Tailwind por CDN (`cdn.tailwindcss.com`) |
| `src/input.css` | Entrada de Tailwind (`@import "tailwindcss";`) |
| `src/output.css` | CSS generado por Tailwind (852 líneas), el que usan `index.html` y `componentes.html` |
| `package.json` | Dependencia `tailwindcss` ^4.3.5 |
| `node_modules/` | Dependencias instaladas (solo `tailwindcss`), subidas a la rama junto con el resto |

**Rutas de la campaña Rueda Nocturna** (punto de encuentro: Sede Rueda Libre):

| Ruta | Nivel | Distancia | Duración | Precio por persona |
|------|-------|-----------|----------|--------------------|
| Luces del Centro | Fácil | 10 km | 2 h | $55.000 |
| Miradores de la Ciudad | Medio | 16 km | 3 h | $75.000 |
| Luna en Las Palmas | Difícil | 22 km | 3,5 h | $95.000 |

**Kit de componentes** (`componentes.html`):

1. **Botones:** primario (esmeralda), secundario (gris pizarra) y de contorno, con estados `hover` y anillo de foco (`focus:ring`).
2. **Card de ruta:** ficha con los datos de cada recorrido y botón de inscripción.
3. **Alertas del sistema:** información (azul), éxito (esmeralda) y advertencia (ámbar).
4. **Campos de formulario:** correo electrónico y número de celular con sus etiquetas.

### Comparativa: Bootstrap (Semana 2) vs. Tailwind CSS

Está en la bitácora y compara cómo se construye un mismo botón:

- **Bootstrap:** componentes predefinidos y semánticos (`class="btn btn-primary"`). El framework encapsula diseño, colores y estados de `hover`.
- **Tailwind (utility-first):** el botón se arma combinando clases de bajo nivel directamente en el HTML (`class="bg-emerald-600 hover:bg-emerald-500 text-white font-semibold py-3 px-6 rounded-xl"`). Da control granular sin escribir hojas de estilo aparte.

**¿Qué se encontró en `src/output.css` y por qué?** Aparecen clases como `bg-emerald-600` o `text-white`, que sí se usan en el HTML, pero no clases que nadie escribió (como `bg-pink-500`). Tailwind tiene un motor **JIT (Just-In-Time)**: escanea los archivos HTML, busca los nombres de clase y genera solo el CSS de las que encuentra. Por eso el archivo final es muy liviano.

### Contenido heredado de la Semana 2

La rama también incluye el sitio de la Semana 2 (Bootstrap 5.3 personalizado con paleta Verde Ruta `#1E7A4F` y Naranja Pedal `#F39A2B`), documentado en el README de `semana2riwi`: portada con carrusel de promociones, tarifas y recorridos guiados, formulario de reservas con modal de políticas, y la prueba comparativa en `prueba/catalogo-bootstrap.html`.

---

## Cómo ver el proyecto

```bash
git checkout dia1
```

- **Rueda Nocturna:** abre `nocturna/index.html` en el navegador (usa `nocturna/src/output.css` ya generado).
- **Sitio de la Semana 2:** abre `index.html` desde la raíz.
