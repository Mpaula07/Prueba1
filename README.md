# Proyecto Prueba de GitHub

## Automatización de procesos en Linux

**Problema:**Realizar un programa que almacene en un archivo de texto 
todos los resultados de la búsqueda de todos los archivos de configuración modificados
en la carpeta etc durante la última semana, esta rutina se tiene que ejecutar todos
los lunes a las 7 AM y dejarlas en la carpeta del usuario.

#### Solución:

1. Para esto, se utiliza el comando crontab, con el parámetro -e.
Si es la primera vez que se usa el comando, te pondrá a elegir el 
editor de textto que deseas.

![imagen](https://upbeduco-my.sharepoint.com/:i:/g/personal/mariap_florezv_upb_edu_co/Ed_4ue_7xLhDgsfOwTAUTY4Bws8DYxDKfBeM4vuXZlMgfA?e=q8gAUU)

2. **Se despliega la siguiente interfaz:**

![imagen](https://upbeduco-my.sharepoint.com/:i:/g/personal/mariap_florezv_upb_edu_co/EYFi63PpVaBMk2NHnH8PRhYBMcnJPJh4jKBmxEq9HP0wxA?e=EsnPcg)

La instrucción a ejecutar se digita en la última línea, siguiendo
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

3. **Se establece la frecuencia de ejecución:**

m: * , h: 7, dom: * , mon: * ,dow: 0.

En el editor se debe escribir así:

 - * 7 * * 0  

4. **Estructurar el comando**

El comando se escribe justo después de la configuración de la fecha, 
separados únicamente por un espacio.

En este caso necesitamos usar el comando find, que sirve para buscar
ficheros. Como necesitamos buscar los archivos modificados en los últimos
7 días, utilizamos los parámetros -type y -mtime. El primero indica el tipo,
entonces se escribe una f que significa archivo y el segundo, indica el tiempo
en el que ha sido modificado por días.

Es importante ubicarnos en la ruta etc/*.conf, para buscar así los archivos
que sean de configuración en la carpeta que indicó el programa.

Luego, se redirige la salida a un archivo de texto y finalmente, con un punto
y coma se separa la siguiente instrucción que es darle permisos de lectura únicamente
al administrador mediante el comando chmod.

El comando quedaría así:

find etc/*.conf -type f -mtime 7 >> /home/mpaula/archivorutina.txt; chmod 400 archivorutina.txt

5. **Unir fecuencia de ejecución y comando**

Este es el resultado de escribir los dos procesos realizados anteriormente:

![imagen](https://upbeduco-my.sharepoint.com/:i:/g/personal/mariap_florezv_upb_edu_co/Eb9O5JstxhhAuwV-X3Z1PRQBX5xjtZRuemSjCu3knNyL0A?e=HRTBXd)

Finalmente, se guardan los cambios y se espera su ejecución.
