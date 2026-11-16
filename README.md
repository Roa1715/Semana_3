# Semana_3

Proyecto de la **Semana 3** de Riwi. Continúa el sitio de **Rueda Libre** (alquiler de bicicletas y recorridos guiados en Medellín) de la Semana 2 y lo lleva a **Tailwind CSS**, con una campaña nueva llamada **Rueda Nocturna**.

El trabajo de cada día vive en su propia rama. Este README reúne lo que hay en ellas.

| Rama | Tema del día |
|------|--------------|
| `dia1` | Introducción a Tailwind CSS (utility-first): landing de Rueda Nocturna y kit de componentes |
| `dia2` | Tema propio de marca en Tailwind (`@theme`), clase `.btn-primary` con `@apply` y landing ampliada |
| `dia3` | Landing completa con planes y formulario de inscripción, enlazada desde el sitio de la Semana 2 |

> La rama `dia1` viene de la rama `semana3dia1` del repositorio `semana2riwi`, de donde se movió.

---

## Estructura común a las tres ramas

- `nocturna/`: proyecto nuevo de la semana, con Tailwind CSS 4.
- `index.html`, `paginas/`, `css/`, `img/`, `prueba/`: el sitio Rueda Libre de la Semana 2 (Bootstrap 5.3 con paleta Verde Ruta `#1E7A4F` y Naranja Pedal `#F39A2B`). Su documentación está en el README de `semana2riwi`.
- `bitacora.txt`: bitácora acumulada de aprendizaje (Semana 2 y comparativa Bootstrap vs. Tailwind al final).
- `nocturna/node_modules/`: dependencias instaladas, subidas junto con el resto.

### Archivos de `nocturna/`

| Archivo | Qué es |
|---------|--------|
| `index.html` | Landing de **Rueda Nocturna**, campaña nueva de jueves a sábado |
| `componentes.html` | Kit de componentes de la campaña |
| `prototipo.html` | Prototipo corto de la landing, con Tailwind por CDN (`cdn.tailwindcss.com`) |
| `src/input.css` | Entrada de Tailwind |
| `src/output.css` | CSS generado por Tailwind, el que usan `index.html` y `componentes.html` |
| `package.json` | Dependencia `tailwindcss` ^4.3.5 |

### Rutas de la campaña (punto de encuentro: Sede Rueda Libre)

| Ruta | Nivel | Distancia | Duración | Precio por persona |
|------|-------|-----------|----------|--------------------|
| Luces del Centro | Fácil | 10 km | 2 h | $55.000 |
| Miradores de la Ciudad | Medio | 16 km | 3 h | $75.000 |
| Luna en Las Palmas | Difícil | 22 km | 3,5 h | $95.000 |

---

## Rama `dia1`: Tailwind CSS

- `src/input.css` solo importa Tailwind (`@import "tailwindcss";`) y `src/output.css` es el CSS generado sin minificar (852 líneas).
- **Landing** (`nocturna/index.html`): portada "Rueda Nocturna", datos rápidos (3 rutas, desde $55.000) y las tres rutas de la campaña.
- **Kit de componentes** (`nocturna/componentes.html`):
  1. **Botones:** primario (esmeralda), secundario (gris pizarra) y de contorno, con `hover` y anillo de foco (`focus:ring`).
  2. **Card de ruta:** ficha con los datos del recorrido y botón de inscripción.
  3. **Alertas del sistema:** información (azul), éxito (esmeralda) y advertencia (ámbar).
  4. **Campos de formulario:** correo electrónico y número de celular.

### Comparativa: Bootstrap (Semana 2) vs. Tailwind CSS

Está en la bitácora y compara cómo se construye un mismo botón:

- **Bootstrap:** componentes predefinidos y semánticos (`class="btn btn-primary"`). El framework encapsula diseño, colores y estados de `hover`.
- **Tailwind (utility-first):** el botón se arma combinando clases de bajo nivel en el HTML (`class="bg-emerald-600 hover:bg-emerald-500 text-white font-semibold py-3 px-6 rounded-xl"`). Da control granular sin escribir hojas de estilo aparte.

**¿Qué se encontró en `src/output.css` y por qué?** Aparecen clases como `bg-emerald-600` o `text-white`, que sí se usan en el HTML, pero no clases que nadie escribió (como `bg-pink-500`). Tailwind tiene un motor **JIT (Just-In-Time)**: escanea los archivos HTML, busca los nombres de clase y genera solo el CSS de las que encuentra. Por eso el archivo final es muy liviano.

---

## Rama `dia2`: tema de marca y componentes con `@apply`

Cambios respecto a `dia1`, todos dentro de `nocturna/`:

- **Tema propio en `src/input.css`** con `@theme`:
  - Fuentes: `--font-sans` (Open Sans) y `--font-heading` (Montserrat).
  - Colores: `verde-ruta` `#059669`, `naranja-pedal` `#F97316`, `azul-noche` `#0F172A`, `gris-urbano` `#334155`, `blanco-puro` `#FFFFFF` y `amarillo-farol` `#FFD166`.
- **Componente `.btn-primary`** en `@layer components`, que reúne con `@apply` las mismas clases del botón esmeralda de `dia1` (fondo esmeralda, `hover`, sombra, bordes redondeados y anillo de foco).
- **`src/output.css` minificado:** pasó de 852 líneas a una sola.
- **Landing ampliada** (`nocturna/index.html`): Google Fonts (Montserrat y Open Sans), portada más grande y nueva sección **¿Cómo funciona?** con cuatro pasos: elige tu ruta, inscríbete, equípate y a rodar.

---

## Rama `dia3`: landing completa de Rueda Nocturna

Cambios respecto a `dia2`:

**`nocturna/index.html`** (358 líneas) quedó como una landing con navegación y estas secciones:

1. **Inicio:** portada de la campaña.
2. **Rutas:** las tres rutas de la campaña.
3. **¿Cómo funciona?:** los cuatro pasos de `dia2`.
4. **Planes Rueda Nocturna:**

   | Plan | Precio | Incluye |
   |------|--------|---------|
   | Individual | $55.000 por persona | Bicicleta y casco, luces LED y chaleco, guía certificado e hidratación |
   | Pareja (el más elegido) | $99.000 las dos personas | Todo lo del Individual, foto profesional del recorrido, snack para dos y prioridad en la ruta |
   | Grupo (4 a 8) | $45.000 por persona | Todo lo del Individual, guía exclusivo para el grupo, horario a elección y fotos del grupo |

5. **Inscripción:** formulario en dos bloques con validación en el navegador:
   - *Información personal:* nombre (mínimo 3 caracteres), correo y celular (10 dígitos que empiezan por 3).
   - *Detalles de la rodada:* ruta (con precio), día de salida (jueves, viernes o sábado), número de acompañantes (0 a 3) y experiencia.
6. **Pie de página.**

**Sitio de la Semana 2, enlazado con la campaña:**

- Enlace "Rueda Nocturna" en el menú de `index.html`, `tarifas.html` y `reservas.html`.
- Nueva diapositiva en el carrusel de promociones de la portada, con enlace a `nocturna/index.html`.
- En `formulario_exitoso.html`, el enlace "Enviar otro formulario" ahora lleva a `reservas.html` (antes a `index.html`).
- Se quitó el atributo `integrity` del script de Bootstrap en `index.html`, `tarifas.html` y `reservas.html`.

---

## Cómo ver el proyecto

```bash
git checkout dia3   # o dia1, dia2
```

- **Rueda Nocturna:** abre `nocturna/index.html` en el navegador (usa `nocturna/src/output.css` ya generado).
- **Sitio de la Semana 2:** abre `index.html` desde la raíz.
