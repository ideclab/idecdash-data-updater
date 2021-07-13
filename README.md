# IDECDash Data Updater
IDECDash Data Updater es un componente de IDECDash, visite la wiki del repositorio para encontrar más información sobre este y otros componentes.

## Requisitos
- Python 3.9
- Supervisord 4.2
- Nodejs 14.0 a v16.0
- [Canvas Data Cli](https://github.com/instructure/canvas-data-cli "Canvas Data Cli")

## Instalación

1) Descarga el proyecto

`git clone https://github.com/xxxxx/interactive_dashboard_backend/`

2) Instala las dependencias

`pip install -r requirements.txt`

4) Compila el paquete 

`python setup.py sdist`

5) Ve a la carpera **/dist** e instala el paquete.

`pip3 install NOMBRE_DEL_ARCHIVO.tar.gz`

6) Crea un script para configurar y ejecutar la actualización de datos, puedes utilizar el fichero **main_example.py** como plantilla.

7) Envuelve el script del paso 6 en una tarea programada o cron job para automatizar el lanzamiento. Se recomienda un intervalo de 24 horas entre cada actualización.

8) Configura supervisord para ejecutar las colas de trabajo que pertenecen a IDECDash Backend, en la carpeta supervisord_config encontrarás una configuración de ejemplo.

[Ir a la documentación de Supervisord](http://supervisord.org/ "Canvas Data Cli")

**Observación:** Al agregar la configuración de supervisord no olvides modificar lo siguiente:
````
directory= PATH_TO_IDECDASH_BACKEND
stderr_logfile=/var/log/idecdash/big_courses.err.log
stdout_logfile=/var/log/idecdash/big_courses.out.log
````
*Los archivos para almacenar los log deben ser creados manualmente*


## Configuración
Una vez que tengamos nuestro fichero de entorno podremos ver que posee nuevas claves en comparación a un fichero de entorno tradicional de laravel, para saber que valores asignar se explicará que hace cada apartado.
