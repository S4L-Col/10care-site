# 10Care – sitio temporal (en modernización)

Sitio estático (un solo `public/index.html`, sin build) publicado en https://10care.s4l.life/

## Despliegue

- **Cloudflare Pages**, proyecto `10care-site`. Dominio `10care.s4l.life` (CNAME hacia `10care-site.pages.dev`).
- **Automático:** cada push a `main` corre `.github/workflows/deploy.yml` (`wrangler pages deploy public`). También se puede lanzar a mano desde Actions (*Run workflow*).
- **Secretos del repo:** `CLOUDFLARE_API_TOKEN` (permiso *Pages Write*; **vence el 16 oct 2027**, el mismo token de `s4l-site`) y `CLOUDFLARE_ACCOUNT_ID`.
- **Despliegue manual de emergencia** (con sesión de wrangler): `npx wrangler pages deploy public --project-name 10care-site --branch main`.
