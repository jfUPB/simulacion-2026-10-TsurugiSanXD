# Unidad 5
## Bitácora de proceso de aprendizaje


## Actividad 1.

**Capa de comportamiento**

<br>

**1)¿Qué propiedades tiene cada partícula? Clasifícalas: ¿Cuáles definen su estado físico? ¿Cuáles su estado vital?** <br>
**R)\:**  Cada partícula tiene:

<br>

**Estado físico:**
posición, velocidad y aceleración (los vectores del motion 101).
<br>

**Estado vital:**
una variable como lifespan (vida), que va disminuyendo con el tiempo.
<br>
Básicamente el estado fisico es cuanto se meueve la particula y el vital que tanto tiempo vive.

<br>

**2)¿Qué condición determina que una partícula “muere”? ¿Es una muerte instantánea o gradual?** <br>
**R)\:**  Una particula muere cada que su "lifespan" llega a 0, muere gradualmente dado que cada frame que pasa se le va quitanto un poquito de vida.

<br>

**3)¿Cómo se actualiza la partícula en cada frame? Identifica el patrón motion 101 dentro de la partícula.** <br>
**R)\:** En cada frame la particula suma aceleración a velocidad, velodidad a posición y resuce el "lifespan", lo cual es basicamente motion 101.

<br>

***Capa de estrcutura***

<br>

**4)¿Quién crea las partículas? ¿En qué momento?** <br>
**R)\:** Las particulas de crean en "draw()" con algo como "particles.push(new Particle(...));" por lo tanto se crea constantemente en el tiempo.

<br>

**5)¿Quién decide cuándo eliminar una partícula del array?** <br>
**R)\:** El programa es qui decide cuando se eliminan, ya que cuando dice " if (particle.isDead()) {
  particles.splice(i, 1);
}" el sistema las elimina cuando ya no sirven. 

<br>

**6)¿Por qué se recorre el array en orden inverso para eliminar? ¿Qué pasaría si no se hiciera así?** <br>
**R)\:** Porque al eliminar los elementos "(splice)" cambian los indices, si no lo hace al reves puede saltar particulas o generar errores.

<br>

**7)Si no eliminaras nunca las partículas, ¿Qué pasaría con la memoria y el rendimiento? Haz el experimento: comenta la línea que elimina y observa el frame rate.** <br>
**R)\:** Si no eliminamos las particulas estas se acumulan infinitamente, baja el rendimiento, el sismtema puede decir "estoy cansado jefe" y puede colgarse, debido a que el sistema maneja cada particula en cada frame.

<br>

***Capa de estrcutura***

<br>

**8)¿Qué elementos visuales usa para representar una partícula?** <br>
**R)\:** Las particulas se represntan usualmente con circulos de colores semitrasnparentes.

<br>

**9)¿Cómo se conecta el “tiempo de vida” con la apariencia visual?** <br>
**R)\:** El "lifespan" se usa para hacerla mas transparente o cambiar su color a mediada que la particula muere, osea, se desvanece.

<br>

**10)Si quisieras cambiar la representación visual (por ejemplo, usar líneas en vez de círculos), ¿Qué cambiarías y qué NO cambiarías?** <br>
**R)\:** A una particula se le puede cambiar la forma (linear, cuadrado, imagen), el color y em tamaño. Pero no se le debe cambiar la logica de movimiento (posición, velocidad, aceleración), el sistema de vida ("lifespan") o la estructura del array, debido a que eso puede romper el sistema


## Actividad 2.

**1)¿Qué responsabilidades que antes estaban en draw() ahora están dentro de la clase Emitter?** <br>
**R)\:** Antes en el ejemplo 4.2 el "draw()" hacia casi todo, tenia a su cargo funciones como: creal particular, guardarlas en su propio array, actulizarlas, dibujarlas y eliminarlas cuando morian. Ahora, "draw()" ya no maneja particulas directamente, ahora maneja "emitters", por lo tanto ahora este tiene la responsabilidad que antes tenia "draw()".

<br>

**2)¿Cuál es la ventaja de encapsular la lógica de emisión en una clase separada?** <br>
**R)\:** La gran ventaja esta en la escapabilidad y el orden. Antes todo estaba en un solo lugar y era dificil de controlar cuando crece. Ahora cada "emitter" es autonono y puede tener varios "emitters" funcionando al mismo tiempo, esto hace que pasemos de “manejar partículas sueltas” a “manejar sistemas completos de partículas”.

<br>

**3)En este ejemplo hay un array de emitters. ¿Quién crea los emitters? ¿Quién crea las partículas dentro de cada emitter?** <br>
**R)\:** Los "emitters" son creados por el sketch principal (setup o draw) y los guarda en el array de "emitters".Cada "emitter" crea sus propias particulas, osea el sketch crea sistemas y cada sistema crea sus elementos internos.

<br>

**4)Dibuja un diagrama que muestre la jerarquía: sketch → [emitters] → [partículas]. ¿Cuántos niveles de “colección” hay?**

<img width="750" height="599" alt="image" src="https://github.com/user-attachments/assets/09648d1c-4e65-4ab7-badb-e0f9f3546d4d" />

<br>

***Transferencia conceptual***

<br>

**5)Describe este ejemplo usando palabras que NO mencionen p5.js, JavaScript, ni ninguna herramienta específica. Usa solo términos como: entidad, estado, colección, emisor, ciclo de vida, fuerza.** <br>
**R)\:** Existe una entidad principal que administra una colección de emisores. Cada emisor tiene su propio estado y contiene una colección de elementos. Estos elementos nacen, evolucionan en el tiempo bajo la influencia de fuerzas y eventualmente desaparecen cuando termina su ciclo de vida. Los emisores funcionan como generadores autónomos: crean nuevos elementos, actualizan su estado y eliminan aquellos que ya no cumplen condiciones de existencia. La entidad principal no gestiona directamente a los elementos individuales, sino que delega esa responsabilidad a cada emisor, permitiendo así una organización jerárquica y modular del sistema.


## Actividad 3.

***1) ¿Qué tienen en común las subclases de partículas? ¿Qué tienen de diferente?*** <br>
Las subclases de partículas tienen en común que todas comparten una misma estructura base: poseen estado (posición, velocidad, vida útil), y comportamientos como actualizarse, mostrarse y desaparecer cuando termina su ciclo de vida. Esto se debe a que heredan de una clase principal. Sin embargo, se diferencian en la forma en que se comportan o se representan visualmente. Por ejemplo, pueden tener distintas formas, movimientos o maneras de mostrarse en pantalla. Es decir, comparten la lógica general pero personalizan ciertos comportamientos.
<br>

***2) ¿Por qué es importante que el Emitter no necesite saber qué tipo específico de partícula está gestionando?*** <br>
Es importante porque permite que el sistema sea flexible y escalable. El Emitter solo se encarga de manejar partículas de forma general (actualizarlas, mostrarlas y eliminarlas), sin preocuparse por sus detalles internos.Esto hace que se pueda trabajar con distintos tipos de partículas sin tener que modificar el Emitter. En otras palabras, el sistema funciona con cualquier tipo de partícula siempre que cumpla con la estructura base, lo que simplifica el diseño y evita dependencias innecesarias.
<br>


***3) Si mañana quisieras agregar un tercer tipo de partícula, ¿Qué tendrías que crear y qué NO tendrías que modificar?*** <br>
Tendría que crear una nueva subclase de partícula que herede de la clase base y definir en ella sus comportamientos específicos (por ejemplo, cómo se mueve o cómo se dibuja). No tendría que modificar el Emitter ni la lógica principal del sistema, ya que este ya está diseñado para trabajar con cualquier tipo de partícula de forma genérica.
<br>

**4) Compara con Example 4.2: ¿Cambió la lógica del Emitter? ¿Cambió la lógica de muerte? ¿Qué capa del sistema se modificó y cuáles permanecieron intactas?*** <br>
La lógica del Emitter se mantiene prácticamente igual, ya que sigue encargándose de crear, actualizar, mostrar y eliminar partículas. Tampoco cambia la lógica de muerte, porque las partículas siguen desapareciendo cuando termina su ciclo de vida. Lo que cambia es la capa de las partículas, ya que ahora se introduce herencia y polimorfismo, permitiendo que existan diferentes tipos de partículas con comportamientos distintos. En resumen, la estructura general del sistema se mantiene, pero se vuelve más flexible al permitir diversidad en los elementos internos sin afectar las capas superiores.

## Actividad 4.

Fuerzas globales vs. locales

***1) En Example 4.6, ¿Dónde se define la gravedad? ¿Quién la aplica a las partículas? ¿Es una fuerza global o local?*** <br>
La gravedad se define en el sistema principal como un vector constante. El Emitter es quien se encarga de aplicarla a cada partícula en cada ciclo. Es una fuerza global porque afecta a todas las partículas por igual, sin importar su posición o estado individual.
<br>

***2) En Example 4.7, ¿Qué diferencia hay entre la gravedad y la fuerza del repeller? ¿Dónde “vive” cada una?***
La gravedad es una fuerza constante y global que siempre apunta en la misma dirección. En cambio, la fuerza del repeller depende de la posición de cada partícula con respecto a él, por lo que cambia constantemente. Esta fuerza “vive” en el objeto repeller, ya que es él quien la calcula y la aplica.
<br>

***3) La fuerza del repeller depende de la distancia entre la partícula y el repeller. ¿Qué principio físico se está modelando?***
Se está modelando un principio similar a las fuerzas de repulsión o atracción como la gravedad o el electromagnetismo, donde la intensidad de la fuerza depende de la distancia entre dos objetos (generalmente de forma inversamente proporcional).
<br>

***4) ¿Cambió la clase Particle entre Example 4.6 y 4.7? ¿Qué implica esto sobre la separación entre comportamiento de la partícula y fuerzas externas?***
La clase Particle no cambia entre ambos ejemplos. Esto implica que las partículas están diseñadas para recibir fuerzas externas sin necesidad de modificarse internamente. Es decir, el comportamiento base de la partícula está desacoplado de las fuerzas, lo que permite agregar nuevas interacciones sin cambiar su estructura.
<br>

***Tabla comparativa***

<br>

<img width="817" height="515" alt="image" src="https://github.com/user-attachments/assets/499a1a06-bcbe-472e-8d50-e972ae8cb381" />

***Modificación quirúrgica***
<br>

***Elección:*** (a) Cambiar la visualización sin cambiar fuerzas ni estructura.
<br>

***¿Qué líneas de código tocaste?***
Se modificó únicamente el método de visualización de la partícula (display o show), cambiando aspectos como color, tamaño o forma.
<br>

***¿Qué clases/funciones modificaste?***
Solo se modificó la clase Particle, específicamente su función de renderizado.
<br>

***¿Qué partes del programa NO necesitaste modificar?***
No fue necesario modificar el Emitter, el repeller, ni la lógica de fuerzas. Tampoco se cambió la estructura general del sistema.
<br>

***¿Por qué fue posible hacer este cambio sin afectar las demás capas?***
Fue posible porque el sistema está bien separado por responsabilidades. La visualización está aislada dentro de la partícula, mientras que las fuerzas y la gestión del sistema están en otras capas. Esto permite hacer cambios específicos (como la apariencia) sin afectar el comportamiento físico ni la estructura del sistema.

## Bitácora de aplicación 


## Bitácora de reflexión
