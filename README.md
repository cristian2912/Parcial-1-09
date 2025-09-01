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

# verificar que este un argumento
if [ -z "$1" ]; then
    echo "Uso: $0 <minutos>"
    exit 1
fi

# guardar el valor del argu
MINUTOS=$1

# que sea n entero
if ! [[ $MINUTOS =~ ^[0-9]+$ ]]; then
    echo "Error: El parametro debe ser un numero entero."
    exit 1
fi

# mostrar mensaje
echo "El equipo se apagara en $MINUTOS minutos."

# programar el apagado
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
El equipo se apagara en 5 minutos.
```
Programar el apagado 
```
Shutdown scheduled for ...
```
#EVIDENCIAS:


<img width="677" height="369" alt="image" src="https://github.com/user-attachments/assets/1dc65d90-185a-4aca-aecc-3496e206be3b" />


# Punto 2
cree un script llamado backup.sh que reciba como argumento la ruta de una carpeta y genere una copia comprimida de su contenido; el script debe validar que la carpeta exista, mostrar un mensaje de confirmacion antes de iniciar, crear un archivo comprimido con formato .tar.gz cuyo nombre incluya la fecha actual (ejemplo: respaldo_2025-09-01.tar.gz) y guardarlo en la misma ubicacion donde se ejecuto el script; pruebe su funcionamiento con un ejemplo de ejecucion como ./backup.sh documentos

# Solucion
terminal:
```
nano backup.sh

```
codigo:

```
#!/bin/bash

# Verificar que se haya pasado un argumento
if [ -z "$1" ]; then
    echo "Uso: $0 <ruta_de_la_carpeta>"
    exit 1
fi

CARPETA=$1

# Validar que la carpeta exista
if [ ! -d "$CARPETA" ]; then
    echo "Error: La carpeta '$CARPETA' no existe."
    exit 1
fi

# Confirmación antes de iniciar
echo "Se creará una copia comprimida de la carpeta: $CARPETA"
read -p "¿Desea continuar? (s/n): " CONFIRMAR

if [[ "$CONFIRMAR" != "s" && "$CONFIRMAR" != "S" ]]; then
    echo "Operación cancelada."
    exit 0
fi

# Generar nombre del respaldo con la fecha actual
FECHA=$(date +%Y-%m-%d)
NOMBRE="respaldo_${FECHA}.tar.gz"

# Crear el archivo comprimido en la carpeta actual
tar -czf "$NOMBRE" -C "$(dirname "$CARPETA")" "$(basename "$CARPETA")"

# Mensaje final
echo "Respaldo creado exitosamente: $NOMBRE"

```
permisos:
```
chmod +x backup.sh
```
ejemplo:
```
./backup.sh documentos
```
salida:
```
Se creará una copia comprimida de la carpeta: documentos
¿Desea continuar? (s/n): s
Respaldo creado exitosamente: respaldo_2025-09-01.tar.gz
```

# punto 6
Explique para que sirven los comandos:

# Solucion:

1. ls -lh: (Listado largo con tamaños legibles)el cual es igual que -l pero con tamaños en formato humano, proporciona al usuario una vista de los archivos y directorios disponibles, incluyendo sus nombres, tamaños y permisos. 

2. ls -l: (Listado largo) muestra información detallada de archivos y directorios 

3. ls -a: (Muestra archivos ocultos) el cual lista todos los archivos, incluyendo los ocultos (que comienzan con punto)

ejemplos 1, 2 y 3:


   <img width="577" height="283" alt="image" src="https://github.com/user-attachments/assets/5d6180d7-6964-4c7a-abcc-51da8023d6f4" />


4. rm: sirve para eliminar archivos y directorios en sistemas operativos tipo Unix.

5. mv: sirve para mover archivos y directorios de un lugar a otro y también para renombrar archivos o directorios, ya sea dentro del mismo directorio o en uno distinto

6. wget: sirve para descargar archivos y contenido de internet, principalmente desde la terminal de línea de comandos

7. traceroute:sirve para diagnosticar problemas en redes, identificando la ruta que los paquetes de datos toman desde un origen hasta un destino y mostrando la latencia y posibles fallos en cada «salto» o enrutador intermedio

9. netstat -i:Muestra todas las conexiones TCP activas y los puertos TCP y UDP en los que escucha el equipo


# punto 7

<img width="1518" height="651" alt="image" src="https://github.com/user-attachments/assets/fbaf18b4-0c4b-4324-be3d-dc390dae1e51" />

# Solucion:



