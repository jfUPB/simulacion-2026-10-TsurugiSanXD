# Unidad 2

## Bitácora de proceso de aprendizaje
## Actividad 1.
El trabajo que más me gusto fue uno de Ravem kwok, más especificamente este: https://openprocessing.org/sketch/111470 . Simplemente los pikachus me parece que se ven muy tiernos y chistosos, sumando que la forma que tienen hace que cuando se muevan se vean gorditos, tambien me gusta el movimiento que tiene de atravesar la pantalla y volver a generarse en el fondo. 
<br>

## Actividad 2. 
**¿Cómo funciona la suma dos vectores en p5.js?**
**R\:** Para realizar una suma de vectores se tienen que sumar el valor de x con el valor de x y el valor de y con el valor de y, debido a que los componentes se suman por separado. 
Por ejemplo: si tengo un "position" de (100, 50) y un "velocity" de (2, 3) al ejecutar "position.add(velocity);" la nueva posición será (102, 53), esto actualiza la posición del objeto en cada frame con su posición y velocidad indicada.
<br>

**¿Por qué esta línea position = position + velocity; no funciona?**
**R\:** Esa linea no funciona ya que como tal ahí no estamos sumando los valores si no los objetos en los que estan contenidos, es decir, "position" y "velocity" no son números si no los contenedores de los números por si decirlo. En p5 el operador "+" solo recibe números, por ende no puede subar objetos, debido a eso es que usamos el "position.add(velocity);" para poder sumar los componetes del vector. 
<br>

## Actividad 3. 
**¿Qué tuviste que hacer para hacer la conversión propuesta?**
**R\:** Usando el codigo de "traditional random walker" hice un cambio haciendo que la posición se maneje mediante coordenadas que se manejan con incrementos y decrementos de 1 unidad. La conversión consistió en reemplazar las variables "this.x" y "this.y" por un unico vector llamado "this.position" creado con "createVector(width / 2, height / 2)" en lugar de modificar valores individuales, se creó un vector de desplazamiento dependiendo de la dirección elegida y luego se utilizó el método .add() para sumarlo a la posición.

```java
let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.position = createVector(width / 2, height / 2);
  }

  show() {
    stroke(0);
    point(this.position.x, this.position.y);
  }

  step() {
    const choice = floor(random(4));
    let step;

    if (choice == 0) {
      step = createVector(1, 0);   // derecha
    } else if (choice == 1) {
      step = createVector(-1, 0);  // izquierda
    } else if (choice == 2) {
      step = createVector(0, 1);   // abajo
    } else {
      step = createVector(0, -1);  // arriba
    }

    this.position.add(step);
  }
}

```
<br>

## Actividad 4. 
**¿Qué resultado esperas obtener en el programa anterior?**
**R\:** Analizando el codigo pues primero que nada espero ver un vector en el preview en la posición (6,9) ya que con esta linea de codigo "position = createVector(6,9);" lo estamos ceando allí, luego tambien supongo que por tener un "ToString()" se va a imprimir en pantalla con algun color de fondo ya que con es linea se le da un color al fondo "background(220);" y con respecto a lo demas creo que se va a multiplicar la posicón del ventor para cambiarla, eso es lo que espero obtener al ver el codigo. 
<br>

**¿Qué resultado obtuviste?**
**R\:** Pues al ejecutar el codigo más o menos obtuve lo que esperaba pero no como creia, porque si se muestra el vector pero no en el preview como yo esperab, si no que sale en la consola, si se imprimio como un string que esperaba eso. Y tambien se hizo un cambio en la posición del vector como creia, pero los valores no se multiplicaron si no que solo se reemplazaron y ahora el vector esta en la posición "(20,30)"
<br>

**Recuerda los conceptos de paso por valor y paso por referencia en programación.**
**R\:** El paso por valor ocurre cuando se envía una copia del dato a una función, por lo que cualquier modificación no afecta al original. En cambio, el paso por referencia ocurre cuando se envía la dirección del objeto en memoria, por lo que cualquier cambio realizado dentro de la función modifica el objeto original.
<br>

**¿Qué tipo de paso se está realizando en el código?**
**R\:** En el codigo del ejemplo se esta realizando paso por referencia, porque estamos cambiando nuestro vector original. El vector es un objeto y al cambiar sus propiedades dentro de la función cambiamos el objeto original.
<br>

**¿Qué aprendiste?**
**R\:** Aprendi que los vectores en p5 son objetos que se pueden cambiar, ya que al ser parametros de una función no se crean copias si no que se modifican a si mismos para seguir trabajando, por lo tanto, aprendi que cualquier modificación hecha dentro de la función afecta el valor original.
<br>

## Actividad 5.
**1)¿Para qué sirve el método mag()? Nota que hay otro método llamado magSq(). ¿Cuál es la diferencia entre ambos? ¿Cuál es más eficiente?**
**R\:** "mag()" sirve para calcular la magnitud (longitud) del vector usando la raiz cuadrada de x^2 + y^2. el otro metodo "magSq()" hace casi lo mismo, solo que este solo calcula x^2 + y^2 sin la raiz cuadrada y devuelve la longitus del vector alcuadrado, siendo es su diferencia con respecto a "mag()". Por suposición, "magSq()" es más eficiente dado que evita calcular la raiz cuadrada, lo cual tengo entendido que es una operación pesada para el equipo. 
<br>

**2)¿Para qué sirve el método normalize()?**
**R\:** "normalize()" sirve para convertir el vector en un vector unitario, osea que hace que la magnitud del vector sea 1. Esta operación mantiene la dirección del vector, lo unico que cambia es la magnitud del mismo.
<br>

**3)Te encuentras con un periodista en la calle y te pregunta ¿Para qué sirve el método dot()? ¿Qué le responderías en un frase?**
**R\:** Le responderia que: El metodo "dot()" sirve para saber que tan alineados estan dos vectores que apuntan a la misma dirección.
<br>

**4)El método dot() tiene una versión estática y una de instancia. ¿Cuál es la diferencia entre ambas?**
**R\:** La diferencia principal entre estos dos es que la versión de intencia trabaja direectamente con el vector, ose trabaja directamente con el objeto; en cambio, la versión estatica trabaja con la clase no desde un objeto en especifico, lo cual viene siendo una forma más general el calculo, sin embargo, si se trabaja con los mismos valores el resultado sera el mismo independientemente de con cual de los dos se trabaje. 
<br>

**5)Ahora el mismo periodista curioso de antes te pregunta si le puedes dar una intuición geométrica acerca del producto cruz. Entonces te pregunta ¿Cuál es la interpretación geométrica del producto cruz de dos vectores? Tu respuesta debe incluir qué pasa con la orientación y la magnitud del vector resultante.**
**R\:** El producto cruz entre dos vectores genera un nuevo vector que es perpendicular a ambos. Su magnitud representa el área del paralelogramo que forman los dos vectores (más grande si están más “abiertos”, cero si están alineados). En cuanto a la orientación, el vector resultante apunta en una dirección determinada por la regla de la mano derecha: en 2D, esto se traduce en que el resultado indica si el giro de un vector hacia el otro es en sentido antihorario (positivo) o horario (negativo).
<br>

**6)¿Para que te puede servir el método dist()?**
**R\:** "dist()" calcula la distancia entre dos vectores, es útil para saber qué tan lejos está un objeto de otro e internamente usa la diferencia entre vectores y su magnitud.
<br>

**7)¿Para qué sirven los métodos normalize() y limit()?**
**R\:** "normalize()" convierte el vector en unitario (magnitud 1) y "limit(max)" limita la magnitud del vector a un valor máximo. Si el vector es más grande que max, lo reduce y si no, lo deja igual.
<br>

## Actividad 6. 

**Codigo con el resultado pedido**
```java
let t = 0;
let step = 0.01;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);

  let base = createVector(80, 320);

  let v1 = createVector(250, 0);     
  let v2 = createVector(0, -250);    

  let vGreen = p5.Vector.sub(v2, v1);
  let vLerp = p5.Vector.lerp(v1, v2, t);

  let c1 = color(255, 0, 0);
  let c2 = color(0, 0, 255);
  let movingColor = lerpColor(c1, c2, t);

  drawArrow(base, v1, 'red');
  drawArrow(base, v2, 'blue');

  let redTip = p5.Vector.add(base, v1);
  drawArrow(redTip, vGreen, 'green');

  drawArrow(base, vLerp, movingColor);

  t += step;
  if (t > 1 || t < 0) {
    step *= -1;
  }
}

function drawArrow(base, vec, myColor) {
  push();
  stroke(myColor);
  strokeWeight(3);
  fill(myColor);
  translate(base.x, base.y);
  line(0, 0, vec.x, vec.y);
  rotate(vec.heading());
  let arrowSize = 7;
  translate(vec.mag() - arrowSize, 0);
  triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
  pop();
}

```

**¿Cómo funciona lerp() y lerpColor().**
**R\:** "lerp()" basicamente calcula un punto intermedio entre dos cosas usando una formula proporcional, en el caso de "p5.Vector.lerp(v1, v2, t)" lo que hace internamente es esto: toma la diferencia entre v2 y v1, la multiplica por t, y se la suma a v1. Si t = 0, no se mueve nada y se queda en v1. Si t = 1, avanza toda la distancia hasta v2. Si t = 0.5, avanza la mitad del camino. Es como moverse progresivamente sobre una línea recta entre dos puntos. por otro lado, "lerpColor()" funciona igual, pero en vez de interpolar posiciones en el espacio (x, y), interpola valores de color (rojo, verde y azul), produciendo una transición suave entre un color y otro a medida que cambia t.
<br>

**¿Cómo se dibuja una flecha usando drawArrow()?**
**R\:** La función drawArrow() primero traslada el sistema de coordenadas al punto base del vector usando translate(), luego dibuja la línea del vector desde el origen hasta (vec.x, vec.y). Después rota el sistema según el ángulo del vector usando vec.heading() para que la punta apunte correctamente, y finalmente coloca un triángulo en el extremo usando la magnitud del vector (vec.mag()) para representar la cabeza de la flecha.

## Bitácora de aplicación 



## Bitácora de reflexión






