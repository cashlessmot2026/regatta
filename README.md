# La Regatta · Taplink con registro, encuesta, ruleta y dashboard

React (Vite) + Supabase. Colores y tipografía tomados de restaurantelaregatta.com
(Poetsen One + Poppins; rosa `#D13F6F`, marrón `#34110D`, dorado `#F6BA33`, crema `#F5E6D3`, teal `#1B8E8F`, azul `#134252`).

## Rutas
- `/` → vista tipo taplink: Página web, Reserva aquí, ¿Por qué elegir La Regatta?, registro → encuesta → ruleta, redes sociales.
- `/admin` → dashboard (sin usuario ni clave).

## Pasos para subirlo
1. Crea un proyecto en https://supabase.com.
2. Abre **SQL Editor**, pega todo `schema.sql` y dale **Run**.
3. Copia `.env.example` a `.env` y pega la `Project URL` y la `anon public key` (Project Settings → API).
4. Local: `npm install` y `npm run dev`.
5. Producción: `npm run build` y sube la carpeta `dist/` (Vercel, Netlify o hosting).
   En Vercel/Netlify agrega las mismas variables `VITE_SUPABASE_URL` y `VITE_SUPABASE_ANON_KEY`.
   `vercel.json` y `public/_redirects` ya hacen que `/admin` funcione.

## El juego
- Se activa/apaga en `/admin → Juego y premios` (por defecto viene **APAGADO**).
- Inventario inicial: 5 × 10 %, 5 × 5 %, 1 × cena para 2 (se entrega una sola vez).
- El resultado lo decide la base de datos (`play_game`), no el navegador; cuando no gana muestra "¡Sigue intentando!".
- Ajustables: probabilidad de ganar por giro e intentos por persona. Cada persona (correo) puede ganar solo un premio.

## Dashboard
Visitas a las URLs, visitantes únicos, clics por botón, registros, clics en reservar,
ciudades de origen, encuestas, giros, ganadores con su código, editor de encuesta
(selección única, múltiple, respuesta libre, escala 1-5, número; cuantitativa/cualitativa)
y exportación de registrados a CSV.

> ⚠️ Como `/admin` no tiene clave, cualquiera que conozca la URL puede ver los datos
> y cambiar la configuración. Para más privacidad, renombra la ruta en `src/main.jsx`
> (ej. `/admin-regatta-8f3k`) o agrega login con Supabase Auth.
