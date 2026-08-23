# ✦ hackdeck

Deck offline de utilidades para pentesting y CTFs en **un solo fichero HTML**. Ábrelo en cualquier navegador — funciona sin conexión, sin servidor, sin extensiones: todo corre en tu navegador y **nada sale de tu máquina**.

```
b64 · url · hex · jwt · sha-1/256/512 · xor · césar · uuid v4 · timestamps
```

## Por qué

CyberChef es enorme; las webs de "decodear base64" te mandan cada pulsación a un analytics ajeno — irónico cuando estás auditando algo. `hackdeck` es lo contrario: un único `index.html` (~15 KB) que guardas en el escritorio o en la barra del navegador, con la estética hyperpop que merece tu terminal.

## Herramientas

| Módulo | Qué hace |
|---|---|
| **Base64** | codifica/decodifica unicode-safe (también JWT base64url) |
| **URL** | percent-encoding ida y vuelta |
| **Hex** | texto ↔ hex (tolera espacios, `0x`, saltos de línea) |
| **JWT** | decodifica header/payload y traduce `exp`/`iat`/`nbf` a fechas |
| **SHA** | SHA-1 / SHA-256 / SHA-512 vía WebCrypto nativo |
| **XOR** | cifrado con clave rotatoria, texto ↔ hex |
| **César** | desplazamiento 1–25 con slider en vivo |
| **Extras** | generador UUID v4, conversor unix ↔ fecha ISO |

Cada tarjeta tiene botón de copiar al portapapeles y validación amable de errores.

## Uso

```bash
# opción 1: descargar y abrir
curl -LO https://thorrijadev.github.io/hackdeck/index.html
xdg-open index.html

# opción 2: directamente online (GitHub Pages)
# https://thorrijadev.github.io/hackdeck/
```

## Privacidad y ética

- Cero JavaScript externo, cero fuentes remotas, cero peticiones tras cargar.
- WebCrypto local para hashes; nada se envía jamás a ningún servidor.
- Herramienta pensada para CTFs, aprendizaje y auditorías **autorizadas**. Úsala solo donde tengas permiso.

## Desarrollo

El propio fichero incluye una batería de auto-tests (`window.__selftest()`), ejecutada en CI headless:

```bash
chromium --headless --dump-dom 'file://.../index.html' | grep ST::
# ST::b64e:PASS b64d:PASS url:PASS hex:PASS hexback:PASS rot13:PASS jwt:PASS xor:PASS uuid:PASS ts:PASS
```

## Licencia

[MIT](LICENSE)
