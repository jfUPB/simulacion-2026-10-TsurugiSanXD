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


***1. Palabra elegida*** <br>
<br>
***BREAK***
<br>
<br>

***2. Justificación conceptual*** <br>
La palabra BREAK fue elegida porque su significado es inseparable de una acción física: romper implica tensión, impacto y ruptura irreversible. No es una palabra que describa un estado, sino un evento. Eso la hace ideal para una pieza donde el comportamiento visual y sonoro no ilustre la palabra sino que la ejecute. La pieza no muestra lo que significa break — la pieza es un break.
<br>
<br>

***3. Análisis de su significado visual y comportamental*** <br>
Visualmente, la palabra aparece estática y centrada, en tipografía serif (Georgia), con peso y presencia. Esa estabilidad inicial es deliberada: la tensión viene de saber que puede romperse. La palabra no cae sola ni se anima sin intervención — espera. Esa espera es parte del significado.
El comportamiento físico está construido con Matter.js: la palabra tiene masa, fricción, restitución y responde a fuerzas reales. Al ser arrastrada y lanzada contra los bordes del canvas, el impacto detona la ruptura. Los fragmentos que quedan no son decorativos — son los restos del evento. La física no acompaña la palabra: la palabra es la física.
La tipografía semántica funciona en dos momentos: antes del impacto, BREAK es una palabra entera bajo tensión; después, deja de existir como palabra y se convierte en fragmentos, perdiendo su legibilidad. Ese tránsito entre signo y ruido visual es el núcleo conceptual de la pieza.
<br>
<br>

***4.Moodboard***
<br>
<img width="893" height="495" alt="image" src="https://github.com/user-attachments/assets/b43a49a4-d5d7-4c47-acf0-7452dc141234" />

<br>
<br>

***5.Boceto***
<br>
<img width="1600" height="1200" alt="WhatsApp Image 2026-05-06 at 1 49 40 AM" src="https://github.com/user-attachments/assets/8368695a-97b4-43a6-9200-4759df8fe564" />

<br>
<br>

***6.Mapa de decisiones***
<br>
<img width="668" height="573" alt="image" src="https://github.com/user-attachments/assets/e6bfcdfd-ab74-44dd-a501-49b3ea1a463f" />

<br>
<br>

***7.Mapa de interpretación***
<br>
La pieza se ejecuta en vivo como un instrumento audiovisual con tres modos de intervención posibles:
<br>
***Modo 1: Silencio y observación***
La palabra aparece estática en pantalla. No ocurre nada. La audiencia enfrenta la palabra como objeto tipográfico bajo tensión implícita.
<br>

***Modo 2: Intervención sonora***
El intérprete o la audiencia produce sonido (voz, palmada, música). La palabra comienza a temblar con audio suave. Un sonido suficientemente fuerte la lanza contra los bordes. Si el impacto supera el umbral, se rompe. La ruptura puede construirse gradualmente (varios golpes pequeños que acumulan movimiento) o detonarse de un solo golpe.
<br>

***Modo 3: Intervención física***
El intérprete arrastra la palabra con el mouse y la lanza deliberadamente contra una pared. La velocidad del lanzamiento determina si rompe o rebota. Es una acción consciente, performativa, donde el gesto del cuerpo sobre el mouse se traduce en destrucción tipográfica.
<br>
En todos los casos, al romperse la palabra suena el efecto de quiebre. La audiencia puede reiniciar la pieza con cualquier tecla y repetir el ciclo, convirtiendo la pieza en un loop performativo.
<br>
<br>

***8. Explicación de la relación entre audio y comportamiento*** <br>
El audio no es un efecto decorativo: es una fuerza física dentro del sistema. El micrófono escucha en tiempo real y traduce el volumen ambiente en comportamiento de la palabra de dos maneras distintas y con sentido semántico:
<br>

***Audio suave (voz baja, ruido de fondo):*** la palabra tiembla visualmente en su lugar. No se mueve, pero acusa la presencia del sonido. Es la tensión antes de la ruptura.
<br>
***Audio fuerte (golpe, palmada, voz alta):*** la palabra recibe un impulso físico real proporcional a la intensidad del sonido. Más volumen equivale a más fuerza. Si ese impulso la lleva a chocar contra un borde del canvas a suficiente velocidad, se rompe.
<br>

Esto significa que la ruptura puede ocurrir sin tocar el mouse: el sonido puede romper la palabra. La relación entre audio y comportamiento refuerza el significado de BREAK porque lo que quiebra la palabra no es solo el contacto físico, sino también la intensidad de lo que se escucha. El sonido tiene peso.
Al momento de la ruptura, se reproduce un efecto sonoro de quiebre que cierra el ciclo: la palabra que fue rota por el audio, responde con audio.
<br>
<br>

***9.Evidencia del uso de IA***
<br>
La IA (Claude) fue utilizada como herramienta de materialización técnica, no como origen conceptual de la pieza. Las decisiones de autoría que permanecieron humanas fueron: la elección de la palabra BREAK, la intención de que el audio fuera una fuerza física y no un efecto decorativo, la decisión de que la ruptura fuera irreversible y dependiera de velocidad real, y la estructura performativa de la pieza en tres modos de intervención.
Lo que se delegó a la IA fue la implementación técnica: la integración de Matter.js con p5.js, la lógica de detección de colisiones, la traducción del volumen del micrófono en impulso físico proporcional, y la depuración de errores de carga de librerías y archivos de sonido. En varios momentos el código generado no funcionó y fue necesario redirigir, corregir el enfoque e identificar el problema real (nombre del archivo de sonido con espacios que rompía la carga silenciosamente).
La IA aceleró la implementación pero no tomó decisiones conceptuales. Cada vez que el código se desvió de la intención original, la decisión de corregirlo y en qué dirección fue humana.
<br>
<br>

***10.Codigo fuente***
<br>

***Index***
<br>

```
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BREAK</title>
    <style>
      * { margin: 0; padding: 0; }
      html, body { overflow: hidden; background: #0a0a0a; }
      canvas { display: block; }
    </style>
  </head>
  <body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.0/addons/p5.sound.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/matter-js/0.19.0/matter.min.js"></script>
    <script src="sketch.js"></script>
  </body>
</html>
```

<br>

***Sketch***
<br>

```

const { Engine, Bodies, Body, World, Events, Mouse, MouseConstraint } = Matter;

let engine, world;
let wordBody, mConstraint;
let walls = [];

let broken = false;
let shards = [];
let sonido;
let fontSize, wordW, wordH;

const PALABRA = "BREAK";

// Audio reactivo
let mic;
let micLevel = 0;
let lastImpulse = 0;

function preload() {
  soundFormats('mp3');
  sonido = loadSound('break');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  textAlign(CENTER, CENTER);
  textFont('Georgia');
  fontSize = constrain(width * 0.13, 80, 160);
  textSize(fontSize);
  wordW = textWidth(PALABRA) + 20;
  wordH = fontSize * 0.85;

  mic = new p5.AudioIn();
  mic.start();

  initMatter();
}


function initMatter() {
  engine = Engine.create({ gravity: { x: 0, y: 0 } });
  world  = engine.world;

  let t = 60;
  walls = [
    Bodies.rectangle(width/2,     height+t/2, width*3, t,        { isStatic:true, label:'floor' }),
    Bodies.rectangle(width/2,     -t/2,        width*3, t,        { isStatic:true, label:'ceil'  }),
    Bodies.rectangle(-t/2,        height/2,    t,       height*3, { isStatic:true, label:'wallL' }),
    Bodies.rectangle(width+t/2,   height/2,    t,       height*3, { isStatic:true, label:'wallR' }),
  ];
  World.add(world, walls);

  wordBody = Bodies.rectangle(width/2, height/2, wordW, wordH, {
    isStatic:    true,
    restitution: 0.3,
    friction:    0.05,
    frictionAir: 0.01,
    label:       'word',
    density:     0.005,
  });
  World.add(world, wordBody);

  let m = Mouse.create(document.querySelector('canvas'));
  m.pixelRatio = pixelDensity();
  mConstraint = MouseConstraint.create(engine, {
    mouse: m,
    constraint: { stiffness: 0.2, damping: 0.1, render: { visible:false } }
  });
  World.add(world, mConstraint);

  Events.on(mConstraint, 'startdrag', function(e) {
    if (e.body && e.body.label === 'word') {
      Body.setStatic(wordBody, false);
    }
  });

  Events.on(engine, 'collisionStart', function(event) {
    if (broken) return;
    for (let pair of event.pairs) {
      let a = pair.bodyA.label;
      let b = pair.bodyB.label;
      if ((a === 'word' || b === 'word') &&
          (a === 'floor' || b === 'floor' ||
           a === 'ceil'  || b === 'ceil'  ||
           a === 'wallL' || b === 'wallL' ||
           a === 'wallR' || b === 'wallR')) {
        if (wordBody.speed > 5) {
          triggerBreak();
          return;
        }
      }
    }
  });
}


function triggerBreak() {
  broken = true;
  userStartAudio();
  if (sonido && sonido.isLoaded()) sonido.play();

  let cx = wordBody.position.x;
  let cy = wordBody.position.y;

  World.remove(world, wordBody);
  wordBody = null;

  shards = [];
  for (let i = 0; i < 280; i++) {
    let angle = random(TWO_PI);
    let spd   = random(3, 13);
    shards.push({
      x:    cx + random(-wordW/2, wordW/2),
      y:    cy + random(-wordH/2, wordH/2),
      vx:   cos(angle) * spd * random(0.3, 1),
      vy:   sin(angle) * spd - random(1, 5),
      w:    random(4, 18),
      h:    random(2, 7),
      rot:  random(TWO_PI),
      rotV: random(-0.12, 0.12),
      a:    255
    });
  }
}


function resetSketch() {
  broken = false;
  shards = [];
  World.clear(world);
  Engine.clear(engine);
  initMatter();
}

function draw() {
  background(10);
  Engine.update(engine, 1000/60);

  micLevel = mic.getLevel();

  if (!broken && wordBody) {

    let umbral = 0.04;
    if (micLevel > umbral && millis() - lastImpulse > 300) {
      lastImpulse = millis();

      if (wordBody.isStatic) Body.setStatic(wordBody, false);

      let fuerza = map(micLevel, umbral, 0.4, 8, 35);
      fuerza = constrain(fuerza, 8, 35);

      let angle = random(TWO_PI);
      Body.setVelocity(wordBody, {
        x: cos(angle) * fuerza,
        y: sin(angle) * fuerza
      });
      Body.setAngularVelocity(wordBody, random(-0.08, 0.08) * (fuerza / 10));
    }

    
    let vibracion = micLevel > 0.01 ? map(micLevel, 0.01, umbral, 0, 2.5) : 0;

    let pos = wordBody.position;
    let ang = wordBody.angle;

    push();
    translate(pos.x + random(-vibracion, vibracion),
              pos.y + random(-vibracion, vibracion));
    rotate(ang);
    textAlign(CENTER, CENTER);
    textSize(fontSize);
    textFont('Georgia');
    fill(255);
    noStroke();
    text(PALABRA, 0, 0);
    pop();

  } else if (broken) {
    noStroke();
    let vivos = 0;
    for (let s of shards) {
      if (s.a <= 0) continue;
      vivos++;
      s.x  += s.vx;
      s.y  += s.vy;
      s.vy += 0.35;
      s.vx *= 0.988;
      s.rot += s.rotV;
      s.a  -= 2.5;
      push();
      translate(s.x, s.y);
      rotate(s.rot);
      fill(255, s.a);
      rect(-s.w/2, -s.h/2, s.w, s.h);
      pop();
    }
    if (vivos === 0) {
      fill(255, 60);
      textSize(13);
      textAlign(CENTER, CENTER);
      text('presiona cualquier tecla para reiniciar', width/2, height/2);
    }
  }
}


function mousePressed() {
  userStartAudio();
  mic.start();
  if (!fullscreen()) fullscreen(true);
}

function keyPressed() {
  if (broken) resetSketch();
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```
<br>
<br>

***11.Enlace al sketch***
<br>
***Link:*** https://editor.p5js.org/luisafer1845/sketches/VKPx9CD4F

<br>
<br>

***12.Capturas***
<br>
<br>

<img width="1477" height="797" alt="Captura de pantalla 2026-05-06 020726" src="https://github.com/user-attachments/assets/51a19180-3bcb-45aa-875d-87a5d7ad7e22" />
<img width="1919" height="1079" alt="Captura de pantalla 2026-05-06 020720" src="https://github.com/user-attachments/assets/d0445887-8f05-4e1b-8628-896e73c42764" />
<img width="1090" height="969" alt="Captura de pantalla 2026-05-06 020712" src="https://github.com/user-attachments/assets/1f13ec7e-b03d-4450-836b-c60c04965014" />
<img width="1919" height="1079" alt="Captura de pantalla 2026-05-06 020708" src="https://github.com/user-attachments/assets/2505c144-024a-41f1-82c0-0692b7461ff2" />



## Bitácora de reflexión
