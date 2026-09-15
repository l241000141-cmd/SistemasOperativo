# Nombre del proyecto
Monitoreo de Procesos y Rendimiento del Sistema en Ubuntu

## Descripción
El objetivo de esta práctica es analizar, supervisar y controlar la ejecución de procesos y el consumo de recursos de hardware en tiempo real desde la consola de Ubuntu.

## Objetivos de aprendizaje
Comprender el ciclo de vida de los procesos en Linux y el uso de métricas del sistema mediante herramientas de monitoreo (`ps`, `top`, `htop`, `kill`, `killall`, `df`, `free`), aprendiendo a identificar cuellos de botella de memoria o CPU y a finalizar tareas bloqueadas enviando señales al kernel.

## Material utilizado
* Computadora con sistema operativo Ubuntu Linux
* Consola de comandos Bash y monitor interactivo de procesos (`htop`)

## Informe
[Ver informe](Informe/informe_CB.pdf)

## Evidencias de la práctica
* Capturas del seguimiento de uso de RAM/CPU y terminación controlada de subprocesos.

## Comandos
[ver comandos](Comandos/Readme.txt)

## Video del funcionamiento
`Readme.md`  
[Ver video en YouTube](https://youtu.be/ejemplo_monitoreo_ubuntu)

## Conclusiones
La actividad permitió entender cómo el sistema operativo asigna prioridades y recursos a cada tarea activa mediante identificadores únicos (PID). Se comprobó la eficacia de filtrar procesos en segundo plano con tuberías (`ps aux | grep`) y la importancia de administrar la memoria disponible (`free -h`) antes de que el sistema empiece a usar la memoria swap en exceso. Asimismo, se aprendió a manejar la terminación segura de programas con señales graduales como SIGTERM (`15`) antes de recurrir a la detención forzada con SIGKILL (`9`), evitando la corrupción de datos o inconsistencias en servicios críticos del sistema.

## Resultados
`Resultados_Metricas_Sistema.pdf`
