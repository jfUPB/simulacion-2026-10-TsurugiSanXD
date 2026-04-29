<img width="1919" height="872" alt="image" src="https://github.com/user-attachments/assets/0f8c7f64-5f86-4462-ba7f-190410e7d826" /># Unidad 7

## Bitácora de proceso de aprendizaje

## Actividad 1.

***1) Analiza 3 o 4 ejemplos de Ji Lee.*** <br>
***R\:*** El proyecto consiste en representar visualmente una palabra usando únicamente las letras que la componen, sin añadir elementos externos. La idea es transformar la tipografía en imagen sin perder la legibilidad ().
<br>

***Ejemplo 1: “Smile”***
En este caso, la palabra forma una sonrisa dentro de las letras.

Manipulación tipográfica: se curvan o reorganizan los caracteres para simular la forma de una boca sonriente.
Refuerzo del significado: la palabra no solo se lee, sino que también “actúa” como una sonrisa, generando una conexión directa entre forma y significado.
<br>

***Ejemplo 2: “Moon”***
La palabra suele transformarse en una forma circular o incluir fases de la luna dentro de las letras.

Manipulación tipográfica: las letras se adaptan para sugerir la forma redonda o las fases.
Refuerzo del significado: la tipografía imita visualmente el objeto real, facilitando la comprensión inmediata.
<br>

***Ejemplo 3: “Exit”***
Generalmente se representa con una letra que “sale” o se desplaza.

Manipulación tipográfica: una de las letras se mueve fuera de la estructura de la palabra.
Refuerzo del significado: la acción de salir se refleja directamente en la composición.
<br>

***Ejemplo 4: “Idea”***
Suele representarse con una bombilla integrada en las letras.

Manipulación tipográfica: las letras se modifican para sugerir la forma de una bombilla.
Refuerzo del significado: la palabra se convierte en el símbolo universal de “idea”.
<br>

***2) Explica cómo la manipulación tipográfica refuerza el significado.*** <br>
***R\:*** En todos los casos, Ji Lee demuestra que las letras no son solo signos para leer, sino también formas visuales con gran potencial expresivo. El significado se refuerza cuando la forma tipográfica se convierte en imagen, generando una doble lectura: textual y visual.
<br>

***3) Propón 2 o 3 palabras propias y esboza cómo podrían representarse visualmente.*** <br>
***R\:*** 
<br>

***Palabra 1: “Caída”***
<br>

Las letras podrían ir descendiendo en diagonal, como si estuvieran cayendo.
Algunas letras podrían estar más abajo que otras para reforzar la sensación de movimiento.
<br>

***Palabra 2: “Silencio”***
<br>
La letra “i” podría ser un dedo sobre la boca (forma vertical).
El resto de la palabra podría estar más delgada o tenue.
<br>

***Palabra 3: “Explosión”****
<br>
Las letras podrían separarse desde el centro hacia afuera.
Algunas partes podrían fragmentarse o distorsionarse.
<br>

***3) Indica cuál de esas palabras te interesa más y por qué.*** <br>
***R\:*** La palabra que más me interesa desarrollar es “Silencio”, porque permite trabajar tanto lo visual como lo conceptual. Se puede jugar con el contraste, el espacio y la sutileza, logrando una composición simple pero muy expresiva. Además, transmite una idea clara sin necesidad de muchos elementos.


## Actividad 2.

***1) Explica con tus palabras qué hace cada uno de esos conceptos.*** <br>
***R\:*** Para poder dar comportamiento físico a una palabra, primero es necesario entender cómo funciona el motor de físicas:
<br>

***Engine***
Es el “cerebro” del sistema. Se encarga de calcular todo lo que ocurre en la simulación: movimiento, gravedad, colisiones, etc. Actualiza constantemente el estado de los objetos.
<br>

***World***
Es el espacio donde existen todos los elementos. Aquí se agregan los objetos físicos (cuerpos) para que el motor los procese.
<br>

***Bodies***
Son los objetos físicos dentro del mundo. Pueden ser cajas, círculos u otras formas. Tienen propiedades como masa, velocidad, rebote, fricción, etc.
<br>

***Constraint***
Son conexiones entre cuerpos. Funcionan como ligas o cuerdas que unen objetos, permitiendo crear estructuras más complejas (por ejemplo, letras que no se separen completamente).
<br>

***MouseConstraint***
Permite interactuar con los objetos usando el mouse. Gracias a esto, puedes arrastrar elementos como si fueran reales.
<br>

***2) Replica al menos dos experimentos básicos integrando Matter.js con p5.js.*** <br>
***R\:***


***Codigo***
<br>

```
// Importar módulos de Matter.js
const { Engine, World, Bodies } = Matter;

let engine;
let world;
let boxes = [];
let ground;

function setup() {
  createCanvas(400, 400);

  engine = Engine.create();
  world = engine.world;

  // Suelo
  ground = Bodies.rectangle(200, 390, 400, 20, { isStatic: true });
  World.add(world, ground);

  // Cajas (simulan letras)
  for (let i = 0; i < 5; i++) {
    let box = Bodies.rectangle(200, 50 + i * 60, 40, 40);
    boxes.push(box);
    World.add(world, box);
  }
}

function draw() {
  background(220);
  Engine.update(engine);

  rectMode(CENTER);
  fill(100);

  // Dibujar cajas
  for (let box of boxes) {
    push();
    translate(box.position.x, box.position.y);
    rotate(box.angle);
    rect(0, 0, 40, 40);
    pop();
  }

  // Dibujar suelo
  rect(ground.position.x, ground.position.y, 400, 20);
}
```

<img width="1919" height="872" alt="image" src="https://github.com/user-attachments/assets/ec88fa9c-e4a1-4939-95f6-63dd76c2291c" />

***Codigo2***
<br>

```
// Importar módulos de Matter.js
const { Engine, World, Bodies, Mouse, MouseConstraint } = Matter;

let engine;
let world;
let box;
let mConstraint;

function setup() {
  createCanvas(400, 400);

  engine = Engine.create();
  world = engine.world;

  // Crear objeto
  box = Bodies.rectangle(200, 200, 80, 80);
  World.add(world, box);

  // Mouse
  let canvasMouse = Mouse.create(canvas.elt);
  canvasMouse.pixelRatio = pixelDensity();

  let options = {
    mouse: canvasMouse
  };

  mConstraint = MouseConstraint.create(engine, options);
  World.add(world, mConstraint);
}

function draw() {
  background(220);
  Engine.update(engine);

  rectMode(CENTER);
  fill(150);

  push();
  translate(box.position.x, box.position.y);
  rotate(box.angle);
  rect(0, 0, 80, 80);
  pop();
}
```

<img width="1917" height="867" alt="image" src="https://github.com/user-attachments/assets/26bb1702-e93d-434e-8519-8472cbbc5ff6" />



***5) Describe qué tipo de comportamiento físico te interesa explorar en tu palabra.*** <br>
***R\:*** Para mi proyecto, me interesa explorar un comportamiento donde las letras de una palabra:

Se comporten como objetos independientes al inicio (caen o se dispersan).
Luego se conecten mediante constraints, formando la palabra nuevamente.
Permitan interacción con el usuario (arrastrarlas o desordenarlas).

Esto crea una experiencia dinámica donde la palabra no es estática, sino que se construye, se rompe y se vuelve a formar, reforzando su significado a través del movimiento.


## Bitácora de aplicación 


## Bitácora de reflexión
