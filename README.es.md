# Eyes on Guard

**Extensión de [Eyes on Claude](https://github.com/dfadify-web/eyes-on-claude).** Vigilancia de seguridad en vivo de lo que ejecuta Claude: comandos destructivos, curl | sh, force push, secretos en claro, archivos sensibles y cambios de configuración persistente.

[English](README.md)

![Eyes on Guard](docs/screenshot.png)

## Qué hace

- 17 reglas en tres niveles sobre cada llamada real (comandos, contenido escrito, rutas).
- Los secretos (claves de Anthropic/OpenAI/GitHub/AWS/Slack/Google, claves privadas) siempre enmascarados.
- Puntuación de riesgo, lista de hallazgos con el fragmento resaltado y resumen por sesión.
- Activa o desactiva reglas. Solo observa: no bloquea ni cambia nada.

Todo sale del stream real de Eyes on Claude (los transcripts de Claude Code): nada se inventa.

## Instalar

Requiere Eyes on Claude **v2.3+** y Node 18+.

```bash
npx -y github:dfadify-web/eyes-on-guard
```

Abre Eyes on Claude → **Extensiones** → **Eyes on Guard** (`http://localhost:7777/#ext/eyes-on-guard`). Desinstalar: `npx -y github:dfadify-web/eyes-on-guard --uninstall`.

Suelta: `node server.js` → `http://localhost:7783` (necesita Eyes on Claude en :7777).

## Cómo funciona

Un servidor Node sin dependencias (`server.js`) sirve `public/` y reenvía el stream en vivo `/events` de Eyes on Claude. Solo escucha en 127.0.0.1.

MIT © dfadify-web
