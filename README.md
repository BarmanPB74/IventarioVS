<p align="center"><img src="icon-192.png" width="96" alt="Logo EK"></p>

# IventarioVS · Inventario Capiro

App de control de inventario para Café Capiro (vivero Capiro, La Ceja, Antioquia). Lleva un registro independiente de Loggro Restobar para comprobar con conteos físicos fechados si el inventario y las ventas del POS coinciden con lo que realmente hay y realmente salió.

**Lo que hace**

- Registra entradas con lote, vencimiento y costo; mermas con motivo; consumo interno y mise en place.
- Indica cada día qué lote sacar primero (FEFO), qué está bajo el mínimo y cuánto pedir.
- Cuadra el conteo físico contra el stock y las ventas que reporta Loggro, y calcula ventas sin registrar y error de stock por producto.
- Importa el reporte de ventas o inventario de Loggro (.xlsx o CSV) y empareja los productos por nombre o código.
- Exporta reportes en Excel con formato de oficina (cuadre con hallazgos, inventario, movimientos, combos, costos) y guarda copias de seguridad en JSON.
- Arma el pedido por proveedor con la salida real de los últimos 28 días, lo envía por WhatsApp y genera un PDF de aprobación para la administración.
- Diagnostica cada cuadre: productos que cuadran, cruces de códigos, faltantes y productos sin inventario en Loggro.
- Calcula costo, margen y costo % de cada bebida, producto de reventa y combo, y sugiere el precio de cada combo.
- Mide cada combo durante 4 semanas contra su semana base y propone mantenerlo, ajustarlo o retirarlo.
- Trae precargados los 91 productos del catálogo del café y 9 combos de la carta.

## Descargar

| Qué | Dónde |
| --- | --- |
| APK para Android 8 o superior | Pestaña [Releases](https://github.com/BarmanPB74/IventarioVS/releases), o `inventario-capiro.apk` en la rama `apk` |
| Versión web | `index.html` (se publica si activas GitHub Pages en Settings → Pages → rama `main`) |

Las actualizaciones se instalan encima sin perder datos: todas las versiones se firman con la misma llave (`android/app/debug.keystore`).

## Documentos

| Documento | Contenido |
| --- | --- |
| [Plan de uso y evolución](docs/03-plan-de-uso-y-evolucion.md) | Cómo se usa la app para inventario, promociones y ventas, y la hoja de ruta de versiones |
| [Manual y propuesta de cambio de POS](docs/02-manual-y-propuesta-pos.md) | Uso pantalla por pantalla, cuadre contra Loggro, expediente de evidencia, solicitud al dueño y alternativas de POS |
| [Sistema de crecimiento](docs/01-sistema-de-crecimiento.md) | Inventario como herramienta, rotación FEFO, mise en place, combos, clientes del vivero, fidelización y contaduría para una nueva sede |

El *Libro maestro de recetas* y la *Tesis de servicio CAPIRO* no están en este repositorio porque son documentos internos y confidenciales del café, y el repositorio es público.

## Estructura

| Ruta | Contenido |
| --- | --- |
| `index.html` | La app completa (HTML, CSS y JS en un archivo). Única fuente: el APK la copia al compilar. |
| `android/` | Envoltura nativa en Java (WebView), ícono adaptativo EK, guardado en Descargas y selector de archivos. |
| `.github/workflows/apk.yml` | Compila, firma y publica el APK en cada cambio de `index.html` o `android/`. |
| `docs/` | Documentación de uso, operación y evolución. |
| `logo-ek.svg`, `icon-*.png` | Identidad visual EK. |

## Datos

En el APK y en la versión web los datos se guardan solo en ese dispositivo. Haz **Más → Guardar copia** cada domingo; el archivo queda en Descargas → Inventario Capiro y se restaura con **Más → Restaurar copia**.

## Versiones

| Versión | Estado |
| --- | --- |
| 0.1 Control | Publicada |
| 0.2 Promociones | Publicada: pestaña Combos con registro diario, ticket promedio y ficha de prueba de 4 semanas |
| 0.3 Costos y margen | Publicada: Stock → Costos y margen, con 33 recetas del libro maestro, 2 preparaciones base, reventa y costo de combos |
| 0.4 Pedido inteligente | Publicada: Stock → Pedido con salida real, proveedores y envío por WhatsApp; diagnóstico automático del cuadre frente a Loggro |
| 0.5 Importar Loggro | Publicada: importa el reporte de Loggro (.xlsx o CSV) al cuadre y exporta reportes en Excel con formato de oficina |
| 0.6 Pedido en PDF | Publicada: Stock → Pedido genera un PDF por proveedor con agotados, bajo mínimo, costo estimado, casillas y firma de aprobación, y lo comparte desde el teléfono |
| 0.7 Tablero para el dueño | Siguiente |
