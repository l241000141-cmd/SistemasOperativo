#!/bin/bash
# ==============================================================================
# GUÍA Y REPRODUCCIÓN COMPLETA: AUTOMATIZACIÓN CON CRONTAB EN LINUX
#
# ¿Qué es cron y crontab?
#   - cron: Demonio (servicio en segundo plano) que ejecuta tareas programadas.
#   - crontab (cron table): Archivo de configuración y comando con el que cada
#     usuario define qué comandos o scripts ejecutar y con qué periodicidad.
# ==============================================================================


# ==============================================================================
# PASO 1: EL SCRIPT QUE SE VA A PROGRAMAR (salud.sh)
# Para que crontab lo ejecute correctamente:
#   1. Debe tener la ruta completa (shebang: #!/bin/bash) al inicio.
#   2. Es recomendable usar rutas absolutas para archivos de salida.
# ==============================================================================

cat > "$HOME/salud.sh" << 'EOF'
#!/bin/bash
# salud.sh - Script ejecutado periódicamente por el demonio cron
REPORTE="$HOME/salud.txt"

# Fecha y hora de la ejecución
echo "=== $(date '+%Y-%m-%d %H:%M:%S') ===" >> "$REPORTE"

# Métrica 1: Memoria RAM (free -m + awk)
RAM_INFO=$(free -m | awk 'NR==2 {printf "RAM usada: %s MB de %s MB (%.1f%%)", $3, $2, $3*100/$2}')
echo "$RAM_INFO" >> "$REPORTE"

# Métrica 2: Espacio en disco raíz (df -h / + awk)
DISCO_INFO=$(df -h / | awk 'NR==2 {print "Disco usado: " $3 " de " $2 " (" $5 ")"}')
echo "$DISCO_INFO" >> "$REPORTE"

# Métrica 3: Carga media del procesador (uptime + awk)
CARGA_INFO=$(uptime | awk -F'load average:' '{print $2}')
echo "Carga del sistema:$CARGA_INFO" >> "$REPORTE"

# Salto de línea entre ejecuciones
echo "" >> "$REPORTE"
EOF


# ==============================================================================
# PASO 2: PERMISOS DE EJECUCIÓN (chmod)
# crontab no puede correr un script si el usuario no tiene permisos de ejecución (+x).
# En la sesión se usó: sudo chmod 777 salud.sh
# ==============================================================================

chmod 777 "$HOME/salud.sh"

# Verificación en terminal (ls -l):
# -rwxrwxrwx 1 root root 556 Sep 29 16:58 salud.sh


# ==============================================================================
# PASO 3: CONFIGURACIÓN EN CRONTAB (crontab -e)
#
# Estructura de los 5 campos temporales de crontab:
#   ┌───────────── Minuto (0 - 59)
#   │ ┌─────────── Hora (0 - 23)
#   │ │ ┌───────── Día del mes (1 - 31)
#   │ │ │ ┌─────── Mes (1 - 12)
#   │ │ │ │ ┌───── Día de la semana (0 - 7, donde 0 y 7 son domingo)
#   │ │ │ │ │
#   * * * * * comando_a_ejecutar
#
# En tu práctica:
#   */2 * * * * /home/cindy-guzman/salud.sh
#
#   - "*/2" en el campo minutos: Se ejecuta cada 2 minutos (en :00, :02, :04...).
#   - "*" en los demás campos: Aplica para cualquier hora, día y mes.
#   - Ruta absoluta: Siempre obligatoria en cron porque cron no carga el $PATH
#     habitual de la terminal interactiva.
# ==============================================================================

# Instalación de la regla sin sobreescribir tareas previas:
LINEA_CRON="*/2 * * * * $HOME/salud.sh"
(crontab -l 2>/dev/null | grep -vF "$HOME/salud.sh" ; echo "$LINEA_CRON") | crontab -

# Salida del comando al guardar en el editor:
# crontab: installing new crontab


# ==============================================================================
# PASO 4: CONSULTAR TAREAS ACTIVAS (crontab -l)
# El modificador '-l' (list) muestra las tareas programadas del usuario actual.
# ==============================================================================

crontab -l

# Salida obtenida en terminal:
# # m h  dom mon dow   command
# */2 * * * * /home/cindy-guzman/salud.sh


# ==============================================================================
# PASO 5: RESULTADOS GENERADOS POR EL DEMONIO CRON (cat ~/salud.txt)
# Cada 2 minutos exactos, el demonio ejecutó el script y anexó la información:
# ==============================================================================

# === 2026-09-29 17:00:01 ===
# RAM usada: 3463 MB de 15160 MB (22,8%)
# Disco usado: 13G de 49G (28%)
# Carga del sistema: 0,94, 0,87, 0,78
#
# === 2026-09-29 17:02:01 ===
# RAM usada: 3350 MB de 15160 MB (22,1%)
# Disco usado: 13G de 49G (28%)
# Carga del sistema: 1,79, 1,17, 0,90

# Para monitorear en tiempo real cómo cron va escribiendo cada 2 minutos:
# tail -f ~/salud.txt

# Para borrar todas las tareas programadas si ya no se ocupan:
# crontab -r
