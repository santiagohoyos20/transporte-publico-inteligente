## Transporte Público Inteligente

Plataforma que gestiona una flota de buses inteligentes. Los usuarios consultan tiempos de 
llegada (ETA) en tiempo real y recargan tarjetas electrónicas. Cada bus dispone de un 
dispositivo embarcado (Bus Device) y un Sidecar que envían telemetría y logs a la nube. El 
sistema integra APIs externas (como GPS) a través de un Ambassador Proxy para garantizar 
solidez.

Objetivo: Ofrecer a pasajeros y operadores información en tiempo real sobre ubicaciones, 
tiempos de llegada y estado operativo de la flota, además de permitir recargas electrónicas. 

### Microservicios
- [Microservicio de Autenticación y Seguridad](https://github.com/santiagohoyos20/Microservicio-de-autenticacion-y-seguridad)
- [Microservicio de Gestión de Usuarios y Pasajeros](https://github.com/santiagohoyos20/Microservicio-de-gestion-de-usuarios-y-pasajeros.)
- [Microservicio de Conductores](https://github.com/santiagohoyos20/Microservicio-de-conductores)
- [Microservicio de Flota](https://github.com/santiagohoyos20/Microservicio-de-flota)
- [Microservicio de Telemetría](https://github.com/santiagohoyos20/Microservicio-de-telemetria)
- [Microservicio de Pagos y Recargas](https://github.com/santiagohoyos20/Microservicio-de-pagos-y-recargas)
- [Microservicio de Reportes y Analítica](https://github.com/santiagohoyos20/Microservicio-de-reportes-y-analitica)


## ¿Cómo correrlo?

###  1️⃣ Ejecución con Docker Compose

Esta es la forma más sencilla de levantar todo el entorno localmente.

###  Requisitos previos
- Tener instalado **Docker Desktop**
- Asegurarte de que ningún servicio use los puertos definidos (por ejemplo, `5432`, `3000`, etc.)

### ▶️ Pasos

1. Clonar este repositorio:
   ```bash
   git clone https://github.com/santiagohoyos20/transporte-publico-inteligente.git
   cd transporte-publico-inteligente

2. Crear los archivos .env requeridos por los microservicios (si no existen):
```bash
cp .env.example .env

Levantar los servicios con:

docker compose up --build


Verificar que todos los contenedores estén corriendo:

docker ps
```
3. Acceder a los endpoints expuestos (por ejemplo):

    Auth: http://localhost:3000

    Users: http://localhost:3001

    Drivers: http://localhost:3003

    Telemetry: http://localhost:3002

    Para detener los servicios:
    ```bash
    docker compose down
    ```



##  Opción 2: Ejecutar con Kubernetes

### 1️⃣ Crear las imágenes manualmente

Ejecuta desde cada carpeta de microservicio (por ejemplo `auth/`):

```bash
docker build -t auth -f Dockerfile.auth .
docker build -t drivers -f Dockerfile.drivers .
docker build -t telemetry -f Dockerfile.telemetry .
docker build -t users -f Dockerfile.users .
```

### 2️⃣ Crear los pods y servicios en Kubernetes

En la carpeta raíz (donde está la carpeta `k8s/`):

```bash
kubectl apply -f k8s/
```

Esto creará los `Deployments` y `Services` necesarios para cada microservicio.

### 3️⃣ Verificar el estado

```bash
kubectl get pods
kubectl get services
```

Cuando los pods estén en estado **Running**, los servicios estarán accesibles en los puertos configurados.

