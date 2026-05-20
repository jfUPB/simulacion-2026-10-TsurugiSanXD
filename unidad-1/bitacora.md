# Unidad 1

## Bitácora de proceso de aprendizaje

## ***Actividad 1.***

*Aleatoriedad en el arte genartivo:*
La aletoriedad le da un factor de cratividad sorpresa al arte generativo.


## ***Actividad 2.***
**¿Que espero que suceda?**
R\: Con las modificaciones que hice espero que cambie de color a un azul, que en la pantalla se muestre una elipse en vez de un punto y que la elipse suba más de lo que.
<br>
<br>
<br>
***¿Que paso realmente?*** 
R\: Cuando ejecute el codigo casi todo lo que plantee funciono. En vez de un punto tenia una elipse, la elipse si era de color azul, pero lo que me fallo fue el movimiento, dado que la elipse se quedo quieta en el centro. Fue facil de solucinar porque en realidas solo habia pasado que en uno de los condicionales escribí "choise" en vez de "choice", pero cuando corregi la sintaxis ya funciono como yo esperaba.

## ***Codigo***

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
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(100, 150, 255);
    ellipse(this.x, this.y, 4, 4);
  }

  step() {
    const choice = floor(random(5));
    if (choice == 0) {
      this.x++;
    } else if (choice == 1) {
      this.x--;
    } else if (choice == 2) {
      this.y++;
    } else if (choice == 3){
      this.y--;
    } else {
      this.y--;
    }
  }
}
```

## ***Actividad 3.***

1)R:\ La diferencia entre la distribución uniforme y la no uniforme consiste en, que ladistrobucipon uniforme podemos tomarla por así decirlo como igualitaria, dado que todas las variables tendran la misma probabilidad de "creecer" por así decirlo. En cambio la ditribución uniforme no actua igual para todas las variables, habra unas que creceran más rapido que otras, dado que las probabilidades no seran iguales y el mayor crecimiento se vera en en la media de las variables.

## ***Codigo: Modificación traditional random walker donde se favorezca ir a la derecha***

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
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(255, 150, 255);
    ellipse(this.x, this.y, 4, 4);
    fill(100, 150, 255, 255);
  }

  step() {
    const choice = floor(random(5));
    if (choice == 0) {
      this.x++;
    } else if (choice == 1) {
      this.x++;
    } else if (choice == 2) {
      this.y++;
    } else if (choice == 3){
      this.x++;
    } else {
      this.y--;
    }
  }
}
```

## **Actividad 4.**
***Codigo***
```java
let bins = [];
let numBins = 40;

function setup() {
  createCanvas(640, 240);
  background(255);

  // inicializamos el histograma
  for (let i = 0; i < numBins; i++) {
    bins[i] = 0;
  }
}

function draw() {
  background(255);

  // generar un valor con distribución normal
  let x = randomGaussian(width / 2, 60);

  // convertir el valor a un índice del histograma
  let index = floor(map(x, 0, width, 0, numBins));

  if (index >= 0 && index < numBins) {
    bins[index]++;
  }

  // dibujar las barras
  let w = width / numBins;

  for (let i = 0; i < numBins; i++) {
    let h = bins[i];
    fill(120, 150, 255);
    noStroke();
    rect(i * w, height - h, w - 1, h);
  }
}

```
<br>
<br>
<br>

***Link al codigo en p5:*** https://editor.p5js.org/luisafer1845/sketches/iffAJJKJs
<br>
<br>
<br>

***Captura de pantalla:***
<img width="1918" height="811" alt="image" src="https://github.com/user-attachments/assets/5966deda-1b49-467e-874a-965fab4b5e68" />


## **Actividad 5.**

**Resultado esperado:** Bueno, para esta tecnica utilice LÉVY FLIGHT debido a que queria lograr hacer saltos grandes y aleatorios. Utilizando el codigo del traditional random walk con algunas modificaciones implemente en el codigo un par de lineas con las que espero lograr que el random walk ya no sea totalmente seguido, si no que puedar dar saltos y desplazarse a los largo de todo el canva.

***Codigo***
```java
let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(100, 150, 255, 50);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(200, 255, 100, 100);
    square(this.x, this.y, 20);
  }

  step() {
    // tamaño del paso
    let stepSize = random(1);

    // de vez en cuando, salto grande
    if (random(1) < 0.01) {
      stepSize = random(50, 120);
    }

    let direction = floor(random(4));

    if (direction === 0) this.x += stepSize;
    else if (direction === 1) this.x -= stepSize;
    else if (direction === 2) this.y += stepSize;
    else this.y -= stepSize;
  }
}
```
<br>
<br>
<br>

***Link al codigo en p5:*** https://editor.p5js.org/luisafer1845/sketches/9woKjoJux
<br>
<br>
<br>

***Captura de pantalla:***
<img width="1919" height="815" alt="image" src="https://github.com/user-attachments/assets/9c078ec5-31d9-4532-86b4-e48eb233d580" />


## ***Actividad 6.***

**Resultado esperado:** Para esta parte pretendia simular más o menos el movimiento de una nube, por eso lo hice con varios circulos Ya para el funcionamiento, esperaba mostrar el concepto de ruido perlin a través de hacer que el circulo se moviera suavemente y sin cambios muy grandes entra cada "paso" que daba; quiero mostrar un movimiento continuo y natural.

***Codigo***
```java
let t = 0;

function setup() {
  createCanvas(640, 240);
}

function draw() {
  background(135, 206, 235); // cielo azul

  // posición base vertical (la nube se mantiene a esta altura)
  let baseY = height / 2;

  // ruido Perlin para movimiento horizontal
  let offsetX = map(noise(t), 0, 1, -100, 100);

  // posición base horizontal + movimiento suave
  let baseX = width / 2 + offsetX;

  noStroke();
  fill(255, 230); // blanco con un poco de transparencia

  // dibujamos varios círculos = nube
  circle(baseX - 40, baseY, 50);
  circle(baseX, baseY - 10, 60);
  circle(baseX + 40, baseY, 50);
  circle(baseX + 10, baseY + 10, 45);

  // avanzar suavemente en el ruido
  t += 0.01;
}
```
<br>
<br>
<br>

***Link al codigo en p5:*** https://editor.p5js.org/luisafer1845/sketches/8cRvwr9WK
<br>
<br>
<br>

***Captura de pantalla:***
<img width="1912" height="812" alt="image" src="https://github.com/user-attachments/assets/b5b7c15c-3348-4993-8bb2-07a097fcdb1b" />

## Bitácora de aplicación 

## **Actividad 7.**

1)R:\ **¿Ques una obra generativa?**
Una obra generativa es basicamente una creación artistica basada en la alatoriedad y el tiempo para producir resultados variables (que no son fijos). En las obras genarativas el artistas en vez de hacer algo fijo, que tenga la misma apariencia crea una serie de instrucciones/normas que seguir para que la obra cambie por si misma, lo cual, hace que la obra nunca sea la misma. Ya que la obra depende de la aleatoriedad esta siempre sera diferente dependiende la acción que el usuario ejecute con ella, la cual la convierte en una experiencia unica siempre. 
<br>
<br>
<br>

2)R:\ **Link al codigo en p5:** https://editor.p5js.org/luisafer1845/sketches/YaxjOJLqG
<br>
<br>
<br>

3)R:\ **Captura de pantalla:**
<img width="1919" height="868" alt="image" src="https://github.com/user-attachments/assets/86126318-2ebf-4cec-a319-915714a805bf" />

<br>


## Bitácora de reflexión

## ***Actividad 8.***
**1)R\:** **Diferencia entre random() y noise() ¿En que casos se utilizan?:** La principal diferencia es como actuan estos dos; mientras random da valores completamente al azar, que pueden estar muy dispersos entre si, causando cambios bruscos e impredecibles. Por otro lado, noise es mucho más organizado, el movimiento es mucho más suave y continuo, ya que al tomar valores muy cercanos entre si hace que el movimiento sea más natural y tenga transiciones suaves.
<br>
<br>

**2)R\:** **distribución de probabilidad ¿Qué diferencia visual produce una caminata aleatoria con una distribución uniforme versus una con una distribución normal?** Una distribución de probabilidad basicamente describe qué tan probable es que aparezcan ciertos valores cuando usamos números aleatorios. La principal diferencia entre estas dos es que en la distribución unirforme al tener todos los valores la misma probabilidad hace que en una caminata aleatoria se vea mucho más dispersa y tenga saltos más bruscos e impredecibles, en cambio, la caminata normal esta más llevada por un promedio, los valores tienden a quedarse más en el centro, probocando que en una caminada aleatoria se vean acumulaciones y zonas mucho más oscuras, junto con un movimiento más controlado.
<br>
<br>

**3)R\:** **¿Cuál es el papel de la aleatoriedad en el arte generativo?** La aleatoriedad es importante en el arte generativo dado que es lo que le brinda la capacidad al codigo de introducir una **variación** que hace que cada interacción con el codigo en tiempo real sea totalmente nueva usando el mismo codigo. Tambien rompe **patrones rigidos** que hacen que las obras sean demasido perfectas o hasta iguales, donde así un resultado más natural a través de la aleatoriedad.

**4)R\:** En mi obra final utilicé aleatoriedad uniforme mediante la función random(), aplicada al color, tamaño y posición de las figuras, combinada con la interacción del mouse. Esta elección fue adecuada porque permitió generar variaciones constantes dentro de rangos controlados, haciendo que cada interacción produjera un resultado distinto sin perder coherencia visual. La aleatoriedad uniforme aporta dinamismo y hace que la obra sea verdaderamente generativa, ya que no se repite nunca de la misma forma y responde directamente al usuario.

**5)R\:** **¿Qué es un “paseo” o “caminata” (walk) en el contexto de la simulación? ¿Qué característica particular tiene una caminata de tipo “Lévy flight”?:** Un paseo o walk en simulación es basicamente un proceso en donde un objeto se mueve paso a paso, el cual decide en que dirección ir según valores aleatorios. En el caso de una caminata tipo Lévy flight consiste en que una caminata se ejecute y basado en una probabilidad establecida en el codigo de repente en el walk se va a dar un paso muy grande, por ejemplo: el sistema va contando 1,2,3... y de repende cae en el valor de la probabilidad establecida y pum salta a otra posición muy alejada y totalmente aleatoria.






























