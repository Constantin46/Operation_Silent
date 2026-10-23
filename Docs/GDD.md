# Operación Silencio: documento de diseño del juego

**Hito 1: concepto**  
**Estado del documento:** primera versión del diseño. Las decisiones y los valores propuestos podrán ajustarse durante el desarrollo.

## 1. Ficha del juego

| Dato | Información |
|---|---|
| Título provisional | Operación Silencio |
| Autor | Constantin |
| Género | Sigilo y resolución de situaciones sencillas |
| Dimensiones | 2D top-down |
| Plataforma | Windows |
| Motor | Unity 6 |
| Pipeline de renderizado | URP, utilizando la plantilla Universal 2D |
| Jugadores | Un jugador |
| Público objetivo | Público adolescente y adulto interesado en juegos de sigilo |
| Clasificación orientativa | PEGI 7 como referencia de diseño, pendiente de revisar según el contenido final. No es una clasificación oficial |
| Duración prevista | Aproximadamente 10 minutos para completar los tres niveles |
| Repositorio | https://github.com/Constantin46/Operation_Silent |
| Página de itch.io | Pendiente de crear para la publicación del juego |

La estética prevista será un estilo 2D sencillo, con personajes y objetos fáciles de distinguir. Los escenarios representarán diferentes zonas de una base. Se utilizará una paleta común y recursos con una escala similar para mantener la coherencia visual.

## 2. Concepto

### Resumen

Operación Silencio es un juego de sigilo con vista desde arriba en el que un personaje debe infiltrarse en una base, conseguir los objetos necesarios para avanzar y recuperar unos documentos. Para completar la misión tendrá que observar las patrullas, utilizar escondites y activar distracciones sin ser descubierto y antes de agotar el tiempo. Al repetir los niveles podrá mejorar sus récords, entrar en la tabla local de mejores tiempos y completar retos de rapidez y sigilo.

### Pilares de diseño

1. **Observar antes de actuar.** El jugador debe fijarse en las rutas y la orientación de los guardias para encontrar el momento adecuado para pasar.
2. **Utilizar el escenario.** Los escondites, las radios, las tarjetas y los interruptores permiten resolver los obstáculos.
3. **Detección comprensible.** Los campos de visión y una barra de detección ayudarán a entender cuándo existe peligro.
4. **Aprendizaje progresivo.** El primer nivel presenta las mecánicas y los siguientes las combinan con nuevos obstáculos.
5. **Mejora personal.** Repetir un nivel permite optimizar la ruta, mejorar el tiempo y completar retos de sigilo.

### Referencias

La principal referencia será **Metal Gear Solid**, especialmente la observación de las patrullas y el uso de ruidos para atraer la atención de los guardias.

Se tomará esa idea general de infiltración para desarrollar una propuesta pequeña, con escenarios y comportamientos sencillos.

### Qué lo hace diferente

El juego se centrará en resolver situaciones de sigilo mediante elementos colocados en el escenario. Cada radio estará relacionada con un guardia concreto y permitirá apartarlo temporalmente de su posición.

El jugador tendrá que combinar las distracciones con los escondites y las rutas disponibles para llegar al objetivo. La acción se desarrollará en tiempo real. La rejugabilidad se basará en mejorar los resultados en esos mismos escenarios: terminar más rápido, evitar cualquier sospecha y conseguir una puntuación mayor.

### Alcance previsto

El proyecto tendrá tres niveles cortos, cada uno en una escena de juego distinta. La primera versión se centrará en cuatro sistemas: esconderse, activar distracciones, conseguir objetos que permitan avanzar y utilizar interruptores.

El personaje no tendrá armas ni ataques. Los guardias seguirán rutas preparadas y las distracciones utilizarán puntos de investigación definidos de antemano.

Se añadirá una capa sencilla de rejugabilidad con un límite de tiempo por nivel, récords personales, una clasificación local, retos y estadísticas. Estos sistemas se incorporarán cuando las mecánicas de sigilo del prototipo sean estables y utilizarán los mismos tres niveles.

## 3. Historia y ambientación

### Premisa

La historia ocurre en una base ficticia donde se guardan unos documentos confidenciales. El protagonista recibe la misión de entrar, recuperarlos y alcanzar la salida sin ser descubierto.

Para acceder al centro de control deberá atravesar el patio exterior y un almacén de seguridad.

### Protagonista

El protagonista es un agente especializado en infiltración. Su objetivo es completar la misión utilizando la observación, los escondites y los dispositivos del escenario.

### Ambientación

La base estará formada por tres zonas:

- Un patio exterior con cajas, muros y una entrada vigilada.
- Un almacén con pasillos, estanterías y puertas de seguridad.
- Un centro de control donde se encuentran los documentos.

Los elementos importantes se distinguirán mediante su forma, color y una indicación de interacción cuando el personaje esté cerca.

### Cómo se contará la historia

Al comenzar aparecerá un texto breve explicando la misión. Cada nivel mostrará su objetivo y, al completar el último, una pantalla confirmará que los documentos se han recuperado.

La historia se contará mediante estos mensajes y el propio escenario.

## 4. Jugabilidad

### Objetivo

Completar los tres niveles sin ser descubierto y antes de agotar el tiempo de cada nivel. En los dos primeros será necesario conseguir una tarjeta y alcanzar la puerta de salida. En el tercero habrá que recuperar los documentos y llegar al punto de extracción.

Después de completar un nivel, el jugador podrá repetirlo para reducir su tiempo, aumentar su puntuación y conseguir los retos pendientes.

### Bucle de juego

El jugador repetirá estas acciones:

1. Observar la zona y los movimientos de los guardias.
2. Identificar una ruta hacia el objetivo.
3. Esperar, esconderse o activar una distracción.
4. Cruzar la zona vigilada.
5. Conseguir el objeto necesario y alcanzar la salida antes de que termine el tiempo.
6. Consultar el resultado y elegir entre continuar o repetir para mejorar la marca.

### Detección

Los guardias tendrán un campo de visión visible delante de ellos. Para detectar al personaje, este deberá encontrarse dentro de ese campo y no estar protegido por una pared u otro obstáculo sólido.

Cuando un guardia vea al personaje, se llenará una barra de detección. Como valor inicial, se propone un segundo de exposición continua para ser descubierto.

Si el personaje sale del campo de visión o se esconde antes de completar la barra, la detección se reiniciará. Mientras esté dentro de un escondite permanecerá inmóvil y no podrá ser detectado.

Estos valores se ajustarán después de probar el prototipo.

### Comportamiento de los guardias

Los guardias tendrán tres comportamientos básicos:

- **Vigilancia:** recorrer su ruta o permanecer en un puesto fijo.
- **Investigación:** desplazarse hasta un punto preparado cerca de una radio activada.
- **Regreso:** volver a su ruta o puesto después de investigar.

La detección completa del jugador provocará la derrota. Este comportamiento permite empezar con una IA sencilla.

### Condiciones de victoria y derrota

**Superación de un nivel:** conseguir el objeto requerido y entrar en la salida correspondiente antes de que el contador llegue a cero.

**Victoria final:** recuperar los documentos del tercer nivel y llegar al punto de extracción.

**Derrota:** completar la barra de detección de un guardia o de una cámara activa, o agotar el tiempo del nivel.

Tras perder, se podrá reiniciar el nivel actual o volver al menú principal. El reinicio restaurará los objetos, puertas, radios, guardias, cronómetro y datos del intento. Los récords, retos conseguidos y estadísticas acumuladas se conservarán.

### Progresión

| Nivel | Objetivo | Novedad respecto al anterior |
|---|---|---|
| 1. Patio exterior | Conseguir la tarjeta de entrada y alcanzar la puerta | Presenta una patrulla sencilla, los escondites y una radio |
| 2. Almacén de seguridad | Conseguir una segunda tarjeta y acceder al centro de control | Introduce un vigilante fijo y pasillos que obligan a combinar las mecánicas |
| 3. Centro de control | Recuperar los documentos y alcanzar la extracción | Introduce una cámara de vigilancia y un interruptor para desactivarla |

Cada nivel tendrá su propia distribución. La dificultad aumentará combinando los obstáculos y reduciendo los espacios seguros, manteniendo oportunidades para observar y planificar.

### Contrarreloj

Cada intento tendrá un cronómetro de tiempo transcurrido y un contador de tiempo restante. Como punto de partida se propone un límite de 180 segundos por nivel; se ajustará por separado para cada mapa después de las pruebas.

El tiempo empezará cuando el jugador pueda controlar al personaje. Se detendrá al completar el nivel y quedará congelado durante la pausa y en las pantallas de resultado. Llegar a cero provocará una derrota por tiempo.

### Récords y tabla de mejores tiempos

Se guardará el mejor tiempo personal y una tabla con los cinco mejores tiempos de cada nivel. La clasificación será local, almacenada en el mismo ordenador y conservada al cerrar y abrir el juego.

Solo se registrarán intentos completados correctamente. La tabla se ordenará de menor a mayor tiempo; en caso de empate, se utilizará la puntuación más alta. Se mostrarán posición, tiempo, puntuación y retos conseguidos. El cronómetro conservará suficiente precisión para mostrar centésimas.

Cada nivel tendrá su propia clasificación. El récord se actualizará únicamente cuando se consiga un tiempo menor; repetir un nivel con peor resultado no lo sustituirá.

### Retos de rejugabilidad

| Reto | Condición |
|---|---|
| Veloz | Completar el nivel dentro de su tiempo objetivo. Se propone inicialmente 120 segundos, ajustables por nivel |
| Fantasma | Completar el nivel sin que la barra de detección de ningún guardia o cámara llegue a empezar a llenarse |
| Experto | Conseguir Veloz y Fantasma en el mismo intento |

Una vez conseguido un reto, quedará marcado como completado en ese nivel. Un intento posterior fallido no borrará el logro.

Para comprobar Fantasma se conservará un indicador de si hubo sospecha durante el intento, aunque después la barra de detección vuelva a cero. Los mapas y los tiempos objetivo se probarán para que los retos sean alcanzables.

### Puntuación

La puntuación se calculará al completar un nivel mediante esta propuesta inicial:

**Puntuación = 1000 puntos por completar + 10 × segundos completos restantes + 500 puntos si se consigue Fantasma.**

Por ejemplo, terminar con 40 segundos restantes y sin generar sospecha daría 1900 puntos. Los valores se ajustarán tras las pruebas. Utilizar radios o escondites no restará puntos, porque forman parte de las herramientas previstas para resolver los niveles.

Los intentos fallidos no entrarán en la clasificación ni actualizarán los récords de tiempo o puntuación.

### Estadísticas

Se guardarán estos datos sencillos:

- Intentos iniciados, contando cada reinicio como un nuevo intento.
- Intentos completados con éxito, incluyendo las repeticiones de un mismo nivel.
- Derrotas, diferenciando detección y tiempo agotado.
- Mejor tiempo y puntuación máxima de cada nivel.

Las estadísticas acumuladas se conservarán entre sesiones. El cronómetro y los indicadores de los retos pertenecerán solo al intento actual y se reiniciarán al volver a jugar.

### Elementos generales previstos

El proyecto incluirá menú principal, pausa, opciones, créditos y pantallas de victoria y derrota. Las pantallas de resultado permitirán volver a jugar y regresar al menú.

Al completar cada nivel se mostrará un resumen con el tiempo, el récord personal, la puntuación y los retos conseguidos, con opciones para continuar, repetir ese nivel o volver al menú. Tras el tercer nivel, la pantalla de victoria presentará el resultado final y permitirá acceder de nuevo a los niveles completados.

El menú tendrá acceso a una pantalla de Mejores tiempos y estadísticas, con la clasificación de cada nivel. Desde ella se podrá repetir un nivel ya completado para mejorar su marca. El progreso de niveles completados también se conservará entre sesiones.

El menú de opciones permitirá ajustar música y efectos por separado, conservando los valores entre escenas. Habrá música de fondo y sonidos para las acciones principales y la interfaz.

## 5. Mecánicas

| Mecánica | Descripción | Control previsto | Nivel en el que aparece |
|---|---|---|---|
| Esconderse | Entrar en un escondite señalado para quedar oculto e inmóvil. Volver a interactuar permite salir | E junto al escondite | 1, 2 y 3 |
| Activar distracciones | Encender una radio para atraer temporalmente al guardia asociado hacia un punto preparado | E junto a la radio | 1, 2 y 3 |
| Conseguir objetos y abrir accesos | Recoger una tarjeta o los documentos. La salida comprueba que se dispone del objeto necesario | E junto al objeto o la puerta | 1, 2 y 3 |
| Activar interruptores | Utilizar un panel para desactivar una cámara de vigilancia | E junto al panel | 3 |

El movimiento se realizará con WASD o las flechas. Se considera un control básico y no se cuenta entre las mecánicas anteriores. La pausa se abrirá con Esc.

### Combinación de las mecánicas

Una situación prevista consiste en activar una radio para alejar a un guardia, esconderse mientras se aproxima y aprovechar su investigación para llegar hasta una tarjeta.

En el último nivel, el jugador tendrá que alcanzar un interruptor para desactivar la cámara y continuar hasta los documentos.

### Funcionamiento inicial propuesto

- Cada escondite admitirá al personaje hasta que vuelva a pulsar E.
- Al activar una radio, su guardia se desplazará a un punto cercano, esperará aproximadamente dos segundos y regresará a su puesto.
- La radio podrá volver a utilizarse cuando el guardia haya regresado.
- Los recorridos de investigación se prepararán para que los guardias puedan completarlos sin atravesar paredes.
- Cada nivel tendrá un objeto principal necesario para utilizar la salida.
- El interruptor del tercer nivel desactivará su cámara durante el resto del intento.
- La indicación de interacción señalará qué elemento se utilizará al pulsar E.

Como valores iniciales se propone una velocidad del personaje de 3 unidades por segundo y una velocidad de patrulla de 1,5 unidades por segundo. Se modificarán si las pruebas muestran que dificultan demasiado el juego.

El cronómetro, los récords, los retos y las estadísticas utilizarán las acciones de estas mecánicas. Los valores de tiempo y puntuación son propuestas de diseño pendientes de validar en un prototipo.

## 13. Recursos de terceros

-

## 14. Declaración de uso de IA

He utilizado ChatGPT como apoyo para organizar el contenido del GDD según la plantilla y revisar la ortografía, la gramática y la claridad del texto. La ayuda recibida en este hito se ha centrado en la claridad de la informacion enviada al agente.

En la ampliación del 2026-10-23 se ha utilizado ChatGPT para proponer y documentar el sistema de contrarreloj, mejores tiempos locales, retos, puntuación y estadísticas. Esta ampliación corresponde al diseño del juego; su implementación y sus pruebas están pendientes.

## 16. Diario de desarrollo

### 2026-10-18: definición inicial del proyecto

**Trabajo realizado**

- Revisión del enunciado, los requisitos y los apartados correspondientes al hito 1.
- Preparación de una propuesta de sigilo 2D con vista desde arriba.
- Redacción de la primera versión del concepto, la historia, la jugabilidad y las mecánicas.

**Riesgos identificados**

La investigación libre de ruidos y las persecuciones podrían aumentar demasiado la complejidad de la IA.

**Decisiones de diseño**

- Organizar el juego en tres niveles.
- Utilizar radios fijas como distracciones.
- Preparar las rutas de patrulla y los recorridos de investigación.
- Resolver la derrota mediante una barra de detección.
- Introducir las mecánicas de forma progresiva.

**Siguiente paso**

Crear una escena de prueba con un personaje, una pared, un guardia, un escondite y una radio para comprobar el funcionamiento básico del sigilo.

**Registro en Git**

Añadir esta documentación al repositorio y realizar el commit.

### 2026-10-23: rejugabilidad, tiempos y retos

**Trabajo realizado**

- Ampliación del GDD con un sistema de contrarreloj y una nueva condición de derrota por tiempo.
- Definición de récords y una tabla local de los cinco mejores tiempos de cada nivel.
- Propuesta de los retos Veloz, Fantasma y Experto.
- Definición de una puntuación sencilla y de las estadísticas que se guardarán.
- Actualización del flujo de resultados para permitir repetir niveles completados.

**Decisiones de diseño**

- Aprovechar los mismos tres niveles para mejorar tiempos y conseguir retos.
- Guardar los datos de forma local y conservarlos entre sesiones.
- Separar los datos persistentes de los datos temporales de cada intento.
- Congelar el cronómetro durante la pausa y las pantallas de resultado.
- Registrar únicamente intentos completados en la clasificación.

**Siguiente paso**

Después de comprobar el prototipo de sigilo, implementar un cronómetro que respete la pausa y añadir el registro de mejores tiempos. Después se incorporarán los retos, la puntuación y las estadísticas. Habrá que probar los límites de tiempo y que un reinicio conserve los datos persistentes sin conservar los del intento anterior.

**Estado**

Ampliación de diseño y documentación. Los sistemas descritos todavía están pendientes de implementación y pruebas.
