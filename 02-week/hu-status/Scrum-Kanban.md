# Scrum vs Kanban

## 1. ¿Qué son?

### Scrum

**Scrum** es un framework ágil orientado a desarrollar productos mediante **iteraciones cortas y planificadas llamadas Sprints**. El equipo organiza el trabajo en ciclos, define objetivos y revisa los resultados al finalizar cada Sprint.

Su enfoque principal es:

> **Planificar → desarrollar → revisar → mejorar → repetir**

### Kanban

**Kanban** es un método de gestión visual del trabajo que busca mantener un **flujo continuo**, evitando acumulaciones y limitando la cantidad de tareas que se realizan simultáneamente.

Su enfoque principal es:

> **Visualizar → limitar trabajo en progreso → mantener el flujo → mejorar continuamente**

---

# 2. Diferencias principales

| Aspecto                        | Scrum                                               | Kanban                                        |
| ------------------------------ | --------------------------------------------------- | --------------------------------------------- |
| **Forma de trabajo**           | Iteraciones o Sprints                               | Flujo continuo                                |
| **Planificación**              | Se realiza al inicio de cada Sprint                 | Se realiza continuamente                      |
| **Duración**                   | Sprints de duración fija                            | No requiere ciclos fijos                      |
| **Cambios durante el trabajo** | Se intenta mantener estable el Sprint               | Los cambios pueden incorporarse continuamente |
| **Roles**                      | Define roles específicos                            | No exige roles específicos                    |
| **Reuniones**                  | Daily, Sprint Planning, Review y Retrospective      | No establece reuniones obligatorias           |
| **Límite de trabajo**          | El Sprint define la capacidad                       | Utiliza límites explícitos de WIP             |
| **Entrega**                    | Normalmente al finalizar el Sprint                  | Puede entregarse continuamente                |
| **Métricas**                   | Velocidad, Burndown, objetivos del Sprint           | Lead Time, Cycle Time, Throughput, WIP        |
| **Objetivo principal**         | Entregar incrementos de producto de forma iterativa | Optimizar el flujo de trabajo                 |
| **Adaptabilidad**              | Alta, pero principalmente entre Sprints             | Muy alta y continua                           |
| **Estructura**                 | Más estructurado                                    | Más flexible                                  |

---

# 3. Lo mejor de Scrum

## 🎯 1. Organización clara

Scrum proporciona una estructura definida para organizar el trabajo:

* Product Backlog
* Sprint Backlog
* Sprint
* Incremento
* Product Goal
* Sprint Goal

Esto facilita que el equipo sepa **qué hacer, por qué hacerlo y cuándo revisarlo**.

## 👥 2. Roles y responsabilidades

Scrum define responsabilidades claras:

* **Product Owner:** maximiza el valor del producto y gestiona el Product Backlog.
* **Scrum Master:** ayuda a que Scrum se aplique correctamente y elimina impedimentos.
* **Developers:** construyen el incremento del producto.

Esto reduce ambigüedades dentro del equipo.

## 🔄 3. Mejora continua

La **Sprint Retrospective** permite analizar:

* Qué funcionó.
* Qué salió mal.
* Qué se puede mejorar.
* Qué acción concreta se implementará en el siguiente Sprint.

## 📦 4. Entregas frecuentes

Al finalizar cada Sprint debe existir un **Incremento** que cumpla con la Definition of Done.

Esto permite recibir retroalimentación frecuentemente.

## 📊 5. Excelente para proyectos con objetivos definidos

Scrum funciona especialmente bien cuando existe:

* Un producto que construir.
* Un backlog priorizado.
* Historias de usuario.
* Requerimientos que pueden evolucionar.
* Un equipo dedicado al producto.

---

# 4. Lo mejor de Kanban

## 👀 1. Visualización del trabajo

Kanban permite observar rápidamente el estado de cada tarea.

Ejemplo:

```text
BACKLOG       EN PROGRESO       REVIEW          DONE
─────────     ────────────      ──────         ─────
HU-101        HU-102            HU-099         HU-095
HU-103        HU-104            HU-100         HU-096
HU-105
```

Esto facilita detectar dónde se está acumulando trabajo.

## 🚦 2. Límites de WIP

**WIP = Work In Progress**

Kanban limita cuántas tareas pueden estar simultáneamente en progreso.

Ejemplo:

```text
EN PROGRESO
────────────
Máximo: 2 tareas

HU-102
HU-104
```

Si ya existen dos tareas en progreso, el equipo debe ayudar a terminarlas antes de comenzar otra.

Esto evita:

> "Empezamos 10 tareas y no terminamos ninguna."

## ⚡ 3. Flujo continuo

No es necesario esperar a que termine un Sprint.

Cuando una tarea está terminada:

```text
Backlog → Desarrollo → Review → Done
```

se puede comenzar inmediatamente la siguiente.

## 🔀 4. Muy adaptable a cambios

Kanban permite incorporar nuevas prioridades cuando existe capacidad disponible.

Es especialmente útil cuando las tareas llegan de manera impredecible.

## 📈 5. Excelente para medir el flujo

Kanban permite analizar métricas como:

### Lead Time

Tiempo desde que se solicita una tarea hasta que se entrega.

### Cycle Time

Tiempo desde que se comienza a trabajar hasta que se termina.

### Throughput

Cantidad de tareas terminadas durante un período.

Estas métricas permiten detectar problemas reales del proceso.

---

# 5. Scrum vs Kanban: ¿cuál es mejor?

No existe uno que sea universalmente mejor.

La elección depende del tipo de trabajo.

### Scrum es mejor cuando:

* Se está construyendo un producto.
* Existe un roadmap.
* Hay objetivos por iteración.
* Se necesita planificación periódica.
* Se trabaja con historias de usuario.
* Se quiere una estructura clara.
* Se necesita revisar el producto regularmente.

### Kanban es mejor cuando:

* El trabajo llega continuamente.
* Las prioridades cambian constantemente.
* Hay soporte o mantenimiento.
* Se atienden incidencias.
* Se necesita entrega continua.
* Se quiere reducir tiempos de espera.
* El flujo es más importante que las iteraciones.

---

# 6. Ejemplo práctico

Supongamos un equipo que desarrolla un sistema de odontología.

## Usando Scrum

Se define un Sprint de 2 semanas:

```text
SPRINT 1

HU-01 → Registro de pacientes
HU-02 → Inicio de sesión
HU-03 → Gestión de odontólogos
HU-04 → Agenda de citas
```

Durante las dos semanas el equipo trabaja en esas historias.

Al finalizar:

```text
Sprint Review
      ↓
Producto funcionando
      ↓
Retrospective
      ↓
Sprint 2
```

---

## Usando Kanban

El mismo equipo podría trabajar mediante un tablero:

```text
BACKLOG
   ↓
TODO
   ↓
IN PROGRESS
   ↓
CODE REVIEW
   ↓
TEST
   ↓
DONE
```

Con un límite:

```text
IN PROGRESS = máximo 2
```

Cuando una tarea pasa a `DONE`, se toma otra del backlog.

---

# 7. ¿Se pueden combinar?

**Sí.**

De hecho, existe un enfoque conocido como **Scrumban**, que combina elementos de Scrum y Kanban.

Por ejemplo:

### Scrum aporta

* Sprints.
* Product Backlog.
* Sprint Planning.
* Sprint Review.
* Retrospective.
* Roles y responsabilidades.
* Sprint Goal.

### Kanban aporta

* Tablero visual.
* Límites WIP.
* Gestión del flujo.
* Cycle Time.
* Lead Time.
* Mejora del flujo.

Un equipo podría trabajar así:

```text
                 SCRUM
                   │
             Sprint de 2 semanas
                   │
                   ▼
        ┌─────────────────────┐
        │      KANBAN         │
        │                     │
        │ Todo → Doing → Test │
        │              → Done │
        │                     │
        │ WIP máximo = 2      │
        └─────────────────────┘
```

---

# 8. ¿Cuál elegir para un proyecto de software?

Para un **proyecto académico de desarrollo de software**, Scrum suele ser una buena opción porque permite organizar el proyecto en entregas:

```text
Product Backlog
       ↓
Sprint Planning
       ↓
Sprint 1
       ↓
Incremento
       ↓
Sprint Review
       ↓
Retrospective
       ↓
Sprint 2
       ↓
Incremento
       ↓
...
```

Kanban puede utilizarse dentro del Sprint para controlar el flujo de las tareas.

Por ejemplo:

```text
SPRINT
│
├── TODO
│
├── IN PROGRESS
│     └── WIP ≤ 2
│
├── CODE REVIEW
│
├── TEST
│
└── DONE
```

---

# 9. Resumen rápido

| 🟦 Scrum                           | 🟩 Kanban                            |
| ---------------------------------- | ------------------------------------ |
| Trabaja por Sprints                | Trabaja por flujo continuo           |
| Tiene una estructura definida      | Es más flexible                      |
| Tiene roles específicos            | No exige roles específicos           |
| Planificación por Sprint           | Planificación continua               |
| Ideal para desarrollo de productos | Ideal para flujo de trabajo continuo |
| Sprint Goal                        | Límites WIP                          |
| Sprint Review                      | Gestión visual                       |
| Retrospective                      | Mejora continua                      |
| Velocidad                          | Cycle Time                           |
| Burndown                           | Throughput                           |

---

# 10. Idea clave para recordar

> **Scrum organiza el trabajo en ciclos; Kanban optimiza el flujo del trabajo.**

Una forma sencilla de diferenciarlos:

```text
SCRUM
"¿Qué vamos a entregar en este Sprint?"
              ↓
       PLANIFICAR
              ↓
          SPRINT
              ↓
          ENTREGAR
              ↓
          MEJORAR


KANBAN
"¿Cómo hacemos que el trabajo fluya mejor?"
              ↓
         VISUALIZAR
              ↓
          LIMITAR WIP
              ↓
        OPTIMIZAR FLUJO
              ↓
        ENTREGAR CONTINUAMENTE
```

## 🏆 Lo mejor de cada uno

**Scrum → estructura + planificación + objetivos + inspección.**

**Kanban → flexibilidad + flujo + visualización + reducción de tiempos.**

**Scrumban → estructura de Scrum + optimización del flujo de Kanban.**
