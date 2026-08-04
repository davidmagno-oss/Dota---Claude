# Instruções — Briefing diário de conteúdo Dota 2

Objetivo: todo dia, gerar uma lista rápida (bullet points) de ideias de vídeo
**longo para YouTube** sobre Dota 2, sempre ancoradas em dados/eventos dos
**últimos 3 a 5 dias** (nunca mais velhos que isso, a menos que ainda estejam
claramente moldando o meta atual).

## Passo a passo

1. **Definir a janela de tempo**: hoje menos 5 dias. Qualquer dado, partida
   ou patch usado como gancho precisa estar dentro dessa janela.

2. **Levantar dados recentes via WebSearch** (não há acesso direto a APIs
   externas neste ambiente — ver nota técnica no final). Fazer buscas
   direcionadas cobrindo:
   - Patch/balance update mais recente ("Dota 2 patch notes [semana atual]",
     "Dota 2 balance update this week").
   - Tendências do **pub**: heróis em alta/baixa de win rate e pick rate
     (buscar por menções a "dotabuff hero trends", "Dota 2 meta heroes
     trending [mês/ano atual]").
   - Tendências do **competitivo**: heróis mais picados/banidos em partidas
     pro recentes, resultados de torneios em andamento (buscar por menções a
     "dotaprotracker", "Dota 2 pro matches this week", nome do torneio atual
     + "results").
   - Jogadas/replays notáveis dos últimos dias (upsets, plays de destaque,
     performances de times/jogadores específicos).
   - Opcional, best-effort: buscar por 2-3 canais da lista de referência
     (`config/channels.md`) + "Dota 2" para sentir que temas estão em alta
     na comunidade agora.

3. **Filtrar por data**: descartar qualquer resultado de busca mais antigo
   que 5 dias, exceto quando ainda for claramente o assunto dominante do
   meta atual (ex.: um patch de 6 dias atrás que ainda é a versão vigente).

4. **Ler `config/channels.md`** para pegar a lista completa de canais de
   referência, por categoria.

5. **Gerar de 8 a 12 ideias de vídeo**, em português, em formato de lista
   rápida (bullet points), misturando os dois ângulos pedidos:
   - **Jogadas específicas / replays de pro** — análise de uma partida,
     jogador ou play real dos últimos dias.
   - **Conceito / mentoria** — por que uma decisão foi certa ou errada,
     explicação de meta, itemização, timing, etc.

   Quando fizer sentido, indicar o estilo de referência
   (ex.: "replay breakdown estilo DotaCinema sobre...", "vídeo educacional
   estilo Purge explicando...").

   Cada bullet deve citar o dado concreto por trás da ideia (herói, patch,
   partida/time, data aproximada) para deixar claro por que é atual.

6. **Salvar o briefing** em `briefings/AAAA-MM-DD.md` com as seções:
   - `## Contexto da semana` (patch atual + resumo curto do meta)
   - `## Ideias de vídeo` (a lista de bullets)
   - `## Fontes` (links/buscas usadas)

7. **Commitar e dar push** do arquivo no branch de trabalho do repositório.

8. **Entregar a lista de bullets diretamente na conversa com o usuário** —
   esse é o entregável principal, não só o arquivo salvo.

9. **Nunca inventar números/estatísticas**. Se uma fonte não puder ser
   confirmada, marcar como "via busca web, não confirmado" em vez de
   apresentar como fato.

## Nota técnica

Este ambiente não tem acesso de rede direto a `dotabuff.com`,
`dotaprotracker.com` ou `api.opendota.com` (bloqueado pela política de rede
do sandbox, testado em 2026-08-04). Por isso os dados são obtidos via
`WebSearch` (busca na web), não via chamada direta às APIs/sites. Se no
futuro o ambiente permitir acesso direto a essas APIs, o passo 2 pode ser
substituído por chamadas diretas para dados mais precisos.
