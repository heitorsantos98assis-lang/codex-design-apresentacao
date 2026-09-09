# Guia completo — Apresentação executiva de desempenho no Codex Design

> Não é um prompt. É um **playbook** com 1 prompt master, 5 prompts setoriais, prompts de iteração, layout slide-a-slide, anti-patterns, checklist de qualidade e estratégia de defesa de número em reunião.
>
> Lê o índice. Vai direto pra seção que faz sentido pro seu caso.

---

## Índice

1. [Antes de colar o prompt — prepare seus arquivos](#1)
2. [Variáveis a personalizar](#2)
3. [Prompt MASTER (genérico, alta densidade)](#3)
4. [5 prompts setoriais (SaaS / E-commerce / Agência / Infoproduto / Tijolo)](#4)
5. [Layout slide-a-slide — tipografia, dataviz e composição](#5)
6. [Speaker notes — 3 templates por situação](#6)
7. [Prompts de iteração (revisão, encurtar, encompridar, adaptar público)](#7)
8. [Prompts de defesa em Q&A](#8)
9. [Anti-patterns (errado × certo, com exemplo)](#9)
10. [Checklist de qualidade (15 itens — passa ou refaz)](#10)
11. [Como iterar em 3 rodadas (D-2, D-1, D-0)](#11)
12. [Exportação avançada — branding, fonte custom, watermark](#12)
13. [Variações por duração de reunião (5 / 15 / 30 / 60 min)](#13)

---

<a name="1"></a>
## 1. Antes de colar o prompt — prepare seus arquivos

Codex Design lê o que você sobe. Lixo entra, lixo sai. **15 minutos preparando os arquivos economiza 2 horas iterando o deck.**

### 1.1. Renomeie os arquivos com semântica

Errado: `Pasta1/REL_FINAL_v3 (2).xlsx`
Certo: `comercial_maio_2026.xlsx`, `meta_ads_maio_2026.csv`, `financeiro_dre_maio_2026.pdf`, `nps_pesquisa_maio_2026.csv`

O Codex usa o nome do arquivo como dica de contexto. Nome descritivo = análise mais precisa.

### 1.2. Limpe planilha antes de subir

| Mexa | Por quê |
|---|---|
| Remova abas vazias | Codex tenta analisar todas — perde tempo e contexto |
| Renomeie abas: `vendas_diarias`, `vendas_mensais`, `cohort_clientes` | Sem isso, vira "Sheet1", "Tabela_2" — você paga em precisão |
| Padronize cabeçalho na linha 1 | Sem linhas mescladas, sem títulos coloridos no meio |
| Padronize data: `2026-05-15` ISO | Brasileiro `15/05/26` é ambíguo |
| Padronize R$: número puro `12487.50` | Não `R$ 12.487,50` — Codex tem que parsear |
| Adicione coluna "fonte" se mesclou planilhas | "Origem: comercial / e-commerce / parceria" |

### 1.3. Crie um arquivo `CONTEXTO.md` (faz toda a diferença)

Esse é **o arquivo que separa amador de sênior.** Texto livre, ~1 página, contendo:

```markdown
# Contexto do período

## O que aconteceu fora da planilha
- Dia 12/05: parada do sistema das 14h-19h. Perda estimada R$ 18k em pedidos.
- Semana 20-26/05: lançamento do produto Premium. Esperávamos +25% receita, deu +9%.
- Concorrente X baixou preço em 30% no dia 8/05.

## Como o time enxerga o mês
- Comercial: "Premium não converteu como prometido pelo marketing"
- Marketing: "Comercial não estava treinado pra vender Premium"
- Sócio: "Margem caiu mas faturamento bateu meta — tô em dúvida se foi bom"

## O que vai estar na cabeça do público
- {nome 1, cargo}: vai querer saber por que CAC subiu
- {nome 2, cargo}: vai pedir comparação com Q1
- {nome 3, cargo}: já avisou que vai pedir cortar canal X
```

**Por quê:** sem isso, o Codex vê números nus. Com isso, ele entende **porquê** e o deck sai já com o discurso pronto pro Q&A.

### 1.4. Defina o conjunto mínimo

Suba **3 a 6 arquivos**, não 20. Mais que isso o Codex dilui foco. Conjunto mínimo:

- 1 financeiro (DRE ou cash flow mensal)
- 1 comercial (vendas/pipeline)
- 1 marketing (CAC/leads/canal)
- 1 de operação (pedidos/atendimentos/produção)
- `CONTEXTO.md`

---

<a name="2"></a>
## 2. Variáveis a personalizar

Preencha estas 8 variáveis no topo do prompt antes de colar:

```
EMPRESA: [nome]
SETOR: [SaaS | E-commerce | Agência/Serviço B2B | Infoproduto | Varejo/Tijolo | Outro: ___]
PERIODO: [Maio/2026 | Q1 2026 | últimos 30 dias | semana 19]
COMPARAR_COM: [Abril/2026 | Q4 2025 | mesmo período 2025 | meta orçada]
PUBLICO: [3-5 pessoas, com cargo: "2 sócios + CFO" | "conselho 5p + 2 investidores observadores"]
DURACAO: [10 | 20 | 45 minutos de apresentação + Q&A]
OBJETIVO_REUNIAO: [aprovar X | decidir entre A/B | defender contratação | reportar antes de fechar trimestre]
DECISAO_ESPECIFICA: [pedido concreto, ex: "aprovar R$ 80k extras em mídia paga para junho"]
```

Quanto mais específica a `DECISAO_ESPECIFICA`, melhor o deck. Vago = "alinhar próximos passos". Específico = "aprovar contratação de 2 SDRs no nível pleno, salário R$ 5.5k + variável, início 15/06".

---

<a name="3"></a>
## 3. Prompt MASTER (cole abaixo, alta densidade)

```
# Sua identidade

Você é um analista sênior de business operations com 12 anos de experiência em consultoria estratégica (estilo McKinsey/Bain), sentado comigo numa sala de reunião. Não é seu primeiro deck. Você já viu sócio enfurecer porque o consultor não entendeu o negócio. Você já viu conselho rejeitar deck por slide vago. Sua reputação está em jogo.

Sua missão: montar um deck executivo PRONTO pra eu abrir hoje em frente a {PUBLICO}, num laptop, sem ajuste.

# Contexto

- Empresa: {EMPRESA} ({SETOR})
- Período: {PERIODO} comparado com {COMPARAR_COM}
- Tempo de apresentação: {DURACAO}
- Objetivo da reunião: {OBJETIVO_REUNIAO}
- Decisão que preciso EU NA MÃO no fim: {DECISAO_ESPECIFICA}
- Arquivos: anexei {N} arquivos + CONTEXTO.md que explica os fatores qualitativos do período.

# Como você opera

## Princípio 1 — Conclusão primeiro (regra de Barbara Minto, "Pyramid Principle")
Cada slide tem um TÍTULO-CONCLUSÃO, não título-tópico.
- Errado: "Receita por canal"
- Certo: "Meta carregou 62% da receita — concentração de risco subiu 14pp vs Q1"

## Princípio 2 — Ranking por impacto em R$ (não por sentimento)
Toda lista é ordenada pelo R$ que mexeu. "Foi importante", "merece atenção" não são critérios.

## Princípio 3 — Densidade controlada (Edward Tufte, "Visual Display of Quantitative Information")
Cada centímetro de slide carrega informação. Espaço em branco é informação também — ele dirige o olho. Nada de decoração.

## Princípio 4 — Storytelling executivo (Nancy Duarte, "Resonate")
O deck tem curva emocional: estado atual → tensão (gap entre real e desejado) → resolução (sua recomendação). Não é dump de KPI.

## Princípio 5 — Stickiness (Heath Brothers, "Made to Stick" — SUCCESs)
Cada slide tem 1 número que gruda. Slide sem número-âncora é slide pra cortar.

# Estrutura obrigatória

## Bloco A — Abertura (3 slides, 2 minutos)
**Slide 1 — Capa**
- Título do deck (conclusão de 1 linha, não rótulo): ex. "Maio fechou +8% receita com margem -3pp — alavanca de junho é precificação Premium"
- Período + autor + data
- Logo da empresa pequeno, canto inferior

**Slide 2 — TL;DR**
- 3 takeaways, cada um com 1 número e 1 implicação
- Ex: "1. Receita R$ 1,28mi (+8% vs Abr) puxada por Meta — mas CAC subiu 22%. 2. Premium converteu 9% vs 25% projetado — problema é discurso, não preço. 3. Cash em caixa cobre 4,2 meses de OPEX — espaço pra investir, não pra cortar."
- Cada takeaway tem uma cor: 🟢 vencedor / 🟡 atenção / 🔴 alerta

**Slide 3 — Sumário da reunião** (só se DURACAO > 20min)
- "Vamos passar por X, Y, Z. Decisão no fim: {DECISAO_ESPECIFICA}"
- Mostra que você sabe pra onde está indo. Fecha contrato de atenção.

## Bloco B — Diagnóstico (3-4 slides, 6 minutos)

**Slide 4 — KPIs vs meta**
- Tabela 5-7 linhas: Métrica / Meta / Realizado / Δ Abs / Δ % / 🟢🟡🔴
- KPIs financeiros (Receita, Margem Bruta, EBITDA, Cash) + KPIs operacionais setoriais (ver Seção 4)
- Footer: "Fonte: financeiro_dre_maio_2026.pdf, linha X"

**Slide 5 — O que funcionou (top 3 por R$)**
- 3 vencedores em barra horizontal ordenada por impacto R$
- Pra cada um: o que era → o que virou → causa raiz provável
- Não termina sem responder: "isso é replicável em junho?"

**Slide 6 — O que falhou (top 3 por R$)**
- Mesma estrutura, lado oposto
- Pra cada um: cortar (parar) / corrigir (melhorar) / observar (mais 1 ciclo de dado)
- Não é punição — é decisão de alocação

**Slide 7 — Drilldown do principal driver**
- Escolha o NÚMERO ÚNICO que mais mexeu (positivo ou negativo)
- Abra em 3 níveis: O QUE mudou → POR QUE mudou → QUEM controla
- Use waterfall chart se for variação financeira (R$ início → R$ fim com cada componente)

## Bloco C — Análise temporal e comparativa (2 slides, 4 minutos)

**Slide 8 — Comparativo {PERIODO} vs {COMPARAR_COM}**
- Barras duplas lado a lado, Δ% absoluto em cima de cada par
- Selecione 4-6 dimensões: por canal, por produto, por segmento, por região (o que faz sentido pro setor)
- Anote os pares onde o gap > 10% — não deixa o público descobrir, aponte

**Slide 9 — Tendência (linha temporal)**
- Linha de 6 ou 12 meses pra mostrar trajetória
- Marque eventos: lançamento, contratação, crise, sazonalidade
- Mostra "esse mês é anomalia ou tendência?" — pergunta clássica de sócio

## Bloco D — Risco e recomendação (3 slides, 5 minutos)

**Slide 10 — Riscos identificados (matriz Prob × Impacto R$)**
- 3-5 riscos plotados em quadrante 2x2
- Cada risco: 1 linha de descrição + 1 linha de mitigação proposta + dono
- Não inclui "concorrência" genérica — inclui risco específico: "Cliente X (12% receita) com contrato vence em Set, está negociando."

**Slide 11 — Recomendações priorizadas (RICE simplificado, Intercom)**
- 3-5 ações em tabela: Ação / Impacto R$ ou % / Esforço (sprints) / Confiança (B/M/A) / RICE score
- Ordene pelo RICE
- Cada ação tem dono + prazo + métrica de sucesso ("em 60 dias, MRR de Premium passa de R$ 90k pra R$ 180k")

**Slide 12 — Pedido (THE ASK)**
- 1 frase: {DECISAO_ESPECIFICA}
- Embaixo: "Se SIM, próximos 7 dias: [3 marcos]. Se NÃO, plano B: [1 frase]"
- Slide deve caber em 5 segundos de leitura — esse é o slide que vai pra cabeça do público

## Bloco E — Apêndice (não conta tempo)

**Slide 13 — Definição de métricas**
- Glossário: "CAC = soma gasto mídia + salário time comercial / clientes novos pagantes"
- Sem isso, brigam sobre definição em vez de decidir

**Slides 14+ — Tabelas detalhadas**
- O dado granular fica aqui. Conselheiro que quer drilldown pega no apêndice durante Q&A.

# Speaker notes (obrigatório)

Para cada slide, gere notas em até 5 linhas seguindo SUCCESs:
- **Simple**: frase de 1 linha que resume o slide
- **Unexpected**: o número que vai prender atenção (geralmente um contra-intuitivo)
- **Concrete**: um exemplo específico — nome de cliente, mês, R$, %
- **Credible**: arquivo + aba/página de onde veio o dado
- **Emocional/Story**: 1 frase que conecta com o próximo slide (cliffhanger)

Inclua tempo estimado pra falar cada slide: "Slide 4 — falar em 90s. Não mais que isso."

# Defesa em Q&A (obrigatório, slide oculto no fim)

Gere um slide oculto "DEFESA_QA" com:
- 5 perguntas DIFÍCEIS que o público vai fazer (não as fáceis)
- Pra cada uma:
  - Resposta direta em 2-3 linhas
  - Dado que sustenta (qual arquivo, qual linha)
  - Se eu não tenho o dado: roteiro de "deixa eu te trazer essa resposta até [data]"
- Inclua a pior pergunta possível — a que destrói a recomendação. Tenha resposta.

# Formatação do deck

## Tipografia
- 1 família de fonte só. Inter, Roboto, ou a fonte da marca.
- Título-conclusão: 28-32pt, peso 600-700
- Corpo: 16-20pt, peso 400
- Número-âncora (o KPI gigante): 80-120pt, peso 700
- Footer/fonte do dado: 10-12pt, peso 400, cor 60% opacidade
- NUNCA fonte serifada no corpo. Sans-serif sempre.

## Cores
- Verde sucesso, vermelho falha, neutro pra resto.
- Cego pra cor: posição + ícone + cor (nunca só cor).
- Paleta: 1 cor primária + 1 secundária + 3 tons de cinza. Não mais.

## Dataviz por tipo de dado
- Comparação temporal → linha (com marcadores nos pontos-chave)
- Comparação categórica → barra horizontal ordenada (maior em cima)
- Parte/todo ≤4 → donut com label central mostrando total
- Parte/todo ≥5 → barra empilhada 100%
- Variação entre 2 momentos → waterfall (Δ por componente)
- Distribuição → histograma ou box plot (só pra audiência analítica)
- Correlação → scatter com linha de tendência
- Funil → funnel ou waterfall (NUNCA pizza, NUNCA donut)
- Cohort → heatmap mensal (linhas: mês de aquisição, colunas: mês N pós-aquisição)
- Pizza só com 2-3 fatias e MUITO contexto. Caso contrário, banir.

## Números
- R$ formatado: "R$ 1,28 mi" / "R$ 380 mil" / "R$ 4.872" — não "1280000"
- % com 1 casa decimal no máximo
- Variação sempre com sinal: "+8%" / "-3,2pp"
- pp para pontos percentuais, % para porcentagem — não confunda

# Tom de voz

- Português brasileiro, primeira pessoa do singular ("eu vou mostrar"), nunca "nós" corporativo.
- Direto. Sem hedging ("aparentemente", "podemos observar").
- Números, não adjetivos. "Caiu R$ 87 mil" > "caiu significativamente".
- Se dado falta: [DADO FALTANDO: arquivo X, aba Y, motivo Z]. Nunca invente.
- Verbo no início da frase ativa. "Cortar canal X em junho" > "Sugere-se que seja considerada a possibilidade de cortar o canal X".

# O que NUNCA fazer

- Inventar número. Falta dado → marca [FALTANDO].
- Recomendação genérica ("melhorar comunicação", "alinhar times"). Toda recomendação tem: verbo + dono + prazo + métrica.
- Slide terminando em pergunta retórica.
- Mais de 1 fonte tipográfica.
- Stock photo. Se precisa visual, é gráfico ou ícone monocromático.
- Bullet com mais de 1 linha. Se a frase passa de 1 linha, vira corpo de texto, não bullet.
- Slide com mais de 1 ideia. Duas ideias = dois slides.

# Saída esperada

Gere agora:
1. Os 12 slides do deck (Blocos A-D) com layout, conteúdo, dataviz, speaker notes.
2. Os slides 13+ de apêndice (Bloco E).
3. O slide oculto DEFESA_QA com 5 perguntas + respostas.
4. No fim, me dê 3 versões alternativas do Slide 12 (THE ASK):
   - Versão conservadora (pedido mínimo)
   - Versão alvo (o que eu quero de verdade)
   - Versão ambiciosa (se a reunião correr bem, expando pra essa)
5. Sugestão de export: PPTX se for editar mais, PDF se for travar.

# Arquivos anexados

[anexe aqui os 3-6 arquivos preparados conforme Seção 1]
```

---

<a name="4"></a>
## 4. Prompts setoriais (cole o seu setor por cima do MASTER)

Cada setor tem KPIs e narrativa próprios. Cola este bloco extra depois do MASTER, na seção "# Contexto":

### 4.1. SaaS B2B

```
# KPIs obrigatórios pro setor SaaS
- MRR (início, +new, +expansion, -contraction, -churn, fim) → waterfall obrigatório
- NRR (Net Revenue Retention) — alvo > 100% saudável, >115% excelente
- GRR (Gross Revenue Retention) — alvo > 90%
- Logo churn % mensal
- ARR projetado fim de ano (run-rate × 12)
- CAC payback em meses
- LTV/CAC (alvo > 3, excelente > 5)
- Magic Number ((New ARR Q ÷ S&M gasto Q anterior) × 4)
- Rule of 40 (Growth % + EBITDA %)
- ACV (Annual Contract Value) por segmento
- Cohort retention por mês de aquisição (heatmap)

# Narrativas tipicas pra abrir o deck
- "MRR cresceu X% mas NRR caiu Y pp — expansion morreu" (sinal de produto saturando na base)
- "Logo churn estável mas downgrade subiu — pricing pressionado" (concorrente)
- "Magic Number caiu de X pra Y — eficiência de aquisição piorando, hora de revisar canais"
```

### 4.2. E-commerce / D2C

```
# KPIs obrigatórios pro setor E-commerce
- Receita bruta, líquida, GMV
- AOV (Average Order Value)
- Taxa de conversão por canal (Meta, Google, orgânico, e-mail, direto)
- CAC por canal
- ROAS por canal (Receita atribuída ÷ gasto mídia)
- Repeat Rate (% clientes que compraram 2+ vezes)
- Taxa de devolução
- Ticket médio por categoria
- Margem de contribuição por SKU (top 10 + bottom 10)
- Estoque parado (>90 dias) em R$
- Funil: Sessões → Carrinho → Checkout → Pago (com taxa de abandono em cada etapa)

# Narrativas típicas
- "ROAS Meta caiu de 4,2 pra 2,8 — fadiga criativa ou leilão pressionando"
- "Repeat rate parou de crescer em 18% — produto não gera retorno suficiente"
- "Margem por SKU mostra que top 3 carrega 80% da margem — concentração de risco"
```

### 4.3. Agência / Serviço B2B

```
# KPIs obrigatórios pro setor Agência/Serviço
- Faturamento (recorrente vs projeto)
- Margem por cliente (receita - custo de delivery) em R$ e %
- Headcount × utilization rate (% horas faturáveis ÷ horas disponíveis)
- Revenue por funcionário
- DSO (Days Sales Outstanding — quanto leva pra receber)
- Pipeline qualificado em R$ × probabilidade
- Win rate por origem (indicação, inbound, outbound)
- Churn de cliente em #, R$ e tempo médio de retenção
- LTV de cliente (receita total ÷ # clientes encerrados)
- Inflow / outflow de clientes no período (waterfall de clientes)
- Margem por linha de serviço (consultoria, implementação, suporte)

# Narrativas típicas
- "Faturamento bateu meta mas utilization caiu de 78% pra 64% — equipe ociosa, ou cliente reduzindo escopo"
- "Win rate inbound dobrou (8% pra 16%) mas outbound caiu (12% pra 4%) — quase certeza, marketing trabalhando, comercial não"
- "Top 3 clientes = 47% da receita — bus factor 1 cliente, mexer já"
```

### 4.4. Infoproduto / Curso digital

```
# KPIs obrigatórios pro setor Infoproduto
- Faturamento de lançamento (se foi período de lançamento) vs perpetuo
- CAC por canal (Meta, Google, YouTube, afiliados, orgânico)
- Tx conversão da Landing Page / Webinar / VSL
- Tx conversão checkout (visitou checkout → comprou)
- Reembolso % (alvo < 5%, atenção > 10%)
- NPS após 30 dias da compra
- LTV (compra inicial + upsell + recompra de outros produtos)
- Receita por canal de tráfego
- Mensagens de WhatsApp por lead (carga atendimento)
- Taxa de execução do aluno (curso terminado ≥ 50%)
- Ticket médio (FE + OB + US)

# Narrativas típicas
- "Lançamento bateu meta de faturamento mas NPS pós-30d caiu de 72 pra 58 — entregou expectativa demais na copy"
- "Reembolso subiu de 6% pra 14% — investigar: copy enganosa OU produto sem entrega real OU galera errada comprando"
- "Afiliado X gerou 38% da receita do lançamento — concentração de risco"
```

### 4.5. Varejo / Tijolo / Operação física

```
# KPIs obrigatórios pro setor Tijolo
- Receita por loja (e por m²)
- Ticket médio por loja
- Conversão por loja (visitantes → compradores)
- Tráfego (visitantes/dia) — se você mede
- Estoque em R$ e em DIO (Days Inventory Outstanding)
- Mark-up médio e mark-up por categoria
- Margem por categoria
- Quebra de estoque (perda, vencimento, furto)
- Custo de mão de obra ÷ receita
- Same-store sales growth (vs mesmo mês ano anterior)
- Mix de venda (% receita por categoria)

# Narrativas típicas
- "Loja Vila Madalena com 42% da receita mas margem 4pp menor que Higienópolis — investigar mix"
- "Same-store sales -3% mas margem +1pp — vendendo menos, vendendo melhor"
- "DIO subiu de 45 pra 71 dias — capital de giro travado em mercadoria"
```

---

<a name="5"></a>
## 5. Layout slide-a-slide — tipografia e composição exatas

### 5.1. Slide 2 (TL;DR) — layout exato

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  Maio fechou +8% receita com margem -3pp.                   │  ← Título-conclusão, 32pt
│  Alavanca de junho é precificação Premium.                  │
│                                                             │
│  ────────────────                                           │
│                                                             │
│   🟢  RECEITA               R$ 1,28 mi   (+8% vs Abr)        │  ← Linha 1: KPI gigante 48pt
│       Meta carregou 62% — Google e orgânico estáveis        │  ← Sub-explicação 18pt
│                                                             │
│   🟡  MARGEM BRUTA          61% (-3pp)                       │
│       Custo Meta subiu 22% por leilão sazonal               │
│                                                             │
│   🔴  PREMIUM               9% conv (vs 25% projetado)       │
│       Comercial não treinado no discurso de valor           │
│                                                             │
│  ────────────────                                           │
│                                                             │
│  Pedido hoje: R$ 80k extras pra junho + treino comercial    │  ← Pedido em 1 linha
│                                                             │
│  Slide 2/13 · maio/2026 · HL · Fonte: 4 anexos          │  ← Footer 11pt 60% op
└─────────────────────────────────────────────────────────────┘
```

### 5.2. Slide 4 (KPIs vs Meta) — tabela exata

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  Bati 4 de 7 KPIs. Os 3 que falharam têm 1 causa comum:    │  ← Título-conclusão
│  custo de aquisição em Meta.                                │
│                                                             │
│  ┌────────────────┬──────────┬──────────┬─────┬──────┬───┐ │
│  │ KPI            │ Meta     │ Realizado│ Δ%  │ Status│   │ │
│  ├────────────────┼──────────┼──────────┼─────┼──────┼───┤ │
│  │ Receita        │ R$ 1,2mi │ R$ 1,28mi│ +7  │  🟢  │   │ │
│  │ Margem Bruta   │ 64%      │ 61%      │ -3pp│  🔴  │   │ │
│  │ EBITDA         │ R$ 280k  │ R$ 198k  │ -29 │  🔴  │   │ │
│  │ CAC            │ R$ 180   │ R$ 220   │ +22 │  🔴  │   │ │
│  │ LTV/CAC        │ 4,5x     │ 4,8x     │ +6  │  🟢  │   │ │
│  │ Pedidos        │ 4.200    │ 4.560    │ +9  │  🟢  │   │ │
│  │ Reembolso %    │ <5%      │ 3,8%     │ ok  │  🟢  │   │ │
│  └────────────────┴──────────┴──────────┴─────┴──────┴───┘ │
│                                                             │
│  Fonte: financeiro_dre_maio (l.12-18), meta_ads_maio (l.4) │
└─────────────────────────────────────────────────────────────┘
```

### 5.3. Slide 7 (Drilldown waterfall) — composição

```
┌─────────────────────────────────────────────────────────────┐
│  CAC saltou R$ 40 — leilão Meta carregou 75% do estrago.   │
│  ─────────────                                              │
│                                                             │
│  CAC Abril    +Custo Meta  +Sal SDR  -Conv site   = CAC Mai │
│   R$ 180  →    +R$ 30  →    +R$ 6  →  +R$ 4    →  R$ 220   │
│   ████          ▲             ▲         ▲          ████    │
│                75%           15%       10%                  │
│                                                             │
│  ─────────────                                              │
│  O QUE mudou: Meta CPM passou de R$ 28 pra R$ 41 (+46%)    │
│  POR QUE: leilão sazonal (dia das mães) + novo concorrente │
│  QUEM controla: Pedro (Marketing) — plano: trocar criativo │
│  + diversificar pra Google Search (POC em junho)           │
└─────────────────────────────────────────────────────────────┘
```

### 5.4. Princípios de composição (todos os slides)

| Regra | Por quê | Exemplo violação |
|---|---|---|
| **Margem 60-80px** | Slide com texto colado na borda parece amador | Tabela tocando a borda esquerda |
| **Grid de 8 ou 12 colunas** | Alinhamento implícito = sensação de ordem | KPIs em posição random |
| **1 ponto de foco por slide** | Olho não sabe pra onde ir = perde 5s | 3 gráficos do mesmo tamanho |
| **Hierarquia tipográfica 4 níveis máx** | Título, subtítulo, corpo, footer | 8 tamanhos de fonte diferentes |
| **Branco respira** | Espaço vazio = "tô confiante no que tô mostrando" | Slide 100% preenchido |
| **Footer com fonte do dado** | Auditabilidade = credibilidade | Slide sem footer |

---

<a name="6"></a>
## 6. Speaker notes — 3 templates por situação

### 6.1. Template "Resultado positivo" (slide de vencedor)

```
[Slide N — Premium converteu acima da meta no segmento Enterprise]

ABERTURA (5s, calmo):
"Antes de entrar no que falhou, quero abrir com o que ganhou."

NÚMERO-ÂNCORA (5s, pausa):
"Premium Enterprise: 23% de conversão. A projeção era 15%."

PORQUÊ (15s, didático):
"Funcionou porque o discurso de quem sabia vender Premium era o do João. Ele vendia em 2 reuniões, sem proposta escrita. Os outros estavam mandando proposta antes do segundo call — ali o cliente esfriava."

GANCHO PRO PRÓXIMO SLIDE (5s):
"Vou mostrar agora o lado oposto — Premium SMB caiu. Mesmo time, mesmo discurso, contexto diferente."

TEMPO TOTAL: 30s
```

### 6.2. Template "Resultado negativo" (slide de perdedor)

```
[Slide N — CAC subiu 22%, Meta carregou 75% do estrago]

ENQUADRAMENTO (10s, neutro — NÃO defensivo):
"CAC subiu de R$ 180 pra R$ 220. Não foi 1 fator — foram 3, mas 1 carregou 75%."

NÚMERO + CAUSA (15s, factual):
"Meta CPM passou de R$ 28 pra R$ 41 — +46%. Leilão de dia das mães + entrada de concorrente novo que não estava no nosso mapa de Q1."

O QUE EU JÁ FIZ (15s, mostra ownership):
"Quarta passada o Pedro trocou os 3 criativos topo de funil. CPM já caiu pra R$ 36. Não chegou no R$ 28, mas tá descendo."

PROPOSTA (10s, específica):
"Proposta: diversificar pra Google Search em junho. POC R$ 20k. Se ROAS ≥ 3 em 30 dias, escala. Se < 3, mata."

ANTECIPA OBJEÇÃO (10s):
"Sei que vão perguntar 'por que não TikTok'. Resposta: ticket médio nosso é R$ 380, público TikTok converte abaixo disso na média da categoria — não compensa o custo de aprender o canal agora."

TEMPO TOTAL: 60s
```

### 6.3. Template "Pedido / Slide 12 (THE ASK)"

```
[Slide 12 — Pedido: R$ 80k extras em junho + 2 SDRs]

TRANSIÇÃO (5s):
"Vou fechar com o pedido."

PEDIDO EM 1 FRASE (10s, devagar, olho no decisor):
"R$ 80k extras em mídia paga em junho, 60% pra Google Search 40% pra reforço Meta, mais aprovação pra contratar 2 SDRs pleno entrando 15/06."

JUSTIFICATIVA (15s):
"Justificativa: cada SDR amortiza em 4 meses no nosso CAC payback atual. Junho é a janela porque julho entra férias e o ciclo de venda é 3-4 semanas."

SE SIM (15s, prepara o que acontece):
"Se aprovado, próximos 7 dias: abro 2 vagas, brief dos criativos pra Google até sexta, primeiro relatório de ROAS Google dia 18/06."

SE NÃO (15s, plano B real):
"Se reprovado, plano B: mantemos só Meta com mesmo orçamento. Risco: receita junho fica flat ou cai 5%, porque CAC continua pressionado."

SILÊNCIO (3-5s):
"Posso seguir com o sim?"
[Não preenche silêncio. Deixa ele decidir.]

TEMPO TOTAL: 75s
```

---

<a name="7"></a>
## 7. Prompts de iteração (depois do MASTER gerar o deck)

### 7.1. Rodada 1 — "Está raso, aprofunda"

```
Revisa o deck que você gerou. Pra cada slide:
1. Pergunta "esse título é conclusão ou tópico?" Se for tópico, reescreve como conclusão.
2. Pergunta "qual o número-âncora?" Se não tem, ou está pequeno demais, refaz.
3. Pergunta "uma pessoa olhando 5s, o que ela leva?" Se for "vários gráficos", refaz.
4. Pergunta "essa recomendação tem dono + prazo + métrica?" Se não, refaz.

Me devolve a lista de slides que você refez e por quê, antes de me mandar o deck novo.
```

### 7.2. Rodada 2 — "Encurta pra 8 slides"

```
Reduz o deck pra 8 slides mantendo o pedido intacto. Critérios de corte:

1. Slide com info que já está em outro = mergeia ou corta
2. Slide explicando KPI = corta (vai pra apêndice)
3. Drilldown que não muda decisão = corta
4. Gráfico de evolução temporal redundante com o comparativo = corta o menos relevante
5. Slide de "agenda da reunião" = corta se duração < 30min

NÃO corte: TL;DR, Vencedores, Perdedores, Pedido, Defesa Q&A oculta.

Me explica o que cortou e por quê em 5 linhas antes do deck novo.
```

### 7.3. Rodada 3 — "Adapta pra outro público"

```
Adapta o deck pra apresentar pra {NOVO_PUBLICO}. Mudanças:

1. Linguagem: mais técnica se for time, mais executiva se for board, mais comercial se for cliente
2. Profundidade: simplifica métricas que esse público não usa (ex: tira "Magic Number" se for sócio operacional)
3. THE ASK: o pedido muda — pra time é "comprometimento", pra board é "aprovação de capital", pra cliente é "renovação"
4. Defesa Q&A: as 5 perguntas difíceis mudam — antecipa o que ESSE público vai perguntar

Não regenera deck inteiro. Me lista as 5-7 mudanças e me deixa aprovar antes de mexer.
```

### 7.4. Iteração de slide individual

```
Refaz o Slide N. Quero:
- Título-conclusão diferente — não falando do problema, falando do CAMINHO.
- Dataviz diferente — em vez de barra, quero waterfall mostrando o gap.
- Número-âncora mais agressivo: o número que VAI MEXER a sala.
- Speaker notes em 4 linhas. Frase 1 é o gancho.

Não mexe nos outros slides. Só esse.
```

---

<a name="8"></a>
## 8. Prompts de defesa em Q&A

Antes da reunião, rode esse prompt:

```
Olha o deck que você gerou. Esquece sua versão e entra no papel do PIOR CRÍTICO POSSÍVEL — um conselheiro cético com 30 anos de mercado que já viu de tudo. Ele NÃO acredita no que tô mostrando.

Lista as 10 perguntas que ele vai me fazer, ordenadas pela mais perigosa primeiro. Pra cada uma:

1. A pergunta exata (com o tom certo — cético, não educado)
2. Por que ela é perigosa (qual hipótese da minha recomendação ela ataca)
3. Resposta que eu vou dar:
   - Em 1 frase (resposta-elevador)
   - Em 3 frases (resposta com dado)
   - Se eu não tenho o dado: o que eu falo pra não perder a credibilidade
4. Se ele insistir, próxima resposta — uma "segunda camada"
5. Se mesmo assim ele não comprar: a saída elegante ("posso te trazer essa resposta detalhada até [data]")

A pior pergunta — a que destrói a recomendação — coloca em primeiro.
```

Exemplo de output esperado:

```
PERGUNTA 1 (mais perigosa):
"Você tá pedindo R$ 80k pra Meta numa hora que CAC tá subindo 22% — isso não é jogar dinheiro fora?"

POR QUE É PERIGOSA: ataca diretamente o pedido. Confunde "alocar mais no que tá subindo de custo" com "ineficiência".

RESPOSTA 1 FRASE:
"60% do pedido NÃO é Meta — é Google Search, justamente pra diversificar."

RESPOSTA 3 FRASES:
"Só R$ 32k vai pra Meta, manutenção. O grosso (R$ 48k) é POC Google Search por 30 dias. Se ROAS Google ≥ 3, escala — se < 3, mato e devolvo o saldo. Critério de mata/escala já definido."

SE INSISTIR:
"Outra opção: aprova só os R$ 48k de Google. Mantenho Meta no orçamento atual. Aceita?"

SAÍDA ELEGANTE:
"Posso te mandar a projeção de cenários (POC sucesso, POC fracasso, status quo) hoje à noite. Decisão fica pra sexta."
```

---

<a name="9"></a>
## 9. Anti-patterns (errado × certo com exemplo)

### 9.1. Título-tópico × título-conclusão

| Errado | Certo |
|---|---|
| "Análise de receita por canal" | "Meta carregou 62% da receita — concentração subiu 14pp vs Q1" |
| "KPIs de marketing" | "Bati 4 de 7 KPIs. Os 3 que falharam têm uma causa comum: Meta" |
| "Próximos passos" | "Pedido: R$ 80k pra junho + 2 SDRs. Decisão hoje" |

### 9.2. Recomendação genérica × recomendação acionável

| Errado | Certo |
|---|---|
| "Melhorar o discurso comercial" | "Pedro (Comercial) refaz pitch Premium até 04/06, valida com Mariana (CS), aplica nos próximos 10 calls — meta: conversão de 9% pra 18%" |
| "Otimizar mídia paga" | "Diversificar 25% do budget Meta pra Google Search — POC R$ 20k em junho, critério mata/escala: ROAS ≥ 3 em 30 dias" |
| "Reduzir CAC" | "Reduzir CAC de R$ 220 pra R$ 190 até fim de junho via troca de criativo (Pedro, até 04/06) + Google POC (André, até 10/06)" |

### 9.3. Dataviz errada × certa

| Caso | Errado | Certo |
|---|---|---|
| Receita por 5 canais | Pizza 5 fatias | Barra horizontal ordenada |
| MRR evolução 12 meses | Tabela com 12 colunas | Linha com marcadores |
| CAC: o que mudou | Texto narrativo | Waterfall mostrando cada Δ |
| Cohort retention 6 meses | Tabela enorme | Heatmap mensal |
| Funil de venda 5 etapas | 5 barras separadas | Funnel chart com taxa entre etapas |

### 9.4. Bullet × frase

| Errado (bullet 3 linhas) | Certo (1 linha + corpo embaixo) |
|---|---|
| • CAC subiu de R$ 180 para R$ 220 devido a um aumento de 22% no custo de mídia do Meta combinado com um aumento na folha dos SDRs | **CAC: +R$ 40** (75% Meta CPM, 15% folha SDR, 10% queda de conv) |

### 9.5. Slide-resumo no fim × pedido

| Errado | Certo |
|---|---|
| "Conclusões: 1) Mês foi bom; 2) Margem caiu; 3) Vamos seguir monitorando" | "Pedido: aprovar R$ 80k em junho. Se SIM: 7 dias [marcos]. Se NÃO: plano B [...]" |

---

<a name="10"></a>
## 10. Checklist de qualidade (15 itens — passa ou refaz)

Antes de fechar o deck, passe esse checklist. Se 1 item falhar, refaz o slide.

```
DECK:
[ ] 1. Slide 1 (Capa) tem título-conclusão, não rótulo
[ ] 2. Slide 2 (TL;DR) cabe em 5s de leitura
[ ] 3. Existe 1 slide com o número-âncora maior do mês (80pt+)
[ ] 4. Slide 12 (THE ASK) tem pedido específico — verbo + valor + prazo + métrica
[ ] 5. Slide oculto DEFESA_QA tem 5 perguntas, a pior em primeiro
[ ] 6. Apêndice tem definição de cada KPI principal

CADA SLIDE:
[ ] 7. Título é conclusão, não tópico (passe os 12 títulos pelo teste)
[ ] 8. 1 ponto de foco visual — não 3 gráficos do mesmo tamanho
[ ] 9. Footer com fonte do dado (arquivo + linha/aba)
[ ] 10. Speaker notes em até 5 linhas seguindo SUCCESs
[ ] 11. Nenhum bullet com mais de 1 linha

DATAVIZ:
[ ] 12. Nenhuma pizza com 4+ fatias
[ ] 13. Toda barra horizontal está ORDENADA
[ ] 14. Toda variação tem sinal (+ ou −) e está em pp ou %

CONTEÚDO:
[ ] 15. Recomendações têm dono + prazo + métrica (não apenas verbo)
```

Se passar nos 15 → manda. Se falhar 1 → refaz o slide específico com o prompt 7.4.

---

<a name="11"></a>
## 11. Como iterar em 3 rodadas (D-2, D-1, D-0)

### D-2 (2 dias antes) — Rodada 1: gerar o esqueleto

- Cole o MASTER + setorial.
- Sobe 3-4 arquivos + `CONTEXTO.md`.
- Roda.
- Lê só os títulos dos 12 slides. Os títulos contam a história sozinhos? Se não, refaz com prompt 7.1.

### D-1 (1 dia antes) — Rodada 2: aprofundar e defender

- Aplica checklist (Seção 10) — refaz os slides que falharam.
- Roda prompt de defesa Q&A (Seção 8).
- Lê as 5 perguntas perigosas. Você tem resposta? Se sim, ensaia. Se não, busca o dado HOJE.
- Encurta pra duração real da reunião (prompt 7.2).

### D-0 (dia da reunião) — Rodada 3: tunagem final

- Lê speaker notes em voz alta cronometrando. Slide 4 não pode demorar 4min — tem que ser 90s.
- Se algum slide está demorando demais, é porque você não confia nele. Refaz ou corta.
- Imprime versão papel pra você ter como backup (Wi-Fi falha).
- Salva 2 versões: PPTX editável + PDF travado.

---

<a name="12"></a>
## 12. Exportação avançada — branding, fonte custom, watermark

### 12.1. Aplicar identidade da empresa

Depois de gerar o deck, rode:

```
Aplica a identidade visual da {EMPRESA}:
- Paleta primária: {hex_primaria}
- Paleta secundária: {hex_secundaria}
- Fonte: {nome_da_fonte} (ou fallback: Inter)
- Logo na capa (canto inferior esquerdo) e no rodapé dos outros slides (canto inferior direito, 60% opacidade)
- Watermark se for confidencial: "CONFIDENCIAL — {nome}" diagonal 15% opacidade

Cor pra status:
- Verde sucesso: {hex} ou default #16A34A
- Vermelho falha: {hex} ou default #DC2626
- Amarelo atenção: {hex} ou default #EAB308

NÃO toque na estrutura nem nos números — só visual.
```

### 12.2. Exportar

| Caso | Formato | Por quê |
|---|---|---|
| Reunião interna onde vou ajustar | PPTX | Edita slide |
| Apresentação travada (sócio, board) | PDF | Não dá pra cliente editar acidentalmente |
| Envio prévio pra leitura | PDF + 1-pager resumo | PDF do deck + 1 página com TL;DR + ASK |
| Apresentação remota | Compartilha tela com PPT/PDF aberto | Não compartilhe Codex Design ao vivo — risco de regenerar |

### 12.3. Versionar

Salva como `{empresa}_{periodo}_{publico}_v{N}.pptx`:

- `HL_maio2026_socios_v1.pptx` ← rodada 1
- `HL_maio2026_socios_v2.pptx` ← depois de checklist
- `HL_maio2026_socios_FINAL.pptx` ← versão que apresentou
- `HL_maio2026_socios_POS-REUNIAO.pptx` ← com anotações do Q&A pra próximo mês

---

<a name="13"></a>
## 13. Variações por duração de reunião

| Duração | # Slides apresentados | Apêndice | Notas |
|---|---|---|---|
| **5 min flash** | 4 | sem | Capa, TL;DR, Pedido, Plano B. Slides 1-2-11-12. |
| **15 min** | 7-8 | curto (3-4 slides) | Tira drilldown profundo. Mantém vencedores/perdedores + ASK |
| **30 min** | 10-12 (versão MASTER) | sim | Versão padrão |
| **45-60 min** | 12 + drilldowns + apêndice | extenso | Adiciona drilldown por canal, cohort, segment analysis |

Pra encurtar, use o prompt 7.2. Pra encompridar, rode:

```
O deck está com 12 slides. Reunião agora é de 60 minutos. Adiciona:

1. Drilldown por canal (1 slide por canal principal — Meta, Google, Orgânico, E-mail)
2. Cohort de clientes adquiridos nos últimos 6 meses (heatmap)
3. Análise por segmento (SMB vs Enterprise vs Self-serve)
4. Comparativo Q1 vs Q2 (não só mês a mês)
5. Slide de cenários pra junho (conservador / alvo / ambicioso) — só pré-mostrar pra ancorar o Pedido

Não inflar — cada slide adicional precisa de número-âncora claro.
```

---

## Próximo passo

1. Abre `Codex.ai/design`.
2. Escolhe "Apresentação de slides".
3. Cola o **Prompt MASTER (Seção 3)** + setorial (Seção 4) com as variáveis preenchidas.
4. Anexa os 3-6 arquivos preparados (Seção 1) + `CONTEXTO.md`.
5. Roda. Espera ~5min.
6. Aplica o checklist (Seção 10).
7. Itera (Seção 7).
8. Roda defesa Q&A (Seção 8) na véspera.
9. Apresenta.
10. Salva versão pós-reunião com anotações pro próximo ciclo.

---

*Material criado pela HL.*
