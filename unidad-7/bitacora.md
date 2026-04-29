## Unidad 7

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


## Actividad 3.

***1) Realiza al menos dos experimentos simples de audio-reactividad.*** <br>
***R\:*** En esta actividad exploré cómo el audio puede influir en lo visual o físico dentro de una simulación. Utilicé herramientas de p5.js como análisis de amplitud y frecuencia para transformar sonido en comportamiento visual.
<br>

***2) Realiza al menos dos experimentos simples de audio-reactividad.*** <br>
***R\:*** 
<br>

***EXPERIMENTO 1***
<br>

***¿Qué dato se lee?***
La amplitud del audio, que representa qué tan fuerte suena en un momento determinado.
<br>

***¿Qué comportamiento activa?***
El tamaño de una figura cambia dependiendo del volumen: mientras más fuerte el sonido, más grande el objeto.
<br>


https://github.com/user-attachments/assets/9e524180-2a8e-451c-8678-aa5994dbd5da

***Resultado:***
El círculo “respira” con el sonido. Esto es una respuesta continua, porque cambia constantemente.

***EXPERIMENTO 2***
<br>

***¿Qué dato se lee?***
La energía en frecuencias bajas (bajos) usando FFT (Fast Fourier Transform).
<br>

***¿Qué comportamiento activa?***
El color cambia dependiendo de la intensidad de los bajos.
<br>


https://github.com/user-attachments/assets/cf90f8ca-9a20-44c8-ba7a-bdf23e272a28

***Resultado:***
El color cambia con los golpes de bajo. Esto permite detectar momentos específicos del audio.
<br>

***3) Explica qué comportamiento visual o físico activa ese dato.*** <br>
***R\:*** La amplitud es útil para movimientos suaves y continuos.
Las frecuencias permiten detectar eventos más específicos (como beats o golpes). Esto demuestra que el sonido puede traducirse en distintos tipos de comportamiento dependiendo del dato que se use.
<br>

***4) Describe qué tipo de respuesta sonora te serviría más para tu palabra y por qué.*** <br>
***R\:*** Para mi proyecto (palabra: “Silencio”), me interesa trabajar con:
<br>

Amplitud baja → estabilidad (las letras permanecen quietas)>}<br>
Picos de sonido → ruptura o movimiento
<br>

***¿Por qué?****
Porque el concepto de “silencio” se puede representar mejor cuando:
<br>
No pasa nada visual (calma)
Y solo reacciona cuando el sonido aparece (interrupción del silencio) Esto crea un contraste claro entre ausencia y presencia de sonido.

## Actividad 4.

***Prueba inicial****
<br>
En esta prueba integré una parte de la palabra “Silencio”, utilizando la letra (S) como cuerpo físico dentro de un sistema con Matter.js y reacción al audio mediante p5.js.

Las letras están representadas como cajas que caen por gravedad y reaccionan al sonido modificando su comportamiento.

<img width="1919" height="865" alt="image" src="https://github.com/user-attachments/assets/4a801f8d-8360-4836-914b-73c442f603df" />

<img width="1913" height="862" alt="image" src="https://github.com/user-attachments/assets/2a130afe-7a2e-45ed-b5b4-6303703a1c67" />

https://github.com/user-attachments/assets/ef41b454-06ba-4086-954d-07f75fcb9577

<br>

***¿Qué parte de la palabra construí?***
En esta nueva prueba trabajé con una sola letra de la palabra “Silencio”, específicamente la “S”.
La letra fue convertida en un conjunto de puntos usando tipografía digital, lo que permitió tratarla como una forma flexible en lugar de un bloque rígido.
<br>

***¿Qué propiedad física manipulé?***
En lugar de usar físicas tradicionales de Matter.js (como gravedad o colisiones), manipulé una propiedad más cercana a lo físico pero desde lo visual:
Deformación de la forma (desplazamiento de puntos)
Dispersión controlada de la estructura de la letra
Esto simula un comportamiento tipo vibración o inestabilidad, como si la letra tuviera una “estructura interna flexible”.
<br>

***¿Qué aspecto del audio afecta qué comportamiento?***
Dato leído: amplitud del audio (volumen)
Comportamiento activado:
<br>
Volumen bajo → la letra se mantiene estable y legible <br>
Volumen medio → la letra vibra ligeramente <br>
Volumen alto → la letra se deforma fuertemente y pierde su forma <br>

Esto genera una relación directa entre sonido y forma visual. 
<br>


***Evaluación***
<br>

Lo que funcionó:
<br>

La deformación ocurre directamente en la letra, no en una caja externa.
Se logra una conexión clara entre audio y transformación visual.
La letra mantiene su identidad cuando el sonido es bajo, lo cual refuerza la legibilidad.
<br>

Lo que no funcionó del todo:
<br>

No hay interacción física real (no hay gravedad ni colisiones).
La deformación es aleatoria, no estructural (no hay control fino del movimiento).
Aún no se integra toda la palabra, solo una parte.
<br>

***Relación con el significado***
<br>

Este comportamiento se acerca más al concepto de “silencio”, ya que:
<br>

El estado base es estable (silencio)
El sonido introduce perturbación (ruptura del silencio)

Sin embargo, aún falta reforzar el contraste para que el concepto sea más claro, por ejemplo haciendo que la deformación sea más extrema o que la forma colapse completamente en presencia de sonido.





## Bitácora de aplicación 

## Actividad 5.




## Bitácora de reflexión
