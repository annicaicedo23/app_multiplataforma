# Actividad Evaluativa - Unidad 3

## Diseño técnico de una aplicación móvil multiplataforma para un contexto real

**Estudiante:** [Tu nombre]
**Asignatura:** Lenguaje de Computación para Móviles
**Unidad:** Unidad 3 - Desarrollo web multiplataforma orientado a dispositivos móviles
**Fecha:** [Fecha de entrega]

---

# 1. Descripción del problema

Actualmente, los estudiantes universitarios reciben información académica mediante diferentes canales como correos electrónicos, grupos de WhatsApp, plataformas institucionales y páginas web. Esta situación provoca pérdida de información importante, dificultades para realizar seguimiento a las actividades académicas y problemas de acceso cuando la conexión a internet es limitada o inexistente.

Para resolver esta problemática se propone **AcadémIA Mobile**, una aplicación móvil multiplataforma orientada a estudiantes universitarios que centraliza toda la información académica en un único lugar.

La aplicación permitirá consultar actividades académicas, recibir notificaciones y recordatorios, almacenar información para uso sin conexión a internet, registrar evidencias mediante fotografías, capturar la ubicación GPS cuando sea necesario y consultar dudas frecuentes a través de un chatbot académico.

## Público objetivo

* Estudiantes universitarios.
* Docentes.
* Personal administrativo de apoyo académico.

## Escenarios principales de uso

* Consultar tareas y actividades pendientes.
* Recibir recordatorios de fechas importantes.
* Acceder a información académica sin conexión.
* Registrar evidencias fotográficas de trabajos o prácticas.
* Consultar información institucional mediante un chatbot académico.

---

# 2. Historias de Usuario

| Prioridad | Historia de Usuario                                                                                                    |
| --------- | ---------------------------------------------------------------------------------------------------------------------- |
| Alta      | Como estudiante, quiero consultar mis actividades académicas para organizar mejor mi tiempo.                           |
| Alta      | Como estudiante, quiero recibir notificaciones sobre nuevas actividades para mantenerme informado.                     |
| Alta      | Como estudiante, quiero acceder a mis actividades sin conexión a internet para consultarlas en cualquier momento.      |
| Media     | Como estudiante, quiero capturar fotografías desde la aplicación para registrar evidencias de mis trabajos académicos. |
| Media     | Como estudiante, quiero registrar mi ubicación GPS para validar la realización de ciertas actividades.                 |
| Media     | Como estudiante, quiero consultar un chatbot académico para resolver dudas frecuentes rápidamente.                     |
| Baja      | Como estudiante, quiero visualizar información obtenida desde una API institucional para acceder a datos actualizados. |

---

# 3. Matriz Comparativa de Enfoques Técnicos

| Criterio                                      | PWA      | Híbrida (Capacitor) | Nativa Android | Flutter   |
| --------------------------------------------- | -------- | ------------------- | -------------- | --------- |
| Costo de desarrollo                           | Bajo     | Medio               | Alto           | Medio     |
| Reutilización de código                       | Alta     | Alta                | Baja           | Muy alta  |
| Acceso a cámara y GPS                         | Limitado | Bueno               | Excelente      | Excelente |
| Funcionamiento offline                        | Bueno    | Muy bueno           | Excelente      | Excelente |
| Rendimiento en dispositivos gama media o baja | Medio    | Bueno               | Excelente      | Excelente |
| Facilidad de mantenimiento                    | Alta     | Alta                | Media          | Alta      |
| Publicación e instalación                     | Limitada | Buena               | Excelente      | Excelente |
| Escalabilidad                                 | Media    | Alta                | Alta           | Muy alta  |
| Curva de aprendizaje                          | Baja     | Media               | Alta           | Media     |

## Decisión final

Se selecciona **Flutter** debido a su excelente rendimiento, acceso a funcionalidades nativas, reutilización de código y facilidad para implementar características como almacenamiento local, notificaciones, cámara, GPS y chatbot académico.

---

# 4. Selección Tecnológica

## Enfoque seleccionado

**Aplicación compilada a nativo mediante Flutter.**

## Framework principal

**Flutter + Dart**

## Tecnologías complementarias

* Firebase Cloud Messaging (notificaciones).
* SQLite o Hive (almacenamiento local).
* API REST institucional.
* Google Maps o Geolocator (GPS).
* Cámara del dispositivo mediante plugins de Flutter.
* Chatbot académico integrado.

## Justificación

Flutter permite desarrollar una única aplicación para múltiples plataformas utilizando una sola base de código. Además, ofrece un excelente rendimiento en dispositivos Android de gama media y baja, acceso a funcionalidades nativas, soporte para trabajo offline y una arquitectura escalable que facilita futuras mejoras.

---

# 5. Arquitectura Mínima Viable

## Arquitectura por capas

```text
┌───────────────────────────────┐
│       Interfaz de Usuario      │
│                               │
│ Inicio                        │
│ Actividades                   │
│ Chatbot Académico             │
│ Evidencias                    │
│ Notificaciones                │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│      Capa de Servicios        │
│                               │
│ API REST                      │
│ Gestión de Notificaciones     │
│ Sincronización de Datos       │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│   Almacenamiento Local        │
│                               │
│ SQLite / Hive                 │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ Funcionalidades del Dispositivo│
│                               │
│ Cámara                        │
│ GPS                           │
│ Notificaciones Push           │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ Backend / API Institucional   │
└───────────────────────────────┘
```

## Componentes principales

### Pantallas

* Inicio.
* Actividades académicas.
* Chatbot académico.
* Evidencias fotográficas.
* Perfil de usuario.
* Notificaciones.

### Servicios

* Consumo de API REST.
* Gestión de sincronización.
* Servicio de chatbot.
* Gestión de notificaciones.

### Almacenamiento local

* Consulta offline de actividades.
* Caché de información académica.

---

# 6. Consideraciones Móviles

## Conectividad limitada

La aplicación almacenará información localmente para permitir el acceso incluso cuando no exista conexión a internet.

## Bajo consumo de datos

Solo se sincronizará información necesaria para reducir el uso de datos móviles.

## Rendimiento

Se optimizará para dispositivos Android de gama media y baja mediante interfaces ligeras y carga eficiente de recursos.

## Experiencia de usuario

* Diseño adaptable.
* Navegación sencilla.
* Acceso rápido a funciones principales.
* Interfaz intuitiva.

## Permisos

* Cámara.
* Ubicación GPS.
* Notificaciones.

## Seguridad

* Comunicación mediante HTTPS.
* Validación de datos.
* Protección básica de información almacenada localmente.

---

# 7. Riesgos y Limitaciones

| Riesgo                                 | Impacto                                      | Estrategia de mitigación                                     |
| -------------------------------------- | -------------------------------------------- | ------------------------------------------------------------ |
| Fallos de conexión a internet          | Imposibilidad de actualizar información      | Implementar almacenamiento local y sincronización automática |
| Denegación de permisos del dispositivo | Algunas funciones dejarían de operar         | Solicitar permisos de forma clara y opcional                 |
| Fallos en la API institucional         | Información desactualizada                   | Utilizar caché local y manejo de errores                     |
| Almacenamiento insuficiente            | Problemas al guardar evidencias fotográficas | Comprimir imágenes y limpiar archivos temporales             |
| Respuestas incorrectas del chatbot     | Información confusa para el usuario          | Actualizar periódicamente la base de conocimientos           |

---

# 8. Conclusiones

AcadémIA Mobile representa una solución tecnológica que responde a las necesidades actuales de los estudiantes universitarios al centralizar la información académica en una única plataforma móvil. La utilización de Flutter permite garantizar rendimiento, accesibilidad, soporte offline y escalabilidad, mientras que la integración de un chatbot académico aporta un valor diferencial al facilitar la resolución rápida de dudas frecuentes.

La propuesta mejora la comunicación entre la institución y los estudiantes, reduce la pérdida de información y proporciona una experiencia de usuario moderna y eficiente.

---

# 9. Videorespuesta

**Enlace del video:**
(Pegar aquí el enlace de YouTube o Vimeo una vez realizado el video).
