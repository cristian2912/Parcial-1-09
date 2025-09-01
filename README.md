# Parcial-1-09

# Punto 1
Cree un archivo de sript llamado apagar.sh que permita programar el apagado del equipo desde la terminal; el script debe recibir como parametros un numero entero que representa la cantidad de minutos a esperar antes del apagado mostrar un mensaje en pantalla indicando "el equipo se apagara en x minutos" donde x corresponde al valor ingresado y posteriormente ejecutar el comando que programe el apagado en linux; asegurese de que el script pueda ejecutarse directamente desde la termina otorgandole los permisos adecuados y valide que funcione con un ejemplo de ejecucion como ./apagar.sh5.

# Solución

terminal:
```
nano apagar.sh
```
codigo:
```
#!/bin/bash

# Verificar que el usuario ingrese un argumento
if [ -z "$1" ]; then
    echo "Uso: $0 <minutos>"
    exit 1
fi

# Guardar el valor del primer argumento
MINUTOS=$1

# Verificar que sea un número entero
if ! [[ $MINUTOS =~ ^[0-9]+$ ]]; then
    echo "Error: El parámetro debe ser un número entero."
    exit 1
fi

# Mostrar mensaje en pantalla
echo "El equipo se apagará en $MINUTOS minutos."

# Programar el apagado
sudo shutdown -h +$MINUTOS
```
Permisos:
```
chmod +x apagar.sh
```
Ejemplo 5mn:
```
./apagar.sh 5
```
Salida
```
El equipo se apagará en 5 minutos.
```
Programar el apagado 
```
Shutdown scheduled for ...
```


#Punto 2
cree un script llamado backup.sh que reciba como argumento la ruta de una carpeta y genere una copia comprimida de su contenido; el script debe validar que la carpeta exista, mostrar un mensaje de confirmacion antes de iniciar, crear un archivo comprimido con formato .tar.gz cuyo nombre incluya la fecha actual 
