# 🛡️ Elysium — Comunidad de Gremio (Frontend y Backend)

**🔗 Despliegue (demo en vivo):** https://www.elysiumclan.com.ar

> 📩 Nota para reclutadores: este repositorio público contiene únicamente este README y el enlace de despliegue. Si desea revisar el código fuente completo, por favor envíe un correo cordial a **marioagallego91@gmail.com** con su nombre, empresa y motivo; responderé con acceso temporal al repositorio privado o con un paquete del código según prefiera.

---

## 🧭 Tabla de contenidos

- [Resumen](#resumen)
- [Características (completas)](#características-completas)
- [Arquitectura y tech stack](#arquitectura-y-tech-stack)
- [Flujo técnico de registro y aprobación](#flujo-técnico-de-registro-y-aprobación)
- [Variables de entorno](#variables-de-entorno)
- [Endpoints serverless incluidos](#endpoints-serverless-incluidos)
- [Requisitos y ejecución local](#requisitos-y-ejecución-local)
- [Seguridad y despliegue](#consideraciones-de-seguridad-y-despliegue)
- [Qué contiene este repo demo](#qué-contiene-este-repo-demo)
- [Contacto para reclutadores](#contacto-para-reclutadores)
- [Licencia](#licencia)

---

## 📋 Resumen

Elysium es la interfaz web para una comunidad/gremio de juego online. Es una SPA moderna (React + Tailwind) pensada para:

- gestionar eventos (piedras/asedios),
- organizar partys fijas,
- recibir y procesar solicitudes de ingreso,
- administrar wishlist de ítems,
- compartir clips de la comunidad,
- ofrecer mini-juegos y utilidades sociales.

Este repositorio público sirve como demo (enlace arriba). El código fuente completo está disponible bajo petición para procesos de reclutamiento.

---

## ✨ Características 

- 🗓️ Gestión de eventos (piedras, asedios): crear, editar, listar y marcar asistencia.
- 👥 Partys fijas: crear grupos por evento, añadir/quitar miembros desde la UI.
- 📨 Sistema de solicitudes de ingreso:
  - Envío público de solicitudes.
  - Almacenamiento en Firestore (`solicitudes`) con estados: `pendiente`, `aprobado`, `rechazado`.
  - Panel de administración para revisar solicitudes.
- ✅ Aprobación y registro automatizado:
  - Generación de código único (token) al aprobar.
  - Envío automático del código por correo (endpoint serverless).
  - Validación de códigos y activación de miembros.
- 🔐 Autenticación y proveedores:
  - Firebase Auth (email/password).
  - Login con Google (OAuth) integrado.
  - Roles en Firestore: `miembro`, `admin`.
- 🖼️ Subida y visualización de imágenes (Imgur) para fotos de vanguardia y eventos.
- 🎯 Wishlist de ítems/armas (visible en demo solo para administradores).
- 🎬 Clips de la comunidad: subir y reproducir clips (YouTube o vídeo directo).
- 🎮 Micro-juegos integrados: Parry Game, Historia sin Fin, y más.
- 🧭 Dashboard de administración: controlar eventos, miembros, solicitudes y contenido.
- 🔎 Búsqueda y herramientas: búsqueda de build/equipamiento por miembro, eliminación de miembros, exportes básicos.

## 🖼️ GAleria

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
  <img src="https://github.com/user-attachments/assets/e6a4e4d8-2471-4f82-9b27-ab32a444ffbd" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/8d5719e8-b297-49dd-bcd0-e3cf09e27ea6" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/eabba1cc-5c20-4faf-9b6f-b9d73dab54a7" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/c50d7e80-ca8c-443c-8051-3f58d0373a9e" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/9b22530b-813a-42b9-a67c-a3188905eb23" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/51a46567-06c5-4a95-a150-7f439b1e76bd" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/0de1cfe4-4dbf-4b35-9fbe-3e866e905c70" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/7b061938-fc91-4fb9-ae7b-1c709fbfe6ee" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/578746b4-9134-4ef1-94c8-86c028e1beda" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/2d70f689-523f-4a94-bf31-0bf453a904ba" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/f957fe9f-cc38-4a03-a58c-59a12fe77d87" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/c62468a4-c85d-40f2-9370-404405da3c78" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/fdf6ac0a-11a4-4ac2-9480-c26776c5e6de" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/15984a31-6e86-41fe-93ef-5aa9c4e4fe49" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/c7e676e1-d795-4fbe-8392-0a0e83feb485" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/0431b608-9e8f-4612-902e-f81ca08116c3" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/93a769ad-f7eb-4241-a804-6aa06950cd2c" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/f93a03f9-9127-4f80-9655-c49951a1daf8" width="200" alt="image" />
  <img src="https://github.com/user-attachments/assets/387340c3-44fc-445f-bc79-405946bc1e76" width="200" alt="image" />
</div>

## 🏗️ Arquitectura y tech stack

- Frontend: React 18 + Vite
- Estilos: Tailwind CSS
- Animaciones: Framer Motion
- BBDD y Auth: Firebase (Firestore, Auth). Opcional: Firebase Admin SDK para funciones seguras.
- Serverless / Endpoints: Node.js en `api/` (ejemplos preparados para Vercel/Netlify)
- Email: Nodemailer o integraciones (SendGrid, Mailgun, SES)

Dependencias clave: `firebase`, `firebase-admin`, `framer-motion`, `nodemailer`, `vite`.

---

## 🔁 Flujo técnico de registro y aprobación (detallado)

1. El usuario completa un formulario de solicitud en la UI pública.
2. El frontend crea un documento en `solicitudes` en Firestore con estado `pendiente`.
3. El administrador revisa la solicitud desde la interfaz de administración.
4. Al aprobar, `api/registrarMiembro.js`:
   - Genera un token único con TTL (expiración) y lo marca de un solo uso.
   - Guarda la referencia en Firestore.
   - Llama a `api/sendEmail.js` para enviar el código al solicitante.
5. El solicitante usa el código para activar su cuenta o el sistema lo marca como miembro según la configuración.

**Seguridad:** los endpoints críticos deben validar que la petición provenga de un admin autenticado (verificación con Firebase Admin o comprobación de rol en Firestore). Los tokens son de un solo uso y expiran.

---

## 🔑 Variables de entorno (ejemplos)

- `VITE_IMGUR_CLIENT_ID` — Client ID Imgur
- `VITE_FIREBASE_API_KEY`, `VITE_FIREBASE_AUTH_DOMAIN`, `VITE_FIREBASE_PROJECT_ID`, `VITE_FIREBASE_STORAGE_BUCKET`, `VITE_FIREBASE_MESSAGING_SENDER_ID`, `VITE_FIREBASE_APP_ID`
- `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS` — credenciales SMTP o API key proveedor de email
- `GOOGLE_OAUTH_CLIENT_ID`, `GOOGLE_OAUTH_CLIENT_SECRET` — para login con Google (si no se usa Firebase delegando)

> ⚠️ Nunca incluir credenciales en repositorios públicos. Usar variables de entorno en el proveedor de hosting.

---

## ⚙️ Endpoints serverless incluidos (resumen)

- `api/registrarMiembro.js` — genera código de registro y coordina su envío.
- `api/sendEmail.js` — wrapper para envío de correos (SMTP o API externa).
- `api/validarCodigo.js` — valida códigos de registro y completa la activación.

> Estos archivos son ejemplos que requieren configuración de variables de entorno y permisos adecuados.

---

## 🚀 Requisitos y ejecución local

Requisitos:
- Node.js >= 18
- npm o yarn
- (Opcional) Firebase CLI para emulación local

Instalación y ejecución:

```bash
npm install
# configurar .env con variables necesarias
npm run dev
```

Para desarrollar y probar endpoints serverless se recomienda la emulación de Firebase o ejecutar un servidor Node apuntando a `api/`.

---

## 🔒 Consideraciones de seguridad y despliegue

- Revisar y endurecer reglas de Firestore (read/write) antes de exponer datos.
- Validar que los endpoints que generan códigos o envían correos solo permitan peticiones de admins autenticados.
- Configurar CORS y servir siempre mediante HTTPS.
- Evitar logs con datos personales sensibles.

---

## 📦 Qué contiene este repositorio demo

Incluye:
- README completo y enlace de despliegue público.
- Demo en producción que muestra la interfaz (sin exponer credenciales).

No incluye:
- Credenciales (Firebase admin keys, SMTP)
- Repositorio completo del código (se entrega bajo petición a reclutadores)

---

## 📬 Contacto para reclutadores

**Mario A. Gallego** — marioagallego91@gmail.com

Por favor incluya en el correo: nombre, compañía, puesto y motivo de la solicitud. Responderé con acceso privado al código o instrucciones para revisar el proyecto según su preferencia.
---

---

## 📜 Licencia

Contenido demo para evaluación técnica. Para acuerdos de licencia o uso en producción, contactar al autor.
