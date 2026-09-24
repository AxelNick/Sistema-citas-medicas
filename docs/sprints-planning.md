# Planificación de Sprints y Guía de Git

**Proyecto:** Sistema de Gestión de Citas Médicas  
**Periodo:** Septiembre 2026 – Diciembre 2026  
**Metodología:** Scrum / Sprints Quincenales  

---

## 1. Cronograma General de Sprints

[25 Sep - 08 Oct]     [09 Oct - 22 Oct]     [23 Oct - 05 Nov]     [06 Nov - 19 Nov]     [20 Nov - 03 Dic] Sprint 1              Sprint 2              Sprint 3              Sprint 4              Sprint 5 (6 Puntos)            (10 Puntos)           (13 Puntos)           (10 Puntos)            (4 Puntos)

---

## 2. Detalle por Sprint

### Sprint 1 (25 Sep – 08 Oct) — Base e Infraestructura
* **Historias de Usuario:** `US-1.1`, `US-1.3`
* **Carga de Trabajo:** UX: 0 pts | Front: 1 pt | Back: 5 pts | **Total: 6 pts**
* **Entregable Demostrable:** Contenedor PostgreSQL en Docker Compose, esqueletos iniciales de Spring Boot y React con Tailwind CSS, y aspectos AOP ejecutando logs/auditoría.

### Sprint 2 (09 Oct – 22 Oct) — Seguridad y Gestión Administrativa
* **Historias de Usuario:** `US-1.2`, `US-2.1`
* **Carga de Trabajo:** UX: 2 pts | Front: 3 pts | Back: 5 pts | **Total: 10 pts**
* **Entregable Demostrable:** Pantallas de Registro y Login con autenticación JWT, control de acceso por roles (RBAC) y módulo CRUD de Especialidades para el perfil Administrador.

### Sprint 3 (23 Oct – 05 Nov) — Motor Transaccional de Citas
* **Historias de Usuario:** `US-2.2`, `US-2.3`
* **Carga de Trabajo:** UX: 3 pts | Front: 5 pts | Back: 5 pts | **Total: 13 pts**
* **Entregable Demostrable:** Búsqueda con filtros dinámicos (< 2s), flujo de reserva transaccional ACID en PostgreSQL, cancelación de citas y pantallas de agenda por perfil.

### Sprint 4 (06 Nov – 19 Nov) — Asistente Inteligente (IA) y Triage
* **Historias de Usuario:** `US-3.1`, `US-3.2`
* **Carga de Trabajo:** UX: 2 pts | Front: 3 pts | Back: 5 pts | **Total: 10 pts**
* **Entregable Demostrable:** Widget de Chatbot en React comunicándose con la API del LLM externo, detección de palabras clave para alertas de emergencia y fallback a búsqueda manual.

### Sprint 5 (20 Nov – 03 Dic) — Calidad, Documentación y Cierre
* **Historias de Usuario:** `US-4.1`, `US-4.2`
* **Carga de Trabajo:** UX: 0 pts | Front: 0 pts | Back: 4 pts | **Total: 4 pts**
* **Entregable Demostrable:** Batería de pruebas automatizadas con JUnit 5/Mockito, interfaz de Swagger UI activa y empaquetado para la presentación final.

---

## 3. Convención de Commits para Evidencia en Git

Para vincular los avances en el código con las Historias de Usuario de Taiga, utiliza la siguiente estructura en los mensajes de commit:

### Formato
`tipo(módulo): [US-X.Y] descripción clara de lo realizado`

### Tipos Permitidos
* `feat`: Nueva funcionalidad.
* `fix`: Corrección de errores.
* `docs`: Cambios en la documentación.
* `test`: Adición o modificación de pruebas.
* `refactor`: Refactorización de código sin cambiar comportamiento.
* `chore`: Tareas de configuración o mantenimiento de build/docker.

### Ejemplos
* `git commit -m "feat(auth): [US-1.2] implementacion de login y generacion de token JWT"`
* `git commit -m "fix(citas): [US-2.2] correccion en la transaccion ACID al reservar horario"`
* `git commit -m "docs: [US-1.1] adicion de configuracion Docker y WBS"`
* `git commit -m "test(citas): [US-4.1] pruebas unitarias con Mockito para el servicio de reserva"`
