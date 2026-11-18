# Nexus Collective — página principal

Página estática para publicar en `https://nexuscollective.app/`.

## Archivos

- `index.html`: página principal con estilos y JavaScript integrados.
- `favicon.svg`: icono de la página.

## Publicación en GitHub Pages

1. Crea un repositorio independiente, por ejemplo `nexuscollective`.
2. Sube el contenido de esta carpeta (`index.html` y `favicon.svg`) a la raíz del repositorio, no una carpeta adicional.
3. En **Settings → Pages**, selecciona **Deploy from a branch**, rama `main` y carpeta `/ (root)`.
4. En **Custom domain**, escribe `nexuscollective.app` y guarda. GitHub añadirá el archivo `CNAME` si publicas desde una rama.
5. En Cloudflare → DNS, configura el dominio raíz `@` con estos cuatro registros `A`, todos como **DNS only** mientras se verifica el dominio y se genera el certificado:

   | Type | Name | IPv4 |
   |---|---|---|
   | A | @ | `185.199.108.153` |
   | A | @ | `185.199.109.153` |
   | A | @ | `185.199.110.153` |
   | A | @ | `185.199.111.153` |

6. Opcionalmente, añade los registros `AAAA` para IPv6:

   | Type | Name | IPv6 |
   |---|---|---|
   | AAAA | @ | `2606:50c0:8000::153` |
   | AAAA | @ | `2606:50c0:8001::153` |
   | AAAA | @ | `2606:50c0:8002::153` |
   | AAAA | @ | `2606:50c0:8003::153` |

7. Opcionalmente, para que `www.nexuscollective.app` también funcione, añade un `CNAME` con nombre `www` y destino `charachoco999.github.io`.
8. Comprueba que no queden registros `A`, `AAAA` o `ALIAS` adicionales en `@` que apunten a otro proveedor. Espera a que GitHub Pages verifique el dominio y active TLS; después podrás activar **Enforce HTTPS**.

Los cambios DNS pueden tardar hasta 24 horas en propagarse. No configures `nexuscollective.app` como un CNAME normal si tu proveedor no ofrece `ALIAS`/`ANAME` o aplanamiento de CNAME para el dominio raíz.

## Navegación incluida

- `https://chat.nexuscollective.app/`
- `https://coallition.nexuscollective.app/`

Los enlaces externos se abren en una pestaña nueva. No hay backend, base de datos, Workers ni dependencias externas.
