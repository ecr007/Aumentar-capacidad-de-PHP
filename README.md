# Aumentar capacidad de PHP

## Encontrar el php.ini que esta usando el server en estos momentos
```
php -i | grep php.ini

// Buscarlo en windows
php -i | find /i "Configuration File"

// Ver Información completa
phpinfo();
```

## Parametros aumentar

```
upload_max_filesize = 100M
post_max_size = 100M
memory_limit = 32M
max_input_time =  // No cam
max_execution_time =
```

## Descripciones

* upload_max_filesize: 2M | El tamaño máximo de un fichero subido

* post_max_size: Define el tamaño máximo de datos de POST permitidos. Esta opción también afecta a la subida de ficheros. Para subir ficheros grandes, este valor debe ser mayor que upload_max_filesize. Por norma general, memory_limit debe ser mayor que post_max_size. Cuando se usa un integer, el valor del mismo es medido en bytes. También se puede usar la notación reducida, tal como se describe en esta FAQ. Si el tamaño de los datos de POST es mayor que post_max_size, las superglobales $_POST y $_FILES estarán vacías. Esto se puede rastrear de varias maneras, por ejemplo, pasando la variable $_GET al script que procesa los datos, esto es, ```<form action="edit.php?procesado=1">```, y luego comprobar si la variable ```$_GET['procesado']``` existe.
  

* memory_limit: 128M |Establece el máximo de memoria en bytes que un script puede consumir. Ayuda a prevenir que scripts mal programados consuman toda la memoria disponible en el servidor. Observe que para no tener límite de memoria, se ha de establecer esta directiva a -1.
  
* max_input_time: (Por defecto es -1) Establece el tiempo máximo en segundos que se permite a un script analizar datos de entrada, como POST y GET. La medición comienza en el momento en que PHP es invocado en el servidor y finaliza cuando la ejecución comienza.
  
* max_execution_time: (Por default is 30) | Este valor establece el tiempo máximo en segundos que se permite ejecutar antes de que el analizador termine. Esto ayuda a prevenir que scripts mal escritos bloqueen el servidor. El valor por defecto es 30. Cuando se ejecuta PHP desde la línea de comandos el valor por defecto es 0.

El tiempo de ejecución máxima no está afectada por llamadas al sistema, operaciones de stream etc. Por favor véase la función set_time_limit() para más información.

El servidor web puede tener otras configuraciones de tiempo de espera que quizá interrumpan la ejecución de PHP. Apache tiene la directiva Timeout y IIS tiene la función CGI timeout. Las dos de 300 segundos por omisión. Véase la documentación del servidor web para información específica.
  



Para mas información consultar: 

https://www.php.net/manual/es/ini.core.php
https://www.php.net/manual/es/info.configuration.php

## Gestionar php FPM
https://github.com/ecr007/Gestionar-PHP-FPM/blob/master/README.md
