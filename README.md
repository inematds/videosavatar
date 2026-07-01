# 🎬 VideosAvatar — avatar falante INEMA com HeyGen

Ecossistema para gerar vídeos de **avatar falante** no HeyGen a partir de um roteiro de texto (9:16, 720p, voz PT-BR) e **entregar o MP4 no bot do openpcbot** (Telegram).

**Página de guia:** https://inematds.github.io/videosavatar/

## Os dois caminhos (mesma geração, billing diferente)

| Caminho | Cofre que gasta | Auth | Skill do Claude Code |
|---|---|---|---|
| **API direta** (`POST /v3/videos`) | pool de **API** (pay-as-you-go) | API key | `heygen-cli` |
| **MCP remoto** (`mcp.heygen.com`) | créditos da **assinatura** (plano) | OAuth | `heygen-mcp` |

Os dois usam os mesmos IDs de avatar/voz e entregam no mesmo bot. Prefira a **assinatura** (créditos já pagos no mês); deixe a API como reserva.

## Uso rápido (skill heygen-cli)

```bash
node ~/.claude/skills/heygen-cli/scripts/heygen.mjs --text "sua fala aqui"
node ~/.claude/skills/heygen-cli/scripts/heygen.mjs voices --lang pt   # vozes PT
node ~/.claude/skills/heygen-cli/scripts/heygen.mjs avatars            # seus perfis
```

Defaults: 9:16 · 720p · voz PT-BR · entrega no bot. Saída em `~/projetos/output/heygen/<slug>/`.

## Assinatura (skill heygen-mcp)

```bash
claude mcp add --transport http heygen https://mcp.heygen.com/mcp/v1/
# depois: /mcp → heygen → Authenticate (login no navegador)
```

## Configuração

Tudo vem do `.env` do openpcbot: `HEYGEN_API_KEY`, `HEYGEN_AVATAR_ID_NEI`, `HEYGEN_VOICE_ID_NEI`, `TELEGRAM_BOT_TOKEN`, `ALLOWED_CHAT_ID`. **Nenhuma credencial fica neste repo.**

---
INEMA.CLUB · https://inema.club
