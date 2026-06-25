# Forecast de Demanda — App lista para desplegar

Este es el proyecto completo de la herramienta de Forecast de Demanda, listo para
publicar en internet con un link que cualquiera puede abrir y usar (subiendo su
propio CSV o usando los datos de demostración).

## Opción A — Desplegar en Vercel (recomendado, gratis, ~5 minutos)

### Método más simple: arrastrar y soltar

1. Entra a **https://vercel.com** y crea una cuenta gratis (puedes usar tu correo o GitHub).
2. En tu computador, abre una terminal dentro de esta carpeta y ejecuta:
   ```bash
   npm install
   npm run build
   ```
   Esto crea una carpeta `dist/` con la app lista.
3. Instala la herramienta de Vercel (una sola vez):
   ```bash
   npm install -g vercel
   ```
4. Despliega:
   ```bash
   vercel --prod
   ```
   La primera vez te pedirá iniciar sesión y confirmar el proyecto (acepta los
   valores por defecto presionando Enter). Al terminar te entrega un link público
   tipo `https://forecast-demanda-xxx.vercel.app`.

5. Comparte ese link. Quien lo abra puede usar la herramienta completa y subir su CSV.

### Alternativa con GitHub (si prefieres)

1. Sube esta carpeta a un repositorio en GitHub.
2. En Vercel, "Add New Project" → importa el repositorio.
3. Vercel detecta Vite automáticamente. Presiona "Deploy".
4. Cada cambio que subas a GitHub se actualiza solo.

## Opción B — Netlify (igual de simple)

1. Entra a **https://app.netlify.com/drop**
2. Ejecuta `npm install && npm run build` localmente.
3. Arrastra la carpeta `dist/` a esa página. Te da un link al instante.

## Probar localmente antes de desplegar

```bash
npm install
npm run dev
```
Abre el link que aparece (normalmente http://localhost:5173).

## Formato del CSV que acepta la herramienta

Columnas mínimas: `SKU`, `Fecha` (formato AAAA-MM), `Venta`.
Opcionales: `Sucursal` (activa el top-down por local) y `Nombre`.

Ejemplo:
```
SKU,Nombre,Sucursal,Fecha,Venta
ENE-AA4,Energizer MAX AA x4,Santiago Centro,2023-01,415
```

## Notas

- La herramienta funciona 100% en el navegador. No envía datos a ningún servidor:
  el CSV que sube cada usuario se procesa localmente en su propia sesión.
- Por lo mismo, los datos no se guardan entre sesiones (cada visita parte de cero).
  Para persistencia y multi-usuario se necesita el backend (carpeta `backend/` aparte).
