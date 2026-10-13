# Manual de Inventario Capiro y propuesta de cambio de POS

12 de octubre de 2026 · Pablo, barista de Café Capiro

## 1. Para qué sirve la app

Inventario Capiro es un registro independiente de Loggro que permite comprobar, con conteos físicos fechados, si el inventario y las ventas que muestra Loggro coinciden con lo que realmente hay y realmente salió. Loggro sigue siendo el sistema de ventas y facturación; la app es el auditor.

La app demuestra tres cosas:

1. **Cuánto salió de verdad** de cada producto entre dos conteos, sin depender de que alguien registre cada venta.
2. **Cuánto difiere Loggro** de la nevera real, en unidades y en pesos.
3. **Cuánto se pierde** por vencimiento, daño o preparación fallida, con motivo y fecha.

También sirve para trabajar mejor cada día: avisa qué lotes vencen primero, qué productos están bajo el mínimo y cuánto pedir para llegar al ideal del fin de semana.

## 2. Instalación

Usa el APK como versión principal en el teléfono del café. Las tres versiones tienen las mismas pantallas, pero cada una guarda sus datos en un lugar distinto y no se sincronizan entre sí.

| Versión | Dónde se abre | Dónde quedan los datos | Cuándo usarla |
| --- | --- | --- | --- |
| APK Android 0.1 | Ícono EK en el teléfono | Solo en ese teléfono | Uso diario en la barra; funciona sin internet |
| Web | `index.html` del repositorio [IventarioVS](https://github.com/BarmanPB74/IventarioVS), publicado si activas GitHub Pages | Solo en ese navegador | Probar en otro dispositivo |
| Claude | Tarjeta Inventario Capiro en el proyecto de Claude | Nube del artifact, visible desde cualquier dispositivo con tu cuenta | Respaldo en la nube y análisis con Claude |

**Instalar el APK (Android 8 o superior):**

1. Descarga `inventario-capiro-0.1.apk` desde el chat o desde la sección [Releases de IventarioVS](https://github.com/BarmanPB74/IventarioVS/releases).
2. Ábrelo. Si Android lo bloquea, toca Configuración y permite instalar apps desde esa fuente (Chrome, Archivos o Telegram, según desde dónde lo abras).
3. Si aparece Google Play Protect, elige «Instalar de todos modos». La advertencia sale porque la app no viene de la tienda.
4. Abre **Inventario Capiro**. La primera vez carga los 91 productos del libro maestro.

**Respaldo obligatorio:** cada domingo, en **Más → Guardar copia**. El archivo queda en Descargas → Inventario Capiro. Si cambias de teléfono o desinstalas la app, se restaura con **Más → Restaurar copia**. Ese mismo archivo sirve para pasar los datos a la versión de Claude.

Las actualizaciones futuras se instalan encima sin perder datos, porque todas se firman con la misma llave.

## 3. Uso diario, pantalla por pantalla

La app tiene cinco pantallas en la barra inferior. En un día normal usas Hoy al abrir, Mover durante el turno y Cuadre al cerrar.

| Pantalla | Qué muestra | Qué haces ahí |
| --- | --- | --- |
| **Hoy** | Misión del día según el ciclo semanal, valor del stock, merma del mes, lotes que vencen en 5 días, pedido sugerido y perecederos sin contar en 48 h | Al abrir: mueve al frente de la nevera lo que sale en rojo |
| **Mover** | Formulario de movimiento y lista de lo registrado hoy | Registrar cada entrada, merma o consumo en el momento |
| **Stock** | Cada producto con su existencia, barra contra el ideal y estado (OK, Bajo, Agotado, Sin mínimo) | Configurar costo, mínimo, ideal, ubicación y prioridad; agregar o archivar productos |
| **Cuadre** | Conteo por categoría contra el esperado de la app y los datos de Loggro | Contar al cierre y guardar el cuadre |
| **Más** | Exportar CSV, últimos movimientos, copia de seguridad y rutina de rotación | Exportar evidencia y respaldar |

**Los cinco tipos de movimiento:**

| Tipo | Cuándo | Dato extra | Efecto en el stock |
| --- | --- | --- | --- |
| Entrada | Llega mercancía | Lote, vencimiento y costo unitario (opcional; actualiza el costo del producto) | Suma |
| Merma | Algo se pierde | Motivo: vencido, dañado, preparación fallida, caída, degustación, otro | Resta |
| Consumo | Uso interno o mise en place (leche para preparar, café de prueba, consumo del personal) | Nota | Resta |
| Venta | Opcional; las ventas viven en Loggro | Nota | Resta |
| Ajuste | Corrección puntual; número negativo para restar | Nota con la razón | Suma o resta |

**Configuración inicial de un producto (2 minutos cada uno):** abre Stock, toca el producto y llena costo unitario de compra, stock mínimo y stock ideal. Empieza por los P1 a P4: lácteos, cervezas, hojaldres y almojábana. Un producto sin mínimo nunca aparecerá en el pedido sugerido.

**Regla de oro:** si algo entra o se pierde y no lo registras, el cuadre lo mostrará como venta sin registrar. La app solo es tan buena como la disciplina de anotar en el momento.

## 4. El cuadre contra Loggro

El cuadre es la función que convierte la app en evidencia. Cada producto contado se compara con dos fuentes: lo que la app esperaba y lo que dice Loggro.

**Paso a paso (15 minutos por categoría):**

1. En Loggro, abre el reporte de inventario y el de ventas por producto, filtrado desde la fecha y hora del cuadre anterior hasta ahora.
2. En la app, abre **Cuadre** y elige la categoría.
3. Cuenta físicamente cada producto, sin mirar el número esperado primero, y escríbelo en **Físico**.
4. Copia de Loggro el **Stock Loggro** y las **Ventas Loggro** del periodo.
5. Escribe una nota («cierre domingo», «apertura martes») y toca **Guardar cuadre**.

El primer cuadre de cada producto solo crea el punto de partida. Las diferencias aparecen a partir del segundo.

**Cómo leer cada resultado:**

| Casilla | Fórmula | Si es positiva | Si es negativa |
| --- | --- | --- | --- |
| Salió (calculado) | Conteo anterior + entradas + ajustes − mermas − consumo − físico | Unidades que realmente salieron por venta | Hay una entrada sin registrar o un error de conteo |
| Ventas sin registrar | Salió − ventas Loggro | Salieron más unidades de las que Loggro registró: ventas no cobradas, consumo sin anotar o pérdida | Loggro registró más ventas de las que salieron: receta mal configurada, producto vendido con otro código o descuento mal aplicado |
| Error stock Loggro | Stock Loggro − físico | Loggro cree que hay más de lo que hay | Loggro cree que hay menos de lo que hay |

El cero aparece en el color normal del texto, los negativos en rojo y los positivos en ámbar. El historial guarda cada cuadre con su diferencia valorizada en pesos, usando el costo unitario del producto.

**Ejemplo con números inventados para mostrar la lectura:** el martes había 12 yogures de gulupa; entraron 24 el jueves; se registró 1 merma; el domingo hay 9. Salieron 12 + 24 − 1 − 9 = 26. Loggro reporta 22 ventas y un stock de 14. Resultado: 4 ventas sin registrar y un error de stock de Loggro de +5 unidades.

## 5. Seguimiento semanal y expediente de evidencia

Una diferencia aislada se explica como descuido. Un expediente de tres semanas con el mismo patrón demuestra un problema del sistema.

**Cada domingo al cierre:**

- [ ] Cuadre de lácteos, cervezas y hojaldres con los reportes de Loggro de la semana.
- [ ] Exportar el CSV del cuadre (Cuadre → historial → Exportar CSV).
- [ ] Exportar el stock actual y los movimientos (Más → Exportar).
- [ ] Guardar copia de seguridad.
- [ ] Guardar captura o PDF de los dos reportes de Loggro usados.
- [ ] Anotar en una línea qué productos mostraron diferencias y la causa probable.

**Carpeta del expediente** (en Drive o en el teléfono): una subcarpeta por semana con los tres CSV, las capturas de Loggro y la nota. Después de tres semanas, el expediente contiene la tabla que se presenta al dueño:

| Semana | Productos auditados | Ventas sin registrar (und) | Error de stock Loggro (und) | Diferencia valorizada ($) | Causa probable |
| --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  |
| 2 |  |  |  |  |  |
| 3 |  |  |  |  |  |

**Antes de culpar al sistema, descarta tres causas propias:** entradas que no se registraron en la app, conteos hechos con el café abierto y productos sin receta o con código duplicado en Loggro. Si después de corregirlas la diferencia persiste, es del sistema.

## 6. Solicitud formal al dueño

Presenta la solicitud solo después de tres semanas de expediente y de haber descartado las causas propias de la sección 5. Pide primero una prueba de 30 días, no un cambio inmediato: es más fácil de aprobar y protege al café si la alternativa falla.

Plantilla para enviar por correo o WhatsApp, o imprimir. Reemplaza lo que está entre corchetes con los datos del expediente.

> **Asunto:** Propuesta para mejorar el control de inventario y ventas de Café Capiro
>
> Buenos días, [nombre del dueño].
>
> Durante las últimas tres semanas llevé un control de inventario independiente con conteos físicos de [número] productos de unidad cerrada (lácteos, cervezas y hojaldres), comparados cada domingo con los reportes de Loggro Restobar.
>
> **Lo que encontré:**
>
> - Loggro registró [número] unidades vendidas menos de las que salieron realmente, equivalentes a $[valor] a costo.
> - El stock que muestra Loggro difiere del conteo físico en [número] unidades en promedio por semana.
> - Los descuentos se aplican de forma incorrecta en [describir casos con fecha].
> - Ya verifiqué que no se debe a entradas sin registrar ni a recetas mal configuradas: [lo que revisaste].
>
> Adjunto los CSV de cada cuadre y las capturas de los reportes de Loggro.
>
> **Lo que propongo:**
>
> 1. Probar durante 30 días un sistema alternativo en paralelo con Loggro, sin cancelar el contrato actual.
> 2. Medir en esa prueba las mismas diferencias con el mismo método de conteo.
> 3. Cambiar solo si la alternativa reduce las diferencias y cuesta igual o menos que Loggro.
>
> Yo me encargo de configurar el catálogo, las recetas y de llevar la medición, en horario de trabajo. La decisión final y el contrato quedan en tus manos.
>
> Quedo atento para mostrarte los datos en la app cuando te quede bien.
>
> [Tu nombre] — Barista, Café Capiro

**Cómo presentarla:** diez minutos, con el teléfono en la mano. Muestra el historial de cuadres, abre un cuadre con diferencias y explica un solo producto de principio a fin. Cierra con la propuesta de prueba, no con la crítica a Loggro.

## 7. Alternativas de POS económicas

Siigo POS GastroBar PRO y Alegra POS son las dos alternativas que vale la pena probar: cuestan menos que Loggro Restobar según los precios publicados y son marcas colombianas establecidas. Ninguna está comprobada como más confiable para este café; eso lo decide la prueba de 30 días.

| Sistema | Precio publicado | Inventario por receta | Facturación electrónica | Punto a verificar | Fuente |
| --- | --- | --- | --- | --- | --- |
| Loggro Restobar (actual) | Cerca de $108.990/mes | Sí, según su ficha de app | Sí, integrada | Es el sistema que se está auditando | [Klikit, jun. 2026](https://klikit.io/en/learn/best-restaurant-pos-colombia-2026) |
| Siigo POS GastroBar PRO | $74.995/mes con pago anual ($899.940 al año, descuento de cliente nuevo) | Sí: descuenta ingredientes de cada venta; combos y recetas | Documentos ilimitados desde Siigo nube; la página indica que no incluye el documento equivalente electrónico de máquina POS | Confirmar con Siigo cómo se factura en caja; precio sube al renovar | [Siigo](https://www.siigo.com/sistema-pos/restaurantes) |
| Alegra POS (plan Emprendedor) | $74.900/mes; 25 % menos con pago anual | No confirmado en la fuente | Emite documento equivalente electrónico POS | Preguntar si maneja recetas y mesas para cafetería | [Alegra, jul. 2026](https://blog.alegra.com/colombia/alegra-vs-loggro-colombia/) |
| WARO | Cerca de $9.000/mes | No confirmado | En desarrollo | Marca nueva; sin facturación electrónica lista, no sirve todavía | [Klikit, jun. 2026](https://klikit.io/en/learn/best-restaurant-pos-colombia-2026) |

Los precios cambian y algunos dependen de promociones; cotiza directamente antes de presentar la propuesta.

**Criterios de la prueba, en orden de importancia:**

1. **Inventario por receta exacto:** vende 10 capuchinos de prueba y verifica que descuente 120 g de café (12 g × 10) y la leche de la ficha C-003.
2. **Descuentos correctos:** aplica un combo y un descuento manual y revisa que el reporte cuadre al peso.
3. **Facturación electrónica DIAN completa en caja**, incluido el documento equivalente POS.
4. **Pago con QR y efectivo**, que es como se cobra hoy en la barra.
5. **Reporte de ventas por producto y de inventario exportables** a Excel.
6. **Funciona desde el teléfono** si se cae el computador de caja.
7. **Costo total anual**, incluida la renovación sin descuento.

**Opción cero, sin costo:** antes de cambiar, pide revisar con soporte de Loggro las recetas y descuentos configurados. Si el expediente muestra que el problema era de configuración, corregirla es más barato que migrar. Si persiste después de corregirla, la propuesta de cambio queda mucho más fuerte.

## 8. Plan de migración sin cerrar el café

La migración se hace en cuatro fases y Loggro sigue funcionando hasta que la alternativa pase la prueba. El café nunca queda sin sistema de cobro.

1. **Semanas 1 a 3, expediente:** cuadres semanales con la app, descarte de causas propias y revisión de configuración con soporte de Loggro.
2. **Semana 4, aprobación:** presentar la solicitud de la sección 6 y elegir una alternativa para probar.
3. **Semanas 5 a 8, prueba en paralelo:** cargar en el sistema nuevo el catálogo (el CSV de stock de la app sirve de base) y las recetas del libro maestro. Registrar en él una muestra de ventas (por ejemplo, todas las de la tarde) y cuadrar cada domingo con el mismo método.
4. **Semana 9, decisión:** comparar las diferencias de ambos sistemas en la misma tabla. Si la alternativa gana, migrar el primer martes del mes (día de surtido, después del descanso del lunes), con conteo físico completo como inventario inicial del sistema nuevo.

**Lo que no cambia con la migración:** la app de inventario sigue siendo el auditor independiente. Ningún sistema de ventas se audita a sí mismo.

## Fuentes

- [Repositorio IventarioVS en GitHub](https://github.com/BarmanPB74/IventarioVS)
- [Klikit: mejores POS para restaurantes en Colombia 2026](https://klikit.io/en/learn/best-restaurant-pos-colombia-2026)
- [Siigo POS para restaurantes](https://www.siigo.com/sistema-pos/restaurantes)
- [Alegra vs Loggro (blog de Alegra, favorece a Alegra)](https://blog.alegra.com/colombia/alegra-vs-loggro-colombia/)
- [Loggro Restobar en App Store](https://apps.apple.com/ca/app/loggro-restobar/id6480476721)
- Café Capiro, *Libro maestro de recetas y procedimientos*, edición 1.0 (documento interno, no incluido en el repositorio).

## Anexo: pantalla Combos (versión 0.2)

La pestaña **Combos** mide qué promoción funciona. Trae 9 combos de la carta cargados e inactivos.

| Paso | Dónde | Qué haces |
| --- | --- | --- |
| 1. Activar | Combos → toca un combo → **Activar prueba** | La prueba arranca hoy; la semana base son los 7 días anteriores |
| 2. Revisar | **Editar** | Precio, productos que rota y, si ya la conoces por Loggro, la semana base |
| 3. Registrar | **Combos vendidos hoy** | Suma con + cada combo vendido, o copia al cierre el número del reporte de Loggro |
| 4. Ticket | **Ticket promedio de hoy** | Ventas totales y número de cuentas de Loggro al cierre |
| 5. Decidir | Ficha del combo | Después de 4 semanas completas, la app propone mantener, ajustar o retirar |

**Regla de decisión:** se compara el promedio semanal de las semanas completas con la semana base en tres números: combos vendidos (debe subir), merma valorizada de sus productos rotativos (debe bajar) y ticket promedio (debe subir). Mejora en 2 o 3 → mantener; en 1 → ajustar; en 0 → retirar. Antes de la cuarta semana la lectura es provisional.

La pantalla **Hoy** muestra el **Combo del día**: el combo activo que incluye el producto que vence primero. Mantén máximo 4 combos activos; la app avisa si pasas de ese número. Las fichas se exportan en **Más → Fichas de combos (CSV)**.
