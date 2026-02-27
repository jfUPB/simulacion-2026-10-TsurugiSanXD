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

**Actividad 4.**
<br>

**1)R\:** Mi obra “Relación de tres” trata sobre dos particulas de distinto tipo que se atraen constantemente, como si fueran una pareja. Esa atracción está basada en una fórmula tipo gravedad, que hace que su aceleración dependa de la distancia entre ellas. Agregue fricción para que no se muevan sin control y puedan estabilizarse. Tambien hay una pequeña repulsión entre particulas del mismo tipo para que no se amontonen, el mouse funciona como un tercer elemento que altera la relación, porque cuando se acerca atrae a ambas partículas y rompe el equilibrio. La historia se cuenta a través de las fuerzas y el movimiento, no con texto sino con el comportamiento del sistema.

<br>
<br>

**Codigo de la aplicación**

<br>

```java
let particles = [];
let G = 0.4;   // fuerza suficiente para que se busquen
let mu = 0.02; // fricción constante

function setup() {
  createCanvas(700, 500);

  for (let i = 0; i < 10; i++) {
    particles.push(new Particle(random(width), random(height), "A"));
    particles.push(new Particle(random(width), random(height), "B"));
  }
}

function draw() {
  background(15, 20);

  for (let p of particles) {
    p.applyInteractions(particles);
    p.applyMouseForce();
    p.applyFriction();   // usamos FRICCIÓN real
    p.applyBounds();
    p.update();
    p.show();
  }
}

class Particle {
  constructor(x, y, type) {
    this.position = createVector(x, y);
    this.velocity = p5.Vector.random2D().mult(1.5);
    this.acceleration = createVector(0, 0);
    this.mass = 2;
    this.type = type;
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acceleration.add(f);
  }

  applyInteractions(others) {
    for (let other of others) {
      if (other !== this) {

        let force = p5.Vector.sub(other.position, this.position);
        let distance = force.mag();
        distance = constrain(distance, 15, 200);

        // Atracción entre distintos tipos
        if (this.type !== other.type) {

          let strength = (G * this.mass * other.mass) / (distance * distance);
          force.setMag(strength);
          this.applyForce(force);

        } else {

          // ligera repulsión entre iguales
          if (distance < 60) {
            let repel = p5.Vector.sub(this.position, other.position);
            repel.normalize();
            repel.mult(0.3);
            this.applyForce(repel);
          }

        }
      }
    }
  }

  // FRICCIÓN CONSTANTE (actividad 3)
  applyFriction() {
    if (this.velocity.mag() > 0) {
      let friction = this.velocity.copy();
      friction.mult(-1);
      friction.normalize();
      friction.mult(mu);
      this.applyForce(friction);
    }
  }

  applyMouseForce() {
    let mouse = createVector(mouseX, mouseY);
    let force = p5.Vector.sub(mouse, this.position);
    let distance = force.mag();

    if (distance < 200) {
      force.setMag(2);
      this.applyForce(force);
    }
  }

  applyBounds() {
    let margin = 40;
    let force = createVector(0, 0);

    if (this.position.x < margin) force.x = 0.6;
    if (this.position.x > width - margin) force.x = -0.6;
    if (this.position.y < margin) force.y = 0.6;
    if (this.position.y > height - margin) force.y = -0.6;

    this.applyForce(force);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.velocity.limit(4);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    noStroke();

    if (this.type === "A") {
      fill(255, 120, 160, 180);
    } else {
      fill(120, 160, 255, 180);
    }

    circle(this.position.x, this.position.y, 11);
  }
}
```

<br>
<br>

**Enlace P5:**  https://editor.p5js.org/luisafer1845/sketches/uHhD4WnA7

<br>
<br>

**Capturas de pantalla**

<br>

<img width="1<img width="1916" height="868" alt="Captura de pantalla 2026-02-27 004506 - copia" src="https://github.com/user-attachments/assets/09eba5df-d9ca-46ba-b114-aabf27ceedc0" />

<img width="1919" height="868" alt="Captura de pantalla 2026-02-27 004518 - copia" src="https://github.com/user-attachments/assets/f239947b-26c9-433a-8dff-30c1e4e8c3bc" />


<img width="1919" height="865" alt="Captura de pantalla 2026-02-27 004551" src="https://github.com/user-attachments/assets/03b11e31-e2b0-412d-a8b6-ab39c8e633de" />



## Bitácora de reflexión

