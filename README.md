# MediTurn - Sistema de Gestión de Turnos Médicos

## Descripción del proyecto

MediTurn es una plataforma basada en microservicios que permite a pacientes reservar,
modificar y cancelar turnos médicos de forma online, mientras que los profesionales de
la salud pueden gestionar su disponibilidad y agenda en tiempo real.

En muchos centros médicos, la gestión de turnos se realiza de forma manual o con sistemas
poco integrados, lo que genera problemas como sobre-reservas, largas esperas, pérdida de
información y mala experiencia para el paciente.

MediTurn resuelve esta problemática mediante una arquitectura distribuida basada en
microservicios independientes, comunicación REST y descubrimiento dinámico de servicios.

---

## Integrantes del equipo

| Nombre | Rol |
|---------|--------------------|
| Ramses Escalona | Backend Developer |
| Elio Millan | Backend Developer |

---

## Tecnologías utilizadas

- Java 17
- Spring Boot 3.5.0
- Spring Cloud 2025.0.0
- Spring Cloud Gateway
- Eureka Server
- Spring Security
- JWT
- OpenFeign
- Spring Data JPA
- MariaDB / MySQL
- Swagger OpenAPI
- JUnit 5
- Mockito
- JaCoCo
- Docker
- Maven
- GitHub

---

## Arquitectura del sistema

La solución utiliza una arquitectura basada en microservicios.

Componentes principales:

- **Eureka Server:** Registro y descubrimiento de servicios.
- **API Gateway:** Punto único de entrada para todos los clientes.
- **Microservicios independientes:** Cada servicio posee su propia lógica de negocio.
- **OpenFeign:** Comunicación REST entre microservicios.
- **Bases de datos desacopladas:** Cada microservicio administra sus propios datos.

---

## Microservicios implementados

| Servicio | Nombre de aplicación | Puerto | Descripción |
|----------|----------------------|--------|-------------|
| ms-eureka | ms-eureka | 8761 | Servidor de registro y descubrimiento de servicios |
| ms-gateway | ms-gateway | 8090 | API Gateway centralizado |
| ms-usuario | ms-usuario | 8080 | Gestión de usuarios del sistema |
| ms-auth | ms-auth | 8081 | Autenticación y autorización JWT |
| ms-pacientes | ms-pacientes | 8082 | Gestión de pacientes |
| ms-medicos | ms-medicos | 8083 | Gestión de médicos |
| ms-especialidades | ms-especialidades | 8084 | Gestión de especialidades médicas |
| ms-historial-medico | ms-historial-medico | 8085 | Historial clínico de pacientes |
| ms-turno | ms-turno | 8086 | Reserva y gestión de turnos |
| ms-disponibilidad | ms-disponibilidad | 8087 | Disponibilidad horaria de médicos |
| ms-notificaciones | ms-notificaciones | 8088 | Envío de notificaciones |
| ms-pago | ms-pago | 8089 | Gestión de pagos de turnos |

---

## Rutas principales del Gateway

Todas las peticiones ingresan a través de:

```text
http://localhost:8090
```

| Microservicio | Ruta |
|---------------|------|
| ms-usuario | `/api/v2/usuarios/**` |
| ms-auth | `/api/v2/auth/**` |
| ms-pacientes | `/api/v2/pacientes/**` |
| ms-medicos | `/api/v2/medicos/**` |
| ms-especialidades | `/api/v2/especialidades/**` |
| ms-historial-medico | `/api/v2/historial/**` |
| ms-disponibilidad | `/api/v2/disponibilidad/**` |
| ms-turno | `/api/v2/turnos/**` |
| ms-notificaciones | `/api/v2/notificaciones/**` |
| ms-pago | `/api/v2/pagos/**` |

---

## Documentación Swagger

Una vez levantados los servicios, la documentación estará disponible en:

| Microservicio | URL Swagger |
|---------------|-------------|
| ms-usuario | http://localhost:8080/swagger-ui.html |
| ms-auth | http://localhost:8081/swagger-ui.html |
| ms-pacientes | http://localhost:8082/swagger-ui.html |
| ms-medicos | http://localhost:8083/swagger-ui.html |
| ms-especialidades | http://localhost:8084/swagger-ui.html |
| ms-historial-medico | http://localhost:8085/swagger-ui.html |
| ms-turno | http://localhost:8086/doc/swagger-ui.html |
| ms-disponibilidad | http://localhost:8087/swagger-ui.html |
| ms-notificaciones | http://localhost:8088/swagger-ui.html |
| ms-pago | http://localhost:8089/swagger-ui.html |

---

## Pruebas Unitarias

Los microservicios implementan pruebas unitarias utilizando:

- JUnit 5
- Mockito
- JaCoCo

### Ejecutar pruebas

```bash
mvn test
```

### Generar reporte de cobertura

```bash
mvn clean verify
```

El reporte JaCoCo se genera en:

```text
target/site/jacoco/index.html
```

---

## Instrucciones de ejecución

### Requisitos previos

- Java 17 o superior
- Maven 3.9 o superior
- Docker Desktop
- MariaDB/MySQL

---

## Ejecución local

1. Levantar `ms-eureka` (puerto 8761).
2. Levantar `ms-gateway` (puerto 8090).
3. Levantar el resto de microservicios.
4. Verificar el registro de servicios desde:

```text
http://localhost:8761
```

Cada microservicio debe tener previamente creada su base de datos.

El perfil activo por defecto es:

```text
dev
```

---

## Ejecución con Docker

Clonar todos los repositorios dentro de una carpeta raíz:

```text
proyecto/
├── docker-compose.yml
├── ms-eureka-main/
├── ms-gateway-main/
├── ms-auth-main/
├── ms-usuario-main/
├── ms-pacientes-main/
├── ms-medicos-main/
├── ms-especialidades-main/
├── ms-historial-medico-main/
├── ms-turno-main/
├── ms-disponibilidad-main/
├── ms-notificaciones-main/
└── ms-pago-main/
```

### Construir y levantar contenedores

```bash
docker-compose up --build -d
```

### Verificar servicios registrados

```text
http://localhost:8761
```

### Detener contenedores

```bash
docker-compose down
```

---

## Repositorio

Repositorio GitHub:

```text
https://github.com/Sistema-de-gestion-de-turnos-medicos/carpeta-con-info-del-proyecto
```

---

## Estado del proyecto

Proyecto desarrollado para la asignatura de Arquitectura de Software utilizando una arquitectura basada en microservicios.
