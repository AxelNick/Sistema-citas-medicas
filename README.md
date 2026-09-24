# 🏥 Sistema de Gestión de Citas Médicas

> **Cliente / Organización:** Universidad Nacional de Ingeniería (UNI)  
> **Arquitectura:** Monolítica Modular por capas con Programación Orientada a Aspectos (AOP)  
> **Taiga PM:** [http://159.195.245.124:8085/project/sistema-citas-medicas/](http://159.195.245.124:8085/project/sistema-citas-medicas/)  
> **Estado:** En desarrollo (Sprints 1 a 5 - 2026)

---

## 📋 Descripción del Proyecto

El **Sistema de Gestión de Citas Médicas** es una solución web monolítica modular diseñada para centralizar el agendamiento clínico de la Universidad Nacional de Ingeniería (UNI). Integra un **Asistente Inteligente (IA)** que procesa lenguaje natural para realizar un *triage operativo* (sugiriendo especialidades y facilitando la búsqueda de horarios), garantizando transacciones seguras de citas y aplicando **Spring AOP** para la separación de aspectos transversales como auditoría, logging y manejo de excepciones.

---

## 🛠️ Stack Tecnológico

| Capa / Módulo | Tecnología / Herramienta | Descripción |
| :--- | :--- | :--- |
| **Lenguaje Backend** | Java 21 LTS | Código robusto, moderno y mantenible. |
| **Framework Backend** | Spring Boot 3.x | Desarrollo de la API RESTful. |
| **Capa Transversal** | Spring AOP + AspectJ | Logging centralizado, auditoría de citas y medición de rendimiento. |
| **Seguridad** | Spring Security + JWT | Autenticación basada en tokens y control de acceso por roles (RBAC). |
| **Base de Datos** | PostgreSQL 15+ | Persistencia relacional de datos. |
| **ORM / Persistencia**| Spring Data JPA + Hibernate | Mapeo objeto-relacional y transacciones ACID. |
| **Migraciones DB** | Flyway | Control de versiones del esquema de base de datos. |
| **Frontend SPA** | React 18 + TypeScript | Interfaz de usuario interactiva y tipada. |
| **Diseño y Estilos** | Tailwind CSS | Estilos adaptables (Azul `#1E3A5F`, Turquesa `#0F8B8D`). |
| **Inteligencia Artificial**| API REST de LLM Externa | Chatbot de triage operativo y detección de emergencias. |
| **Pruebas** | JUnit 5 + Mockito | Pruebas unitarias e integración backend. |
| **Documentación API**| Springdoc OpenAPI / Swagger UI | Especificación interactiva de endpoints REST. |
| **Contenedores** | Docker & Docker Compose | Entorno de desarrollo aislado con PostgreSQL. |
| **Control de Versiones**| Git & GitHub / Taiga | Gestión del código fuente y metodologías ágiles. |

---

## 🚀 Características Principales (Dentro del Alcance)

- **Módulo de Autenticación y RBAC (RF-001 - RF-004):** Registro e inicio de sesión seguro con tokens JWT para roles de `PACIENTE`, `MEDICO` y `ADMINISTRADOR`.
- **Capa Transversal con Spring AOP (RNF-007):** Captura automática de eventos de auditoría (registro de quién modifica una cita), logs estructurados y gestión centralizada de errores.
- **Catálogo de Especialidades (RF-005):** Mantenimiento administrativo con protección de integridad referencial.
- **Motor Transaccional de Citas (RF-006 - RF-009):** Búsqueda de horarios con filtros dinámicos (respuesta < 2s) y reservas garantizadas bajo ACID.
- **Asistente Inteligente / Chatbot IA (RF-010):** Triage operativo no clínico en lenguaje natural para orientar al paciente.
- **Detección de Emergencias y Fallback (RF-011):** Alertas inmediatas ante situaciones críticas y canalización automática al flujo manual si la API de IA no responde.

---

## 🚫 Fuera del Alcance (Exclusiones)

- ❌ **Sin responsabilidad clínica:** El chatbot de IA no emite diagnósticos, recetas ni tratamientos.
- ❌ **Sin procesamiento de pagos:** No incluye facturación ni pasarelas de pago electrónico.
- ❌ **Sin Historias Clínicas Complejas (EHR):** No gestiona imágenes médicas ni exámenes externos.

---

## 📁 Estructura del Repositorio

```text
sistema-citas-medicas/
├── docker-compose.yml          # Servicio de PostgreSQL para desarrollo local
├── README.md                   # Documentación principal del repositorio
├── .gitignore                  # Exclusión de archivos binarios y temporales
├── .env.example                # Variables de entorno de ejemplo (DB, JWT, LLM Key)
├── docs/                       # Documentación del proyecto
│   ├── wbs-taiga.md            # Estructura de Desglose de Trabajo (WBS) y Backlog
│   ├── sprints-planning.md     # Cronograma de Sprints y guía de commits
│   └── ARQUITECTURA.md         # Documentación técnica de arquitectura y AOP
├── backend/                    # Proyecto Spring Boot (Java 21)
└── frontend/                   # Proyecto React + TypeScript (Tailwind CSS)
```

---

## 🛠️ Requisitos Previos e Instalación

### Prerrequisitos
- **Java 21 LTS** o superior.
- **Node.js v20+** y `npm`.
- **Docker Desktop** y **Docker Compose**.
- **Git**.

### Pasos de Configuración

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/tu-usuario/sistema-citas-medicas.git
   cd sistema-citas-medicas
   ```

2. **Configurar variables de entorno:**
   ```bash
   cp .env.example .env
   ```

3. **Iniciar la Base de Datos PostgreSQL con Docker Compose:**
   ```bash
   docker compose up -d
   ```

4. **Ejecutar el Backend (Spring Boot):**
   ```bash
   cd backend
   ./mvnw spring-boot:run
   ```
   *La API estará disponible en `http://localhost:8080` y Swagger UI en `http://localhost:8080/swagger-ui.html`.*

5. **Ejecutar el Frontend (React + TypeScript):**
   ```bash
   cd ../frontend
   npm install
   npm run dev
   ```
   *La aplicación estará disponible en `http://localhost:5173`.*

---

## 📊 Planificación y Gestión en Taiga

- **URL de Taiga:** [http://159.195.245.124:8085/project/sistema-citas-medicas/](http://159.195.245.124:8085/project/sistema-citas-medicas/)

Para consultar el desglose detallado de las **4 Épicas**, **10 Historias de Usuario**, asignación de **Puntos de Historia por capa (UX, Frontend, Backend)** y el plan de **5 Sprints**, revisa los documentos en la carpeta `/docs`:
- 📄 [`docs/wbs-taiga.md`](docs/wbs-taiga.md) — Estructura WBS y Backlog.
- 📄 [`docs/sprints-planning.md`](docs/sprints-planning.md) — Cronograma de Sprints y Convención de Commits.

---

## 📝 Licencia y Créditos

Desarrollado para el curso de Desarrollo de Software de la **Universidad Nacional de Ingeniería (UNI)**.
