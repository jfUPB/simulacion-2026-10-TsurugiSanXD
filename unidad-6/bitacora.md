# Unidad 6

## Bitácora de proceso de aprendizaje


## Actividad 1.

***1) Selecciona dos imágenes o piezas de Tyler Hobbs que te llamen la atención.*** <br>
***R\:*** La dos referencias que seleccione son: Las obras de la serie Flow Fields (explicadas en su texto) y la serie Fidenza, que utiliza flow fields como base visual.

<br>

***2) Describe qué decisiones visuales reconoces en ellas:*** <br>
***R\:*** <br>

***Composición*** <br>
Las piezas están organizadas a partir de trayectorias curvas que recorren todo el espacio. No hay un centro fijo, sino una distribución que se siente fluida y continua.

<br>

***Densidad*** <br>
La densidad varía: hay zonas más cargadas de líneas y otras más vacías. Esto genera contraste visual y guía la mirada.

<br>

***Dirección del movimiento*** <br>
El movimiento está determinado por un sistema invisible (flow field) que define hacia dónde se mueven las líneas. Todas siguen reglas locales pero crean patrones globales coherentes.

<br>

***Color*** <br>
Se utilizan paletas controladas (a veces probabilísticas), donde ciertos colores aparecen más que otros. Esto genera armonía sin perder variación.

<br>

***Ritmo*** <br>
El ritmo se percibe en la repetición de curvas y en la longitud de las trayectorias: líneas largas generan fluidez, líneas cortas generan textura.

<br>

***Repetición y variación*** <br>
Se repiten estructuras (curvas), pero cada una tiene pequeñas variaciones en dirección, tamaño o color, lo que evita que la imagen se vea mecánica.

<br>

***3) Explica por qué esas decisiones te parecen potentes.*** <br>
***R\:*** Estas decisiones son potentes porque logran un equilibrio entre orden y caos, por un lado, hay reglas claras (el sistema que guía las líneas), pero por otro lado hay variación suficiente para que el resultado se vea orgánico. Esto hace que la obra parezca natural, como si fuera un flujo de agua, viento o crecimiento biológico, aunque en realidad está completamente generada por un sistema.

<br>

***4) Escribe una hipótesis: ¿Qué tipo de reglas o sistema crees que podrían estar detrás de esa pieza?*** <br>
***R\:*** Creo que estas piezas funcionan a partir de una grilla donde cada punto tiene una dirección que, en conjunto, forma un campo de flujo que guía el movimiento de líneas o partículas. Estas se desplazan siguiendo esas direcciones desde distintos puntos iniciales, mientras el sistema aplica reglas como evitar superposición, variar el color y controlar la longitud. Esto genera curvas orgánicas y fluidas, ya que los cambios de dirección son suaves, produciendo un resultado visual natural.

## Actividad 2.

***1) Explica con tus propias palabras qué es un agente autónomo.*** <br>
***R\:*** Un agente autónomo es una entidad que puede tomar decisiones por sí misma dentro de un entorno. No solo reacciona a fuerzas externas, sino que percibe lo que ocurre y actúa según objetivos propios, como acercarse, evitar o seguir algo, lo que hace que su comportamiento se vea más natural.

<br>

***2) Explica qué es una "steering force".*** <br>
***R\:*** Una steering force es una fuerza que el mismo agente genera para cambiar su movimiento según un objetivo. Surge al comparar hacia dónde quiere ir con cómo se está moviendo, aplicando una corrección para dirigir su trayectoria.

<br>

***3) compara una "steering force" con una fuerza externa como la gravedad.*** <br>
***R\:*** Las fuerzas externas, como la gravedad, actúan siempre igual sobre un objeto sin que este tenga control. En cambio, una steering force depende del agente y de lo que percibe, por lo que cambia según la situación y el objetivo.

<br>

***4) Describe por qué estas ideas son útiles para diseñar comportamiento visual y no solo para simular movimiento.*** <br>
***R\:*** Estas ideas permiten crear comportamientos complejos a partir de reglas simples, generando movimientos más naturales y orgánicos. Esto ayuda a diseñar sistemas visuales que parecen tener vida propia, en lugar de animaciones rígidas hechas manualmente.


## Actividad 3. 

***1) ¿Cómo está construido el campo de flujo?.*** <br>
***R\:*** El campo de flujo está construido como una grilla (una cuadrícula) dividida en celdas, donde cada celda contiene un vector. Esta estructura funciona como un mapa invisible que cubre todo el espacio y define direcciones en cada punto.

<br>

***2) ¿Qué representa cada celda o vector del campo?.*** <br>
***R\:*** Cada celda contiene un vector que representa una dirección (y a veces magnitud) hacia donde debería moverse un agente en esa posición. Es como una flecha que indica el “flujo” del sistema en ese punto, similar a los campos de vectores en física donde cada punto tiene una dirección asociada.

<br>

***3) ¿Cómo usa un agente su posición para consultar el campo?.*** <br>
***R\:*** El agente toma su posición en el espacio y la convierte en índices de la grilla para saber en qué celda está. Luego consulta el vector de esa celda para saber hacia dónde debería moverse, usando ese valor como guía.

<br>

***4) Cómo se convierte el vector consultado en una decisión de movimiento?.*** <br>
***R\:*** El vector obtenido se usa como una dirección deseada, y el agente genera una steering force para ajustar su velocidad hacia esa dirección. Es decir, no se mueve instantáneamente, sino que corrige su movimiento poco a poco para alinearse con el flujo.

<br>

***5) Identifica parámetros importantes del sistema.*** <br>
***R\:*** La resolución define qué tan grande o pequeña es cada celda del campo, afectando el detalle del movimiento. El "maxspeed" limita la velocidad máxima del agente, mientras que el "maxforce" controla qué tan rápido puede cambiar de dirección. La cantidad de agentes influye en la densidad visual y en qué tan complejo se ve el sistema.

<br>

***6) Realiza al menos una modificación y analiza el efecto visual que produce.*** <br>
***R\:*** Si se modifica, por ejemplo, la resolución o los valores del ruido (Perlin noise), el campo cambia completamente: puede volverse más suave y fluido o más caótico. Esto altera el comportamiento de los agentes, haciendo que el movimiento se vea más organizado o más impredecible.

<br>

***A) ¿Qué tipo de movimiento produce este algoritmo?*** <br>
***R\:*** Produce un movimiento fluido y continuo, donde los agentes parecen seguir corrientes invisibles, similar al comportamiento de partículas en agua o viento, generando trayectorias suaves y conectadas.

<br>

***B) ¿Qué sensaciones visuales te sugiere?*** <br>
***R\:***  Genera sensaciones de fluidez, organicidad y naturaleza, como si se tratara de corrientes, humo o enjambres. Dependiendo de los parámetros, puede sentirse calmado o caótico, pero siempre dinámico.

<br>

***C) ¿En qué tipo de pieza musical imaginas que podría funcionar bien?*** <br>
***R\:*** Podría funcionar muy bien en música ambiental, electrónica o experimental, donde los movimientos fluidos acompañen sonidos continuos o atmósferas. También encaja con música lo-fi o sound design más orgánico.


## Actividad 4. 


***1) Explica con tus palabras las tres reglas básicas: separación, alineación, cohesión.*** <br>
***R\:*** La separación es la regla que hace que cada agente evite estar demasiado cerca de los demás, generando una fuerza que lo aleja de sus vecinos cercanos. La alineación hace que el agente intente igualar su velocidad con la de los otros agentes que tiene alrededor, moviéndose en la misma dirección. La cohesión, en cambio, hace que el agente se mueva hacia el centro del grupo de vecinos, manteniendo la unión del conjunto. Estas tres reglas trabajan juntas y, aunque son simples, permiten que surja un comportamiento colectivo complejo.

<br>

***2) Identifica qué parámetros controlan estas reglas.*** <br>
***R\:*** Estas reglas se controlan principalmente mediante los pesos que se les asignan a cada comportamiento (separación, alineación y cohesión), que determinan qué tan fuerte influye cada uno. También intervienen parámetros como la distancia de percepción, que define qué vecinos afectan al agente, y valores como maxspeed y maxforce, que limitan la velocidad máxima y la intensidad de las fuerzas aplicadas.

<br>

***3) Modifica uno o más pesos del sistema y describe el efecto visual y colectivo.*** <br>
***R\:*** Al modificar los pesos de las reglas, el comportamiento cambia notablemente. Por ejemplo, al aumentar el peso de separación, los agentes tienden a dispersarse más; al aumentar la cohesión, se agrupan con mayor fuerza; y al aumentar la alineación, se mueven más sincronizados. Esto transforma la forma y dinámica del grupo, haciendo que el sistema se vea más ordenado o más desorganizado según el ajuste.

<br>

***4) Describe el comportamiento emergente observado: compacto, disperso,  estable, nervioso, caótico, fluido.*** <br>
***R\:*** El comportamiento emergente depende del equilibrio entre las tres reglas. Puede verse compacto si predomina la cohesión, disperso si domina la separación, estable si hay balance entre las fuerzas, nervioso si los cambios son bruscos, caótico si no hay coherencia clara, o fluido cuando los agentes se mueven de manera continua y armoniosa. Todo esto surge sin un control central, solo a partir de reglas locales.

<br>

***A) ¿Qué atmósfera visual produce el flocking?*** <br>
***R\:*** El flocking genera una atmósfera orgánica y dinámica, donde los agentes parecen comportarse como un sistema vivo. Se percibe movimiento colectivo coherente, con patrones que cambian constantemente pero mantienen cierta unidad.

<br>

***B) ¿En qué tipo de relación con una canción podría funcionar mejor este algoritmo?*** <br>
***R\:*** Este algoritmo funciona bien con música que tenga continuidad y capas, como ambient o electrónica suave, donde el movimiento colectivo pueda acompañar el flujo del sonido. También puede responder a cambios en intensidad, volviéndose más caótico o más ordenado según la energía de la música.


## Actividad 5. 

***Comparación entre flow fields y flocking*** <br>
Los flow fields producen un movimiento continuo y fluido donde los agentes siguen direcciones definidas por un campo de vectores, lo que genera trayectorias suaves y parecidas a corrientes de agua o viento. En cambio, el flocking produce un movimiento colectivo más dinámico basado en la interacción entre agentes, donde se forman grupos que se separan, se alinean y se reorganizan constantemente. En términos de control visual, los flow fields ofrecen un mayor control global, ya que el diseñador define directamente la estructura del campo, mientras que el flocking tiene menos control directo y depende más de la interacción local entre agentes.

En cuanto al nivel de emergencia, en los flow fields es moderado porque aunque el movimiento es generado por reglas, el comportamiento está guiado por una estructura previa; en el flocking es alto, ya que patrones complejos surgen únicamente de reglas simples sin una guía global. A nivel de atmósfera, los flow fields generan sensaciones más calmadas, fluidas y orgánicas, mientras que el flocking puede sentirse más vivo, energético y cambiante. En relación con la música, los flow fields funcionan bien con sonidos continuos o ambientales, mientras que el flocking se adapta mejor a ritmos dinámicos o cambios de intensidad. Como ventaja, los flow fields permiten dirigir el comportamiento de forma clara, pero pueden volverse predecibles; el flocking genera comportamientos más naturales y variados, pero es más difícil de controlar con precisión.

<br>

***¿Qué algoritmo usar según el tipo de canción?***
Para una canción contemplativa usaría flow fields, porque su movimiento suave y continuo genera una sensación de calma y flujo constante. Para una canción agresiva usaría flocking, ya que puede volverse caótico, rápido y con cambios bruscos que transmiten energía. En una canción melancólica también elegiría flow fields, porque sus trayectorias fluidas pueden transmitir suavidad y sensación emocional sostenida. Finalmente, para una canción eufórica usaría flocking, ya que el movimiento colectivo, dinámico y cambiante puede representar mejor la intensidad y la energía alta.

## Actividad 6.

## Bitácora de aplicación 


## Bitácora de reflexión
