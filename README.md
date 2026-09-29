# 🌸 Programación II — Clientes API

# 💗 API REST para Gestión de Clientes

### ASP.NET Core · .NET 10 · Entity Framework Core · MySQL

![.NET](https://img.shields.io/badge/.NET-10.0-ec4899?style=for-the-badge&logo=dotnet&logoColor=white)
![ASP.NET Core](https://img.shields.io/badge/ASP.NET_Core-Web_API-f472b6?style=for-the-badge&logo=dotnet&logoColor=white)
![C%23](https://img.shields.io/badge/C%23-CSharp-db2777?style=for-the-badge&logo=csharp&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-f9a8d4?style=for-the-badge&logo=mysql&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-API_Docs-ec4899?style=for-the-badge&logo=swagger&logoColor=white)

### 🌷 Proyecto académico de Programación II

**Desarrollado por:**  
**Sharon Georgette Nahomy Calancho Toledo**

---

## 🌸 Descripción del proyecto

**Programacion2ClientesAPI** es una API REST desarrollada con **ASP.NET Core sobre .NET 10** para la administración de clientes.

La aplicación permite realizar operaciones **CRUD** sobre la información almacenada en una base de datos **MySQL**, utilizando **Entity Framework Core** como ORM.

La API funciona como backend del proyecto de **Blazor WebAssembly**, permitiendo que el frontend consulte y modifique la información mediante peticiones HTTP y objetos JSON.

También cuenta con documentación interactiva para probar los endpoints de la API.

---

# 💗 Arquitectura del sistema

La API funciona como intermediaria entre la aplicación Blazor y la base de datos MySQL.

```text
┌─────────────────────────────┐
│     Blazor WebAssembly      │
│          Frontend           │
└──────────────┬──────────────┘
               │
               │ HTTP / JSON
               ▼
┌─────────────────────────────┐
│      ASP.NET Core API       │
│   Programacion2ClientesAPI  │
└──────────────┬──────────────┘
               │
               │ Entity Framework Core
               ▼
┌─────────────────────────────┐
│            MySQL            │
│       Base de Datos         │
└─────────────────────────────┘
```

### 🌷 Flujo general

```text
Cliente / Blazor
       ↓
Petición HTTP
       ↓
ClientesController
       ↓
ClienteService
       ↓
AppDbContext
       ↓
Entity Framework Core
       ↓
MySQL
```

---

# 🌷 Tecnologías utilizadas

| Tecnología                           | Uso                               |
| ------------------------------------ | --------------------------------- |
| **.NET 10**                          | Plataforma principal              |
| **C#**                               | Lenguaje de programación          |
| **ASP.NET Core**                     | Desarrollo de la API REST         |
| **Entity Framework Core**            | ORM y acceso a datos              |
| **Pomelo.EntityFrameworkCore.MySql** | Proveedor de EF Core para MySQL   |
| **MySQL**                            | Base de datos                     |
| **Swagger / OpenAPI**                | Documentación y pruebas de la API |
| **JSON**                             | Intercambio de información        |
| **Postman**                          | Pruebas de endpoints              |
| **Visual Studio Code**               | Entorno de desarrollo             |
| **Git**                              | Control de versiones              |
| **GitHub**                           | Repositorio del proyecto          |

---

# 💕 Objetivo del proyecto

El objetivo principal es desarrollar una **API REST** que permita administrar la información de clientes mediante operaciones CRUD.

La API permite:

- 🌸 **Consultar todos los clientes**
- 💗 **Consultar un cliente específico**
- 🌷 **Registrar nuevos clientes**
- 🩷 **Actualizar clientes existentes**
- 🗑️ **Eliminar clientes**
- 🔄 **Intercambiar información mediante JSON**
- 📝 **Validar la información recibida**
- 🌐 **Ser consumida desde Blazor WebAssembly**

---

# 🌸 Modelo Cliente

La entidad `Cliente` representa la información almacenada en la base de datos.

| Campo              | Tipo       | Descripción                         |
| ------------------ | ---------- | ----------------------------------- |
| `Id_cliente`       | `int`      | Identificador único del cliente     |
| `CUI`              | `string`   | Código Único de Identificación      |
| `NIT`              | `string`   | Número de Identificación Tributaria |
| `Nombres`          | `string`   | Nombres del cliente                 |
| `Apellidos`        | `string`   | Apellidos del cliente               |
| `Direccion`        | `string`   | Dirección del cliente               |
| `Telefono`         | `string`   | Número de teléfono                  |
| `Fecha_Nacimiento` | `DateTime` | Fecha de nacimiento                 |

---

# 💗 Operaciones CRUD

## 🌸 Consultar clientes

Permite obtener todos los clientes registrados.

```http
GET /api/clientes
```

Ejemplo:

```text
http://localhost:5169/api/clientes
```

---

## 🌷 Consultar cliente por ID

Permite obtener la información de un cliente específico.

```http
GET /api/clientes/{id}
```

Ejemplo:

```text
http://localhost:5169/api/clientes/1
```

---

## 💗 Registrar cliente

Permite registrar un nuevo cliente.

```http
POST /api/clientes
```

Ejemplo de JSON:

```json
{
  "cui": "1234567890101",
  "nit": "1234567-8",
  "nombres": "Sharon",
  "apellidos": "Calancho Toledo",
  "direccion": "Guatemala",
  "telefono": "55555555",
  "fecha_Nacimiento": "2000-01-01"
}
```

---

## 🩷 Actualizar cliente

Permite modificar la información de un cliente existente.

```http
PUT /api/clientes/{id}
```

Ejemplo:

```http
PUT /api/clientes/1
```

La información actualizada se envía en formato JSON.

---

## 🗑️ Eliminar cliente

Permite eliminar un cliente utilizando su identificador.

```http
DELETE /api/clientes/{id}
```

Ejemplo:

```http
DELETE /api/clientes/1
```

---

# 🌸 Endpoints

|  Método  | Endpoint             | Descripción                |
| :------: | -------------------- | -------------------------- |
|  `GET`   | `/api/clientes`      | Obtener todos los clientes |
|  `GET`   | `/api/clientes/{id}` | Obtener cliente por ID     |
|  `POST`  | `/api/clientes`      | Registrar cliente          |
|  `PUT`   | `/api/clientes/{id}` | Actualizar cliente         |
| `DELETE` | `/api/clientes/{id}` | Eliminar cliente           |

---

# 💕 Estructura del proyecto

```text
Programacion2ClientesAPI/
│
├── Controllers/
│   └── ClientesController.cs
│
├── Data/
│   └── AppDbContext.cs
│
├── DTOs/
│   └── ClienteDto.cs
│
├── Models/
│   └── Cliente.cs
│
├── Services/
│   ├── IClienteService.cs
│   └── ClienteService.cs
│
├── Migrations/
│
├── Properties/
│   └── launchSettings.json
│
├── Program.cs
├── appsettings.json
├── Programacion2ClientesAPI.csproj
├── Programacion2ClientesAPI.http
├── README.md
└── .gitignore
```

> 🌷 La estructura puede variar ligeramente dependiendo de la versión final del proyecto.

---

# 💗 Separación de responsabilidades

El proyecto busca mantener separadas las responsabilidades principales:

```text
🌸 Controllers
       ↓
Reciben las peticiones HTTP

💗 Services
       ↓
Procesan la lógica de la aplicación

🌷 Entity Framework Core
       ↓
Gestiona el acceso a los datos

🩷 MySQL
       ↓
Almacena la información
```

Esto permite mantener el código organizado y facilita su mantenimiento.

---

# 🌸 Configuración de MySQL

La conexión con MySQL se configura en:

```text
appsettings.json
```

Ejemplo:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "server=localhost;port=3306;database=db_clientes;user=root;password=TU_PASSWORD"
  }
}
```

> ⚠️ **Importante:** no se recomienda publicar contraseñas reales de MySQL en repositorios públicos.

Cada estudiante debe configurar sus propias credenciales de conexión local.

---

# 🌷 Entity Framework Core

Para trabajar con Entity Framework Core se utilizan migraciones.

Crear una migración:

```bash
dotnet ef migrations add InitialCreate
```

Aplicar las migraciones a MySQL:

```bash
dotnet ef database update
```

Para consultar las migraciones disponibles:

```bash
dotnet ef migrations list
```

---

# 💕 Ejecución del proyecto

## 1️⃣ Restaurar dependencias

Desde la carpeta del proyecto:

```bash
dotnet restore
```

---

## 2️⃣ Compilar la API

```bash
dotnet build
```

Si todo está configurado correctamente deberá finalizar sin errores.

---

## 3️⃣ Ejecutar la API

```bash
dotnet run
```

La consola mostrará la dirección donde está disponible la aplicación.

Por ejemplo:

```text
http://localhost:5169
```

---

# 🌸 Probar la API

La API puede probarse utilizando:

### 💗 Swagger / OpenAPI

Al ejecutar el proyecto, abrir la dirección correspondiente a la documentación de la API.

Por ejemplo:

```text
http://localhost:5169/swagger
```

Desde esta interfaz es posible probar las operaciones:

```text
GET
POST
PUT
DELETE
```

### 🌷 Postman

También se pueden realizar peticiones utilizando **Postman**.

Ejemplo:

```http
GET http://localhost:5169/api/clientes
```

---

# 💗 Comunicación con Blazor

Esta API está diseñada para ser consumida por el proyecto:

```text
Programacion2ClientesBlazor
```

El flujo de comunicación es:

```text
Blazor WebAssembly
        ↓
     HttpClient
        ↓
      HTTP
        ↓
Programacion2ClientesAPI
        ↓
Entity Framework Core
        ↓
      MySQL
```

El intercambio de información entre **Blazor** y la **API** se realiza principalmente mediante objetos en formato **JSON**.

---

# 🌸 Requisitos

Para ejecutar el proyecto se recomienda contar con:

- 💗 **.NET SDK 10**
- 🌷 **MySQL Server**
- 🩷 **Visual Studio Code o Visual Studio 2022**
- 🌸 **Entity Framework Core**
- 🧪 **Postman**
- 📝 **Git**
- 🌐 **Navegador web moderno**

---

# 🌷 Autora

### 💗 Sharon Georgette Nahomy Calancho Toledo

**Curso:** Programación II  
**Proyecto:** API REST para Gestión de Clientes  
**Backend:** ASP.NET Core Web API  
**Framework:** .NET 10  
**ORM:** Entity Framework Core  
**Base de datos:** MySQL

---

### 🌸 Tecnologías principales

`C#` · `.NET 10` · `ASP.NET Core` · `Entity Framework Core` · `MySQL` · `REST API` · `Swagger`

---

> 🌷 **Proyecto desarrollado con fines académicos para el curso de Programación II.**
