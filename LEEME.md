# Tarjeta de lealtad digital — Kupuri Cocina de Mar

Mismo sistema que ya conoces de Püri Café: GitHub + Netlify + Firebase Firestore (gratis).

## Archivos que debes subir a GitHub

Sube **toda la carpeta**, no solo los HTML:
- `index.html` (link para clientes)
- `staff.html` (link para el restaurante, con PIN)
- `LEEME.md` (opcional, referencia tuya)
- carpeta `assets/` completa (logo y fotos)

## Paso 1 — Crear el proyecto en Firebase

1. https://console.firebase.google.com → "Agregar proyecto" → nómbralo `kupuri-lealtad` (o el que prefieras).
2. Compilación → Firestore Database → "Crear base de datos" → **modo de producción** → región más cercana.
3. Pestaña "Reglas" → pega esto → "Publicar":

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /clientes/{clienteId} {
      allow read, write: if true;
    }
  }
}
```

4. Ícono de engrane ⚙️ → Configuración del proyecto → "Tus apps" → ícono `</>` (Web) → regístrala → copia los 6 valores del `firebaseConfig`.

## Paso 2 — Pegar la configuración

Pega esos 6 valores **en los dos archivos**: `index.html` Y `staff.html` (busca "TU_API_KEY" en cada uno, aparece una sola vez por archivo).

## Paso 3 — GitHub y Netlify

Igual que con Püri Café: crea el repositorio, sube la carpeta completa (index.html + staff.html + assets), conéctalo a Netlify, dale deploy.

## Links una vez desplegado

- **Clientes:** `tu-sitio.netlify.app`
- **Staff (con PIN):** `tu-sitio.netlify.app/staff.html`
- **PIN por default:** `2026` — puedes cambiarlo dentro de `staff.html`, busca la línea `const PIN_STAFF = "2026";`

## Programa de lealtad

- Sello 3 de 10 → 1 empanada de camarón gratis
- Sello 5 de 10 → 1 cubeta de 5 Coronitas o Victorias 210ml
- Sello 10 de 10 → 1 aguachile grande gratis (reinicia la tarjeta)

## Funciones incluidas

- Botón de WhatsApp para el staff, con mensaje que avisa cuántos sellos faltan para cada recompensa.
- Captura opcional de datos extra del cliente (correo, Instagram, colonia, cumpleaños, cómo conoció el lugar, ocupación).
- Dashboard en `staff.html` → pestaña "Todos los clientes": lista completa con filtro, y estadísticas (total de clientes, promedio de sellos, tarjetas completadas).
