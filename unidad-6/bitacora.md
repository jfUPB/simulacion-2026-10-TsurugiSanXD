# Unidad 6

## Bitácora de proceso de aprendizaje


## Actividad 1.

***1) Selecciona dos imágenes o piezas de Tyler Hobbs que te llamen la atención.*** <br>
***R\:*** La dos referencias que seleccione son: Las obras de la serie Flow Fields (explicadas en su texto) y la serie Fidenza, que utiliza flow fields como base visual.

<br>

***2) Describe qué decisiones visuales reconoces en ellas:*** <br>
***R\:*** <br>

***Composición*** <br>
Las piezas están organizadas a partir de trayectorias curvas que recorren todo el espacio. No hay un centro fijo, sino una distribución que se siente fluida y continua.

<br>

***Densidad*** <br>
La densidad varía: hay zonas más cargadas de líneas y otras más vacías. Esto genera contraste visual y guía la mirada.

<br>

***Dirección del movimiento*** <br>
El movimiento está determinado por un sistema invisible (flow field) que define hacia dónde se mueven las líneas. Todas siguen reglas locales pero crean patrones globales coherentes.

<br>

***Color*** <br>
Se utilizan paletas controladas (a veces probabilísticas), donde ciertos colores aparecen más que otros. Esto genera armonía sin perder variación.

<br>

***Ritmo*** <br>
El ritmo se percibe en la repetición de curvas y en la longitud de las trayectorias: líneas largas generan fluidez, líneas cortas generan textura.

<br>

***Repetición y variación*** <br>
Se repiten estructuras (curvas), pero cada una tiene pequeñas variaciones en dirección, tamaño o color, lo que evita que la imagen se vea mecánica.

<br>

***3) Explica por qué esas decisiones te parecen potentes.*** <br>
***R\:*** Estas decisiones son potentes porque logran un equilibrio entre orden y caos, por un lado, hay reglas claras (el sistema que guía las líneas), pero por otro lado hay variación suficiente para que el resultado se vea orgánico. Esto hace que la obra parezca natural, como si fuera un flujo de agua, viento o crecimiento biológico, aunque en realidad está completamente generada por un sistema.

<br>

***4) Escribe una hipótesis: ¿Qué tipo de reglas o sistema crees que podrían estar detrás de esa pieza?*** <br>
***R\:*** Creo que estas piezas funcionan a partir de una grilla donde cada punto tiene una dirección que, en conjunto, forma un campo de flujo que guía el movimiento de líneas o partículas. Estas se desplazan siguiendo esas direcciones desde distintos puntos iniciales, mientras el sistema aplica reglas como evitar superposición, variar el color y controlar la longitud. Esto genera curvas orgánicas y fluidas, ya que los cambios de dirección son suaves, produciendo un resultado visual natural.

## Actividad 2.

***1) Explica con tus propias palabras qué es un agente autónomo.*** <br>
***R\:*** Un agente autónomo es una entidad que puede tomar decisiones por sí misma dentro de un entorno. No solo reacciona a fuerzas externas, sino que percibe lo que ocurre y actúa según objetivos propios, como acercarse, evitar o seguir algo, lo que hace que su comportamiento se vea más natural.

<br>

***2) Explica qué es una "steering force".*** <br>
***R\:*** Una steering force es una fuerza que el mismo agente genera para cambiar su movimiento según un objetivo. Surge al comparar hacia dónde quiere ir con cómo se está moviendo, aplicando una corrección para dirigir su trayectoria.

<br>

***3) compara una "steering force" con una fuerza externa como la gravedad.*** <br>
***R\:*** Las fuerzas externas, como la gravedad, actúan siempre igual sobre un objeto sin que este tenga control. En cambio, una steering force depende del agente y de lo que percibe, por lo que cambia según la situación y el objetivo.

<br>

***4) Describe por qué estas ideas son útiles para diseñar comportamiento visual y no solo para simular movimiento.*** <br>
***R\:*** Estas ideas permiten crear comportamientos complejos a partir de reglas simples, generando movimientos más naturales y orgánicos. Esto ayuda a diseñar sistemas visuales que parecen tener vida propia, en lugar de animaciones rígidas hechas manualmente.


## Actividad 3. 

***1) ¿Cómo está construido el campo de flujo?.*** <br>
***R\:*** El campo de flujo está construido como una grilla (una cuadrícula) dividida en celdas, donde cada celda contiene un vector. Esta estructura funciona como un mapa invisible que cubre todo el espacio y define direcciones en cada punto.

<br>

***2) ¿Qué representa cada celda o vector del campo?.*** <br>
***R\:*** Cada celda contiene un vector que representa una dirección (y a veces magnitud) hacia donde debería moverse un agente en esa posición. Es como una flecha que indica el “flujo” del sistema en ese punto, similar a los campos de vectores en física donde cada punto tiene una dirección asociada.

<br>

***3) ¿Cómo usa un agente su posición para consultar el campo?.*** <br>
***R\:*** El agente toma su posición en el espacio y la convierte en índices de la grilla para saber en qué celda está. Luego consulta el vector de esa celda para saber hacia dónde debería moverse, usando ese valor como guía.

<br>

***4) Cómo se convierte el vector consultado en una decisión de movimiento?.*** <br>
***R\:*** El vector obtenido se usa como una dirección deseada, y el agente genera una steering force para ajustar su velocidad hacia esa dirección. Es decir, no se mueve instantáneamente, sino que corrige su movimiento poco a poco para alinearse con el flujo.

<br>

***5) Identifica parámetros importantes del sistema.*** <br>
***R\:*** La resolución define qué tan grande o pequeña es cada celda del campo, afectando el detalle del movimiento. El "maxspeed" limita la velocidad máxima del agente, mientras que el "maxforce" controla qué tan rápido puede cambiar de dirección. La cantidad de agentes influye en la densidad visual y en qué tan complejo se ve el sistema.

<br>

***6) Realiza al menos una modificación y analiza el efecto visual que produce.*** <br>
***R\:*** Si se modifica, por ejemplo, la resolución o los valores del ruido (Perlin noise), el campo cambia completamente: puede volverse más suave y fluido o más caótico. Esto altera el comportamiento de los agentes, haciendo que el movimiento se vea más organizado o más impredecible.

<br>

***A) ¿Qué tipo de movimiento produce este algoritmo?*** <br>
***R\:*** Produce un movimiento fluido y continuo, donde los agentes parecen seguir corrientes invisibles, similar al comportamiento de partículas en agua o viento, generando trayectorias suaves y conectadas.

<br>

***B) ¿Qué sensaciones visuales te sugiere?*** <br>
***R\:***  Genera sensaciones de fluidez, organicidad y naturaleza, como si se tratara de corrientes, humo o enjambres. Dependiendo de los parámetros, puede sentirse calmado o caótico, pero siempre dinámico.

<br>

***C) ¿En qué tipo de pieza musical imaginas que podría funcionar bien?*** <br>
***R\:*** Podría funcionar muy bien en música ambiental, electrónica o experimental, donde los movimientos fluidos acompañen sonidos continuos o atmósferas. También encaja con música lo-fi o sound design más orgánico.


## Actividad 4. 


***1) Explica con tus palabras las tres reglas básicas: separación, alineación, cohesión.*** <br>
***R\:*** La separación es la regla que hace que cada agente evite estar demasiado cerca de los demás, generando una fuerza que lo aleja de sus vecinos cercanos. La alineación hace que el agente intente igualar su velocidad con la de los otros agentes que tiene alrededor, moviéndose en la misma dirección. La cohesión, en cambio, hace que el agente se mueva hacia el centro del grupo de vecinos, manteniendo la unión del conjunto. Estas tres reglas trabajan juntas y, aunque son simples, permiten que surja un comportamiento colectivo complejo.

<br>

***2) Identifica qué parámetros controlan estas reglas.*** <br>
***R\:*** Estas reglas se controlan principalmente mediante los pesos que se les asignan a cada comportamiento (separación, alineación y cohesión), que determinan qué tan fuerte influye cada uno. También intervienen parámetros como la distancia de percepción, que define qué vecinos afectan al agente, y valores como maxspeed y maxforce, que limitan la velocidad máxima y la intensidad de las fuerzas aplicadas.

<br>

***3) Modifica uno o más pesos del sistema y describe el efecto visual y colectivo.*** <br>
***R\:*** Al modificar los pesos de las reglas, el comportamiento cambia notablemente. Por ejemplo, al aumentar el peso de separación, los agentes tienden a dispersarse más; al aumentar la cohesión, se agrupan con mayor fuerza; y al aumentar la alineación, se mueven más sincronizados. Esto transforma la forma y dinámica del grupo, haciendo que el sistema se vea más ordenado o más desorganizado según el ajuste.

<br>

***4) Describe el comportamiento emergente observado: compacto, disperso,  estable, nervioso, caótico, fluido.*** <br>
***R\:*** El comportamiento emergente depende del equilibrio entre las tres reglas. Puede verse compacto si predomina la cohesión, disperso si domina la separación, estable si hay balance entre las fuerzas, nervioso si los cambios son bruscos, caótico si no hay coherencia clara, o fluido cuando los agentes se mueven de manera continua y armoniosa. Todo esto surge sin un control central, solo a partir de reglas locales.

<br>

***A) ¿Qué atmósfera visual produce el flocking?*** <br>
***R\:*** El flocking genera una atmósfera orgánica y dinámica, donde los agentes parecen comportarse como un sistema vivo. Se percibe movimiento colectivo coherente, con patrones que cambian constantemente pero mantienen cierta unidad.

<br>

***B) ¿En qué tipo de relación con una canción podría funcionar mejor este algoritmo?*** <br>
***R\:*** Este algoritmo funciona bien con música que tenga continuidad y capas, como ambient o electrónica suave, donde el movimiento colectivo pueda acompañar el flujo del sonido. También puede responder a cambios en intensidad, volviéndose más caótico o más ordenado según la energía de la música.


## Actividad 5. 

***Comparación entre flow fields y flocking*** <br>
Los flow fields producen un movimiento continuo y fluido donde los agentes siguen direcciones definidas por un campo de vectores, lo que genera trayectorias suaves y parecidas a corrientes de agua o viento. En cambio, el flocking produce un movimiento colectivo más dinámico basado en la interacción entre agentes, donde se forman grupos que se separan, se alinean y se reorganizan constantemente. En términos de control visual, los flow fields ofrecen un mayor control global, ya que el diseñador define directamente la estructura del campo, mientras que el flocking tiene menos control directo y depende más de la interacción local entre agentes.

En cuanto al nivel de emergencia, en los flow fields es moderado porque aunque el movimiento es generado por reglas, el comportamiento está guiado por una estructura previa; en el flocking es alto, ya que patrones complejos surgen únicamente de reglas simples sin una guía global. A nivel de atmósfera, los flow fields generan sensaciones más calmadas, fluidas y orgánicas, mientras que el flocking puede sentirse más vivo, energético y cambiante. En relación con la música, los flow fields funcionan bien con sonidos continuos o ambientales, mientras que el flocking se adapta mejor a ritmos dinámicos o cambios de intensidad. Como ventaja, los flow fields permiten dirigir el comportamiento de forma clara, pero pueden volverse predecibles; el flocking genera comportamientos más naturales y variados, pero es más difícil de controlar con precisión.

<br>

***¿Qué algoritmo usar según el tipo de canción?***
Para una canción contemplativa usaría flow fields, porque su movimiento suave y continuo genera una sensación de calma y flujo constante. Para una canción agresiva usaría flocking, ya que puede volverse caótico, rápido y con cambios bruscos que transmiten energía. En una canción melancólica también elegiría flow fields, porque sus trayectorias fluidas pueden transmitir suavidad y sensación emocional sostenida. Finalmente, para una canción eufórica usaría flocking, ya que el movimiento colectivo, dinámico y cambiante puede representar mejor la intensidad y la energía alta.


## Bitácora de aplicación 

## Actividad 6.

***Tema visual de la pieza*** <br>
Usando la canción "secret garden" busco representa a través de un flujo continuo de agentes el crecimiento y surgimiento de la flores. Usando como base para el concepto la enfermedad ficticia "hanahaki" que consiste en que al enefermo le crecen flores desde el interior de su cuerpo; siendo que la protagonista de la canción sufre de esta enfermedad.

<br>

***Relación con el tema musical*** <br>
En las partes más fuertes de la canción el número de agentes que forman las flores en pantalla va aumentando, para representar el avance y empeoro de la enfermedad.

<br>

***Moodboard*** 
<br>
<img width="1920" height="1080" alt="Diseño sin título" src="https://github.com/user-attachments/assets/fd3ec58a-a3a0-4afa-8553-38e6a6c1ec69" />
<br>


***boceto*** 
<br>
<img width="960" height="1280" alt="WhatsApp Image 2026-04-17 at 4 08 23 AM" src="https://github.com/user-attachments/assets/71d44e5f-66a7-44e7-96ff-be7ba1fa7eaf" />
<br>

***Mapa de decisiones*** <br>
***Color negro de fondo:*** Representa el vacio y la muerte que atrae la enfermedad.
<br>

***Color amarillo de las flores:*** Representan el brillo efimero de una person a punto de morir.
<br>

***Color rojo de las flores:*** Representan el deterioro de la persona y su inminente final.
<br>

***tallo de la flor*** Representan el crecimiento de una nueva vida, que se aferra a otra, la desgasta y la desaparece para poder crecer.
<br>

***Mapa de interpretación*** <br>
***C:*** Hace que la flor vuelva a crecer y cambie de color, ya sea amaraillo o rojo.
<br>

***Espacio:*** Causa que el flow field se vuelva caotico.
<br>

***Musica:*** Controla la frecuencia con la que emergen las flores. 

<br>

***Link al instrumento visual:*** https://editor.p5js.org/luisafer1845/sketches/cmGOlhJ2F

<br>

***codigo:*** <br>

```


let stressMode = false;

let song, amp, fft;
let particles = [];
let started = false;
let flowfield;
let spacing = 20;

let centerX, centerY;
let centralRadius = 180;

let maxParticles = 2500;

let growPhase = 0;
let openAmt = 0;
let stemLen = 0;

let useRed = false;

let centralDead = false;
let respawnTimer = 0;

let bassAvg = 0;

const COL_YELLOW = [255, 220, 60];
const COL_RED = [220, 40, 60];
let currentCol = COL_YELLOW;

function preload(){
  soundFormats('mp3','wav');
  song = loadSound('flower.mp3');
}

function setup(){
  createCanvas(windowWidth, windowHeight);
  background(5,0,8);

  amp = new p5.Amplitude();
  fft = new p5.FFT(0.85, 64);

  initializeFlowField();

  centerX = width/2;
  centerY = height/2 + 40;
}

function draw(){

  if(!started){
    background(5,0,8);

    fill(180,140,60);
    textAlign(CENTER,CENTER);
    text('"Tus flores brotan sin permiso"', width/2, height/2);
    text("click para florecer", width/2, height/2 + 40);
    return;
  }

  background(5,0,8,20);

  let level = amp.getLevel();
  fft.analyze();

  let bass = fft.getEnergy("bass");
  let mid  = fft.getEnergy("mid");
  let treble = fft.getEnergy("treble");

  currentCol = useRed ? COL_RED : COL_YELLOW;

  bassAvg = lerp(bassAvg, bass, 0.05);

  flowfield.update(level);

 
  if(growPhase === 1){
    stemLen += map(level, 0, 0.3, 0.5, 3);
    stemLen = constrain(stemLen, 0, 140);

    drawStem();

    if(stemLen >= 140){
      growPhase = 2;
    }
    return;
  }

  if(growPhase === 2){

    drawStem();

    let growthSpeed = map(level, 0, 0.3, 0.003, 0.03);
    openAmt = min(openAmt + growthSpeed, 1);

    let radius = map(openAmt, 0, 1, 20, 220);

    if(frameCount % 10 === 0){
      spawnFlower(centerX, centerY - stemLen, radius, 120, currentCol, true);
      spawnCore(centerX, centerY - stemLen, radius * 0.5, bass);
    }

    if(openAmt >= 1){
      growPhase = 3;
    }
  }

  if(growPhase === 3){

    drawStem();

    if(frameCount % 8 === 0){
      let size = map(bass, 0, 255, 140, 240);

      spawnFlower(centerX, centerY - stemLen, size, 140, currentCol, true);
      spawnCore(centerX, centerY - stemLen, size * 0.5, bass);
    }

  
    let voiceEnergy = mid;

    let spawnRate = map(voiceEnergy, 0, 255, 80, 10);
    let spawnAmount = floor(map(voiceEnergy, 0, 255, 1, 6));

    if(frameCount % floor(spawnRate) === 0){
      for(let i = 0; i < spawnAmount; i++){
        spawnCanvasFlowers(voiceEnergy);
      }
    }

    if(level < 0.025){
      centralDead = true;
    }

    if(centralDead){
      respawnTimer++;
      if(respawnTimer > 60){
        resetCentral();
      }
    }
  }


  for(let i = particles.length - 1; i >= 0; i--){
    let p = particles[i];
    p.update(level, bass, treble);
    p.show();

    if(p.isDead()){
      particles.splice(i,1);
    }
  }

  if(particles.length > maxParticles){
    particles.splice(0, particles.length - maxParticles);
  }
}


function drawStem(){
  let x = centerX;
  let baseY = height/2 + 120;
  let tipY = baseY - stemLen;

  stroke(70,130,70,200);
  strokeWeight(3);
  noFill();

  beginShape();
  vertex(x, baseY);
  bezierVertex(
    x+20, baseY - stemLen*0.3,
    x-20, baseY - stemLen*0.7,
    x, tipY
  );
  endShape();
}


function spawnCore(cx, cy, radius, intensity){

  let layers = floor(map(intensity, 0, 255, 3, 10));
  let points = 20;

  for(let l = 0; l < layers; l++){

    let rFactor = map(l, 0, layers, 0.1, 0.9);

    for(let i = 0; i < points; i++){

      if(particles.length > maxParticles) return;

      let angle = map(i, 0, points, 0, TWO_PI);

      let petal = pow(abs(sin(angle * 4)), 0.6);
      let r = radius * rFactor * (0.4 + petal * 0.6);

      let x = cx + cos(angle) * r;
      let y = cy + sin(angle) * r;

      particles.push(new Particle(x,y,cx,cy,angle,radius,currentCol,true));
    }
  }
}


function spawnCanvasFlowers(energy){

  let distFromCenter = map(energy, 0, 255, width*0.45, width*0.25);
  let angle = random(TWO_PI);

  let x = centerX + cos(angle)*distFromCenter;
  let y = centerY + sin(angle)*distFromCenter;

  if(dist(x,y,centerX,centerY) < centralRadius + 60) return;

  let r = map(energy, 0, 255, 30, 80);

  spawnFlower(x,y,r,80,currentCol,false);
  spawnCore(x,y,r*0.5,energy);
}


function spawnFlower(cx,cy,radius,count,col,isCentral){

  for(let i=0;i<count;i++){

    if(particles.length > maxParticles) return;

    let angle = map(i,0,count,0,TWO_PI);
    let petal = pow(abs(sin(angle*4)),0.6);
    let r = radius*(0.35 + petal*0.68);

    let x = cx + cos(angle)*r;
    let y = cy + sin(angle)*r;

    particles.push(new Particle(x,y,cx,cy,angle,radius,col,isCentral));
  }
}


function initializeFlowField(){
  flowfield = new FlowField(spacing);
}

class FlowField{
  constructor(spacing){
    this.spacing = spacing;
    this.cols = floor(width/spacing)+1;
    this.rows = floor(height/spacing)+1;
    this.field = [];
    this.zoff = 0;
    this.init();
  }

  init(){
    for(let i=0;i<this.cols;i++){
      this.field[i]=[];
      for(let j=0;j<this.rows;j++){
        let angle = noise(i*0.1,j*0.1)*TWO_PI;
        this.field[i][j]=p5.Vector.fromAngle(angle);
      }
    }
  }

  update(level){
    let speed = stressMode ? 0.01 : map(level,0,0.4,0.001,0.004);
    this.zoff += speed;

    for(let x=0;x<this.cols;x++){
      for(let y=0;y<this.rows;y++){
        let angle = noise(x*0.05,y*0.05,this.zoff)*TWO_PI*2;

        if(stressMode){
          angle *= 2; // 🔥 caos
        }

        this.field[x][y]=p5.Vector.fromAngle(angle);
      }
    }
  }

  lookup(pos){
    let col = floor(constrain(pos.x/this.spacing,0,this.cols-1));
    let row = floor(constrain(pos.y/this.spacing,0,this.rows-1));
    return this.field[col][row].copy();
  }
}


class Particle{
  constructor(x,y,cx,cy,angle,radius,col,isCentral){
    this.pos=createVector(x,y);
    this.prev=this.pos.copy();
    this.vel=p5.Vector.random2D().mult(0.2);
    this.acc=createVector();

    this.center=createVector(cx,cy);
    this.angle=angle;
    this.radius=radius;
    this.col=col;

    this.life = isCentral ? random(180,240) : random(120,180);
    this.maxLife=this.life;

    this.size = isCentral ? random(1.2,2) : random(1,1.6);
  }

  update(level,bass,treble){
    this.prev=this.pos.copy();

    let petal = pow(abs(sin(this.angle*4)),0.6);
    let r = this.radius*(0.35 + petal*0.68);

    let target=createVector(
      this.center.x+cos(this.angle)*r,
      this.center.y+sin(this.angle)*r
    );

    let force=p5.Vector.sub(target,this.pos);
    force.mult(0.05);
    this.acc.add(force);

    let flow=flowfield.lookup(this.pos);
    let strength = stressMode ? 0.6 : map(level,0,0.4,0.03,0.3);
    flow.mult(strength);
    this.acc.add(flow);

    this.vel.add(this.acc);
    this.vel.limit(stressMode ? 4 : 2);
    this.pos.add(this.vel);
    this.acc.mult(0);

    this.life -= stressMode ? 3 : 2;
  }

  show(){
    let alpha = map(this.life,0,this.maxLife,0,200);
    stroke(...this.col,alpha);
    strokeWeight(this.size);
    line(this.prev.x,this.prev.y,this.pos.x,this.pos.y);
  }

  isDead(){
    return this.life <= 0;
  }
}


function mousePressed(){
  if(!started){
    userStartAudio();
    song.play();
    started = true;
    growPhase = 1;

    fullscreen(true);
    noCursor();
  }
}


function keyPressed(){
  if(key === 'c' || key === 'C'){
    useRed = !useRed;

    particles = [];
    growPhase = 1;
    openAmt = 0;
    stemLen = 0;
    centralDead = false;
  }

  if(key === ' '){
    stressMode = true;
  }
}

function keyReleased(){
  if(key === ' '){
    stressMode = false;
  }
}

function windowResized(){
  resizeCanvas(windowWidth, windowHeight);
  initializeFlowField();

  centerX = width/2;
  centerY = height/2 + 40;
}

```

<br>

***Capturas de pantalla:*** 
<img width="1912" height="1079" alt="Captura de pantalla 2026-04-17 103928" src="https://github.com/user-attachments/assets/547b5ada-8f73-4010-ab0d-e37f5b2afe8b" />

<img width="1919" height="1079" alt="Captura de pantalla 2026-04-17 103938" src="https://github.com/user-attachments/assets/69bd030f-d281-4ea2-92ed-efbb7755c03a" />

<img width="1513" height="820" alt="Captura de pantalla 2026-04-17 103955" src="https://github.com/user-attachments/assets/8c85963a-113f-44c1-8dc1-7c18de58ca52" />

<img width="1919" height="1079" alt="Captura de pantalla 2026-04-17 104019" src="https://github.com/user-attachments/assets/b3dc05f5-7081-42ed-b34e-e06a3982f4c5" />






## Bitácora de reflexión
