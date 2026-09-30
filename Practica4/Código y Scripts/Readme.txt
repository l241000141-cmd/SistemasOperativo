# 1. Abre mi_demonio.sh en gedit con permisos de root (sudo pide tu contraseña).
#    Los avisos de Peas, PeasGtk, gtksourceview (Yaru.xml) y dconf/dbus-launch
#    son inofensivos: salen por ejecutar gedit con sudo y no afectan el script.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ sudo gedit ~/mi_demonio.sh
[sudo: authenticate] Contraseña:

* (gedit:20670): WARNING *: 22:54:42.785: Could not load Peas repository: Typelib file for namespace 'Peas', version '1.0' not found

* (gedit:20670): WARNING *: 22:54:42.785: Could not load PeasGtk repository: Typelib file for namespace 'PeasGtk', version '1.0' not found

(gedit:20670): libgedit-gtksourceview-WARNING **: 22:54:42.982: Failed to load style scheme file '/usr/share/libgedit-gtksourceview-300/styles/Yaru.xml': Error en la línea 3, carácter 1: attribute 'version' invalid for element 'style-scheme'

(gedit:20670): libgedit-gtksourceview-WARNING **: 22:54:42.982: Failed to load style scheme file '/usr/share/libgedit-gtksourceview-300/styles/Yaru-dark.xml': Error en la línea 3, carácter 1: attribute 'version' invalid for element 'style-scheme'

(gedit:20670): dconf-WARNING **: 22:54:54.520: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)

(gedit:20670): dconf-WARNING **: 22:54:54.520: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)

(gedit:20670): dconf-WARNING **: 22:54:54.532: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)

(gedit:20670): dconf-WARNING **: 22:54:54.532: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)


# 2. Lista tu carpeta personal con detalles (permisos, dueño, tamaño, fecha).
#    mi_demonio.sh aparece con dueño root y permisos -rw-r--r-- (sin ejecución)
#    porque lo guardaste con sudo gedit.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ ls -l
total 60
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Sep 13 21:28 Descargas
drwxr-xr-x 5 cindy-guzman cindy-guzman 4096 Sep 27 17:37 Documentos
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Aug 14 16:46 Escritorio
drwxr-xr-x 3 cindy-guzman cindy-guzman 4096 Sep 29 17:13 Imágenes
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Aug 14 16:46 Música
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Aug 14 16:46 Plantillas
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Aug 14 16:46 Público
drwxr-xr-x 3 cindy-guzman cindy-guzman 4096 Sep 13 21:05 Vídeos
-rw-r--r-- 1 cindy-guzman cindy-guzman 1638 Sep 29 22:54 bitacora_demonio.txt
-rw-r--r-- 1 root         root          337 Sep 29 22:54 mi_demonio.sh
-rwxrwxrwx 1 root         root           33 Sep 21 10:19 mundo.sh
-rwxrwxrwx 1 root         root          556 Sep 29 17:11 salud.sh
-rw-rw-r-- 1 cindy-guzman cindy-guzman 6834 Sep 29 22:54 salud.txt
drwx------ 7 cindy-guzman cindy-guzman 4096 Aug 17 22:26 snap


# 3. Da permisos de lectura, escritura y ejecución a todos los usuarios.
#    Funciona, pero 755 sería suficiente y más seguro.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ sudo chmod 777 ~/mi_demonio.sh
(sin salida: en Linux, sin mensaje significa que funcionó)


# 4. Vuelve a listar para comprobar el cambio: mi_demonio.sh ahora es -rwxrwxrwx.
#    La bitácora creció (1638 → 2016 bytes) porque el servicio sigue escribiendo.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ ls -l
total 60
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Sep 13 21:28 Descargas
drwxr-xr-x 5 cindy-guzman cindy-guzman 4096 Sep 27 17:37 Documentos
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Aug 14 16:46 Escritorio
drwxr-xr-x 3 cindy-guzman cindy-guzman 4096 Sep 29 17:13 Imágenes
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Aug 14 16:46 Música
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Aug 14 16:46 Plantillas
drwxr-xr-x 2 cindy-guzman cindy-guzman 4096 Aug 14 16:46 Público
drwxr-xr-x 3 cindy-guzman cindy-guzman 4096 Sep 13 21:05 Vídeos
-rw-r--r-- 1 cindy-guzman cindy-guzman 2016 Sep 29 22:55 bitacora_demonio.txt
-rwxrwxrwx 1 root         root          337 Sep 29 22:54 mi_demonio.sh
-rwxrwxrwx 1 root         root           33 Sep 21 10:19 mundo.sh
-rwxrwxrwx 1 root         root          556 Sep 29 17:11 salud.sh
-rw-rw-r-- 1 cindy-guzman cindy-guzman 6834 Sep 29 22:54 salud.txt
drwx------ 7 cindy-guzman cindy-guzman 4096 Aug 17 22:26 snap


# 5. Ejecuta el script a mano. Lo interrumpiste con Ctrl+C (^C).
#    Mientras corría, escribía en la bitácora al mismo tiempo que el servicio.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ ~/mi_demonio.sh
^C


# 6. Muestra todo el contenido de la bitácora: fecha, procesos y RAM disponible
#    cada 5 segundos. Se ve la línea duplicada (22:56:05 y 22:56:06) por los dos
#    procesos escribiendo a la vez.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ cat ~/bitacora_demonio.txt
2026-09-29 22:52:50 | Procesos: 319 | RAM disponible: 11565 MB
2026-09-29 22:52:55 | Procesos: 319 | RAM disponible: 11564 MB
2026-09-29 22:53:00 | Procesos: 319 | RAM disponible: 11568 MB
2026-09-29 22:53:05 | Procesos: 318 | RAM disponible: 11595 MB
2026-09-29 22:53:10 | Procesos: 318 | RAM disponible: 11595 MB
2026-09-29 22:53:15 | Procesos: 321 | RAM disponible: 11521 MB
2026-09-29 22:53:20 | Procesos: 321 | RAM disponible: 11583 MB
2026-09-29 22:53:25 | Procesos: 321 | RAM disponible: 11579 MB
2026-09-29 22:53:30 | Procesos: 321 | RAM disponible: 11522 MB
2026-09-29 22:53:35 | Procesos: 321 | RAM disponible: 11579 MB
2026-09-29 22:53:40 | Procesos: 321 | RAM disponible: 11578 MB
2026-09-29 22:53:46 | Procesos: 322 | RAM disponible: 11574 MB
2026-09-29 22:53:51 | Procesos: 322 | RAM disponible: 11586 MB
2026-09-29 22:53:56 | Procesos: 322 | RAM disponible: 11592 MB
2026-09-29 22:54:01 | Procesos: 322 | RAM disponible: 11593 MB
2026-09-29 22:54:06 | Procesos: 322 | RAM disponible: 11596 MB
2026-09-29 22:54:11 | Procesos: 322 | RAM disponible: 11596 MB
2026-09-29 22:54:16 | Procesos: 322 | RAM disponible: 11518 MB
2026-09-29 22:54:21 | Procesos: 323 | RAM disponible: 11215 MB
2026-09-29 22:54:26 | Procesos: 323 | RAM disponible: 11248 MB
2026-09-29 22:54:31 | Procesos: 323 | RAM disponible: 11243 MB
2026-09-29 22:54:36 | Procesos: 323 | RAM disponible: 11247 MB
2026-09-29 22:54:41 | Procesos: 325 | RAM disponible: 11248 MB
2026-09-29 22:54:46 | Procesos: 333 | RAM disponible: 11209 MB
2026-09-29 22:54:51 | Procesos: 333 | RAM disponible: 11221 MB
2026-09-29 22:54:56 | Procesos: 326 | RAM disponible: 11259 MB
2026-09-29 22:55:01 | Procesos: 324 | RAM disponible: 11259 MB
2026-09-29 22:55:06 | Procesos: 324 | RAM disponible: 11262 MB
2026-09-29 22:55:11 | Procesos: 324 | RAM disponible: 11260 MB
2026-09-29 22:55:16 | Procesos: 324 | RAM disponible: 11261 MB
2026-09-29 22:55:21 | Procesos: 324 | RAM disponible: 11260 MB
2026-09-29 22:55:26 | Procesos: 324 | RAM disponible: 11258 MB
2026-09-29 22:55:31 | Procesos: 324 | RAM disponible: 11257 MB
2026-09-29 22:55:36 | Procesos: 322 | RAM disponible: 11263 MB
2026-09-29 22:55:41 | Procesos: 322 | RAM disponible: 11261 MB
2026-09-29 22:55:46 | Procesos: 322 | RAM disponible: 11261 MB
2026-09-29 22:55:51 | Procesos: 322 | RAM disponible: 11259 MB
2026-09-29 22:55:56 | Procesos: 322 | RAM disponible: 11260 MB
2026-09-29 22:56:01 | Procesos: 322 | RAM disponible: 11257 MB
2026-09-29 22:56:05 | Procesos: 324 | RAM disponible: 11256 MB
2026-09-29 22:56:06 | Procesos: 324 | RAM disponible: 11257 MB
2026-09-29 22:56:11 | Procesos: 322 | RAM disponible: 11259 MB
2026-09-29 22:56:16 | Procesos: 322 | RAM disponible: 11260 MB
2026-09-29 22:56:21 | Procesos: 322 | RAM disponible: 11261 MB


# 7. Abre (con sudo) la unidad de systemd que define tu servicio.
#    Salen los mismos avisos inofensivos de gedit con sudo.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ sudo gedit /etc/systemd/system/mi-demonio.service

* (gedit:21346): WARNING *: 22:57:17.977: Could not load Peas repository: Typelib file for namespace 'Peas', version '1.0' not found

* (gedit:21346): WARNING *: 22:57:17.977: Could not load PeasGtk repository: Typelib file for namespace 'PeasGtk', version '1.0' not found

(gedit:21346): libgedit-gtksourceview-WARNING **: 22:57:18.190: Failed to load style scheme file '/usr/share/libgedit-gtksourceview-300/styles/Yaru.xml': Error en la línea 3, carácter 1: attribute 'version' invalid for element 'style-scheme'

(gedit:21346): libgedit-gtksourceview-WARNING **: 22:57:18.190: Failed to load style scheme file '/usr/share/libgedit-gtksourceview-300/styles/Yaru-dark.xml': Error en la línea 3, carácter 1: attribute 'version' invalid for element 'style-scheme'

(gedit:21346): dconf-WARNING **: 22:57:38.450: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)

(gedit:21346): dconf-WARNING **: 22:57:38.450: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)

(gedit:21346): dconf-WARNING **: 22:57:38.450: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)

(gedit:21346): dconf-WARNING **: 22:57:38.460: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)

(gedit:21346): dconf-WARNING **: 22:57:38.460: failed to commit changes to dconf: Falló al ejecutar el proceso hijo «dbus-launch» (No existe el archivo o el directorio)


# 8. Le pide a systemd que relea los archivos de unidad para reconocer los cambios.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ sudo systemctl daemon-reload
(sin salida: funcionó correctamente)


# 9. Consulta el estado del servicio: "enabled" (arranca con el sistema) y
#    "active (running)" desde las 22:41:21. Procesos: 17028 (el script) y
#    22080 (sleep 5). Memoria: 2.9M.
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ systemctl status mi-demonio
● mi-demonio.service - Mi primer demonio
     Loaded: loaded (/etc/systemd/system/mi-demonio.service; enabled; preset: enabled)
     Active: active (running) since Tue 2026-09-29 22:41:21 CST; 17min ago
 Invocation: 14c59ee2ee1d47a5af6a3abc1b3df405
   Main PID: 17028 (mi_demonio.sh)
      Tasks: 2 (limit: 18132)
     Memory: 2.9M (peak: 5.9M)
        CPU: 7.307s
     CGroup: /system.slice/mi-demonio.service
             ├─17028 /bin/bash /home/cindy-guzman/mi_demonio.sh
             └─22080 sleep 5

sep 29 22:41:21 cindy-guzman-Inspiron-15-3520 systemd[1]: Started mi-demonio.service - Mi primer demonio.


# 10. Sigue la bitácora en vivo: cada línea nueva aparece conforme se escribe.
#     Se sale con Ctrl+C. (El "^A" es una tecla que se coló durante la captura.)
cindy-guzman@cindy-guzman-Inspiron-15-3520:~$ tail -f ~/bitacora_demonio.txt
2026-09-29 22:58:37 | Procesos: 322 | RAM disponible: 11227 MB
2026-09-29 22:58:42 | Procesos: 322 | RAM disponible: 11231 MB
2026-09-29 22:58:47 | Procesos: 322 | RAM disponible: 11229 MB
2026-09-29 22:58:52 | Procesos: 323 | RAM disponible: 11229 MB
2026-09-29 22:58:57 | Procesos: 323 | RAM disponible: 11228 MB
2026-09-29 22:59:02 | Procesos: 323 | RAM disponible: 11230 MB
2026-09-29 22:59:07 | Procesos: 323 | RAM disponible: 11229 MB
2026-09-29 22:59:13 | Procesos: 323 | RAM disponible: 11231 MB
2026-09-29 22:59:18 | Procesos: 323 | RAM disponible: 11233 MB
2026-09-29 22:59:23 | Procesos: 323 | RAM disponible: 11232 MB
2026-09-29 22:59:28 | Procesos: 324 | RAM disponible: 11227 MB
2026-09-29 22:59:33 | Procesos: 324 | RAM disponible: 11482 MB
2026-09-29 22:59:38 | Procesos: 323 | RAM disponible: 11589 MB
2026-09-29 22:59:43 | Procesos: 324 | RAM disponible: 11491 MB
2026-09-29 22:59:48 | Procesos: 324 | RAM disponible: 11525 MB
2026-09-29 22:59:53 | Procesos: 338 | RAM disponible: 11543 MB
2026-09-29 22:59:58 | Procesos: 333 | RAM disponible: 11526 MB
2026-09-29 23:00:03 | Procesos: 335 | RAM disponible: 11188 MB
2026-09-29 23:00:08 | Procesos: 335 | RAM disponible: 11220 MB
2026-09-29 23:00:13 | Procesos: 335 | RAM disponible: 11220 MB
2026-09-29 23:00:18 | Procesos: 335 | RAM disponible: 11222 MB
2026-09-29 23:00:23 | Procesos: 332 | RAM disponible: 11231 MB
2026-09-29 23:00:28 | Procesos: 331 | RAM disponible: 11231 MB
2026-09-29 23:00:33 | Procesos: 331 | RAM disponible: 11227 MB
2026-09-29 23:00:38 | Procesos: 331 | RAM disponible: 11231 MB
2026-09-29 23:00:43 | Procesos: 331 | RAM disponible: 11229 MB
2026-09-29 23:00:48 | Procesos: 331 | RAM disponible: 11226 MB
2026-09-29 23:00:53 | Procesos: 331 | RAM disponible: 11385 MB
2026-09-29 23:00:58 | Procesos: 330 | RAM disponible: 11578 MB
2026-09-29 23:01:03 | Procesos: 330 | RAM disponible: 11582 MB
2026-09-29 23:01:08 | Procesos: 330 | RAM disponible: 11572 MB
2026-09-29 23:01:13 | Procesos: 336 | RAM disponible: 11535 MB
2026-09-29 23:01:19 | Procesos: 336 | RAM disponible: 11535 MB
2026-09-29 23:01:24 | Procesos: 336 | RAM disponible: 11529 MB
