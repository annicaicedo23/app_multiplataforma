# AcadémIA Mobile — Diseño Técnico de Aplicación Móvil Multiplataforma

---

| Campo | Detalle |
|---|---|
| **Estudiante** | [Nombre del Estudiante] |
| **Asignatura** | Lenguaje de Computación para Móviles |
| **Unidad** | Unidad 3 — Desarrollo web multiplataforma orientado a dispositivos móviles |
| **Fecha** | 25 de mayo de 2026 |

---

## 1. Descripción del Problema

### 1.1 Contexto

Actualmente, los estudiantes universitarios reciben información académica a través de múltiples canales desarticulados: correos electrónicos institucionales, grupos de WhatsApp, plataformas de gestión de aprendizaje (LMS) y páginas web corporativas. Esta dispersión informativa genera tres problemas centrales:

- **Pérdida de información relevante**: los mensajes importantes se diluyen entre el ruido de cada canal.
- **Dificultad de seguimiento**: el estudiante no dispone de una vista unificada de sus actividades y fechas de entrega.
- **Dependencia de conectividad**: la mayoría de plataformas institucionales no funcionan sin acceso estable a internet.

### 1.2 Solución Propuesta

**AcadémIA Mobile** es una aplicación móvil multiplataforma orientada a estudiantes universitarios que centraliza toda la información académica en un único punto de acceso. La aplicación permite:

- Consultar actividades académicas con fecha de entrega y descripción.
- Recibir notificaciones y recordatorios automáticos.
- Almacenar información para consulta sin conexión a internet.
- Registrar evidencias fotográficas vinculadas a actividades específicas.
- Capturar la ubicación GPS al momento de documentar una práctica o trabajo.
- Consultar dudas frecuentes mediante un chatbot académico con soporte de inteligencia artificial.

### 1.3 Público Objetivo

- **Estudiantes universitarios** (usuario principal).
- **Docentes** que publican y gestionan actividades académicas.
- **Personal administrativo** de apoyo académico.

### 1.4 Escenarios Principales de Uso

1. Un estudiante revisa sus tareas pendientes ordenadas por fecha de entrega desde el bus, sin conexión a internet.
2. Un estudiante recibe una notificación push recordándole que una entrega vence en 24 horas.
3. Un estudiante fotografía su trabajo de laboratorio directamente desde la app y lo vincula a la actividad correspondiente.
4. Un estudiante consulta al chatbot académico sobre el reglamento de entregas tardías sin necesidad de esperar respuesta del docente.
5. Un estudiante en zona rural accede a su lista de actividades gracias al almacenamiento offline de la aplicación.

---

## 2. Historias de Usuario

Las siguientes historias de usuario están priorizadas de mayor a menor impacto para el usuario final:

### HU-01 — Consulta de Actividades Académicas `Alta prioridad`

> Como **estudiante**, quiero **consultar mis actividades académicas pendientes con fecha de entrega y descripción**, para **organizar mejor mi tiempo y no perder ninguna tarea**.

**Criterios de aceptación:**
- Las actividades se muestran ordenadas por fecha de entrega más próxima.
- Cada actividad indica: nombre, materia, descripción breve y fecha límite.
- La lista se actualiza automáticamente al recuperar conexión a internet.

---

### HU-02 — Acceso Offline `Alta prioridad`

> Como **estudiante con conectividad limitada**, quiero **acceder a mis actividades y notificaciones aunque no tenga internet**, para **seguir consultando información académica desde zonas sin señal**.

**Criterios de aceptación:**
- La aplicación almacena localmente el último estado sincronizado de actividades.
- Se muestra un indicador visual claro cuando la app opera en modo offline.
- Al recuperar conexión, la sincronización se ejecuta automáticamente en segundo plano.

---

### HU-03 — Registro de Evidencias Fotográficas `Alta prioridad`

> Como **estudiante**, quiero **tomar fotografías de mis trabajos o prácticas directamente desde la app**, para **registrar evidencias y vincularlas a una actividad académica específica**.

**Criterios de aceptación:**
- La app abre la cámara nativa del dispositivo sin redirigir a otra aplicación.
- La imagen capturada se asocia a la actividad académica seleccionada.
- La evidencia queda guardada localmente y se sube al servidor al recuperar conexión.

---

### HU-04 — Notificaciones Push `Media prioridad`

> Como **estudiante**, quiero **recibir notificaciones cuando se publique una nueva actividad o cuando se acerque la fecha de entrega**, para **no perder plazos importantes**.

**Criterios de aceptación:**
- Las notificaciones llegan incluso si la app está cerrada o en segundo plano.
- Cada notificación indica la materia y el tipo de alerta (nueva actividad, recordatorio de entrega).
- El usuario puede configurar desde ajustes qué tipos de alertas desea recibir.

---

### HU-05 — Registro de Ubicación GPS `Media prioridad`

> Como **estudiante**, quiero **que mis evidencias fotográficas registren automáticamente mi ubicación GPS**, para **certificar el lugar donde se realizó la práctica o se tomó la fotografía**.

**Criterios de aceptación:**
- La app solicita el permiso de ubicación en el momento de capturar la evidencia (no al inicio).
- Las coordenadas GPS se almacenan junto con la imagen y la actividad asociada.
- Si el GPS no está disponible, la fotografía se registra igualmente sin coordenadas.

---

### HU-06 — Chatbot Académico con IA `Media prioridad`

> Como **estudiante**, quiero **resolver dudas frecuentes sobre reglamentos, fechas o procedimientos a través de un asistente de inteligencia artificial**, para **obtener respuestas rápidas sin esperar al docente**.

**Criterios de aceptación:**
- El chatbot responde preguntas sobre actividades, reglamentos y calendarios académicos.
- En modo offline, el chatbot utiliza respuestas precargadas para las preguntas más frecuentes.
- En modo online, consulta un modelo de lenguaje externo (LLM) para respuestas complejas.

---

### HU-07 — Interfaz Optimizada para Gama Media/Baja `Baja prioridad`

> Como **estudiante con un teléfono de gama media o baja**, quiero **que la aplicación sea fluida y no consuma recursos excesivos**, para **usarla sin que mi dispositivo se ralentice o la batería se agote rápidamente**.

**Criterios de aceptación:**
- La app no supera 80 MB de almacenamiento instalado en el dispositivo.
- El tiempo de carga inicial es menor a 3 segundos en dispositivos con 2 GB de RAM.
- Las animaciones pueden desactivarse desde el menú de ajustes.

---

## 3. Matriz Comparativa de Enfoques

| Criterio | PWA | Híbrida (Ionic + Capacitor) | Nativa Android | Flutter |
|---|---|---|---|---|
| **Costo de desarrollo** | Bajo — usa tecnologías web estándar (HTML/CSS/JS) | Bajo-Medio — una base de código para varias plataformas | Alto — código específico y equipo especializado por plataforma | Medio — un solo código base genera apps para múltiples plataformas |
| **Reutilización de código** | Alta — HTML/CSS/JS reutilizable en cualquier entorno web | Alta — mismo código base para Android e iOS | Nula — código completamente separado por plataforma | Muy alta — aproximadamente el 95% del código es compartido entre plataformas |
| **Acceso a cámara y GPS** | Limitado — depende del navegador y tiene restricciones en Android | Completo — acceso nativo vía plugins de Capacitor | Completo — acceso directo a las APIs nativas de Android | Completo — paquetes maduros: `image_picker`, `camera`, `geolocator` |
| **Funcionamiento offline** | Parcial — requiere Service Workers con limitaciones en Android | Bueno — SQLite local vía Capacitor, sincronización manual | Excelente — Room/SQLite con soporte offline robusto | Excelente — Hive, SQLite y Drift con soporte offline completo |
| **Rendimiento en gama media/baja** | Bueno — depende del motor del navegador del dispositivo | Aceptable — existe overhead de WebView en cada renderizado | Excelente — sin capas intermedias, acceso directo al hardware | Muy bueno — compilado a código nativo ARM mediante Skia/Impeller |
| **Facilidad de mantenimiento** | Alta — web estándar, fácil de actualizar sin pasar por tiendas | Alta — ecosistema Angular/React ya conocido por muchos equipos | Media — requiere conocimiento específico de Android/Kotlin | Alta — Dart es sencillo, documentación oficial exhaustiva |
| **Publicación e instalación** | Sin tienda de apps; instalable desde el navegador con limitaciones en iOS | Publicable en Google Play y App Store mediante Capacitor | Publicable en Google Play Store | Publicable en Google Play Store y App Store |
| **Limitaciones principales** | Sin notificaciones push nativas confiables; acceso limitado al hardware en Android | Depende de WebView; rendimiento inferior en animaciones complejas | Costo elevado; sin reutilización de código para iOS; tiempo de desarrollo mayor | Curva de aprendizaje inicial con Dart; tamaño base del APK (~8 MB) mayor que una PWA |
| **Decisión final** | ❌ No seleccionada | ❌ No seleccionada | ❌ No seleccionada | ✅ **Seleccionada** |

### Justificación de la decisión

La PWA fue descartada por carecer de notificaciones push nativas confiables en Android y por sus restricciones de acceso al hardware, aspectos críticos para AcadémIA Mobile. La solución híbrida con Capacitor presenta limitaciones de rendimiento derivadas del WebView, lo que afecta negativamente la experiencia en dispositivos de gama baja. El desarrollo nativo Android, aunque técnicamente superior en acceso al hardware, implica un costo y tiempo de desarrollo desproporcionado para el contexto institucional y no permite reutilización de código para futuras versiones iOS. Flutter resuelve de forma equilibrada todos los criterios relevantes: rendimiento cercano al nativo, acceso completo al hardware, soporte offline robusto y un único código base mantenible.

---

## 4. Selección Tecnológica y Justificación

### 4.1 Enfoque Seleccionado

**Aplicación compilada a nativo mediante Flutter.**

### 4.2 Framework Principal

**Flutter 3.x con lenguaje Dart**

### 4.3 Stack Tecnológico Completo

```
Flutter 3.x (Dart)
├── Gestión de estado:       BLoC / Cubit
├── Cliente HTTP:            dio
├── Almacenamiento local:    sqflite + hive
├── Notificaciones push:     firebase_messaging + flutter_local_notifications
├── Cámara:                  image_picker / camera
├── GPS:                     geolocator
├── Chatbot académico:       Integración con API REST (Claude API / OpenAI)
├── Conectividad:            connectivity_plus
├── Seguridad:               flutter_secure_storage
└── Backend simulado:        REST API (Node.js + Express) / Firebase
```

### 4.4 Justificación Técnica Detallada

| Criterio | Justificación |
|---|---|
| **Reutilización de código** | Un único código base en Dart genera la aplicación para Android y, en el futuro, para iOS, reduciendo el tiempo de desarrollo y los costos de mantenimiento a largo plazo. |
| **Acceso a capacidades nativas** | Flutter cuenta con paquetes maduros y mantenidos activamente para cámara (`image_picker`, `camera`), GPS (`geolocator`), notificaciones push (`firebase_messaging`, `flutter_local_notifications`) y almacenamiento local (`hive`, `sqflite`). |
| **Rendimiento** | A diferencia de las soluciones basadas en WebView, Flutter compila directamente a código ARM nativo mediante el motor Skia/Impeller, garantizando 60 fps incluso en dispositivos con 2 GB de RAM, lo que es fundamental para el público objetivo. |
| **Costo y tiempo de desarrollo** | Comparado con el desarrollo nativo Android puro, Flutter reduce significativamente el tiempo de implementación al unificar la interfaz y la lógica de negocio en un solo proyecto, lo que es viable para el presupuesto institucional. |
| **Soporte offline** | `sqflite` y `hive` permiten almacenamiento local robusto. Con el patrón Repository, la app puede operar completamente en modo offline y sincronizar los cambios pendientes al recuperar la conexión, satisfaciendo la HU-02. |
| **Escalabilidad** | La arquitectura con BLoC o Cubit permite escalar la app con nuevas funcionalidades (más módulos, más materias, integración con otros sistemas académicos) sin necesidad de refactorizar la base del proyecto. |
| **Publicación** | El APK generado por Flutter puede publicarse directamente en Google Play Store, cumpliendo el requisito de aplicación instalable y descargable. |

---

## 5. Arquitectura Mínima Viable

La arquitectura de AcadémIA Mobile sigue el patrón de **capas desacopladas** (Clean Architecture simplificada), organizado en tres capas principales: Presentación, Dominio e Infraestructura.

### 5.1 Diagrama de Arquitectura por Capas

```
┌─────────────────────────────────────────────────────────────────┐
│                      CAPA DE PRESENTACIÓN                        │
│                                                                  │
│  ┌─────────────┐  ┌─────────────┐  ┌──────────────────────┐    │
│  │  Pantalla   │  │  Pantalla   │  │       Pantalla        │    │
│  │ Actividades │  │ Evidencias  │  │   Chatbot Académico   │    │
│  └─────────────┘  └─────────────┘  └──────────────────────┘    │
│  ┌─────────────┐  ┌─────────────┐  ┌──────────────────────┐    │
│  │  Pantalla   │  │  Pantalla   │  │       Pantalla        │    │
│  │    Inicio   │  │ Notificac.  │  │    Perfil Usuario     │    │
│  └─────────────┘  └─────────────┘  └──────────────────────┘    │
│                                                                  │
│             ► State Management: BLoC / Cubit ◄                  │
└─────────────────────────────┬───────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                        CAPA DE DOMINIO                           │
│                                                                  │
│  ┌───────────────────────────┐  ┌──────────────────────────┐   │
│  │       Casos de Uso        │  │         Entidades         │   │
│  │  - GetActividades         │  │  - Actividad              │   │
│  │  - RegistrarEvidencia     │  │  - Evidencia              │   │
│  │  - ConsultarChatbot       │  │  - Notificacion           │   │
│  │  - SincronizarDatos       │  │  - Usuario                │   │
│  └───────────────────────────┘  └──────────────────────────┘   │
└─────────────────────────────┬───────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    CAPA DE INFRAESTRUCTURA                       │
│                                                                  │
│  ┌──────────────────┐  ┌──────────────────┐                     │
│  │  API REST Client │  │  Almacenamiento  │                     │
│  │  (dio)           │  │  Local (sqflite  │                     │
│  │                  │  │  + hive)         │                     │
│  └──────────────────┘  └──────────────────┘                     │
│                                                                  │
│  ┌──────────────────┐  ┌──────────────────┐                     │
│  │  Módulo Cámara   │  │   Módulo GPS     │                     │
│  │  (image_picker)  │  │  (geolocator)    │                     │
│  └──────────────────┘  └──────────────────┘                     │
│                                                                  │
│  ┌──────────────────┐  ┌──────────────────┐                     │
│  │  Notificaciones  │  │  Conectividad    │                     │
│  │  (FCM + local)   │  │ (connectivity+)  │                     │
│  └──────────────────┘  └──────────────────┘                     │
└─────────────────────────────┬───────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                BACKEND / APIS EXTERNAS (simuladas)               │
│                                                                  │
│  REST API    ──►  Firebase Firestore / Node.js + Express         │
│  Push        ──►  Firebase Cloud Messaging (FCM)                 │
│  Chatbot     ──►  API de LLM (Claude API / OpenAI)              │
└─────────────────────────────────────────────────────────────────┘
```

### 5.2 Pantallas Principales

| Pantalla | Descripción |
|---|---|
| **Inicio** | Dashboard con resumen de actividades próximas y notificaciones recientes |
| **Actividades** | Lista de actividades ordenadas por fecha de entrega, con filtros por materia |
| **Detalle de Actividad** | Vista completa de una actividad con botón para registrar evidencia |
| **Evidencias Fotográficas** | Captura de foto, vista previa y vinculación a actividad; incluye coordenadas GPS |
| **Chatbot Académico** | Interfaz de conversación con el asistente de IA |
| **Notificaciones** | Historial de alertas recibidas con opción de configuración |
| **Perfil de Usuario** | Datos del estudiante, ajustes de la app y configuración de permisos |

### 5.3 Flujo de Sincronización Offline

```
App inicia
    │
    ├─── [Hay conexión] ──► Fetch API REST ──► Actualiza SQLite/Hive ──► Muestra datos
    │
    └─── [Sin conexión] ──► Lee SQLite/Hive ──► Muestra datos (modo offline)
                                                        │
                                              [Recupera conexión]
                                                        │
                                         Sincroniza cola de cambios pendientes
                                         (evidencias fotográficas, respuestas de chatbot)
```

### 5.4 Módulos Funcionales

**Módulo de API REST (`dio`)**
Gestiona las peticiones HTTP hacia el backend institucional. Implementa interceptores para adjuntar el token de autenticación en cada solicitud y para capturar errores de red, redirigiendo la lógica al almacenamiento local cuando no hay conexión disponible.

**Módulo de Almacenamiento Local (`sqflite` + `hive`)**
- `sqflite` almacena entidades estructuradas: actividades, materias, evidencias pendientes de sincronización.
- `hive` almacena configuraciones de usuario y respuestas FAQ del chatbot en formato clave-valor, con acceso más rápido.

**Módulo de Cámara (`image_picker`)**
Invoca la cámara nativa del dispositivo y devuelve la imagen capturada. La imagen se comprime localmente antes de almacenarse o enviarse al servidor, limitando el tamaño máximo a 800 KB por fotografía.

**Módulo GPS (`geolocator`)**
Solicita el permiso de ubicación de forma contextual y obtiene las coordenadas del dispositivo al momento de capturar una evidencia fotográfica. Si el permiso es denegado o el GPS no está disponible, el registro fotográfico procede sin coordenadas.

**Módulo de Notificaciones (`firebase_messaging` + `flutter_local_notifications`)**
Firebase Cloud Messaging (FCM) gestiona las notificaciones push en segundo plano y con la app cerrada. `flutter_local_notifications` programa recordatorios locales basados en las fechas de entrega almacenadas en el dispositivo, funcionando incluso sin conexión.

**Módulo de Chatbot (integración con LLM API)**
En modo online, realiza peticiones a la API del modelo de lenguaje para respuestas complejas. En modo offline, consulta una base de preguntas frecuentes (FAQ) precargada en `hive` para responder las consultas más habituales sin necesidad de internet.

---

## 6. Consideraciones Móviles

### 6.1 Conectividad Limitada

Se implementa el patrón **offline-first**: la aplicación consulta primero el almacenamiento local (SQLite/Hive) y accede a la API únicamente cuando detecta conexión activa. Un servicio `ConnectivityService` monitorea el estado de red en tiempo real utilizando el paquete `connectivity_plus`. Las evidencias fotográficas y los metadatos GPS se almacenan en una cola de sincronización local y se envían al servidor de forma automática cuando la red lo permite.

### 6.2 Bajo Consumo de Datos

- Las imágenes de evidencias se comprimen localmente antes de enviarse al servidor, con un límite máximo de **800 KB por fotografía**.
- La API implementa **paginación** y la app descarga únicamente las actividades del semestre académico en curso.
- Se utiliza **caché HTTP local** para respuestas repetidas, evitando peticiones innecesarias a la red.
- El chatbot en modo offline utiliza respuestas precargadas, eliminando el consumo de datos para consultas frecuentes.

### 6.3 Rendimiento en Dispositivos Modestos

- Flutter compila a **código nativo ARM** mediante el motor Skia/Impeller, evitando la penalización de rendimiento del WebView presente en soluciones híbridas.
- Las listas de actividades utilizan **`ListView.builder`** (renderizado virtual), cargando únicamente los elementos visibles en pantalla para minimizar el uso de memoria.
- Las animaciones complejas se desactivan automáticamente si el dispositivo reporta modo de bajo rendimiento mediante `MediaQuery.disableAnimations`.
- Se establece como versión mínima **Android 8.0 (API nivel 26)** para garantizar comportamiento uniforme en el parque de dispositivos del público objetivo.

### 6.4 Experiencia de Usuario en Pantallas Pequeñas

- La interfaz usa **diseño adaptativo** con `LayoutBuilder` y `MediaQuery` para ajustarse a pantallas desde 4.5 pulgadas sin degradar la usabilidad.
- Se utiliza la tipografía del sistema con tamaños mínimos de **14 sp** para garantizar legibilidad sin esfuerzo.
- Los botones de acción tienen una zona de toque mínima de **48×48 dp**, cumpliendo las guías de accesibilidad de **Material Design 3**.
- Los colores cumplen el contraste mínimo de **4.5:1** establecido por las pautas WCAG 2.1 nivel AA.

### 6.5 Gestión de Permisos del Dispositivo

Los permisos se solicitan de forma **contextual**, es decir, en el momento exacto en que se necesitan, con una explicación clara de su propósito antes de la solicitud del sistema operativo:

| Permiso | Momento de solicitud |
|---|---|
| `CAMERA` | Al intentar registrar una evidencia fotográfica desde la pantalla de actividades |
| `ACCESS_FINE_LOCATION` | Al activar el registro de ubicación GPS en el flujo de captura de evidencia |
| `POST_NOTIFICATIONS` (Android 13+) | Al iniciar sesión por primera vez en la aplicación |
| `READ/WRITE_EXTERNAL_STORAGE` | Al guardar evidencias localmente en dispositivos con Android < 10 |

Si el usuario deniega un permiso, la aplicación ofrece un flujo alternativo (por ejemplo, registrar la evidencia fotográfica sin coordenadas GPS) y muestra un mensaje explicativo sin bloquear el uso de las demás funcionalidades.

### 6.6 Seguridad Básica de los Datos

- El **token de autenticación** se almacena en `flutter_secure_storage`, que utiliza el Android Keystore del sistema operativo para cifrado a nivel de hardware.
- Las fotografías de evidencias se almacenan en el **directorio privado de la app** (`getApplicationDocumentsDirectory()`), inaccesible para otras aplicaciones instaladas en el dispositivo.
- Toda comunicación con la API y con el servicio de chatbot se realiza exclusivamente mediante **HTTPS/TLS**, validando el certificado del servidor.
- La sesión de usuario expira automáticamente tras **8 horas de inactividad**, requiriendo nueva autenticación.

---

## 7. Riesgos y Limitaciones

| # | Riesgo | Impacto | Probabilidad | Estrategia de mitigación |
|---|---|---|---|---|
| 1 | **Fallos de conexión a internet** | El estudiante no puede sincronizar actividades ni subir evidencias fotográficas actualizadas. | Alta | Implementar almacenamiento local con patrón offline-first y una cola de sincronización automática que se activa al recuperar la conexión. El usuario siempre puede consultar el último estado sincronizado. |
| 2 | **Fragmentación de Android en dispositivos de gama baja** | Comportamiento inconsistente en versiones Android 8–10 con distintos fabricantes (Huawei, Samsung, Motorola, etc.), especialmente en la gestión de procesos en segundo plano y notificaciones push. | Media | Establecer Android 8.0 (API 26) como versión mínima y realizar pruebas de aceptación en dispositivos físicos representativos del público objetivo, incluyendo al menos un modelo Huawei y uno Samsung de gama baja. |
| 3 | **Permisos denegados por el usuario** | Si el usuario rechaza el permiso de cámara o GPS, no puede registrar evidencias georreferenciadas, afectando el cumplimiento de actividades que lo requieren. | Media | Diseñar flujos alternativos que permitan el registro de evidencias sin ubicación GPS si el permiso es denegado. Mostrar explicaciones claras del beneficio de cada permiso antes de solicitarlo. Ofrecer la opción de habilitar el permiso desde ajustes del sistema. |
| 4 | **Tamaño del APK elevado en Flutter** | El APK base de Flutter (~8 MB) puede ser mayor al esperado para estudiantes con dispositivos de almacenamiento muy limitado (16–32 GB con sistema operativo preinstalado). | Baja | Utilizar `flutter build apk --split-per-abi` para generar APKs específicos por arquitectura (arm64-v8a, armeabi-v7a), reduciendo el tamaño descargable hasta en un 40%. Publicar en Google Play Store aprovechando la entrega optimizada por dispositivo (Android App Bundle). |
| 5 | **Disponibilidad del servicio de chatbot externo** | Si la API del modelo de lenguaje (LLM) no está disponible por mantenimiento o fallas del proveedor, el chatbot no puede procesar consultas complejas. | Baja | Implementar un sistema de respuestas predefinidas (FAQ estáticas) almacenadas localmente en Hive como mecanismo de fallback. El chatbot degradará su funcionamiento a respuestas básicas sin interrumpir el resto de la aplicación. |

---

## Enlace al Video de Sustentación

> 📹 **Video explicativo:** [Insertar enlace público de YouTube o Vimeo]
>
> El video cubre: descripción del problema, funcionalidades principales, enfoque tecnológico seleccionado, arquitectura propuesta y justificación de la decisión tecnológica. Duración máxima: 4 minutos.

---

*Documento elaborado como entrega de la Actividad Evaluativa — Unidad 3. Lenguaje de Computación para Móviles. Facultad de Ingeniería.*
