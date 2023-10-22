# Seminario: Mundos virtuales. Introducción a la programación de gráficos 3D.

## Ejercicio 1 Qué funciones se pueden usar en los scripts de Unity para llevar a cabo traslaciones, rotaciones y escalados.

Se utilizan Transform.Translate(Vector3 direction), Transform.Rotate(Rotate(float xAngle, float yAngle, float zAngle) y la propiedad Transform.localScale que permite cambiar el escalado de un objeto con respecto a su padre.

## Ejercicio 2 Como trasladarías la cámara 2 metros en cada uno de los ejes y luego la rotas 30º alrededor del eje Y?. Rota la cámara alrededor del eje Y 30ª y desplázala 2 metros en cada uno de los ejes. ¿Obtendrías el mismo resultado en ambos casos?. Justifica el resultado

En el primer caso, ejecutaría:
```csharp
camera.transform.Translate(2, 2, 2);
camera.transform.Rotate(0, 30, 0);
En el segundo, ejecutaría:
camera.transform.Rotate(0, 30, 0);
camera.transform.Translate(2, 2, 2);
```
El orden afecta al resultado porque en el primer caso la cámara se mueve usando los ejes iniciales, pero en el segundo cuando se mueva tendrá en cuenta los nuevos ejes que se obtienen tras la rotación.
## Ejercicio 3 Sitúa la esfera de radio 1 en el campo de visión de la cámara y configura un volumen de vista que la recorte parcialmente.

## Ejercicio 4 Sitúa la esfera de radio 1 en el campo de visión de la cámara y configura el volumen de vista para que la deje fuera de la vista.

## Ejercicio 5 Como puedes aumentar el ángulo de la cámara. Qué efecto tiene disminuir el ángulo de la cámara.

## Ejercicio 6 Es correcta la siguiente afirmación: Para realizar la proyección al espacio 2D, en el inspector de la cámara, cambiaremos el valor de projection, asignándole el valor de orthographic

## Ejercicio 7 Especifica las rotaciones que se han indicado en los ejercicios previos con la utilidad quaternion.

## Ejercicio 8 ¿Como puedes averiguar la matriz de proyección en perspectiva que se ha usado para proyectar la escena al último frame renderizado?.

## Ejercicio 9 ¿Como puedes averiguar la matriz de proyección en perspectiva ortográfica que se ha usado para proyectar la escena al último frame renderizado?.

## Ejercicio 10 ¿Cómo puedes obtener la matriz de transformación entre el sistema de coordenadas local y el mundial?.

## Ejercicio 11 Cómo puedes obtener la matriz para cambiar al sistema de referencia de vista

## Ejercicio 12 Especifica la matriz de la proyección usado en un instante de la ejecución del ejercicio 1 de la práctica 1.

## Ejercicio 13 Especifica la matriz de modelo y vista de la escena del ejercicio 1 de la práctica 1.

## Ejercicio 14 Aplica una rotación en el start de uno de los objetos de la escena y muestra la matriz de cambio al sistema de referencias mundial.

## Ejercicio 15 ¿Como puedes calcular las coordenadas del sistema de referencia de un objeto con las siguientes propiedades del Transform:?: Position (3, 1, 1), Rotation (45, 0, 45)


