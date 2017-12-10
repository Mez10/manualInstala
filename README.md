# Trabajo Terminal JD BB
## Introducción
Consíderese este repositorio para los avances en la documentación requerida para el Trabajo Terminal.

## Estatus
El estatus actual de la documentación es **sin comenzar**

## Estructura
La estructura propuesta es la siguiente:

1. Introducción
2. Planteamiento del problema
3. Estado del arte
4. Marco teórico
5. Restricciones

## Forma de trabajo
Los *branches* estarán organizados de la siguiente manera:

* `master` - El *branch* principal. En éste se incluirán las versiones del documento
que sean entregados a sinodales, directores o a la CATT.
* `Doc_HUB` - *branch de transición*. En éste branch serán incluídos los cambios
que se generen, desde donde serán *replicados* a los *branches* de desarrollo.
* `Doc_BB` - *branch de desarrollo* de Omar.
* `Doc_JD` - *branch de desarrollo* de Joscelyn.

### Clonar el proyecto
Ejecute la siguiente instrucción desde la carpeta donde desee instalar el proyecto:
```bash
$ git clone https://github.com/Mez10/tt-jd-bd.git
```

### Publicar cambios a ***HUB***
Para ejemplificar el uso de los distintos branches, considérese el siguiente caso:

**Meztli** finalizó de desarrollar su parte de la documentación, y desea compartirla.
En dicho caso, lo que debería de hacer queda resumido en los siguientes pasos:

1. *Publicar* la última versión de la documentación **dentro de su propio branch**:
```bash
(Doc_JD)$ git add .
(Doc_JD)$ git commit -m "Descripción de cambios de la versión nueva"
```

2. *Cambiarse* al **branch de transición** y asegurarse de tener la última 
versión (Sincronizada con el servidor)
```bash
(Doc_JD)  $ git checkout Doc_HUB
(Doc_HUB) $ git pull
```

3. *Fusionar* los cambios de **su propio branch** con el **branch de transición**
```bash
(Doc_HUB) $ git merge Doc_JD
```

4. *Subir* los nuevos cambios.
```bash
(Doc_HUB) $ git push
```

5. *Fusionar*  los nuevos cambios del **branch de transición** con el 
**branch de su compañero(a)**
```bash
(Doc_HUB) $ git checkout Doc_BB
(Doc_BB) $ git pull
(Doc_BB) $ git merge Doc_HUB
(Doc_BB) $ git push
```

6. Regresar a **su propio branch**
```bash
(Doc_BB) $ git checkout Doc_JD
(Doc_JD) $
```

Para que **Omar** tenga los últimos cambios que ha subido Meztli, bastará 
con que baje la última versión de su branch:
```bash
(Doc_BB) $ git pull
```

### Publicar cambios a ***master***
Dado que `Doc_HUB` contendrá siempre la versión más actualizada de 
la documentación, para actualizar el branch ***master***, bastará con:
```bash
(Doc_HUB) $ git checkout master
(master) $ git merge Doc_HUB
(master) $ git push
```

### Añadir una etiqueta
Las etiquetas son útiles dado que nos permiten ver puntos importantes
en la historia de las versiones dentro de git. Para agregar una
etiqueta, bastará con ejecutar el siguiente comando desde cualquier 
branch:
```bash
(master) $ git tag -a vX.X -m "Descripción de la etiqueta"
```

Donde `vX.X` es el nombre de la etiqueta. Por lo general el nombre de la 
etiqueta corresponde al nombre de la versión (Por ejemplo, v1.0).

Para ver todas las etiquetas, simplemente basta ejecutar:
```bash
(master) $ git tag
```

### Ver el historial de versiones
Para consultar todos los *commits* que se han realizado, ejecutar desde
cualquier branch:
```bash
(master) $ git log
```

Para consultar el historial de forma bonita, pero con menos información,
ejecutar desde cualquier branch:
```bash
(master) $ git log --graph --decorate --oneline
```