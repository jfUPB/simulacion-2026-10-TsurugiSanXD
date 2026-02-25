# Unidad 3

## Bitácora de proceso de aprendizaje

## Actividad 1.

Lo que más me sorprendio es la reciliencia y a la vez la rendición del artista. Robert se nego a ser consumido por la IA, sin embargo, se da cuenta que el trabajo que el tanto se esforzo por aprender y lo lograr ahora es sumamente facil de obtener, si uno se pone a pensar bien eso haca cieeto punto deja una sensación de vacío, hasta de reemplazo. Pero Rorbert a pesar de sentirse mal tomo la IA y la uso a su favor, al final se da cuanta de lo que a muchos en el medio nos cuesta aceptar, la gente la pienda que lo que hagas si esta muy bien entonces seguramente piensen que es IA, entonces ¿Porque no usarlo a favor? así como Robert, lo que más claro me queda es que hay que daptarse.
<br>

## Actividad 2.

En est actividad repasamos el motion 101, osea los tres elementos del modelo: Posición, velocidad y aceleración. su funcionamiento los podemos ver claramente en el metodo "update()", primero la aceleración modifica la velocidad "(this.velocity.add(this.acceleration))", y luego la velocidad modifica la posición "(this.position.add(this.velocity))". Ahora, donde viene el cambio es en como calculamos la aceleración, dado que en la unidad anterior lo haciamos manualmente, ahora lo que hacemos es calcularla a través del resultado de las fuerzas del objeto. Por eso utilizamos "this.acceleration.add(force)" para acumular varias fuerzas en lugar de reemplazarlas. Aparte, al final de cada frame reiniciamos la aceleración usando "(this.acceleration.mult(0))" para que solo actúen las fuerzas actuales.
<br>

## Actividad 3.

<br>

**Obras generativas:**
<br>

**Fricción:**

```java
let mover;

function setup() {
  createCanvas(600, 400);
  mover = new Mover(100, 200, 2);
}

function draw() {
  background(220);

  // --- FUERZA CONSTANTE (empujón hacia la derecha)
  let push = createVector(0.2, 0);
  mover.applyForce(push);

  // --- FRICCIÓN
  let friction = mover.velocity.copy();
  friction.mult(-1);

  if (mover.velocity.mag() > 0) {
    friction.normalize();
    let mu = 0.05; // coeficiente de fricción
    friction.mult(mu);
    mover.applyForce(friction);
  }

  mover.update();
  mover.show();
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
    fill(0);
    circle(this.position.x, this.position.y, this.mass * 20);
  }
}
```
<br>

**Resistencia al aire:**

```java
let mover;

function setup() {
  createCanvas(600, 400);
  mover = new Mover(100, 200, 3);
}

function draw() {
  background(220);

  let push = createVector(0.3, 0);
  mover.applyForce(push);

  // --- DRAG (resistencia del aire)
  let speed = mover.velocity.mag();

  if (speed > 0) {
    let drag = mover.velocity.copy();
    drag.mult(-1);

    let c = 0.02; 
    let dragMagnitude = c * speed * speed;

    drag.normalize();
    drag.mult(dragMagnitude);

    mover.applyForce(drag);
  }

  mover.update();
  mover.show();
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
    fill(50);
    circle(this.position.x, this.position.y, this.mass * 20);
  }
}
```
<br>

**Atracción gravitaciona:**

```java
let moverA;
let moverB;
let G = 0.4;

function setup() {
  createCanvas(600, 400);
  moverA = new Mover(width/3, height/2, 10);
  moverB = new Mover(2*width/3, height/2, 20);
}

function draw() {
  background(220);

  let force = gravitationalAttraction(moverA, moverB);
  moverA.applyForce(force);

  moverA.update();
  moverB.update();

  moverA.show();
  moverB.show();
}

function gravitationalAttraction(a, b) {
  let force = p5.Vector.sub(b.position, a.position);
  let distance = force.mag();
  distance = constrain(distance, 5, 50);

  let strength = (G * a.mass * b.mass) / (distance * distance);

  force.setMag(strength);
  return force;
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
    fill(0);
    circle(this.position.x, this.position.y, this.mass);
  }
}
```
<br>

## Bitácora de aplicación 



## Bitácora de reflexión
