# Plan de uso y evolución de la app de inventario

12 de octubre de 2026 · Pablo, barista de Café Capiro

## Resumen

Uso una sola app con tres trabajos: contar lo que hay, decidir qué promocionar y medir qué vendió más. Crece por versiones pequeñas; cada una debe demostrar un resultado medible en el café antes de construir la siguiente.

| Trabajo | Pregunta que responde | Dónde vive hoy |
| --- | --- | --- |
| Inventario | ¿Qué hay, qué vence y cuánto salió de verdad? | App, pantallas Hoy, Mover y Cuadre |
| Promociones | ¿Qué combo empujo hoy y con qué producto? | Reglas de este documento + alertas de la app |
| Ventas | ¿Qué combo funcionó y cuánto dejó? | Reporte de Loggro + cuadre de la app; módulo propio desde la versión 0.2 |

El repositorio es [IventarioVS](https://github.com/BarmanPB74/IventarioVS); la app instalada se llama Inventario Capiro.

## Cómo la uso desde mañana

El seguimiento del inventario depende de cuatro hábitos fijos que toman unos 25 minutos al día en total. El detalle de cada pantalla está en el [Manual](02-manual-y-propuesta-pos.md).

| Momento | Acción en la app | Tiempo | Resultado |
| --- | --- | --- | --- |
| Apertura | Hoy → revisar «Sacar primero» y pedido sugerido | 3 min | Lo que vence va al frente y a la recomendación del día |
| Cada entrada | Mover → Entrada con lote, vencimiento y costo | 30 s por producto | Lotes trazables y costo actualizado |
| Cada pérdida | Mover → Merma con motivo | 20 s | Merma valorizada real, no estimada |
| Cierre | Cuadre de la categoría del día con el reporte de Loggro | 15 min | Salida real y error de Loggro por producto |
| Domingo | Cuadre completo P1–P4, exportar CSV y guardar copia | 30 min | Expediente semanal y respaldo |
| Martes | Pedido hasta el ideal con el pedido sugerido | 10 min | Compras ajustadas a la venta real |

**Primeras dos semanas:** configura costo, mínimo e ideal de los productos P1 a P4 y haz el conteo inicial. Sin esos datos, la app cuenta pero no aconseja.

## Cómo el inventario decide las promociones

La promoción del día no se escoge por intuición: sale de lo que la app muestra al abrir. Cada señal tiene una acción comercial definida.

| Señal en la app | Acción comercial | Combo que la ejecuta |
| --- | --- | --- |
| Un lácteo vence en 2 días o menos | Combo del día con ese producto; primera recomendación en la ruta de proteína o postre | Ligero y fresco, Dulce de la tierra o Tabla Capiro |
| Hojaldres con más stock del ideal el viernes | Ofrecerlos tibios con cada bebida con leche | Pausa con proteína |
| Cerveza con rotación lenta (stock alto dos semanas seguidas) | Incluirla en la ruta de bebidas frescas del fin de semana | Fresco y salado |
| Producto agotado dos martes seguidos | Subir su stock ideal; no promocionarlo hasta tener colchón | Ninguno |
| Merma alta de una categoría | Bajar el ideal y moverla en combo antes de que venza | El combo de esa categoría |
| Domingo al mediodía con perecederos que no llegan al martes | Máxima salida compatible, sin rebajar precios a la vista | Combo del día |

**Regla de prioridad:** si dos productos encajan igual con lo que pide el cliente, se recomienda primero el que la app marca en rojo. Si el producto prioritario no encaja, no se fuerza (criterio de la tesis CAPIRO).

## Cómo mido cada promoción

Cada combo se prueba cuatro semanas con una ficha y se conserva solo si mejora al menos dos de sus tres números frente a la semana base. Hasta la versión 0.2, los datos salen del reporte de Loggro y del cuadre de la app.

| Número | Cómo se obtiene hoy | Qué demuestra |
| --- | --- | --- |
| Combos vendidos por semana | Loggro, si el combo existe como producto | Si la gente lo elige |
| Merma del producto rotativo | App, merma de ese producto | Si el combo salva inventario |
| Ticket promedio | Loggro: ventas ÷ número de cuentas | Si el combo sube el gasto por cliente |

**Ficha de prueba por combo** (una fila por semana, en la carpeta del expediente):

| Semana | Combo | Vendidos | Merma del producto rotativo ($) | Ticket promedio ($) | Decisión |
| --- | --- | --- | --- | --- | --- |
| Base |  |  |  |  |  |
| 1 |  |  |  |  |  |
| 2 |  |  |  |  |  |
| 3 |  |  |  |  |  |
| 4 |  |  |  |  | Mantener, ajustar o retirar |

**Condición para medir bien:** cada combo debe crearse como producto en Loggro con su receta. Si se cobra como dos productos sueltos, no hay forma de contarlo.

## Hoja de ruta de versiones

Cada versión agrega una sola capacidad que se puede demostrar en el café, y solo se empieza cuando la anterior cumplió su condición de paso. Así la app avanza de registro a herramienta de ventas sin convertirse en una lista infinita de ideas.

| Versión | Qué agrega | Cómo genera ventas | Condición para pasar a la siguiente | Esfuerzo estimado |
| --- | --- | --- | --- | --- |
| **0.1 Control** (hoy) | Entradas, mermas, lotes FEFO, cuadre contra Loggro, respaldo | Reduce pérdida y señala qué empujar cada día | 3 domingos seguidos con cuadre y expediente | Hecho |
| **0.2 Promociones** | Catálogo de combos con su producto rotativo; registro diario de combos vendidos; ficha de prueba de 4 semanas dentro de la app | Mide qué combo funciona y retira el que no | Un combo con mejora en 2 de sus 3 números | Publicada el 12 de octubre de 2026 |
| **0.3 Costos y margen** | Recetas del libro maestro con gramajes; costo por bebida y por combo; margen por producto | Precios de combo con margen verificado; foco en lo que más deja | Costo de todas las bebidas de la carta cargado | Publicada el 12 de octubre de 2026 |
| **0.4 Pedido inteligente** | Pedido sugerido según salida real de 4 semanas; lista por proveedor para enviar por WhatsApp | Menos agotados en el pico de jueves a sábado | 4 semanas sin agotar un producto P1–P4 | Publicada el 13 de octubre de 2026 |
| **0.5 Importar Loggro** | Leer el reporte de ventas de Loggro en CSV para llenar el cuadre sin digitar | Ahorra 1 hora por semana que vuelve al servicio | Depende de que Loggro permita exportar; verificar antes de empezar | 1 semana |
| **0.6 Tablero para el dueño** | Resumen semanal: merma, diferencias, combos, ticket promedio y estado de resultados | Decisiones del dueño basadas en datos; base para pedir aumento o bono | Dueño revisando el tablero 4 semanas | 1 a 2 semanas |
| **1.0 Multi-dispositivo** | Sincronización en la nube entre teléfonos y respaldo automático | Permite que otra persona del turno registre; base para una segunda sede | Uso diario estable de 0.1 a 0.6 durante 3 meses | 3 a 4 semanas |
| **Después: BAR BOX** | Lo aprendido aquí pasa a BAR BOX: inventario, combos, costos y sugerencias de compra con IA | Producto vendible a otros cafés y bares | Café Capiro como caso demostrado con números reales | Proyecto propio |

**Cómo construyo cada versión** (ciclo explicar → construir → probar → mejorar):

1. Escribir en una línea qué problema del café resuelve y con qué número se medirá.
2. Construir la función en el mismo archivo de la app; el APK se compila solo al subirla al repositorio.
3. Probarla una semana en turno real.
4. Corregir lo que estorbó en el servicio y registrar el resultado en la bitácora de Obsidian.

Los esfuerzos son estimaciones de trabajo con ayuda de Claude en ratos libres; se ajustan después de la versión 0.2.

## Indicadores de éxito por fase

Una fase se considera exitosa por su número, no por las funciones construidas. Las metas son iniciales y se reemplazan por promedios reales después del primer mes.

| Fase | Indicador principal | Meta inicial | Fuente |
| --- | --- | --- | --- |
| 0.1 Control | Diferencia de inventario contra Loggro documentada | 3 semanas seguidas | Historial de cuadres |
| 0.1 Control | Merma valorizada semanal | Baja cada semana durante el primer mes | Pantalla Hoy |
| 0.2 Promociones | Combos vendidos por semana | Uno de cada cuatro pedidos con alimento | Módulo de combos |
| 0.3 Costos | Costo de ingredientes por combo | 35 % del precio o menos | Módulo de costos |
| 0.4 Pedido | Agotados de P1–P4 en el pico | Cero en 4 semanas | Cuadre y alertas |
| 0.6 Tablero | Ticket promedio | Sube frente a la semana base | Loggro y tablero |
| 1.0 Sedes | Meses de datos limpios acumulados | 6 meses, base razonable para mostrar a un banco o socio | Tablero |

## Límites y riesgos

| Riesgo | Efecto | Cómo lo manejo |
| --- | --- | --- |
| Datos solo en el teléfono (APK) | Si se pierde el teléfono, se pierde el historial | Copia de seguridad cada domingo en Drive; sincronización en la versión 1.0 |
| Disciplina de registro | Entradas o mermas sin anotar aparecen como ventas sin registrar | Registrar en el momento; descartar causas propias antes de culpar a Loggro |
| Soy empleado, no dueño | Combos, precios y cambios de POS requieren aprobación | Presentar cada cambio como prueba de 4 semanas con un número de éxito |
| Loggro puede no exportar CSV | La versión 0.5 no sería posible | Verificarlo antes de construirla; si no exporta, seguir digitando |
| Repositorio público | El nombre y la descripción del repositorio son visibles para cualquiera | Hacerlo privado o neutralizar la descripción antes de mostrarlo al dueño |
| Sin precios ni costos reales todavía | Márgenes y precios de combo quedan como fórmula | Cargar costos en la primera semana |
