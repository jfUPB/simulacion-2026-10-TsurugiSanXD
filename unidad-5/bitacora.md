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




## Bitácora de aplicación 


## Bitácora de reflexión
