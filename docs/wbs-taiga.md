# Estructura de Desglose de Trabajo (WBS) y Backlog para Taiga

**Proyecto:** Sistema de Gestión de Citas Médicas  
**Institución:** Universidad Nacional de Ingeniería (UNI)  
**URL Taiga:** [http://159.195.245.124:8085/project/sistema-citas-medicas/](http://159.195.245.124:8085/project/sistema-citas-medicas/)  
**Stack Tecnológico:** Java 21 | Spring Boot | React | TypeScript | Tailwind CSS | PostgreSQL | Docker Compose | Spring Security (JWT) | Spring AOP | LLM API  

---

## 1. Épicas e Historias de Usuario

### ÉPICA 1: Arquitectura Base, Autenticación (JWT) y Capa AOP
> **Objetivo:** Configuración del entorno de desarrollo con Docker Compose, PostgreSQL, seguridad con Spring Security + JWT y programación orientada a aspectos (AOP).

#### US-1.1: Inicialización del Proyecto y Contenedorización
* **Descripción:** Como desarrollador, quiero inicializar los proyectos backend y frontend e interconectarlos con PostgreSQL para contar con un entorno de desarrollo integrado.
* **Detalle Técnico:** Setup de Spring Boot (Java 21), React + TypeScript con Tailwind CSS, migraciones Flyway y `docker-compose.yml` para PostgreSQL.
* **Etiquetas (Tags):** `docker`, `postgresql`, `java21`, `spring-boot`, `react`, `typescript`, `tailwind`
* **Puntos de Historia:**
  * UX / Design: 0 pts
  * Frontend: 1 pt
  * Backend: 2 pts
  * **Total US-1.1: 3 pts**

#### US-1.2: Registro, Autenticación JWT y Control de Acceso por Roles
* **Descripción:** Como usuario (paciente, médico o administrador), quiero registrarme e iniciar sesión para acceder a las funciones correspondientes a mi rol.
* **Detalle Técnico:** Endpoints `POST /auth/register` y `POST /auth/login`, hash BCrypt, tokens JWT y filtros de Spring Security por rol (`PACIENTE`, `MEDICO`, `ADMINISTRADOR`).
* **Etiquetas (Tags):** `java21`, `spring-boot`, `jwt`, `react`, `typescript`, `tailwind`
* **Puntos de Historia:**
  * UX / Design: 1 pt
  * Frontend: 2 pts
  * Backend: 3 pts
  * **Total US-1.2: 6 pts**

#### US-1.3: Capa Transversal con Spring AOP
* **Descripción:** Como arquitecto de software, quiero implementar aspectos transversales desacoplados para gestionar observabilidad, auditoría y captura de errores.
* **Detalle Técnico:** Aspectos mediante Spring AOP para auditoría de modificaciones de citas (registro automático de usuario/fecha), logging centralizado y manejo de excepciones.
* **Etiquetas (Tags):** `java21`, `spring-boot`, `aop`
* **Puntos de Historia:**
  * UX / Design: 0 pts
  * Frontend: 0 pts
  * Backend: 3 pts
  * **Total US-1.3: 3 pts**

---

### ÉPICA 2: Gestión de Especialidades y Motor Transaccional de Citas
> **Objetivo:** Lógica central (*Core*) para la gestión de especialidades, búsqueda optimizada y reserva/cancelación confiable de citas.

#### US-2.1: Mantenimiento de Especialidades Médicas (Admin)
* **Descripción:** Como administrador, quiero gestionar el catálogo de especialidades (crear, modificar, habilitar/deshabilitar) para mantener actualizada la oferta médica.
* **Detalle Técnico:** Endpoints CRUD en Spring Boot con validación para impedir la eliminación física de especialidades con citas activas. Vista tabular en React.
* **Etiquetas (Tags):** `java21`, `spring-boot`, `postgresql`, `react`, `typescript`, `tailwind`
* **Puntos de Historia:**
  * UX / Design: 1 pt
  * Frontend: 1 pt
  * Backend: 2 pts
  * **Total US-2.1: 4 pts**

#### US-2.2: Búsqueda y Reserva Transaccional de Citas Médicas
* **Descripción:** Como paciente, quiero buscar disponibilidad mediante filtros y reservar un horario médico sin riesgo de doble reserva.
* **Detalle Técnico:** Búsqueda con filtros dinámicos (especialidad, médico, fecha) respondiendo en < 2s. Reserva respaldada por transacciones ACID en Spring Data JPA e Hibernate.
* **Etiquetas (Tags):** `java21`, `spring-boot`, `postgresql`, `react`, `typescript`, `tailwind`
* **Puntos de Historia:**
  * UX / Design: 2 pts
  * Frontend: 3 pts
  * Backend: 3 pts
  * **Total US-2.2: 8 pts**

#### US-2.3: Consulta y Cancelación de Citas por Rol
* **Descripción:** Como usuario, quiero consultar las citas asociadas a mi perfil (paciente ve sus reservas, médico ve su agenda) y cancelar compromisos si es necesario.
* **Detalle Técnico:** Endpoints GET filtrados por JWT y rol. Cancelación de cita liberando automáticamente el horario y registrando el evento mediante auditoría AOP.
* **Etiquetas (Tags):** `java21`, `spring-boot`, `jwt`, `postgresql`, `react`, `typescript`, `tailwind`, `aop`
* **Puntos de Historia:**
  * UX / Design: 1 pt
  * Frontend: 2 pts
  * Backend: 2 pts
  * **Total US-2.3: 5 pts**

---

### ÉPICA 3: Asistente Inteligente (IA) para Triage Operativo
> **Objetivo:** Chatbot integrado con API de LLM externa para orientación al paciente, detección de emergencias y fallback manual.

#### US-3.1: Chatbot Orientativo e Integración con API de LLM Externa
* **Descripción:** Como paciente, quiero interactuar mediante lenguaje natural con un asistente virtual para recibir sugerencias de especialidades y agilizar mi búsqueda de citas.
* **Detalle Técnico:** Cliente HTTP en Spring Boot para consumir la API de un LLM externo resguardando credenciales. Interfaz de Chatbot en React aclarando su rol orientativo y no diagnóstico.
* **Etiquetas (Tags):** `java21`, `spring-boot`, `ia-llm`, `react`, `typescript`, `tailwind`
* **Puntos de Historia:**
  * UX / Design: 1 pt
  * Frontend: 2 pts
  * Backend: 3 pts
  * **Total US-3.1: 6 pts**

#### US-3.2: Detección de Situaciones Urgentes y Fallback Manual
* **Descripción:** Como paciente en situación de riesgo o ante fallos de la IA, quiero recibir alertas de emergencia o ser derivado al flujo de reserva manual.
* **Detalle Técnico:** Detección de palabras clave de urgencia para mostrar alerta de atención inmediata. Control de timeouts y fallos en la API externa de IA redirigiendo al flujo de filtros manuales.
* **Etiquetas (Tags):** `java21`, `spring-boot`, `ia-llm`, `react`, `typescript`, `tailwind`
* **Puntos de Historia:**
  * UX / Design: 1 pt
  * Frontend: 1 pt
  * Backend: 2 pts
  * **Total US-3.2: 4 pts**

---

### ÉPICA 4: Pruebas, Documentación y Entrega Académica
> **Objetivo:** Garantizar la calidad del software con pruebas automatizadas y especificación OpenAPI/Swagger.

#### US-4.1: Pruebas Unitarias y de Integración Backend
* **Descripción:** Como equipo de desarrollo, quiero ejecutar pruebas automatizadas sobre los servicios críticos para validar las reglas de negocio.
* **Etiquetas (Tags):** `java21`, `spring-boot`, `aop`
* **Puntos de Historia:**
  * UX / Design: 0 pts
  * Frontend: 0 pts
  * Backend: 3 pts
  * **Total US-4.1: 3 pts**

#### US-4.2: Documentación Interactiva de la API (OpenAPI / Swagger)
* **Descripción:** Como evaluador/desarrollador, quiero contar con la especificación interactiva de la API para probar los endpoints desde el navegador.
* **Etiquetas (Tags):** `java21`, `spring-boot`
* **Puntos de Historia:**
  * UX / Design: 0 pts
  * Frontend: 0 pts
  * Backend: 1 pt
  * **Total US-4.2: 1 pt**

---

## 2. Matriz Resumen de Puntos de Historia

| Épica | ID | Historia de Usuario | Etiquetas (Tags) | UX/Des | Front | Back | Total |
| :--- | :--- | :--- | :--- | :---: | :---: | :---: | :---: |
| **Épica 1** | **US-1.1** | Inicialización y Docker | `docker` `postgresql` `java21` `spring-boot` `react` `typescript` `tailwind` | 0 | 1 | 2 | **3** |
| | **US-1.2** | Registro, Login JWT y RBAC | `java21` `spring-boot` `jwt` `react` `typescript` `tailwind` | 1 | 2 | 3 | **6** |
| | **US-1.3** | Capa Transversal Spring AOP | `java21` `spring-boot` `aop` | 0 | 0 | 3 | **3** |
| **Épica 2** | **US-2.1** | Mantenimiento Especialidades | `java21` `spring-boot` `postgresql` `react` `typescript` `tailwind` | 1 | 1 | 2 | **4** |
| | **US-2.2** | Búsqueda y Reserva de Citas | `java21` `spring-boot` `postgresql` `react` `typescript` `tailwind` | 2 | 3 | 3 | **8** |
| | **US-2.3** | Consulta y Cancelación de Citas | `java21` `spring-boot` `jwt` `postgresql` `react` `typescript` `tailwind` `aop` | 1 | 2 | 2 | **5** |
| **Épica 3** | **US-3.1** | Chatbot IA e Integración LLM | `java21` `spring-boot` `ia-llm` `react` `typescript` `tailwind` | 1 | 2 | 3 | **6** |
| | **US-3.2** | Detección Urgencias y Fallback | `java21` `spring-boot` `ia-llm` `react` `typescript` `tailwind` | 1 | 1 | 2 | **4** |
| **Épica 4** | **US-4.1** | Pruebas JUnit 5 / Mockito | `java21` `spring-boot` `aop` | 0 | 0 | 3 | **3** |
| | **US-4.2** | Documentación Swagger UI | `java21` `spring-boot` | 0 | 0 | 1 | **1** |
| **TOTALES** | | | | **7** | **12** | **24** | **43** |
