# 📦 grpc-nest-proto

Este repositorio contiene los archivos **.proto** que definen los contratos gRPC compartidos entre los microservicios de la arquitectura.  

## 📁 Estructura

- `proto/`: Carpeta donde se encuentran los contratos `.proto` de cada microservicio.
- `user.proto`: Define el servicio de usuarios.
- `task.proto`: Define el servicio de tareas.

## 🚀 Servicios relacionados

Este repositorio se utiliza en los siguientes proyectos:

- 🔗 [API Gateway](https://github.com/mariana-vallejos/grpc-api-gateway)  
  Actúa como puerta de entrada (REST ↔ gRPC) hacia los microservicios.

- 🔗 [Users Service](https://github.com/mariana-vallejos/grpc-nest-users-svc)  
  Maneja la gestión de usuarios.

- 🔗 [Tasks Service](https://github.com/mariana-vallejos/grpc-nest-task-svc)  
  Maneja la gestión de tareas.

## 📦 Instalación

Clonar el repositorio:

```bash
git clone https://github.com/mariana-vallejos/grpc-nest-proto.git
cd grpc-nest-proto
```
Instalar dependencias:

```bash
npm install
```
## ⚡ Uso en otros repositorios

Este repositorio se incluye como dependencia en los microservicios.
Ejemplo (package.json de un microservicio):

```json
{
  "scripts": {
    "proto:install": "npm i git+https://github.com/mariana-vallejos/grpc-nest-proto.git",
    "proto:users": "npx protoc --ts_proto_out=src/tasks/proto/ --ts_proto_opt=nestJs=true --ts_proto_opt=fileSuffix=.pb -I=./node_modules/grpc-nest-proto/proto node_modules/grpc-nest-proto/proto/user.proto",
    "proto:tasks": "npx protoc --ts_proto_out=src/tasks/proto/ --ts_proto_opt=nestJs=true --ts_proto_opt=fileSuffix=.pb -I=./node_modules/grpc-nest-proto/proto node_modules/grpc-nest-proto/proto/task.proto",
    "proto:all": "npm run proto:users && npm run proto:tasks"
  }
}
```

## 🛠️ Generación de Tipos TypeScript

Se utiliza ts-proto para generar automáticamente los tipos de TypeScript a partir de los archivos .proto.

Comando de ejemplo:

```bash
//primero ejecutar:
npm run proto:install

npm run proto:users
npm run proto:tasks
npm run proto:all
