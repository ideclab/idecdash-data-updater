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
El paquete se encargará de hacer todo lo necesario para actualizar y cargar los datos, sin embargo, este debe ser llamado de algún lado. Para poder ejecutar el puedes guiarte por el archivo de plantilla llamado **main_example.py**, a continuación se detallan de forma general las variables de entorno que se deben establecer.

***

Conexión a la base de datos postgresql
````
os.environ['DB_HOST'] = '127.0.0.1'
os.environ['DB_PORT'] = '5432'
os.environ['DB_NAME'] = ''
os.environ['DB_USERNAME'] = ''
os.environ['DB_PASSWORD'] = ''
````

***

Ruta al directorio data files del script Canvas Data Cli
````
os.environ['PATH_DATA_FILES'] = ''
````

***

Ruta del directorio donde se encuentra el archivo config.js que pertenece a Canvas Data Cli
````
os.environ['PATH_CANVAS_CONFIG'] = ''
````

***

Caracter concatenador de rutas que utiliza tu sistema operativo  

````
os.environ['PATH_CONCAT'] = '/'
````

***

Configuración del SMTP

**Observación:** El SMTP es utilizado para notificar administradores en caso que el proceso de actualización falle en el proceso.

````
os.environ['SMTP_USER']= ''
os.environ['SMTP_PASS']= ''
os.environ['SMTP_HOST']= ''
os.environ['SMTP_PORT']= ''
````

***

Emails de administradores que recibirán notificaciones de fallo

````
mails = ['example@example.cl']
os.environ['NOTIFICATION_EMAILS'] = os.pathsep.join(mails)
````

***

Si es true (Primera carga) no comprobará los archivos requests con los anteriores antes de insertar los nuevos, se recomienda cambiarlo a false luego de ejecutar la carga inicial y una primera actualización.
Cuando es ````False```` comprobará los nuevos requests con los anteriores para prevenir la inserción de duplicados.

**Observación:** Aunque se inserten datos "crudos" duplicados, al procesarse las interacciones no se insertarán actividades duplicados debido a que están protegidas por una clave primaria mixta unica, por lo cual, puede considere esto como un segundo factor de protección.

````
os.environ['FIRST_DATA_UPDATE']= 'True'
````
