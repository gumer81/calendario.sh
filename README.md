# calendario.sh
# Simple fecha hora calendario en consola linux debian.
#!/bin/bash

# Función para resaltar el día
resaltar_dia() {
    local dia_actual=$(date +%d | sed 's/^0//')
    sed -e "s/\b$dia_actual\b/$(printf '\e[48;5;196m')&$(printf '\e[0m')/"
}

# Bucle principal
while true; do
    clear
    
    # Encabezado personalizado
    echo "-- $(date +"%Y / %B") --"
    
    # Calendario horizontal (formato tradicional)
    ncal -b -M -h | tail -n +2 | resaltar_dia
    
    # Hora actual
    echo -e "\n$(date +"%H:%M:%S")"
    
    sleep 1
done
