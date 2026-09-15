# Nombre del proyecto
Comandos Básicos de Navegación y Exploración en Ubuntu

## Descripción
El objetivo principal de esta práctica es adquirir destreza en el uso de la terminal de comandos de Ubuntu Linux, enfocándose en la interacción con el sistema de archivos sin depender de una interfaz gráfica de usuario (GUI). A través de ejercicios prácticos, se busca dominar la navegación por rutas relativas y absolutas, así como la inspección detallada de directorios y ficheros del sistema operativo.

## Objetivos de aprendizaje
* **Dominar la navegación por el árbol de directorios:** Aprender a desplazarse de forma fluida mediante el comando `cd`, utilizando comodines y atajos esenciales como `cd ..` (subir un nivel), `cd ~` o `cd` (ir al directorio personal/home) y `cd -` (volver al directorio anterior).
* **Explorar el contenido del sistema:** Utilizar el comando `ls` para inspeccionar directorios, identificando archivos comunes, directorios y enlaces simbólicos.
* **Comprender y aplicar modificadores (banderas/flags):** Profundizar en el uso de parámetros como:
  * `-l` (formato largo con permisos, dueño, grupo, tamaño y fecha de modificación).
  * `-a` (mostrar todos los archivos, incluidos los ocultos que inician con `.`).
  * `-h` (formato legible para humanos en tamaños: KB, MB, GB).
  * La combinación de estos (`ls -lah`) para obtener un panorama completo de cualquier ubicación.
* **Diferenciar tipos de rutas:** Identificar y aplicar correctamente la diferencia entre rutas relativas (a partir de la ubicación actual) y rutas absolutas (a partir de la raíz `/`).

## Material utilizado
* Computadora portátil con distribución Ubuntu Linux instalada.
* Emulador de terminal de comandos (Bash shell).

## Informe
[Ver informe detallado](Informe/informe_CB.pdf)

## Evidencias de la práctica
* Capturas de pantalla de la terminal mostrando la ejecución progresiva de los comandos.
* Pruebas de navegación entre directorios del sistema (`/etc`, `/var`, `/home`).
* Visualización detallada de atributos y permisos de archivos ocultos en el directorio personal.

## Comandos
[Ver lista de comandos utilizados](Comandos/Readme.txt)

## Video del funcionamiento
`Readme.md`  
[Ver video en YouTube](https://youtu.be/l__w7yTP34Q)

## Conclusiones
La práctica permitió consolidar los fundamentos de interacción con el sistema operativo Linux a bajo nivel. Trabajar exclusivamente desde la terminal demostró que la línea de comandos ofrece una velocidad, precisión y nivel de detalle muy superiores a los del explorador visual de archivos.

Se comprendió la importancia de la estructura jerárquica de Linux (árbol invertido con raíz en `/`) y cómo interpretar la metadata que devuelve `ls -la`, como los permisos de lectura, escritura y ejecución (`rwx`), el propietario y el tamaño real en disco. Asimismo, dominar la sintaxis y los atajos de `cd` y `pwd` resultó indispensable para mantener siempre la orientación espacial dentro del sistema, evitando errores comunes al referenciar rutas y sentando una base sólida para futuras tareas de administración y configuración avanzada del sistema.

## Resultados
[Ver resultados y capturas de la práctica](Resultados/resultado_comandosB)
