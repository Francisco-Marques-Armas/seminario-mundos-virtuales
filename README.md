# Seminario: Mundos virtuales. Introducción a la programación de gráficos 3D.

## Ejercicio 1 Qué funciones se pueden usar en los scripts de Unity para llevar a cabo traslaciones, rotaciones y escalados.

Se utilizan Transform.Translate(Vector3 direction), Transform.Rotate(Rotate(float xAngle, float yAngle, float zAngle) y la propiedad Transform.localScale que permite cambiar el escalado de un objeto con respecto a su padre.

## Ejercicio 2 Como trasladarías la cámara 2 metros en cada uno de los ejes y luego la rotas 30º alrededor del eje Y?. Rota la cámara alrededor del eje Y 30ª y desplázala 2 metros en cada uno de los ejes. ¿Obtendrías el mismo resultado en ambos casos?. Justifica el resultado

En el primer caso, ejecutaría:
```csharp
camera.transform.Translate(2, 2, 2);
camera.transform.Rotate(0, 30, 0);
```
En el segundo, ejecutaría:
```csharp
camera.transform.Rotate(0, 30, 0);
camera.transform.Translate(2, 2, 2);
```

El orden debería influir en lo obtenido porque en el primer caso la cámara se mueve usando los ejes iniciales, pero en el segundo cuando se mueva tendrá en cuenta los nuevos ejes que se obtienen tras la rotación.

## Ejercicio 3 Sitúa la esfera de radio 1 en el campo de visión de la cámara y configura un volumen de vista que la recorte parcialmente.

Podemos cambiar el volumen de vista o frustum en el inspector o alterando las propiedades Camera.nearClipPlane o Camera.farClipPlane. Near representa la distancia mínima necesaria para visualizar un objeto y far la distancia máxima. Se puede observar el resultado en la miniatura:

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/c882e221-3cb1-440d-85e7-d8cbe82070c8)

## Ejercicio 4 Sitúa la esfera de radio 1 en el campo de visión de la cámara y configura el volumen de vista para que la deje fuera de la vista.

Se puede aumentar near todavía más para que ni siquiera se observe la esfera:

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/34910937-ecac-4823-93e8-d7703895f05d)

## Ejercicio 5 Como puedes aumentar el ángulo de la cámara. Qué efecto tiene disminuir el ángulo de la cámara.

Se puede alterar la propiedad Camera.fieldOfView. Se pueden observar los efectos...

1. Aumentando el campo de visión:

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/8a972fbc-3941-4107-a94a-ef7256a42b46)

Un objeto en la misma posición parece de menor tamaño al ocupar menor porción del campo de visión.

2. Disminuyendo el campo de visión:

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/39f3116f-423b-4ba4-9768-8508b06e9513)

Se obtiene el efecto contrario.

## Ejercicio 6 Es correcta la siguiente afirmación: Para realizar la proyección al espacio 2D, en el inspector de la cámara, cambiaremos el valor de projection, asignándole el valor de orthographic

Se pierde el efecto de la perspectiva y la distorsión que proporciona dando sentido de profundidad, así que podría considerarse que sí se realiza una proyección al espacio 2D.

En perspectiva:

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/a9bc154d-4890-4fab-9597-501e4ff60f5d)

En ortográfica:

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/5ead5c64-c527-4057-a577-9b36edf3ae34)

## Ejercicio 7 Especifica las rotaciones que se han indicado en los ejercicios previos con la utilidad quaternion.

En el ejemplo de Unity para el uso de Quaternion.Euler (que permite pasar una rotación especificada con grados x, y, z a cuaternión) se resuelve este problema:

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/23a8b496-8086-4bdd-9cb1-651d442832a1)

Para aplicar todas las operaciones realizadas anteriormente, se ejecutaría:

```csharp
Quaternion rotation = Quaternion.Euler(0, 30, 0);
transform.rotation = rotation * transform.rotation;
camera.transform.Rotate(0, 30, 0);
```

## Ejercicio 8 ¿Como puedes averiguar la matriz de proyección en perspectiva que se ha usado para proyectar la escena al último frame renderizado?.

Con la propiedad Camera.previousViewProjectionMatrix.

Se ha ejecutado el siguiente código:

```csharp
Debug.Log("Previous camera projection matrix: " + GetComponent<Camera>().previousViewProjectionMatrix);
```

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/e217a572-b1ba-48f1-8db7-fbd4de40e6ca)

## Ejercicio 9 ¿Como puedes averiguar la matriz de proyección en perspectiva ortográfica que se ha usado para proyectar la escena al último frame renderizado?.

Con la misma propiedad. El script anterior sigue funcionando sin problemas.

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/6800b3b7-d06c-482c-a7fb-90118411dce5)

## Ejercicio 10 ¿Cómo puedes obtener la matriz de transformación entre el sistema de coordenadas local y el mundial?.

Usando la propiedad Transform.worldToLocalMatrix.

## Ejercicio 11 Cómo puedes obtener la matriz para cambiar al sistema de referencia de vista

Mediante la propiedad Camera.worldToCameraMatrix.

## Ejercicio 12 Especifica la matriz de la proyección usado en un instante de la ejecución del ejercicio 1 de la práctica 1.

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/1ac030e8-fb6c-415a-97b9-d774b2f20042)

Se ha utilizado:

```csharp
Matrix4x4 projectionMatrix = GetComponent<Camera>().projectionMatrix;
Debug.Log("Matriz de proyección: " + projectionMatrix.ToString());
```
## Ejercicio 13 Especifica la matriz de modelo y vista de la escena del ejercicio 1 de la práctica 1.

La matriz de modelo se refiere a la matriz que pasa de posición, rotación y traslación locales de un objeto a las del mundo. Por matriz de vista se supone la matriz para pasar de coordenadas del mundo a las de la cámara principal.

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/ecb8568e-5139-4656-a9c1-4315c6ea47ef)

Se ha ejecutado lo siguiente:
```csharp
Matrix4x4 viewMatrix = main_camera.worldToCameraMatrix;
Debug.Log("Matriz de Vista: " + viewMatrix.ToString());
Matrix4x4 modelMatrix = transform.localToWorldMatrix;
Debug.Log("Matriz de Modelo: " + modelMatrix.ToString());
```

## Ejercicio 14 Aplica una rotación en el start de uno de los objetos de la escena y muestra la matriz de cambio al sistema de referencias mundial.

![imagen](https://github.com/Francisco-Marques-Armas/seminario-mundos-virtuales/assets/72305337/49b2cbf2-b27f-4a0f-80d9-5dc94e949b72)

Se ha ejecutado lo siguiente:
```csharp
transform.Rotate(0, 30, 0);
Debug.Log("Matriz de cambio del sistema local al mundial: " + transform.localToWorldMatrix);
```
## Ejercicio 15 ¿Como puedes calcular las coordenadas del sistema de referencia de un objeto con las siguientes propiedades del Transform:?: Position (3, 1, 1), Rotation (45, 0, 45)

Si con sistema de referencia se refiere al sistema de referencia mundial, y la posición y rotación son locales, para la posición local habría que tener en cuenta la del padre, y para la rotación se podrían aplicar los siguientes cálculos:

```csharp
Quaternion rotation = Quaternion.Euler(45, 0, 45);

// Aplicar la rotación a los ejes estándar.
Vector3 newXAxis = rotation * Vector3.right; // Eje X
Vector3 newYAxis = rotation * Vector3.up;    // Eje Y
Vector3 newZAxis = rotation * Vector3.forward; // Eje Z
```

E interpretar los resultados obtenidos.
