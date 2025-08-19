# Elysium — Comunidad de Gremio (Frontend y Backend)

**Despliegue (demo en vivo):** https://www.elysiumclan.com.ar

> Nota para reclutadores: este repositorio público contiene únicamente este README y el enlace de despliegue. Si desea revisar el código fuente completo, por favor envíe un correo cordial a marioagallego91@gmail.com con su nombre, empresa y motivo; responderé con acceso temporal al repositorio privado o con un paquete del código según prefiera.

---

## Resumen

Elysium es la interfaz web de una comunidad/gremio de juego online. Es una SPA moderna construida con React y Tailwind, diseñada para gestionar eventos, organizar partys, gestionar solicitudes de ingreso, administrar una wishlist de ítems, compartir clips y ofrecer micro-juegos sociales.

El propósito de este repositorio público es mostrar la demo desplegada. El código completo se facilita bajo petición para procesos de reclutamiento.

---

## Características (completas)

- Gestión de eventos (piedras, asedios): crear, editar, listar y marcar asistencia.
- Partys fijas: crear grupos por evento, añadir/quitar miembros desde la UI.
- Sistema de solicitudes de ingreso:
  - Los usuarios pueden enviar solicitudes públicas para ingresar al gremio.
  - Las solicitudes quedan almacenadas en Firestore en la colección `solicitudes` con estados `pendiente`, `aprobado`, `rechazado`.
  - Los administradores revisan y gestionan solicitudes desde el panel de administración.
- Aprobación y registro automatizado:
  - Al aprobar una solicitud, el backend genera un código de registro único (de un solo uso) y lo envía automáticamente por correo al solicitante.
  - Existen endpoints serverless para generar, enviar y validar códigos (`api/registrarMiembro.js`, `api/sendEmail.js`, `api/validarCodigo.js`).
- Autenticación y proveedores:
  - Firebase Auth (email/password) integrado.
  - Login con Google (OAuth) habilitado vía Firebase o configuración OAuth propia.
  - Roles y permisos almacenados en Firestore (miembro, admin).
- Subida y visualización de imágenes (Imgur) para vanguardias y recursos de evento.
- Wishlist de ítems/armas (visible en demo solo para administradores).
- Clips de la comunidad: subir y ver clips (YouTube o vídeo directo).
- Micro-juegos: Parry Game, Historia sin Fin, etc.
- Dashboard de administración con controles sobre eventos, miembros, solicitudes y contenido.
- Busqueda de build(equipamiento de cada miembro).
- Eliminacion de miembros

---

## Arquitectura y tech stack

- Frontend: React 18 + Vite
- Estilos: Tailwind CSS
- UI/animaciones: Framer Motion
- BBDD y Auth: Firebase (Firestore, Auth, optional Admin SDK)
- Serverless / Endpoints: Node.js (carpeta `api/`) — ejemplos para Vercel/Netlify
- Email: Nodemailer o integraciones con SendGrid/Mailgun/Amazon SES

Dependencias clave (ver `package.json`): `firebase`, `firebase-admin`, `framer-motion`, `nodemailer`, `vite`.

---

## Flujo técnico de registro y aprobación (detallado)

1. Usuario completa formulario de solicitud en UI pública.
2. Frontend crea documento en `solicitudes` en Firestore con estado `pendiente`.
3. Admin revisa solicitudes desde la interfaz admin.
4. Al aprobar, el endpoint `api/registrarMiembro.js`:
   - Genera un código único de registro (token) con expiración y marca de uso.
   - Guarda el token y la relación en Firestore.
   - Llama a `api/sendEmail.js` para enviar el código al solicitante.
5. El solicitante utiliza el código para completar la activación o el proceso puede marcarlo automáticamente como miembro según la configuración.

Seguridad:
- Los endpoints que modifican estados críticos (aprobación, generación de códigos, envío de correos) deben requerir autenticación admin (por ejemplo, verificación del token Firebase Admin o comprobación de rol en Firestore).
- Los códigos tienen TTL y caducan si no se usan en un plazo configurable.

---

## Variables de entorno (ejemplos)

- `VITE_IMGUR_CLIENT_ID` — Client ID Imgur
- `VITE_FIREBASE_API_KEY`, `VITE_FIREBASE_AUTH_DOMAIN`, `VITE_FIREBASE_PROJECT_ID`, `VITE_FIREBASE_STORAGE_BUCKET`, `VITE_FIREBASE_MESSAGING_SENDER_ID`, `VITE_FIREBASE_APP_ID`
- `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS` — para envío de correos (o usar credenciales del proveedor)
- `GOOGLE_OAUTH_CLIENT_ID`, `GOOGLE_OAUTH_CLIENT_SECRET` — para login con Google (si no se usa Firebase como proxy)

> Nunca incluir credenciales en repositorios públicos. Usar variables de entorno en el hosting.

---

## Endpoints serverless incluidos (resumen)

- `api/registrarMiembro.js` — genera código de registro y coordina su envío al solicitante.
- `api/sendEmail.js` — envía correos (SMTP o API externa).
- `api/validarCodigo.js` — valida código de registro y completa la activación.

Estos archivos contienen ejemplos y requieren configurar variables de entorno para SMTP y credenciales.

---

## Requisitos y ejecución local

Requisitos
- Node.js >= 18
- npm o yarn
- (Opcional) Firebase CLI para emulación local de Firestore y funciones

Instalación

```bash
npm install
# configurar .env con variables necesarias
npm run dev
```

Para probar endpoints serverless localmente se recomienda usar la emulación de Firebase o ejecutar un servidor Node local apuntando a `api/`.

---

## Consideraciones de seguridad y despliegue

- Revisar y endurecer reglas de Firestore para evitar lecturas/escrituras públicas no autorizadas.
- Asegurar endpoints críticos (generación de códigos, envío de correos) verificando que la petición la realice un administrador autenticado.
- Usar HTTPS y configurar CORS correctamente en los endpoints.
- Limitar logs con datos personales y evitar almacenar información sensible en texto plano.

---

## Qué contiene este repositorio demo

- README completo y enlace de despliegue público.
- La demo desplegada muestra la UI sin exponer credenciales ni datos sensibles.

No incluye:
- Credenciales (Firebase admin keys, SMTP)
- Repositorio completo del código (se entrega bajo petición)

---

## Contacto para reclutadores

Mario A. Gallego — marioagallego91@gmail.com

Por favor incluya en el correo: nombre, compañía, puesto y motivo de la solicitud. Responderé con acceso privado al código o con instrucciones para revisar el proyecto según su preferencia.
---


## Licencia

Contenido demo para evaluación técnica. Para acuerdos de licencia o uso en producción, contacte al autor.
