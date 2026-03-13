# Unidad 4

## Bitácora de proceso de aprendizaje

## Actividad 1.

Algo que me llamo mucho la atención de la obra de Memo es cómo utiliza movimientos simples para generar cosas visuales bastante complejas y soprendentemente organicas. En la obra Simple Harmonic Motion se puede ver como muchos elementos se mueven siguiendo patrones repetitivos que recuerdan al movimiento de ondas o pendulos, tambien me parecio interesante que el movimiento se siente muy natural y fluido, aunque en realidad esta hecho con fóomulas matemáticas relativamente "simples" y piento que eso muestra como en el arte generativo incluso las pequeñas reglas pueden producir cosas visuales bastante buenas. Aparte tambien me gusto como la obra se ve casi como algo vivo, porque los movimientos estan en constante cambio pero siguen un ritmo o patron.
<br>

## Actividad 2. 

***Manejo de angulos:*** <br>

***1) ¿Qué está pasando en esta simulación? ¿Cuál es la interacción?*** <br>
***R)\:*** En la simulación veo una barra con dos circulos en los extremos que está rotando alrededor del centro de la pantalla, la interacción es que el angulo cambia constantemente, por lo que el objeto gira en cada frame.
<br>

***2) Nota que en cada frame se está trasladando el origen del sistema de coordenadas al centro de la pantalla. ¿Por qué crees que se hace esto?*** <br>
***R)\:*** El origen del sistema de coordenadas se traslada al centro de la pantalla porque asi es mas facil hacer que el objeto rote alrededor de su propio centro y si el origen se quedara en la esquina del canvas, la rotación seria alrededor de esa esquina y no se veria bien el efecto.
<br>

***3) Cuál es la relación entre el sistema de coordenadas y la función rotate().*** <br>
***R)\:*** La relación entre el sistema de coordenadas y "rotate()" es que la rotación siempre ocurre alrededor del origen del sistema de coordenadas actual, por eso primero se usa "translate()" para mover el origen al centro y luego se aplica "rotate()".
<br>

***4) C¿Por qué crees que se hace esto? y ¿Por qué aunque en cada frame se hace lo mismo, los elementos gráficos rotan?*** <br>
***R)\:*** los elementos se dibujan alrededor del punto (0,0) porque ese punto ahora representa el centro del sistema de coordenadas despues de usar "translate()" aunque el código dibuja siempre lo mismo en cada frame, los elementos rotan porque antes de dibujarlos se aplica rotate(), lo que cambia la orientación del sistema de coordenadas.

***dirección del movimiento:*** <br>

***1) Identifica el marco motion 101. ¿Qué es lo que se está haciendo en este marco?*** <br>
***R)\:*** En esta simulación se aplica el marco Motion 101. Primero se actualiza la aceleración con fuerzas, luego la velocidad se actualiza con la aceleración y finalmente la posición cambia según la velocidad. Esto permite que el objeto se mueva de manera dinámica.
<br>

***2)¿Qué hace la función heading()?*** <br>
***R)\:*** La función "heading()" obtiene el ángulo del vector de velocidad. Es decir, calcula hacia qué dirección está apuntando el movimiento del objeto.
<br>

***3)¿Qué hace la función push() y pop()? Realiza algunos experimentos para entender su funcionamiento.*** <br>
***R)\:*** Las funciones "push()" y "pop()" guardan y restauran el estado de las transformaciones del sistema de coordenadas. Esto se usa para que las rotaciones o traslaciones aplicadas a un objeto no afecten a los demás.
<br>

***4)¿Qué hace rectMode(CENTER)? Realiza algunos experimentos para entender su funcionamiento.*** <br>
***R)\:*** La función "rectMode(CENTER)" hace que el rectangulo se dibuje desde su centro en lugar de desde una esquina. Esto facilita que el objeto rote correctamente alrededor de su propio centro.
<br>

***5)¿Cuál es la relación entre el ángulo de rotación y el vector de velocidad? Trata de dibujar en un papel el vector de velocidad y cómo se relaciona con el ángulo de rotación y la operación de traslación y rotación.*** <br>
***R)\:*** La relación entre el ángulo de rotación y el vector de velocidad es que el ángulo se calcula directamente a partir de la dirección del vector de velocidad. Luego ese angulo se usa en "rotate()" para que el objeto apunte exactamente hacia donde se esta moviendo. Asi la figura siempre mira en la dirección del movimiento.

## Actividad 3.

En esta actividad quise hacer como pidieron una simulación de un vehiculo triangular que se puede mover usando las flechas del teclado, para hacerlo utilice el marco Motion 101, donde la aceleración modifica la velocidad y la velocidad modifica la posición del vehiculo. Cuando se presionan las flechas izquierda o derecha se aplica una fuerza que cambia la aceleración del vehiculo, esto hace que el objeto se mueva en la pantalla. Para que el vehiculo apunte en la dirección en la que se esta moviendo utilice la función "heading()" del vector de velocidad, que devuelve el angulo del movimiento. Ese angulo se usa con "rotate()" para girar la figura. Tambien se utiliza "translate()" para mover el sistema de coordenadas a la posición del vehículo antes de dibujarlo, y "push()" y "pop()" para que las transformaciones no afecten otros elementos del programa.

## Actividad 4.

***1)Identifica motion 101. ¿Qué modificación hay que hacer al motion 101 cuando se quiere agregar fuerzas acumulativas? Trata de recordar por qué es necesario hacer esta modificación.*** <br>
***R)\:*** En la simulación se usa el marco Motion 101, donde la aceleración cambia la velocidad y la velocidad cambia la posición. Cuando se agregan fuerzas acumulativas, la modificación que se hace es que todas las fuerzas se suman primero en la aceleración y luego se actualiza la velocidad. Después de actualizar, la aceleración se reinicia a 0 para que no se acumulen fuerzas de frames anteriores.
<br>

***2)Identifica dónde está el Attractor en la simulación. Cambia el color de este.*** <br>
***R)\:*** El Attractor en la simulación es el objeto que genera una fuerza de atracción hacia las partículas. En el código se puede cambiar su color modificando el fill() que se usa cuando se dibuja.
<br>

***3)Observa que el Attractor tiene dos atributos this.dragging y this.rollover. Estos atributos no se modifican en el código, pero permitirían mover el attractor con el mouse y cambiar su color cuando el mouse está sobre él. ¿Cómo podrías modificar el código para que esto funcione? considera las funciones que ofrece p5.js para interactuar con el mouse.*** <br>
***R)\:*** Los atributos "dragging" y "rollover" servirian para interactuar con el mouse "dragging" permitiria mover el attractor cuando se mantiene presionado el mouse sobre el, y "rollover" serviria para detectar cuando el mouse esta encima y cambiar su color. Esto se podria implementar usando funciones de p5.js como "mousePressed()", "mouseDragged()" y verificando la distancia entre el mouse y la posición del attractor.
<br>

***Codigo:***
```java
let movers = [];
let attractor;

function setup() {
  createCanvas(600, 400);

  attractor = new Attractor();

  for (let i = 0; i < 10; i++) {
    movers.push(new Mover(random(width), random(height), random(1, 3)));
  }
}

function draw() {
  background(220);

  attractor.update();
  attractor.show();

  for (let mover of movers) {

    let force = attractor.attract(mover);
    mover.applyForce(force);

    mover.update();
    mover.show();

  }
}

function mousePressed() {
  attractor.pressed();
}

function mouseReleased() {
  attractor.released();
}

class Mover {

  constructor(x, y, m) {
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.mass = m;
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acceleration.add(f);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    stroke(0);
    fill(150);
    circle(this.position.x, this.position.y, this.mass * 16);
  }
}

class Attractor {

  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.mass = 20;
    this.dragging = false;
    this.rollover = false;
  }

  attract(mover) {

    let force = p5.Vector.sub(this.position, mover.position);
    let distance = force.mag();

    distance = constrain(distance, 5, 25);

    let G = 1;
    let strength = (G * this.mass * mover.mass) / (distance * distance);

    force.setMag(strength);
    return force;
  }

  update() {

    if (this.dragging) {
      this.position.x = mouseX;
      this.position.y = mouseY;
    }

  }

  show() {

    let d = dist(mouseX, mouseY, this.position.x, this.position.y);

    if (d < this.mass) {
      this.rollover = true;
    } else {
      this.rollover = false;
    }

    stroke(0);
    strokeWeight(2);

    if (this.dragging) {
      fill(50, 200, 50);
    } 
    else if (this.rollover) {
      fill(200, 100, 100);
    } 
    else {
      fill(175);
    }

    circle(this.position.x, this.position.y, this.mass * 2);
  }

  pressed() {

    let d = dist(mouseX, mouseY, this.position.x, this.position.y);

    if (d < this.mass) {
      this.dragging = true;
    }

  }

  released() {
    this.dragging = false;
  }

}
```

## Actividad 5.

***1)Observa de nuevo esta parte del código ¿Cuál es la relación entre r y theta con las posiciones x y y? Puedes repasar entonces la definición de coordenadas polares y cómo se convierten a coordenadas cartesianas.*** <br>
***R)\:***  En las coordenadas polares la posición de un punto se define usando "r" y "theta". "r" representa la distancia desde el origen y theta el ángulo. Para convertir esto a coordenadas cartesianas se usan las fórmulas "x = r · cos(theta)" y "y = r · sin(theta)", que permiten obtener la posición en la pantalla.

***2)Modificar la funcion "draw()" ¿Qué ocurre? ¿Por qué?*** <br>
***R)\:*** En la segunda modificación se usa "p5.Vector.fromAngle(theta)". Esto crea un vector con la dirección del ángulo pero con una magnitud de 1. Por eso el punto queda muy cerca del centro y parece que el círculo solo gira alrededor del origen con un radio pequeño.
<br>

***3)Modifición  "line(0, 0, v.x, v.y);" , ¿Qué ocurre aquí? ¿Por qué?*** <br>
***R)\:*** En la última modificación se usa 2p5.Vector.fromAngle(theta, r)". En este caso el vector ya incluye la magnitud "r", por lo que el punto vuelve a tener la distancia correcta desde el centro y el movimiento circular vuelve a verse como en el primer caso.

## Actividad 6.

La función sinusoide describe un movimiento que se repite de forma periódica, como muchas cosas que ocurren en la naturaleza o en animaciones. En la simulación pude cambiar parámetros como la amplitud, la frecuencia, la velocidad angular y la fase para ver cómo cambia la forma de la onda. La amplitud controla qué tan alta es la onda, mientras que la frecuencia cambia qué tan juntas aparecen las repeticiones. La velocidad angular hace que la onda se mueva más rápido o más lento y la fase desplaza la onda en el eje horizontal. Esto me ayudó a entender que la función seno es muy útil para crear movimientos oscilatorios y animaciones suaves en arte generativo.
<br>

***Codigo:***
```java
let angle = 0;

let amplitudeSlider;
let frequencySlider;
let speedSlider;
let phaseSlider;

function setup() {
  createCanvas(600, 400);

  amplitudeSlider = createSlider(10, 150, 80);
  frequencySlider = createSlider(0.01, 0.1, 0.03, 0.01);
  speedSlider = createSlider(0.01, 0.2, 0.05, 0.01);
  phaseSlider = createSlider(0, TWO_PI, 0, 0.1);
}

function draw() {
  background(255);

  translate(width/2, height/2);

  let amplitude = amplitudeSlider.value();
  let frequency = frequencySlider.value();
  let speed = speedSlider.value();
  let phase = phaseSlider.value();

  stroke(0);
  noFill();

  beginShape();

  for (let x = -width/2; x < width/2; x++) {

    let y = amplitude * sin(frequency * x + angle + phase);

    vertex(x, y);

  }

  endShape();

  angle += speed;
}
```

## Actividad 7.

En esta actividad modifiqué la simulación agregando conceptos de unidades anteriores. De la unidad 1 utilicé "noise()" para generar una variación en la fuerza del viento, lo que produce un movimiento más suave y natural que usar "random()" de la unidad 3 agregué fuerzas al sistema. Por ejemplo, una fuerza de gravedad que empuja los objetos hacia abajo y una fuerza de viento horizontal. Estas fuerzas se aplican usando el marco Motion 101, donde la aceleración modifica la velocidad y la velocidad modifica la posición. Con estas modificaciones la simulación se vuelve más dinámica y los objetos se mueven de forma más orgánica.
<br>

***Codigo:***
```java
let movers = [];
let t = 0;

function setup() {
  createCanvas(600, 400);

  for (let i = 0; i < 10; i++) {
    movers.push(new Mover(random(width), random(height)));
  }
}

function draw() {
  background(220);

  for (let m of movers) {

    // Fuerza de gravedad (unidad 3)
    let gravity = createVector(0, 0.1);
    m.applyForce(gravity);

    // Fuerza de viento usando noise (unidad 1)
    let windStrength = map(noise(t), 0, 1, -0.2, 0.2);
    let wind = createVector(windStrength, 0);

    m.applyForce(wind);

    m.update();
    m.show();
  }

  t += 0.01;
}

class Mover {

  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.mass = 2;
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acceleration.add(f);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    fill(127);
    stroke(0);
    circle(this.position.x, this.position.y, 20);
  }

}
```

## Actividad 8.

En esta actividad modifiqué la simulación de la onda para que se moviera como una ola. Para hacerlo agregué una variable que cambia con el tiempo y la sumé dentro de la función seno. De esta forma la fase de la onda cambia en cada frame y el patrón parece desplazarse horizontalmente. Esto genera el efecto visual de una ola moviéndose en lugar de una onda estática.

```java
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let angle = 0;
let angleVelocity = 0.2;
let amplitude = 100;

function setup() {
  createCanvas(640, 240);
}

function draw() {
  background(255);

  stroke(0);
  strokeWeight(2);
  fill(127, 127);

  let angleTemp = angle; // fase que se moverá

  for (let x = 0; x <= width; x += 24) {

    // posición vertical usando seno
    let y = amplitude * sin(angleTemp);

    // dibujar círculo
    circle(x, y + height / 2, 48);

    // avanzar en la onda
    angleTemp += angleVelocity;
  }

  // esto mueve la ola completa
  angle += 0.05;
}
```

## Actividad 9.

En esta actividad modifiqué la simulación de resortes para crear un sistema con dos resortes en serie. Para hacerlo agregué una segunda masa y un segundo resorte que se conecta después del primero.
Esto hace que las dos masas se muevan y oscilen juntas, porque el movimiento de una afecta a la otra. Así se puede ver cómo funcionan los sistemas de resortes conectados.
<br>

***Codigo:***
```java
let bob1;
let bob2;

let spring1;
let spring2;

function setup() {
  createCanvas(640, 360);

  // masas
  bob1 = new Bob(width / 2, 150);
  bob2 = new Bob(width / 2, 250);

  // resortes
  spring1 = new Spring(width / 2, 0, 150);
  spring2 = new Spring(width / 2, 150, 100);
}

function draw() {
  background(255);

  // gravedad
  let gravity = createVector(0, 0.2);

  bob1.applyForce(gravity);
  bob2.applyForce(gravity);

  // fuerzas de los resortes
  spring1.connect(bob1);
  spring2.connect(bob2);

  // actualizar masas
  bob1.update();
  bob2.update();

  // dibujar resortes
  spring1.displayLine(bob1);
  spring2.displayLine(bob2);

  // dibujar masas
  bob1.display();
  bob2.display();
}

class Bob {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = createVector();
    this.acceleration = createVector();
    this.mass = 24;
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acceleration.add(f);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  display() {
    stroke(0);
    fill(127);
    circle(this.position.x, this.position.y, this.mass * 2);
  }
}

class Spring {
  constructor(x, y, length) {
    this.anchor = createVector(x, y);
    this.restLength = length;
    this.k = 0.2;
  }

  connect(bob) {
    let force = p5.Vector.sub(bob.position, this.anchor);

    let d = force.mag();
    let stretch = d - this.restLength;

    force.normalize();
    force.mult(-1 * this.k * stretch);

    bob.applyForce(force);
  }

  displayLine(bob) {
    stroke(0);
    line(this.anchor.x, this.anchor.y, bob.position.x, bob.position.y);
  }
}
```

## Actividad 10.

En esta actividad modifiqué la simulación para crear un sistema de dos péndulos conectados en serie. Para hacerlo agregué un segundo ángulo y una segunda longitud para calcular la posición del segundo péndulo. El segundo péndulo parte desde la posición del primero, por lo que su movimiento depende del movimiento del primero. Esto genera un sistema más complejo de oscilación.
<br>

```java
let a1 = Math.PI / 2;
let a2 = Math.PI / 2;

let a1_v = 0;
let a2_v = 0;

let r1 = 120;
let r2 = 120;

let m1 = 20;
let m2 = 20;

let g = 0.4;

function setup() {
  createCanvas(640, 360);
}

function draw() {
  background(255);

  translate(width / 2, 80);

  let a1_a = (-g / r1) * sin(a1);
  let a2_a = (-g / r2) * sin(a2);

  a1_v += a1_a;
  a2_v += a2_a;

  a1 += a1_v;
  a2 += a2_v;

  let x1 = r1 * sin(a1);
  let y1 = r1 * cos(a1);

  let x2 = x1 + r2 * sin(a2);
  let y2 = y1 + r2 * cos(a2);

  stroke(0);
  strokeWeight(2);

  line(0, 0, x1, y1);
  circle(x1, y1, m1);

  line(x1, y1, x2, y2);
  circle(x2, y2, m2);
}
```
<br>

## Bitácora de aplicación 

## Actividad 11.

***Ecos del eoceano*** <br>
Mi obra generativa representa un océano abstracto formado por partículas que se mueven como si fueran corrientes marinas. Cada partícula sigue un movimiento ondulatorio basado en funciones sinusoidales, simulando el flujo del agua. Las corrientes no son completamente predecibles porque el sistema incluye variaciones aleatorias, lo que hace que cada ejecución genere un comportamiento distinto. El usuario puede interactuar con la obra moviendo el mouse, lo que altera la amplitud de las ondas y cambia el comportamiento del sistema, como si estuviera perturbando el agua.
<br>

***Codigo:***
```java
let particles = [];
let amplitude = 50;
let angle = 0;

function setup() {
  createCanvas(700, 400);

  // crear partículas con posiciones aleatorias
  for (let i = 0; i < 60; i++) {
    particles.push({
      x: random(width),
      y: random(height),
      speed: random(0.5, 2),
      offset: random(TWO_PI)
    });
  }
}

function draw() {
  background(20, 30, 60);

  angle += 0.03;

  for (let p of particles) {

    // movimiento horizontal
    p.x += p.speed;

    if (p.x > width) {
      p.x = 0;
    }

    // movimiento ondulatorio
    let wave = amplitude * sin(angle + p.offset);

    let y = p.y + wave;

    fill(120, 180, 255);
    noStroke();

    circle(p.x, y, 10);
  }
}

function mouseMoved() {

  // interacción: el mouse cambia la amplitud
  amplitude = map(mouseX, 0, width, 10, 120);

}
```
<br>

***Enlace al proyecto:*** https://editor.p5js.org/luisafer1845/sketches/MluXzFhLB
<br>

***Capturas de pantalla:***

https://drive.google.com/drive/folders/11nmk09Z3J2oCaVgjRK6HUyAZgNA91U9q?usp=drive_link


## Bitácora de reflexión

Estos conceptos pueden aplicarse en el diseño de experiencias interactivas dentro del entretenimiento digital. Los sistemas generativos permiten crear animaciones y comportamientos dinámicos que cambian en tiempo real. También pueden utilizarse para desarrollar efectos visuales, simulaciones de movimiento y obras generativas interactivas en videojuegos o instalaciones digitales.

***Diagrama:***

https://drive.google.com/drive/folders/11nmk09Z3J2oCaVgjRK6HUyAZgNA91U9q?usp=drive_link
