# Tarea-9-Script
~~~
#!/bin/bash
#Autor: José Manuel Lamprea Demski
#Descripción: Tarea 9 Script KVM

# Función para consultar el estado de la red
consultar_estado_red() {
    virsh net-list --all | grep default
}

# Función para ver la configuración de la red
ver_configuracion_red() {
    virsh net-dumpxml default
}

# Función para activar la red
activar_red() {
    virsh net-start default
    echo "Red activada."
}

# Función para desactivar la red
desactivar_red() {
    virsh net-destroy default
    echo "Red desactivada."
}

# Función para inicializar la red
inicializar_red() {
    virsh net-autostart default
    echo "Red configurada para inicio automático."
}

# Función para no inicializar la red
deshabilitar_inicializacion_red() {
    virsh net-autostart --disable default
    echo "Red configurada para no inicio automático."
}

# Función para modificar la configuración de la red
modificar_configuracion_red() {
    echo "Editando configuración de la red..."
    virsh net-edit default
}

# Menú principal
while true; do
    clear
    echo "Menú de configuración de la red en KVM"
    echo "------------------------------------"
    echo "1) Consultar el estado de la red"
    echo "2) Ver la configuración de la red"
    echo "3) Activar la red"
    echo "4) Desactivar la red"
    echo "5) Inicializar la red"
    echo "6) Deshabilitar la inicialización automática de la red"
    echo "7) Modificar la configuración de la red"
    echo "8) Salir"
    echo -n "Elige una opción [1-8]: "
    read opcion

    case $opcion in
        1) consultar_estado_red ;;
        2) ver_configuracion_red ;;
        3) activar_red ;;
        4) desactivar_red ;;
        5) inicializar_red ;;
        6) deshabilitar_inicializacion_red ;;
        7) modificar_configuracion_red ;;
        8) echo "Saliendo..."; exit 0 ;;
        *) echo "Opción no válida, por favor elige de nuevo." ;;
    esac
    echo -n "Presiona cualquier tecla para continuar..."
    read -n 1
done
~~~
