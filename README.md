=====================================================================
DEMONIO DE MONITOREO CON SYSTEMD - COMANDOS UTILIZADOS
Sesion del 29 de septiembre de 2026
=====================================================================

Cada comando incluye una explicacion de lo que hace y del resultado
observado. Solo se incluyen los comandos que funcionaron.

---------------------------------------------------------------------
1. Abrir el script del demonio en el editor con permisos de root
---------------------------------------------------------------------
sudo gedit ~/mi_demonio.sh

Los avisos de Peas, PeasGtk, gtksourceview (Yaru.xml) y dconf/dbus-launch
son inofensivos: aparecen por ejecutar gedit con sudo y no afectan al
script. Efecto secundario: el archivo queda con duenio root.

---------------------------------------------------------------------
2. Listar la carpeta personal con detalles
---------------------------------------------------------------------
ls -l

mi_demonio.sh aparece como -rw-r--r-- root root (337 bytes), es decir,
sin permiso de ejecucion.

---------------------------------------------------------------------
3. Dar permisos al script
---------------------------------------------------------------------
sudo chmod 777 ~/mi_demonio.sh

Sin salida = exito. Nota: 777 permite escribir a cualquier usuario.
Con 755 (dueno edita, todos ejecutan) es suficiente y mas seguro.

---------------------------------------------------------------------
4. Verificar el cambio de permisos
---------------------------------------------------------------------
ls -l

mi_demonio.sh ahora aparece como -rwxrwxrwx. La bitacora crecio de
1638 a 2016 bytes porque el servicio seguia escribiendo en ella.

---------------------------------------------------------------------
5. Ejecutar el script manualmente
---------------------------------------------------------------------
~/mi_demonio.sh

Se interrumpio con Ctrl+C. Mientras corria, escribio en la bitacora al
mismo tiempo que el servicio, lo que produjo una linea duplicada
(22:56:05 y 22:56:06): dos procesos escribiendo en el mismo archivo.

---------------------------------------------------------------------
6. Ver el contenido completo de la bitacora
---------------------------------------------------------------------
cat ~/bitacora_demonio.txt

Muestra 44 lineas (22:52:50 a 22:56:21) con el formato:
fecha | Procesos: N | RAM disponible: M MB

---------------------------------------------------------------------
7. Abrir la unidad de systemd del servicio
---------------------------------------------------------------------
sudo gedit /etc/systemd/system/mi-demonio.service

Se requiere sudo porque /etc/systemd/system pertenece a root.

---------------------------------------------------------------------
8. Recargar la configuracion de systemd
---------------------------------------------------------------------
sudo systemctl daemon-reload

Sin salida = exito. Le indica a systemd que relea las unidades. Solo es
necesario cuando cambia la unidad (.service), no el script.

---------------------------------------------------------------------
9. Consultar el estado del servicio
---------------------------------------------------------------------
systemctl status mi-demonio

Resultado: enabled (arranca con el sistema) y active (running) desde
las 22:41:21. Procesos 17028 (bash, el script) y 22080 (sleep 5).
Tasks: 2, Memory: 2.9M (pico 5.9M), CPU: 7.307 s.

---------------------------------------------------------------------
10. Seguir la bitacora en vivo
---------------------------------------------------------------------
tail -f ~/bitacora_demonio.txt

Cada linea nueva aparece conforme se escribe (22:58:37 a 23:01:24).
Se sale con Ctrl+C.

=====================================================================
COMANDOS DE ADMINISTRACION DEL SERVICIO (referencia)
=====================================================================
systemctl status mi-demonio          # ver estado
sudo systemctl enable --now mi-demonio   # habilitar al arranque e iniciar
sudo systemctl restart mi-demonio    # reiniciar tras editar el script
sudo systemctl stop mi-demonio       # detener
journalctl -u mi-demonio -f          # ver los logs del servicio en vivo
