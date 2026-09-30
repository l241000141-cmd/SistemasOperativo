# Nombre del proyecto

DEMONIO DE MONITOREO CON SYSTEMD

## Descripción

El presente proyecto documenta el diseño, la configuración y el análisis empírico de un demonio de monitoreo para sistemas operativos basados en GNU/Linux. Se implementó un script en Bash (`mi_demonio.sh`) encargado de registrar de forma periódica, cada cinco segundos, el número de procesos activos y la memoria RAM disponible en un archivo de bitácora (`bitacora_demonio.txt`). La ejecución continua y desatendida fue delegada a **systemd**, mediante una unidad de servicio (`mi-demonio.service`) habilitada para iniciar junto con el sistema. Los resultados observados durante una sesión de 78 registros se contrastan con los fundamentos teóricos de la creación y administración de procesos, la gestión de memoria, la planificación de procesos, la concurrencia y la seguridad en sistemas de archivos UNIX.

## Objetivos

Implementar y evaluar un servicio de recolección continua de métricas del sistema operativo mediante utilidades estándar de Bash y el administrador de servicios systemd, analizando las repercusiones en concurrencia, consumo de recursos y políticas de control de acceso.

**Automatización y ejecución desatendida:**
Comprender la semántica, el ciclo de vida y el entorno de ejecución de un demonio administrado por systemd, así como el uso de `systemctl` (`daemon-reload`, `enable`, `restart`, `status`) y de las unidades de servicio.

**Instrumentación y procesamiento de métricas:**
Recolectar datos en tiempo de ejecución empleando utilidades de consulta (`ps`, `free`, `date`) y procesadores de texto estructurado (`awk`), y registrarlos en una bitácora con formato uniforme.

**Seguridad y privilegios en UNIX:**
Analizar los efectos de la delegación de permisos (`chmod`), la propiedad de archivos creados con `sudo gedit` y los riesgos asociados a la asignación de permisos globales (777) frente al principio de privilegio mínimo.

**Modelado y validación de comportamiento:**
Contrastar la dinámica temporal de la memoria disponible (`MemAvailable`) y del conteo de procesos contra la teoría de gestión de memoria y creación de procesos (`fork`/`exec`), e interpretar la deriva temporal del intervalo de muestreo, el consumo de CPU del servicio (aprox. 0.7 %) y la condición de carrera que produjo una línea duplicada en la bitácora.

## Códigos y Scripts

[Ver comandos](Practica4/Código%20y%20Scripts/Readme.txt)

## Reporte

[Reporte](Reporte/D1.pdf)

## Terminal

[Ver Terminal](Practica4/Terminal/D1.png)
[Ver Terminal]Practica4/Terminal/D2.png)
[Ver Terminal](Practica4/Terminal/D3.png)


## Video del funcionamiento

[Ver video en YouTube](https://youtu.be/JWz8FTIMHpM)
