# Dota 2 — Sistema de rotina diária de criação de conteúdo

Sistema que gera, todos os dias, uma lista rápida de ideias de vídeo (formato
longo, YouTube) sobre Dota 2, sempre ancorada em dados/eventos recentes
(últimos 3–5 dias) e inspirada em um conjunto de canais de referência.

## Como funciona

1. Uma **Rotina** (agendamento automático) dispara todo dia às **08:00
   BRT (11:00 UTC)**.
2. A cada disparo, uma sessão nova do Claude:
   - Pesquisa dados recentes de meta (pub e competitivo), patch atual e
     jogadas/partidas em destaque dos últimos 3–5 dias, via `WebSearch`
     (busca na web, referenciando Dotabuff, Dotaprotracker e OpenDota).
   - Lê a lista de canais de referência em [`config/channels.md`](config/channels.md).
   - Gera de 8 a 12 ideias de vídeo em bullet points, misturando análise de
     jogadas/replays de pro com conteúdo de conceito/mentoria.
   - Salva o briefing em `briefings/AAAA-MM-DD.md`, commita e dá push.
   - Cria um card no Trello, board **"Criação de conteúdo"**, lista
     **"Ideias"**, com a lista de ideias do dia na descrição.
   - Envia a lista de ideias diretamente para o usuário, com notificação.

As instruções completas seguidas em cada disparo estão em
[`prompts/daily_briefing.md`](prompts/daily_briefing.md).

## Estrutura

```
config/channels.md       # lista de canais de referência, por categoria
prompts/daily_briefing.md # instruções completas do briefing diário
briefings/AAAA-MM-DD.md   # histórico de briefings gerados
```

## Ajustar o sistema

- **Trocar/adicionar canais de referência**: editar `config/channels.md`.
- **Mudar o formato/regras do briefing**: editar `prompts/daily_briefing.md`.
- **Mudar horário ou frequência**: atualizar a Rotina (pedir para o Claude
  ajustar via `update_trigger`, ou remover e recriar).
- **Gerar um briefing manualmente**, fora do horário programado: basta pedir
  "gera o briefing de hoje" em qualquer conversa com o Claude neste
  repositório — ele vai seguir `prompts/daily_briefing.md`.

## Limitação técnica atual

O ambiente de execução não tem acesso de rede direto a `dotabuff.com`,
`dotaprotracker.com` ou `api.opendota.com` (bloqueado pela política de rede
do sandbox). Por isso os dados vêm de busca na web (`WebSearch`), não de
chamadas diretas às APIs desses sites — o que é suficiente para gerar ideias
com contexto atual, mas é menos preciso que dados brutos de API. Se no
futuro o ambiente permitir acesso de rede mais amplo, o sistema pode evoluir
para puxar dados diretamente dessas fontes.
