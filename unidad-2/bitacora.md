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

```


## Bitácora de aplicación 



## Bitácora de reflexión


