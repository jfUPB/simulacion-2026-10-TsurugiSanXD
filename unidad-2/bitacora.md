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






## Bitácora de aplicación 



## Bitácora de reflexión




