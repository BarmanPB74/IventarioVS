# Sistema de crecimiento Café Capiro

12 de octubre de 2026 · Pablo, barista de Café Capiro

## 1. Decisión para mañana martes

Empieza mañana con la app **Inventario Capiro**, que ya está publicada y cargada con los 91 productos del libro maestro. Obsidian queda como bitácora y archivo de reflexión, no como sistema de inventario.

| Criterio | App Inventario Capiro | Plantillas en Obsidian |
| --- | --- | --- |
| Listo para mañana | Sí, en el teléfono | Hay que crear plantillas y carpetas |
| Suma stock automáticamente | Sí: último conteo + entradas − salidas | No; Dataview ayuda pero exige escribir consultas |
| Lotes y vencimientos | Calcula qué sacar primero | Manual, nota por nota |
| Cuadre contra Loggro | Calcula ventas reales y error de Loggro | Tabla manual, fácil de equivocarse |
| Evidencia para el dueño | Exporta CSV para Excel o Sheets | Exportar Markdown, poco legible para terceros |
| Funciona sin internet | Sí, en el APK | Sí |
| Datos en la nube | En la versión de Claude; en el APK, con copia de seguridad | Solo si sincronizas el vault |

**Arranque del martes 13 de octubre (90 minutos, antes de abrir o durante la primera hora tranquila):**

1. **Configura 15 productos, no 91.** En Stock, abre los productos P1 a P4 (lácteos, cervezas, hojaldres, almojábana) y llena costo unitario, mínimo e ideal. El resto se configura durante la semana.
2. **Haz el conteo inicial.** En Cuadre, cuenta físicamente lácteos, cervezas y hojaldres. Ese primer cuadre es tu inventario inicial: todo lo demás se mide contra él.
3. **Saca el reporte de inventario de Loggro el mismo día** y anota su stock al lado de tu conteo. Esa diferencia es la primera evidencia.
4. **Desde ese momento, toda entrada lleva lote y vencimiento**, y toda pérdida se registra como merma en el momento.
5. **Al cierre del domingo**, segundo cuadre de las mismas categorías con el reporte de ventas de Loggro de la semana.

Con dos cuadres y las entradas de la semana, la app ya puede decir cuántas unidades salieron de verdad y cuántas registró Loggro.

## 2. El inventario como herramienta, no como registro

Un inventario sirve cuando responde tres preguntas cada día: qué pedir, qué vender primero y cuánto dinero se está perdiendo. Si solo anota cantidades, es papeleo.

| Número | Cómo se calcula | Qué decisión toma |
| --- | --- | --- |
| Stock mínimo | Venta diaria promedio × días que tarda el proveedor + 1 día de colchón | Cuándo pedir |
| Stock ideal | Venta promedio de jueves a domingo + mínimo | Cuánto pedir para el pico del fin de semana |
| Pedido sugerido | Ideal − stock actual | La lista del martes |
| Salida real | Conteo anterior + entradas − mermas − consumo − conteo actual | Cuánto se vendió de verdad |
| Merma % | Valor de merma ÷ valor de compras del periodo | Si un producto se pide de más o se cuida mal |
| Rotación (días) | Stock promedio ÷ salida diaria | Cuánto tiempo duerme el dinero en la nevera |
| Valor del inventario | Stock × costo unitario | Capital inmovilizado |

**Cómo leerlos en la práctica:**

- Un lácteo con rotación mayor que su vida útil se va a vencer. Baja el ideal o súbelo en la recomendación del día.
- Merma por encima del 3 % del costo en una categoría indica pedido excesivo o mala rotación en nevera. Úsalo como meta inicial y ajústalo con tus propios datos después de un mes.
- Si la salida real de un producto supera lo que Loggro reporta vendido, hay ventas no registradas, consumo sin anotar o pérdida.

**Regla para el mínimo y el ideal sin historia todavía:** durante las primeras dos semanas usa tu estimación de barista. Después del segundo domingo, reemplázala por la salida real que calcula la app.

## 3. Cómo demostrar que Loggro no cuadra

La prueba no necesita que registres cada venta a mano. Basta con conteos físicos fechados y entradas anotadas: con eso la salida real se calcula sola y se compara con lo que Loggro dice.

```
Salida real = Conteo anterior + Entradas − Mermas − Consumo interno − Conteo actual
```

La app muestra dos diferencias por producto en cada cuadre:

| Diferencia | Fórmula | Qué significa si no es cero |
| --- | --- | --- |
| Ventas sin registrar | Salida real − ventas que reporta Loggro | Positiva: salieron más unidades de las que Loggro cobró o descontó. Negativa: Loggro descontó de más (por ejemplo, recetas mal configuradas o un producto vendido con otro código) |
| Error de stock Loggro | Stock que muestra Loggro − conteo físico | Loggro cree que hay más o menos de lo que hay en la nevera |

**Protocolo para que la evidencia sea aceptada:**

1. Mismo momento: el conteo físico y el reporte de Loggro se toman en la misma hora, antes de abrir o después de cerrar.
2. Mismo periodo: las ventas de Loggro se filtran exactamente entre la fecha del conteo anterior y la del actual.
3. Mismos productos: empieza por 10 a 15 productos de unidad cerrada (cervezas, yogures, quesos, hojaldres). Son imposibles de discutir porque no dependen de recetas.
4. Tres semanas seguidas: un error aislado se explica como descuido; el mismo patrón tres domingos seguidos es un problema del sistema.
5. Separa las causas: revisa en Loggro si los productos con diferencia tienen receta asociada, descuentos manuales o códigos duplicados. Esos tres puntos explican la mayoría de descuadres en sistemas POS con inventario por receta.
6. Presenta el CSV del cuadre y una sola frase de conclusión por producto, sin acusar a nadie.

Loggro anuncia control de recetas por producto para descontar inventario del menú ([App Store](https://apps.apple.com/ca/app/loggro-restobar/id6480476721)). Si un producto preparado tiene la receta incompleta o el gramaje distinto al libro maestro, Loggro descontará mal aunque la venta se haya registrado bien. Compara cada receta de Loggro con las fichas C-001 a C-023 del libro maestro.

## 4. Rotación profesional: PEPS y FEFO

Para perecederos, la regla correcta es FEFO: sale primero lo que vence primero, aunque haya llegado después. PEPS (primero en entrar, primero en salir) es el caso normal cuando todos los lotes tienen la misma vida útil. El libro maestro ya exige PEPS en B-011 y B-013; FEFO lo refina.

| Momento | Acción | Control en la app |
| --- | --- | --- |
| Recepción | Revisar sello, fecha y temperatura. Rechazar lo que llega con menos de la mitad de su vida útil, si el proveedor lo permite | Entrada con lote y vencimiento |
| Almacenamiento | Lo nuevo va atrás o abajo; lo que vence antes queda al frente y a la altura de los ojos | Hoy → Sacar primero |
| Nevera | 2 a 5 °C según B-011. Termómetro visible y lectura anotada al abrir y cerrar | Nota en el movimiento si hay falla |
| Apertura | Revisar lo que vence en 2 días o menos | Alertas rojas en Hoy |
| Servicio | Recomendar primero el producto que vence, si encaja con lo que busca el cliente (regla de la tesis CAPIRO) | Prioridad P1 a P4 |
| Vencimiento | Retirar el mismo día y registrarlo como merma con motivo | Merma → Vencido |

**Escalera de salida para un lácteo que vence pronto** (de menor a mayor pérdida de margen):

1. Recomendarlo en la ruta de proteína o postre del día (sección 9 de la tesis).
2. Incluirlo en el combo del día (sección 7 de este documento).
3. Degustación pequeña en mesa para clientes recurrentes, registrada como merma de degustación.
4. Si vence mañana y no salió: retirar, registrar y reducir el ideal de ese producto la semana siguiente.

Nunca bajes el precio de un producto a punto de vencer a la vista de todos: entrena al cliente a esperar descuentos. Es mejor moverlo dentro de un combo, donde el valor percibido se mantiene.

## 5. Mise en place que se conserva y rota

El mise en place se controla con tres herramientas: una etiqueta en cada envase, un nivel par por preparación y un registro de lo que se bota. Sin etiqueta no hay rotación posible.

**Etiqueta obligatoria (cinta de enmascarar y marcador sirven):** nombre de la preparación · fecha y hora de elaboración · fecha de descarte · iniciales.

| Preparación (libro maestro) | Lote estándar | Descarte sugerido | Nivel par sugerido |
| --- | --- | --- | --- |
| B-001 Almíbar simple | 500 g azúcar + 500 ml agua | Refrigerado, máximo 14 días | El que cubra 7 días de chocolates |
| B-002 Cold brew listo | 70 g café + 1.000 ml agua, 16 h | Refrigerado, máximo 5 días desde el filtrado | 1 lote los martes y 1 los jueves |
| B-004 Zumo de naranja | 60 ml por servicio | No se guarda (lo dice el libro) | Naranjas enteras, no zumo |
| B-006 Porciones de fruta | 45 g fresa + 45 g mora / 90 g maracuyá | Fruta picada: el mismo día | Porcionar solo lo del turno |
| B-007 Siropes abiertos | Botella comercial | Según etiqueta del fabricante una vez abierto | 1 abierta + 1 cerrada por sabor |
| B-003 Leche | Envase comercial | Abierta: según etiqueta, refrigerada | Nunca dos abiertas del mismo tipo |
| Café en grano de barra | Bolsa abierta | Usar dentro de 30 días desde tostión (control B-014) | Solo una bolsa abierta en tolva |

Los tiempos de descarte son estándar interno sugerido, conservador, para validar con el dueño. Si el envase del proveedor dice menos, gana la etiqueta, como establece CE-012.

**Rutina de mise en place:**

1. Apertura: revisa etiquetas, bota lo vencido y regístralo como merma con motivo «Preparación fallida» o «Vencido».
2. Calcula cuánto preparar: nivel par − lo que queda. Prepara solo esa diferencia.
3. Lo recién preparado va detrás de lo anterior en la nevera.
4. Registra en la app la leche, café y fruta que se usan para preparar como **Consumo**, no como venta. Así el cuadre separa uso interno de pérdida.
5. Cierre: anota cuánto se botó. Si una preparación se bota tres días seguidos, baja su nivel par.

## 6. Rutina diaria y semanal

La rutina sigue el ciclo semanal que ya describe la tesis: surtido el martes, pico de jueves a sábado, máxima salida el domingo y descanso el lunes. La app muestra la misión de cada día en la pantalla Hoy.

| Día | Inventario | Mise en place | Ventas |
| --- | --- | --- | --- |
| Martes | Cuadre completo P1–P4 + reporte Loggro. Pedido sugerido hasta el ideal | Cold brew lote 1, almíbar | Combo del día con lo que quedó del domingo |
| Miércoles | Cuadre de lácteos | Revisar etiquetas | Probar argumentos de venta (tesis, sección 9) |
| Jueves | Recibir pedidos con lote y vencimiento | Cold brew lote 2 | Activar combos de fin de semana |
| Viernes | Revisar vencimientos a 2 días | Porciones de fruta por turno | Combos + recomendación P1 |
| Sábado | Mermas en el momento | Igual que viernes | Mayor flujo: MESA-4 activo |
| Domingo | Cierre: cuadre de perecederos + merma de la semana | Botar y registrar lo que no llega al martes | Máxima salida compatible |
| Lunes | Descanso | — | — |

**Cinco minutos diarios, siempre los mismos:**

- Al abrir: Hoy → Sacar primero. Mueve al frente lo que está en rojo.
- Durante el turno: cada entrada y cada merma se registran al momento (20 segundos cada una).
- Al cerrar: cuadre de una sola categoría, rotando por día. Así nunca acumulas un conteo de dos horas.

## 7. Combos y promociones

Cada combo junta una bebida de café, que tiene costo bajo y margen alto, con uno de los productos prioritarios que necesitan rotar. El café financia el pequeño descuento y el combo mueve el inventario sin rebajar precios a la vista.

| Combo | Contenido (fichas del libro maestro) | Momento | Rota | Frase de venta (método CAPIRO) |
| --- | --- | --- | --- | --- |
| Mañana de vivero | Tinto de goteo (C-011) o americano (C-008) + almojábana (A-012) | Apertura a 11 a. m. | P4 | «Algo pequeño y conocido para empezar el recorrido» |
| Pausa con proteína | Capuchino (C-003) o latte (C-009) + hojaldre salado tibio (A-001, A-003 o A-006) | Media mañana y tarde | P3 | «Se lo sirvo tibio; tarda unos cuatro minutos» |
| Ligero y fresco | Yogur griego personal (L-013 o L-014) + infusión Naturio (I-001 a I-004) | Clientes que buscan algo liviano | P1 | «Proteína sin ocupar el espacio del almuerzo» |
| Dulce de la tierra | Tinto de goteo + Miguelucho (L-008) o arroz con leche (L-007) | Tarde | P1 | «Un dulce tradicional de leche y panela que va muy bien con café negro» |
| Fresco y salado | Cerveza (E-005 a E-010) + palito de queso (A-005) o pastel de pollo (A-003) | Fines de semana, mediodía | P2 + P3 | «Algo frío, menos dulce, con un salado» |
| Tabla Capiro para dos | 2 copas de vino tinto o 1 botella + queso madurado El Tabor (L-001 a L-005) | Parejas, tarde | P1 | «Una porción generosa para compartir con el vino» |
| Volcán para compartir | Volcán con helado (D-002) + 2 bebidas calientes | Grupos y familias | Postre | «Sale en 13 minutos; se lo traigo después de las bebidas» |
| Mesa de cuatro | 4 bebidas de la carta + 2 hojaldres + 1 torta (T-001 a T-004) | Familias de fin de semana | P3 + tortas | Se ofrece al aplicar MESA-4 en mesas grandes |
| Llévate el origen | Bebida consumida + bolsa de 250 g (R-003 o R-004) | Al pagar | Café empacado | «El mismo café de La Ceja que acaba de tomar, para su casa» |
| Combo del día | Una bebida + el lácteo o hojaldre que vence primero | Martes y domingo | El que la app marca en rojo | Se presenta como recomendación, no como liquidación |

**Cómo fijar el precio de cada combo:**

```
Precio combo = (precio bebida + precio acompañamiento) × 0,90
```

Luego verifica que el costo de los ingredientes no pase del 35 % del precio del combo. Si pasa, sube el factor a 0,93 o cambia la bebida por una de menor costo, como el tinto de goteo. Ejemplo con precios hipotéticos: bebida de $8.000 + hojaldre de $9.000 = $17.000 × 0,90 = $15.300, redondeado a $15.500.

**Reglas para que los combos vendan y fidelicen:**

- Máximo cuatro combos visibles a la vez; el resto se ofrece de palabra según la ruta de la conversación. La tesis ya documenta por qué menos opciones facilitan decidir.
- El combo se ofrece en el paso **Integrar** del método CAPIRO, después de entender qué busca el cliente: «¿Le agrego un hojaldre tibio? En combo le sale mejor».
- Un tablero pequeño en la entrada del vivero con un solo combo del día hace el trabajo que hoy no hace el aviso de pedido en caja.
- Mide cada combo durante cuatro semanas: unidades vendidas, merma de su producto rotativo y ticket promedio. Retira el que no mueva nada.
- Pide al dueño crear cada combo como producto en Loggro con su receta. Si no, el inventario de Loggro se descuadra aún más.

## 8. Más clientes desde el vivero

La mayor fuente de clientes nuevos ya camina a pocos metros: la gente que visita el vivero. En los garden centres del Reino Unido, la comida llega a representar hasta el 35 % de la facturación y convierte el lugar en un destino durante todo el año ([Glee 2024](https://www.gleebirmingham.com/news-and-views/maximising-success-cafes-food-retail-garden-centres-speaker-spotlight-glee-2024-8qua)). Un centro pequeño en Londres reportó 67 % más ventas de café en su primer año apoyándose en boletín mensual, consejos de temporada y volantes locales ([HortWeek](https://www.hortweek.com/garden-centre-outlet-year-boutique-winner-west-six-garden-centre/retail/article/1426965)).

| Acción | Costo | Cuándo empezar | Cómo se mide |
| --- | --- | --- | --- |
| Tablero con el combo del día en la entrada y en la caja del vivero | Un tablero y tiza | Semana 1 | Combos vendidos por día |
| Acuerdo con el vivero: quien compra plantas recibe un beneficio en el café (por ejemplo, la adición sin costo) presentando la factura | Margen de una adición | Semana 2, con aprobación del dueño | Facturas del vivero recibidas |
| Perfil de Google del café con fotos reales, horario, carta y respuesta a cada reseña | Gratis | Semana 1 | Reseñas nuevas por mes |
| WhatsApp Business con catálogo y estado diario del combo | Gratis | Semana 2 | Mensajes y pedidos por semana |
| Bolsas de Café Capiro en la caja del vivero, con la historia de Finca El Tesoro | Inventario ya existente | Semana 3 | Bolsas vendidas fuera del café |
| Taller mensual en alianza con el vivero (suculentas, huerta en casa) con bebida incluida | Materiales del vivero + bebidas | Mes 2 | Cupos vendidos y regreso de asistentes |
| Cata del café de La Ceja con la historia de Otoniel Ramírez | 1 bolsa de 500 g | Mes 2 | Bolsas vendidas después de la cata |
| Tarde de vino y queso El Tabor, sábado al atardecer | Inventario P1 existente | Mes 2 | Botellas y tablas vendidas |
| Paquete para grupos que visitan los cultivos de flores de la zona | Una hoja con menú fijo | Mes 3 | Grupos atendidos |

Las parcelaciones y casas campestres del sector El Capiro son familias que regresan cada fin de semana. Son el público natural para la tarjeta de fidelidad y para la bolsa de café para la casa.

Todo lo que involucra al vivero requiere aprobación del dueño. Llévalo como propuesta con una métrica de éxito y un plazo de prueba de cuatro semanas.

## 9. Fidelización sin cargar la operación

Usa una tarjeta de sellos de papel: no exige base de datos, respeta la decisión de la tesis de no registrar clientes por ahora y se entrega en tres segundos al pagar.

| Elemento | Diseño propuesto | Por qué |
| --- | --- | --- |
| Sellos para el premio | 7, con el primero ya sellado | Para clientes que vienen una vez al mes se recomienda premiar cada 6 a 10 visitas, y entregar la tarjeta con sellos ya puestos aumenta la participación ([Booksy](https://biz.booksy.com/es-es/blog/como-crear-un-programa-de-fidelizacion)) |
| Qué cuenta como sello | Un combo, o una bebida con acompañamiento | Empuja el ticket promedio y la rotación, no solo la visita |
| Premio | Una bebida de la carta o el combo «Mañana de vivero» | Costo bajo, valor percibido alto |
| Doble sello | Martes y miércoles | Lleva clientes a los días de menor flujo |
| Vigencia | 6 meses | Mantiene la frecuencia sin volver el programa una deuda eterna |
| Diseño | Logo de montaña de Café Capiro, sin datos personales | Coherente con la identidad del libro maestro |

Cuando el programa supere unas 100 tarjetas activas, evalúa pasarlo a una tarjeta digital en Google Wallet. Un café en París registró 20 % más visitas entre los titulares de su tarjeta digital ([Brevo](https://www.brevo.com/es/success-stories/cafe-kitsune/)), pero el papel es lo correcto para empezar con el volumen actual.

El sello también es el momento del paso **Ofrecer un motivo para volver** del método CAPIRO: «Con este sello le falta poco; la próxima vez pruebe el tinto de goteo».

## 10. Contaduría para financiar una nueva sede

Una segunda sede se financia con utilidad acumulada y demostrable, no solo con más ventas. El inventario bien llevado es lo que permite calcular esa utilidad con números reales cada mes.

**Herramientas, cada una con un solo trabajo:**

| Herramienta | Trabajo | Ya existe |
| --- | --- | --- |
| Loggro Restobar | Ventas, facturación electrónica, cierres de caja, reporte de ventas por producto | Sí |
| App Inventario Capiro | Conteos, entradas, mermas, valor del inventario, evidencia de descuadres | Sí |
| Hoja de cálculo mensual (Google Sheets o Excel) | Estado de resultados, punto de equilibrio y fondo de expansión | Por crear |
| Software contable del contador | Impuestos y contabilidad formal | Depende del dueño |
| Obsidian | Bitácora de decisiones, aprendizajes y pruebas de combos | Sí |

**El cálculo que conecta inventario y contabilidad:**

```
Costo de ventas = Inventario inicial + Compras del mes − Inventario final
```

El inventario inicial y final salen del valor de stock de la app el primer y último día del mes. Sin conteos valorizados, el costo de ventas es una adivinanza y la utilidad también.

**Estado de resultados mensual en una hoja:**

| Línea | De dónde sale |
| --- | --- |
| Ventas netas | Loggro, reporte mensual |
| − Costo de ventas | Fórmula de arriba |
| = Utilidad bruta | Meta: costo de ventas ≤ 35 % de ventas |
| − Gastos fijos | Arriendo o participación con el vivero, nómina, servicios, Loggro, insumos desechables |
| = Utilidad operativa | Lo que realmente deja el café |
| − Aporte al fondo de nueva sede | Porcentaje fijo de la utilidad operativa, a cuenta separada |

**Punto de equilibrio:** gastos fijos del mes ÷ (1 − costo de ventas %). Si los gastos fijos fueran $6.000.000 y el costo de ventas 35 %, el café necesitaría vender $9.230.000 al mes solo para no perder (cifras de ejemplo, no del café).

**Cuánto necesita una nueva sede.** Calcúlalo con estas cinco líneas, con cotizaciones reales: equipo de barra (máquina, molino, nevera, horno), adecuación del local, inventario inicial, permisos y apertura, y capital de trabajo equivalente a tres meses de gastos fijos. Divide el total entre el aporte mensual al fondo: ese es el número de meses hasta poder abrir sin deuda.

**Financiación si el fondo no alcanza.** Bancóldex presta a microempresas a través de bancos, cooperativas y microfinancieras ([Bancóldex](https://www.bancoldex.com/sites/default/files/bancoldex_framework_bono_social_actualizado_final.pdf)). Su línea Cultura para la Sostenibilidad 2026, orientada a industrias creativas y turismo, permite hasta $300 millones por microempresa ([circular agosto 2026](https://www.bancoldex.com/sites/default/files/2026-08/Modificacio%CC%81n%201%20-%20Li%CC%81nea%20de%20cre%CC%81dito%20cultura%20para%20la%20sostenibilidad.pdf)). La elegibilidad de un café la decide el intermediario; los intermediarios suelen pedir estados financieros e historial de ventas ordenados, que es justo lo que este sistema produce.

**Tu parte como barista.** Propón al dueño un bono atado a resultados que la app mide: reducción de merma, unidades vendidas en combos y diferencias de inventario corregidas. Los datos de tres meses son tu argumento para un aumento fijo.

## 11. Hoja de ruta de 90 días

La meta de los primeros 90 días es tener tres meses de datos limpios: inventario cuadrado, combos medidos y un estado de resultados mensual. Con eso se negocia el aumento y se planea la nueva sede.

1. **Semanas 1 y 2 (13 al 26 de octubre):** conteo inicial, configuración de P1–P4, entradas con lote y vencimiento, primeros dos cuadres contra Loggro, tablero con un combo del día, perfil de Google.
2. **Semanas 3 y 4 (27 de octubre al 9 de noviembre):** tercer cuadre y primer informe al dueño con el CSV. Lanzar 4 combos y la tarjeta de sellos. Proponer el acuerdo con el vivero.
3. **Mes 2 (noviembre):** ajustar mínimos e ideales con la salida real. Primer estado de resultados con costo de ventas calculado. Primer taller o cata. Retirar el combo que no rote.
4. **Mes 3 (diciembre):** temporada alta de fin de año. Combos de regalo con bolsas de café. Segundo estado de resultados, definición del aporte al fondo de nueva sede y propuesta de bono por resultados.

**Indicadores que revisas cada domingo:**

| Indicador | Fuente | Meta inicial |
| --- | --- | --- |
| Merma valorizada de la semana | App, pantalla Hoy | Bajar cada semana durante el primer mes |
| Diferencia de inventario contra Loggro | App, cuadre | Documentada en 3 domingos seguidos |
| Combos vendidos | Loggro, si se crean como productos | Al menos uno de cada cuatro pedidos con alimento |
| Ticket promedio | Loggro | Subir frente a la semana base |
| Productos vencidos retirados | App, merma «Vencido» | Cero lácteos vencidos en nevera |
| Tarjetas de sellos entregadas y canjeadas | Conteo manual | Ver cuántas vuelven en 30 días |
| Reseñas en Google | Perfil de Google | Una nueva por semana |

Las metas son puntos de partida. Después de cuatro semanas, reemplázalas por tus propios promedios más un 10 %.

## Fuentes

- Café Capiro, *Libro maestro de recetas y procedimientos*, edición 1.0, 14 de agosto de 2026 (documento interno, no incluido en el repositorio).
- Pablo, *Tesis aplicada de servicio: Método CAPIRO*, septiembre de 2026 (documento interno, no incluido en el repositorio).
- [Loggro Restobar en App Store](https://apps.apple.com/ca/app/loggro-restobar/id6480476721)
- [Glee 2024: cafés y venta de comida en garden centres](https://www.gleebirmingham.com/news-and-views/maximising-success-cafes-food-retail-garden-centres-speaker-spotlight-glee-2024-8qua)
- [HortWeek: West Six Garden Centre](https://www.hortweek.com/garden-centre-outlet-year-boutique-winner-west-six-garden-centre/retail/article/1426965)
- [Booksy: cómo crear un programa de fidelización con sellos](https://biz.booksy.com/es-es/blog/como-crear-un-programa-de-fidelizacion)
- [Brevo: caso Café Kitsuné](https://www.brevo.com/es/success-stories/cafe-kitsune/)
- [Bancóldex: marco del Bono Social y crédito a microempresas](https://www.bancoldex.com/sites/default/files/bancoldex_framework_bono_social_actualizado_final.pdf)
- [Bancóldex: modificación línea Cultura para la Sostenibilidad 2026](https://www.bancoldex.com/sites/default/files/2026-08/Modificacio%CC%81n%201%20-%20Li%CC%81nea%20de%20cre%CC%81dito%20cultura%20para%20la%20sostenibilidad.pdf)

Pendiente: precios de venta y costos de compra reales. Sin ellos, los precios de los combos y el punto de equilibrio quedan como fórmula.
