# 10Care – sitio temporal (en modernización)

Sitio estático (un solo `index.html`, sin build) para https://10care.s4l.life/

## Despliegue: GitHub + Cloudflare Pages

1. Crear repo en GitHub (ej. `10care-site`) y subir estos archivos:
   ```bash
   git init && git add . && git commit -m "Sitio temporal en modernización"
   git branch -M main
   git remote add origin https://github.com/<usuario>/10care-site.git
   git push -u origin main
   ```
2. Cloudflare → Workers & Pages → Create → Pages → Connect to Git → elegir el repo.
   - Framework preset: **None**
   - Build command: *(vacío)*
   - Build output directory: `/`
3. Pages → proyecto → Custom domains → Set up a domain → `10care.s4l.life`.
4. En **GoDaddy** (DNS de s4l.life): quitar/editar el registro actual de `10care` (apunta a Latinoamerican Hosting / Wix) y crear:
   - Tipo `CNAME`, Nombre `10care`, Valor `<proyecto>.pages.dev`, TTL 600.
   No hace falta mover el dominio ni los nameservers a Cloudflare.
5. Esperar el certificado SSL (minutos) y verificar.

Nota: antes de cambiar el CNAME, confirmar que `10care` no tenga además un registro A/AAAA, y que el correo (MX) de s4l.life no se vea afectado (solo se toca el subdominio `10care`).
