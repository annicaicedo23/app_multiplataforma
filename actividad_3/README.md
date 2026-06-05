# Diseño técnico de una aplicación móvil multiplataforma para un contexto real

**Estudiante:** Anny Vanessa Caicedo Londoño

**Asignatura:** Lenguaje de Computación para Móviles

**Unidad:** Unidad 3 - Desarrollo web multiplataforma orientado a dispositivos móviles

**Fecha:** 6 de junio de 2026

**Modalidad:** Individual

# Descripción del problema

Actualmente, los estudiantes universitarios reciben información académica mediante diferentes canales como correos electrónicos, grupos de WhatsApp, plataformas institucionales y páginas web. Esta situación provoca pérdida de información importante, dificultades para realizar seguimiento a las actividades académicas y problemas de acceso cuando la conexión a internet es limitada o inexistente.

Para resolver esta problemática se propone **AcadémIA Mobile**, una aplicación móvil multiplataforma orientada a estudiantes universitarios que centraliza toda la información académica en un único lugar.

La aplicación permitirá consultar actividades académicas, recibir notificaciones y recordatorios, almacenar información para uso sin conexión a internet, registrar evidencias mediante fotografías, capturar la ubicación GPS cuando sea necesario y consultar dudas frecuentes a través de un chatbot académico.

## Público objetivo

* Estudiantes universitarios.
* Personal administrativo de apoyo académico.

## Modos de uso

* Consultar tareas y actividades pendientes.
* Recibir recordatorios de fechas importantes.
* Acceder a información académica sin conexión.
* Registrar evidencias fotográficas de trabajos o prácticas.
* Consultar información institucional mediante un chatbot académico.



# Historias de Usuario Priorizadas

| Prioridad | Historia de Usuario                                                                                                    |
| --------- | ---------------------------------------------------------------------------------------------------------------------- |
| Alta      | Como estudiante, quiero consultar mis actividades académicas para organizar mejor mi tiempo.                           |
| Alta      | Como estudiante, quiero recibir notificaciones sobre nuevas actividades para mantenerme informado.                     |
| Alta      | Como estudiante, quiero acceder a mis actividades sin conexión a internet para consultarlas en cualquier momento.      |
| Media     | Como estudiante, quiero capturar fotografías desde la aplicación para registrar evidencias de mis trabajos académicos. |
| Media     | Como estudiante, quiero registrar mi ubicación GPS para validar la realización de ciertas actividades.                 |
| Media     | Como estudiante, quiero consultar un chatbot académico para resolver dudas frecuentes rápidamente.                     |
| Baja      | Como estudiante, quiero visualizar información obtenida desde una API institucional para acceder a datos actualizados. |



# Matriz Comparativa de Enfoques

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

Se selecciona **Flutter** debido a su excelente rendimiento, acceso a funcionalidades nativas, reutilización de código y facilidad para implementar características como almacenamiento local, notificaciones, cámara, GPS y chatbot académico.



# Selección Tecnológica y Justificación

## Enfoque seleccionado

**Aplicación compilada a nativo mediante Flutter.**

## Framework principal

**Flutter + Dart**

### Tecnologías complementarias

* Firebase Cloud Messaging (notificaciones).
* SQLite o Hive (almacenamiento local).
* API REST institucional.
* Google Maps o Geolocator (GPS).
* Cámara del dispositivo mediante plugins de Flutter.
* Chatbot académico integrado.

Flutter permite desarrollar una única aplicación para múltiples plataformas utilizando una sola base de código. Además, ofrece un excelente rendimiento en dispositivos Android de gama media y baja, acceso a funcionalidades nativas, soporte para trabajo offline y una arquitectura escalable que facilita futuras mejoras.



# Arquitectura Mínima Viable

## Arquitectura por capas

```text
┌───────────────────────────────┐
│      Interfaz de Usuario      │
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
│    Almacenamiento Local       │
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



# Consideraciones Móviles

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


# Riesgos y Limitaciones

| Riesgo                                        | Impacto en la aplicación                                                                              | Probabilidad | Estrategia de mitigación                                                                                                               |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| Fallos de conexión a internet                 | Los estudiantes no podrán consultar información actualizada ni sincronizar evidencias en tiempo real. | Alta         | Implementar almacenamiento local (SQLite/Hive) y sincronización automática cuando se restablezca la conexión.                          |
| Denegación de permisos del dispositivo        | Funcionalidades como cámara, ubicación GPS o notificaciones podrían no estar disponibles.             | Media        | Solicitar permisos de forma contextual, explicando su utilidad y ofreciendo alternativas cuando sea posible.                           |
| Fallos en la API institucional                | La información académica podría mostrarse desactualizada o no estar disponible temporalmente.         | Media        | Utilizar almacenamiento en caché, manejo de errores y reintentos automáticos para garantizar la continuidad del servicio.              |
| Almacenamiento insuficiente en el dispositivo | Dificultad para guardar fotografías y evidencias académicas.                                          | Baja         | Comprimir imágenes, optimizar el uso del almacenamiento y notificar al usuario cuando el espacio disponible sea reducido.              |
| Respuestas incorrectas del chatbot académico  | Posible desinformación o confusión por parte del estudiante.                                          | Media        | Actualizar periódicamente la base de conocimientos, supervisar las respuestas y ofrecer la opción de consultar con personal académico. |

### Análisis General de Riesgos
| Aspecto                 | Descripción                                                                                                                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Riesgos principales     | La conectividad limitada, la disponibilidad de servicios externos y el acceso a recursos del dispositivo representan los principales desafíos de la solución.                                          |
| Estrategia global       | Implementar una arquitectura **Offline-First**, almacenamiento local, sincronización automática, manejo robusto de errores y validación continua de la información proporcionada por el chatbot.       |
| Valor de la solución    | AcadémIA Mobile centraliza la información académica, mejora la comunicación institucional y reduce la pérdida de información importante para los estudiantes.                                          |
| Tecnología seleccionada | Flutter proporciona alto rendimiento en dispositivos Android de gama media o baja, soporte para funcionalidades nativas y una arquitectura escalable para futuras mejoras.                             |
| Diferencial competitivo | La integración de un chatbot académico permite resolver dudas frecuentes de manera inmediata, mejorando la experiencia del estudiante y reduciendo la dependencia de canales tradicionales de soporte. |

Aunque existen riesgos asociados a la conectividad, el uso de servicios externos y las limitaciones de algunos dispositivos móviles, la propuesta incorpora mecanismos de mitigación que garantizan una experiencia de usuario estable y confiable. La combinación de almacenamiento local, sincronización inteligente y soporte mediante chatbot convierte a **AcadémIA Mobile** en una solución viable, escalable y adaptada a las necesidades del entorno educativo actual.

# Videorespuesta
https://youtu.be/eR8MLS4hziU

