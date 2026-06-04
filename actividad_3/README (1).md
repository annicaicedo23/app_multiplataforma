# Actividad Evaluativa — Unidad 3
## Lenguaje de Computación para Móviles

| Campo | Detalle |
|---|---|
| **Asignatura** | Lenguaje de Computación para Móviles |
| **Unidad** | Unidad 3. Desarrollo web multiplataforma orientado a dispositivos móviles |
| **Tipo de actividad** | Diseño técnico y sustentación |
| **Fecha** | 2026-05-25 |
| **Modalidad** | Individual |

---

## 1. Descripción del Problema

### Contexto

Las instituciones educativas enfrentan un problema creciente: la información académica se distribuye por múltiples canales (correo, WhatsApp, portales web, carteleras físicas), lo que genera pérdida de mensajes, falta de trazabilidad y desinformación, especialmente cuando los estudiantes no cuentan con conexión estable a internet.

### Solución propuesta: AcadémIA Mobile

**AcadémIA Mobile** es una aplicación móvil multiplataforma para estudiantes universitarios que centraliza toda la información académica en un solo lugar. Sus capacidades principales son:

- 📚 Consulta de actividades y tareas pendientes
- 🔔 Notificaciones y alertas académicas
- 📴 Acceso sin conexión a internet (modo offline)
- 📷 Registro de evidencias mediante fotografías
- 📍 Guardado de ubicación GPS asociado a evidencias
- 🤖 Chatbot académico para resolver dudas frecuentes

### Público objetivo

Estudiantes universitarios que utilizan dispositivos Android de gama media o baja, con acceso intermitente a internet, matriculados en programas de Ingeniería de Software o Tecnología en Implementación de Soluciones Digitales.

### Escenarios principales de uso

| # | Escenario | Descripción |
|---|---|---|
| 1 | **Sin conexión en campus** | El estudiante consulta sus actividades pendientes y fechas de entrega sin necesidad de internet, gracias al almacenamiento local. |
| 2 | **Registro de evidencia en campo** | El estudiante fotografía un artefacto académico (trabajo manual, práctica, etc.) y registra automáticamente la ubicación GPS del momento. |
| 3 | **Recepción de alertas** | La institución publica una nueva actividad o cambio de fecha; el estudiante recibe una notificación push aunque la app esté en segundo plano. |
| 4 | **Consulta de chatbot** | El estudiante tiene una duda sobre el reglamento académico y la resuelve a través del chatbot integrado sin necesidad de contactar al docente. |

---

## 2. Historias de Usuario

Las siguientes historias están priorizadas de mayor a menor impacto para el usuario:

### HU-01 — Consulta de actividades (Alta prioridad)
> **Como** estudiante, **quiero** consultar mis actividades académicas pendientes con fecha de entrega y descripción, **para** organizar mejor mi tiempo y no perder ninguna tarea.

**Criterios de aceptación:**
- Las actividades se muestran ordenadas por fecha de entrega más próxima.
- Cada actividad indica: nombre, materia, descripción breve y fecha límite.
- La lista se actualiza al recuperar conexión a internet.

---

### HU-02 — Acceso offline (Alta prioridad)
> **Como** estudiante con conectividad limitada, **quiero** acceder a mis actividades y notificaciones aunque no tenga internet, **para** seguir consultando información académica desde zonas sin señal.

**Criterios de aceptación:**
- La app almacena localmente el último estado sincronizado de actividades.
- Se muestra un indicador visual cuando la app opera en modo offline.
- Al recuperar conexión, se sincroniza automáticamente.

---

### HU-03 — Registro de evidencias fotográficas (Alta prioridad)
> **Como** estudiante, **quiero** tomar fotografías de mis trabajos o prácticas directamente desde la app, **para** registrar evidencias y vincularlas a una actividad académica específica.

**Criterios de aceptación:**
- La app abre la cámara nativa del dispositivo.
- La imagen se asocia a la actividad seleccionada.
- La evidencia queda guardada localmente y se sube al servidor al recuperar conexión.

---

### HU-04 — Notificaciones push (Media prioridad)
> **Como** estudiante, **quiero** recibir notificaciones cuando se publique una nueva actividad o cuando se acerque la fecha de entrega, **para** no perder plazos importantes.

**Criterios de aceptación:**
- Las notificaciones llegan incluso si la app está cerrada.
- Cada notificación indica la materia y el tipo de alerta (nueva actividad, recordatorio).
- El usuario puede configurar qué tipo de alertas desea recibir.

---

### HU-05 — Registro de ubicación GPS (Media prioridad)
> **Como** estudiante, **quiero** que mis evidencias fotográficas registren automáticamente mi ubicación GPS, **para** certificar el lugar donde se tomó la foto o se realizó la práctica.

**Criterios de aceptación:**
- La app solicita permiso de ubicación al momento de capturar la evidencia.
- Las coordenadas se almacenan junto con la imagen.
- Si el GPS no está disponible, se registra igualmente la foto sin coordenadas.

---

### HU-06 — Chatbot académico (Media prioridad)
> **Como** estudiante, **quiero** resolver dudas frecuentes sobre reglamentos, fechas o procedimientos a través de un asistente de IA, **para** obtener respuestas rápidas sin esperar al docente.

**Criterios de aceptación:**
- El chatbot responde preguntas sobre actividades, reglamentos y calendarios académicos.
- Funciona con respuestas precargadas en modo offline para las preguntas más comunes.
- En modo online, consulta un modelo de lenguaje externo para respuestas más complejas.

---

### HU-07 — Interfaz adaptada a gama media/baja (Baja prioridad)
> **Como** estudiante con un teléfono de gama media o baja, **quiero** que la aplicación sea fluida y no consuma excesivos recursos, **para** usarla sin que mi dispositivo se ralentice o la batería se agote rápidamente.

**Criterios de aceptación:**
- La app no supera 80 MB de almacenamiento instalado.
- El tiempo de carga inicial es menor a 3 segundos en dispositivos con 2 GB de RAM.
- Las animaciones pueden desactivarse desde ajustes.

---

## 3. Matriz Comparativa de Enfoques

| Criterio | PWA | Híbrida (Ionic + Capacitor) | Nativa Android | Flutter |
|---|---|---|---|---|
| **Costo de desarrollo** | Bajo — usa tecnologías web estándar | Bajo-Medio — una base de código para varias plataformas | Alto — código específico por plataforma | Medio — un solo código para múltiples plataformas |
| **Reutilización de código** | Alta — HTML/CSS/JS reutilizable | Alta — mismo código base para Android e iOS | Nula — código separado por plataforma | Muy alta — ~95% de código compartido entre plataformas |
| **Acceso a cámara y GPS** | Limitado — depende del navegador; restricciones en Android | Completo — acceso nativo vía plugins de Capacitor | Completo — acceso directo a APIs nativas de Android | Completo — paquetes nativos (image_picker, geolocator) |
| **Funcionamiento offline** | Parcial — requiere Service Workers; limitaciones en Android | Bueno — SQLite local via Capacitor, sincronización manual | Excelente — Room/SQLite con soporte offline robusto | Excelente — Hive, SQLite, Drift con soporte offline completo |
| **Rendimiento en gama media/baja** | Bueno — depende del motor del navegador | Aceptable — existe overhead de WebView | Excelente — sin capas intermedias | Muy bueno — compilado a código nativo ARM, rendimiento cercano al nativo |
| **Facilidad de mantenimiento** | Alta — web estándar, fácil de actualizar | Alta — ecosistema Angular/React conocido | Media — requiere conocimiento específico de Android/Kotlin | Alta — Dart es sencillo, excelente documentación oficial |
| **Publicación e instalación** | Sin tienda de apps; instalable desde navegador (limitado en iOS) | Publicable en Google Play y App Store con Capacitor | Publicable en Google Play | Publicable en Google Play y App Store |
| **Limitaciones principales** | Sin notificaciones push nativas confiables; acceso limitado a hardware en Android | Depende de WebView; rendimiento inferior en animaciones complejas | Costo alto; sin reutilización de código para iOS | Curva de aprendizaje de Dart; tamaño de APK mayor (~8 MB base) |
| **Decisión final** | ❌ No seleccionada | ❌ No seleccionada | ❌ No seleccionada | ✅ **Seleccionada** |

---

## 4. Selección Tecnológica

### Enfoque seleccionado: Flutter (compilado a nativo)

**Framework principal:** Flutter con Dart  
**Plataforma objetivo:** Android (gama media/baja)

### Justificación

Flutter fue seleccionado por encima de las demás alternativas por las siguientes razones fundamentadas en los requisitos del caso:

| Criterio | Justificación |
|---|---|
| **Reutilización de código** | Un único código base en Dart genera la aplicación para Android (e iOS en el futuro), reduciendo el tiempo de desarrollo y los costos de mantenimiento. |
| **Acceso a capacidades nativas** | Flutter cuenta con paquetes maduros y mantenidos para cámara (`image_picker`, `camera`), GPS (`geolocator`), notificaciones push (`firebase_messaging`, `flutter_local_notifications`) y almacenamiento local (`hive`, `sqflite`). |
| **Rendimiento** | A diferencia de las soluciones híbridas basadas en WebView, Flutter compila directamente a código ARM nativo mediante el motor Skia/Impeller, garantizando 60 fps incluso en dispositivos con 2 GB de RAM. |
| **Costo y tiempo de desarrollo** | Comparado con el desarrollo nativo Android puro, Flutter reduce significativamente el tiempo de implementación al unificar la interfaz y la lógica en un solo proyecto. |
| **Soporte offline** | `sqflite` y `hive` permiten almacenamiento local robusto. Con el patrón Repository, la app puede operar en modo offline y sincronizar al recuperar conexión. |
| **Escalabilidad** | La arquitectura de Flutter con patrón BLoC o Provider permite escalar la app con nuevas funcionalidades (más módulos, más materias, más tipos de evidencias) sin refactorizar la base. |
| **Publicación** | El APK generado por Flutter puede publicarse directamente en Google Play Store, cumpliendo el requisito de aplicación instalable. |

### Stack tecnológico completo

```
Flutter 3.x (Dart)
├── State Management: Bloc / Cubit
├── HTTP Client: dio
├── Almacenamiento local: sqflite + hive
├── Notificaciones: firebase_messaging + flutter_local_notifications
├── Cámara: image_picker / camera
├── GPS: geolocator
├── Chatbot: integración con API REST (Anthropic Claude / OpenAI)
└── Backend simulado: JSON REST API (Node.js + Express o Firebase)
```

---

## 5. Arquitectura Mínima Viable

La arquitectura propuesta sigue el patrón **Clean Architecture** adaptado a Flutter, dividida en tres capas principales:

```
┌─────────────────────────────────────────────────────────────┐
│                    CAPA DE PRESENTACIÓN                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │  Pantalla    │  │  Pantalla    │  │     Pantalla     │  │
│  │  Actividades │  │  Evidencias  │  │     Chatbot      │  │
│  └──────────────┘  └──────────────┘  └──────────────────┘  │
│  ┌──────────────┐  ┌──────────────┐                         │
│  │  Pantalla    │  │  Pantalla    │                         │
│  │  Notific.    │  │  Perfil      │                         │
│  └──────────────┘  └──────────────┘                         │
│              State Management: BLoC / Cubit                  │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                      CAPA DE DOMINIO                         │
│  ┌──────────────────────┐  ┌──────────────────────────────┐ │
│  │  Casos de uso        │  │  Entidades                   │ │
│  │  - GetActividades    │  │  - Actividad                 │ │
│  │  - RegistrarEvidencia│  │  - Evidencia                 │ │
│  │  - ConsultarChatbot  │  │  - Notificacion              │ │
│  └──────────────────────┘  └──────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                   CAPA DE INFRAESTRUCTURA                    │
│                                                             │
│  ┌─────────────────┐  ┌──────────────────┐                  │
│  │  API REST Client│  │ Almacenamiento   │                  │
│  │  (dio)          │  │ Local (sqflite / │                  │
│  │                 │  │  hive)           │                  │
│  └─────────────────┘  └──────────────────┘                  │
│                                                             │
│  ┌─────────────────┐  ┌──────────────────┐                  │
│  │  Módulo Cámara  │  │ Módulo GPS       │                  │
│  │  (image_picker) │  │ (geolocator)     │                  │
│  └─────────────────┘  └──────────────────┘                  │
│                                                             │
│  ┌─────────────────┐                                        │
│  │  Notificaciones │                                        │
│  │  (FCM + local)  │                                        │
│  └─────────────────┘                                        │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│              BACKEND / API EXTERNA (simulada)                │
│                                                             │
│  REST API  ──►  Firebase Firestore / Node.js + Express      │
│  Push      ──►  Firebase Cloud Messaging (FCM)              │
│  Chatbot   ──►  API de LLM (Claude / OpenAI)                │
└─────────────────────────────────────────────────────────────┘
```

### Pantallas / componentes principales

| Pantalla | Descripción | Componentes clave |
|---|---|---|
| **Splash / Login** | Autenticación institucional | TextField, ElevatedButton, HTTP auth |
| **Dashboard** | Resumen de actividades próximas | ListView, Card, Badge de notificaciones |
| **Actividades** | Lista completa con filtros por materia | TabBar, FilterChip, Pull-to-refresh |
| **Detalle de Actividad** | Descripción, fechas y evidencias adjuntas | Hero animation, Gallery, FAB cámara |
| **Registro de Evidencia** | Captura de foto y GPS | CameraPreview, MapPreview, UploadButton |
| **Notificaciones** | Historial de alertas recibidas | NotificationTile, MarkAsRead |
| **Chatbot** | Conversación con IA académica | ChatBubble, TextField, StreamBuilder |
| **Perfil** | Datos del estudiante y configuración | ListTile, Switch (notificaciones), Logout |

### Flujo de sincronización offline

```
App inicia
    │
    ├── [Hay conexión] ──► Fetch API ──► Actualiza SQLite ──► Muestra datos
    │
    └── [Sin conexión] ──► Lee SQLite ──► Muestra datos (modo offline)
                                              │
                                        Recupera conexión
                                              │
                                    Sincroniza cambios pendientes
                                    (evidencias subidas, actividades)
```

---

## 6. Consideraciones Móviles

### 6.1 Conectividad limitada

- Se implementa el patrón **offline-first**: la app consulta primero el almacenamiento local (SQLite/Hive) y solo va a la API cuando hay conexión.
- Un `ConnectivityService` monitorea el estado de red en tiempo real usando el paquete `connectivity_plus`.
- Las evidencias (fotos + GPS) se guardan localmente en una cola de sincronización y se suben cuando la red lo permite.

### 6.2 Bajo consumo de datos

- Las imágenes de evidencias se comprimen antes de enviarse al servidor (máximo 800 KB por foto).
- La API implementa paginación y la app solo descarga actividades del semestre en curso.
- Se utiliza caché HTTP local para respuestas repetidas.

### 6.3 Rendimiento en dispositivos modestos

- Flutter compila a código nativo ARM, evitando la penalización de rendimiento del WebView.
- Las listas de actividades usan `ListView.builder` (renderizado virtual), cargando únicamente los elementos visibles en pantalla.
- Las animaciones complejas se desactivan si el dispositivo reporta modo de bajo rendimiento (`MediaQuery.disableAnimations`).

### 6.4 Experiencia de usuario en pantallas pequeñas

- La interfaz usa diseño adaptativo con `LayoutBuilder` y `MediaQuery` para ajustarse a pantallas desde 4.5 pulgadas.
- Se utiliza la tipografía del sistema con tamaños mínimos de 14 sp para garantizar legibilidad.
- Los botones de acción tienen una zona de toque mínima de 48×48 dp, cumpliendo las guías de Material Design 3.

### 6.5 Permisos del dispositivo

Los permisos se solicitan de forma contextual (justo cuando se necesitan, no al inicio de la app):

| Permiso | Momento de solicitud |
|---|---|
| `CAMERA` | Al intentar registrar una evidencia fotográfica |
| `ACCESS_FINE_LOCATION` | Al activar el registro de ubicación GPS en la evidencia |
| `POST_NOTIFICATIONS` (Android 13+) | Al iniciar sesión por primera vez |
| `READ/WRITE_EXTERNAL_STORAGE` | Al guardar evidencias localmente (Android < 10) |

### 6.6 Seguridad básica de los datos

- El token de autenticación se almacena en `flutter_secure_storage` (cifrado con Android Keystore).
- Las fotos de evidencias se almacenan en el directorio privado de la app (no accesibles por otras apps).
- La comunicación con la API se realiza únicamente por HTTPS/TLS.
- La sesión expira automáticamente tras 8 horas de inactividad.

---

## 7. Riesgos y Limitaciones

| # | Riesgo | Impacto | Probabilidad | Estrategia de mitigación |
|---|---|---|---|---|
| 1 | **Fallos de conexión a internet** | El estudiante no puede sincronizar actividades ni subir evidencias actualizadas. | Alto | Implementar almacenamiento local offline-first con cola de sincronización automática al recuperar la conexión. |
| 2 | **Fragmentación de Android en dispositivos de gama baja** | Comportamiento inconsistente en versiones Android 8–10 con distintos fabricantes (Huawei, Samsung, etc.). | Medio | Establecer como versión mínima Android 8.0 (API 26) y realizar pruebas en dispositivos reales representativos del público objetivo. |
| 3 | **Permisos denegados por el usuario** | Si el usuario rechaza cámara o GPS, no puede registrar evidencias georreferenciadas. | Medio | Diseñar flujos alternativos: permitir registro de evidencia sin ubicación GPS si el permiso es denegado; mostrar explicaciones claras antes de solicitar cada permiso. |
| 4 | **Tamaño del APK elevado en Flutter** | El APK base de Flutter (~8 MB) puede ser mayor al esperado para dispositivos con almacenamiento limitado. | Bajo | Usar `flutter build apk --split-per-abi` para generar APKs específicos por arquitectura (arm64-v8a, armeabi-v7a), reduciendo el tamaño hasta un 40%. |
| 5 | **Disponibilidad del servicio de chatbot externo** | Si la API del LLM no está disponible, el chatbot no responde. | Bajo | Implementar respuestas predefinidas (FAQ estáticas) almacenadas localmente como fallback cuando la API del chatbot no esté disponible. |

---

## 8. Video de Sustentación

> 📹 **Enlace al video:** [Insertar URL de YouTube / Vimeo aquí]  
> *El video explica el problema, las funcionalidades principales, el enfoque tecnológico seleccionado, la arquitectura propuesta y la justificación de la decisión.*

---

## Referencias

- Flutter Documentation. (2024). *Flutter — Build apps for any screen*. https://flutter.dev/docs
- Google. (2024). *Material Design 3 Guidelines*. https://m3.material.io/
- Capacitor Documentation. (2024). *Capacitor — Cross-platform Native Runtime for Web Apps*. https://capacitorjs.com/docs
- Mozilla Developer Network. (2024). *Progressive Web Apps (PWAs)*. https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps
- Google. (2024). *Android Developer Guides*. https://developer.android.com/guide

---

*Documento generado como entrega de la Actividad Evaluativa — Unidad 3, asignatura Lenguaje de Computación para Móviles, 2026.*
