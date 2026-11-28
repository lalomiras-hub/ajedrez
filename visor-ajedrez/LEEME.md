# Visor de partidas de ajedrez (PGN) para tu web o blog

Todo el visor es **un solo archivo**: `visor.html`. No necesita servidor especial, base de datos ni librerías externas.

```
visor.html          <- el visor
partidas/
   ejemplo.pgn      <- aquí vas dejando tus archivos .pgn
```

## 1. Uso en tu ordenador (gestión local)

1. Abre `visor.html` con doble clic.
2. Pulsa **Abrir PGN** o arrastra un `.pgn` encima (sirven bases con muchas partidas: aparece un desplegable para elegir).
3. Ve a la partida y posición que quieras y pulsa **Compartir**: te da el código `<iframe>` listo para pegar.

## 2. Dónde alojarlo (gratis)

### Opción recomendada: GitHub Pages
1. Crea una cuenta en github.com y un repositorio nuevo, por ejemplo `ajedrez` (público).
2. Pulsa *Add file > Upload files* y sube `visor.html` y la carpeta `partidas` con tus PGN.
3. En *Settings > Pages*, elige *Deploy from a branch*, rama `main`, carpeta `/ (root)` y guarda.
4. En un par de minutos tu visor estará en `https://TU_USUARIO.github.io/ajedrez/visor.html`.
5. Para publicar partidas nuevas, solo subes otro `.pgn` a `partidas/`.

### Otras opciones
- **Netlify** (app.netlify.com/drop) o **Cloudflare Pages**: arrastras la carpeta y te dan una dirección.
- **Tu propio hosting / WordPress con dominio propio**: sube la carpeta por FTP o con el gestor de archivos, por ejemplo a `tudominio.com/ajedrez/`.

Lo más cómodo es que **el visor y los PGN estén en el mismo sitio**. Si el PGN está en otro dominio, ese servidor tiene que permitir CORS (GitHub Pages lo permite).

## 3. Insertar en el blog

```html
<iframe src="https://TU_USUARIO.github.io/ajedrez/visor.html?pgn=partidas/torneo.pgn&game=3"
        width="100%" height="600" style="border:0;max-width:100%" loading="lazy"></iframe>
```

- **Blogger**: en la entrada cambia a *Vista HTML* y pega el código.
- **WordPress**: bloque *HTML personalizado*. (En WordPress.com, algunos planes gratuitos eliminan los iframes.)

### Dos formas de compartir (diálogo *Compartir*)
| Modo | Cuándo usarlo |
|---|---|
| **Enlazar al archivo PGN** (`?pgn=...`) | Bases con muchas partidas; si corriges el PGN, se actualiza en todos los iframes. |
| **Partida dentro del enlace** (`#z=...`) | Partidas sueltas: no hace falta subir el PGN, solo el visor. |

## 4. Parámetros de la dirección

| Parámetro | Ejemplo | Qué hace |
|---|---|---|
| `pgn` | `pgn=partidas/liga.pgn` | Archivo a cargar (ruta relativa o URL completa) |
| `game` | `game=5` | Partida del archivo (empieza en 1) |
| `single=1` | | Oculta el desplegable de partidas |
| `ply` | `ply=24` | Empieza en esa media jugada (24 = tras 12...) |
| `flip=1` | | Negras abajo |
| `theme` | `brown`, `blue`, `green`, `gray` | Colores del tablero |
| `dark=1` | | Modo oscuro |
| `autoplay=1` / `speed=1000` | | Reproducción automática / milisegundos por jugada |
| `fig=0` | | Notación con letras en vez de figuras |
| `edit=1` | | Muestra *Abrir PGN* y *Compartir* aunque esté dentro de un iframe |

## 5. Funciones

- Variantes anidadas, comentarios, símbolos de valoración (!, ?, ±, +-, etc.).
- Flechas y casillas de colores de ChessBase/Lichess (`[%cal Ge2e4]`, `[%csl Rd5]`).
- Posiciones iniciales con `[FEN "..."]` (estudios, problemas, finales).
- Teclado (flechas, Inicio, Fin, Espacio, F), rueda del ratón y gestos en el móvil.
- Copiar FEN, descargar PGN, **Analizar** la posición con motor en Lichess.
- Se adapta solo: horizontal en el blog, vertical en el móvil.

Créditos: lógica de reglas chess.js (Jeff Hlywa, licencia BSD), piezas "cburnett" (Colin M. L. Burnett, licencia BSD/GPL).
