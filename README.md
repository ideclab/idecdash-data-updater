# IDECDash Backend
IDECDash Backend es un componente de IDECDash, visite la wiki del repositorio para encontrar más información sobre este y otros componentes.

## Requisitos
- Python 3.9
- Supervisord (v3.0 a v6.0)
- Nodejs (v14 a v16)
- [Canvas Data Cli](https://github.com/instructure/canvas-data-cli "Canvas Data Cli")

## Instalación

1) Descarga el proyecto

`git clone https://github.com/xxxxx/interactive_dashboard_backend/`

## Configuración
Una vez que tengamos nuestro fichero de entorno podremos ver que posee nuevas claves en comparación a un fichero de entorno tradicional de laravel, para saber que valores asignar se explicará que hace cada apartado.
































### IdecDash Data Updater

Idec Python Package  es parte del proyecto IdecDash construido en Python para la descarga y  actualización de datos desde Canvas Data Portal.

### Funcionalidades

- Autentificación mediante token de Canvas
- Descarga de datos desde Canvas Data Portal
- Carga de datos a base de datos Postgres
- Notificaciones via Mail

### Datos
- Los datos son obtenidos desde Canvas Data Portal https://portal.inshosteddata.com/docs

### Instalación

#### Descargar el proyecto
`git clone https://github.com/xxxx/DashboardDataUpdater`

#### Instalar dependencias
`pip install *`

#### Iniciar el proyecto
`python3 main_example.py`

###End
