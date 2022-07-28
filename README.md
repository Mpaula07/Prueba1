# Proyecto Prueba de GitHub

## Automatización de procesos en Linux

*Problema:* Realizar un programa que almacene en un archivo de texto 
todos los resultados de la búsqueda de todos los archivos de configuración modificados
en la carpeta etc durante la última semana, esta rutina se tiene que ejecutar todos
los lunes a las 7 AM y dejarlas en la carpeta del usuario.

#### Solución:

1. Para esto, se utiliza el comando crontab, con el parámetro -e.
Si es la primera vez que se usa el comando, te pondrá a elegir el 
editor de textto que deseas.

![imagen](/MPaula/Images/crontab.jpg)

2. Se despliega la siguiente interfaz:

![imagen](/MPaula/Images/crontab2.jpg)

La instrucción a ejecutar se escribe en la última línea, siguiendo
el orden establecido en la penúltima. Explicaré lo que significa 
cada uno de estos:

- m: minutos (0 a 59)
- h: horas (0 a 23)
- dom: día del mes (1 a 31)
- mon: mes (1 a 12)
- dow: día de la semana (0 a 6)

Entonces para establecer el tiempo de ejecución, se escribe el valor
deseado en cada cambo separado por espacios. En nuestro caso, habrán 
varios campos vacíos, los cuales se representan con un asterisco.


