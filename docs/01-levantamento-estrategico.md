# Weesu — Levantamento para o Plano de Ação Estratégico Comercial

> Fase 1 de 2: levantamento (método, insumos, referências da literatura, métricas e esqueleto do plano).
> Fase 2: documento/app de acompanhamento de metas, fechamentos e conversões.

Contexto: SaaS B2B com duas linhas — **WMS** (gestão de armazém: venda mais consultiva, ticket maior, implantação) e **Hub de Integração** (ERP ↔ marketplaces/e-commerce/transportadoras: venda mais rápida, ticket menor, alto potencial de volume). Partimos de uma base de leads já planejada.

---

## 1. Como montar o plano (sequência de construção)

| # | Etapa | Pergunta que responde | Saída |
|---|-------|-----------------------|-------|
| 1 | Diagnóstico (baseline) | Onde estamos hoje? | MRR/ARR atual, nº clientes, conversões históricas, ciclo, ticket por produto |
| 2 | Metas da companhia → metas comerciais | Aonde precisamos chegar e quando? | Novo MRR/mês, nº de fechamentos por produto, por mês, para 1/3/6/12 meses |
| 3 | ICP e segmentação da base | Para quem vendemos primeiro? | ICP por produto, tiers A/B/C da base de leads, contas-alvo (ABM) |
| 4 | Funil reverso (*sales math*) | Quanto de topo de funil é necessário? | Leads → contatos → reuniões → oportunidades → propostas → fechamentos por mês |
| 5 | Capacidade (*capacity planning*) | Quantas pessoas e quando contratar? | Headcount por função, com rampa (*ramp-up*) de produtividade |
| 6 | Investimento | Quanto custa e quando retorna? | Orçamento mensal (pessoas + ferramentas + marketing + parcerias), CAC, payback |
| 7 | Plano de ação por horizonte | O que fazemos em 30/90/180/365 dias? | Iniciativas, responsáveis, prazos e indicadores de cada fase |
| 8 | Ritual de gestão | Como acompanhamos e corrigimos? | Dashboard, cadência semanal/mensal/trimestral, forecast, PDCA |

Princípio: o plano é **top-down** (meta da empresa) cruzado com **bottom-up** (capacidade real do funil e do time). Onde os dois não fecham, aparece o *gap* — e o investimento é justamente o que fecha esse gap.

### Exemplo ilustrativo de funil reverso (números hipotéticos — serão trocados pelos seus)

| Item | Valor |
|------|-------|
| Meta de novo MRR/mês | R$ 40.000 |
| Ticket médio MRR (mix WMS + Hub) | R$ 2.000 |
| Fechamentos necessários/mês | 20 |
| Win rate (oportunidade → ganho) | 20% → **100 oportunidades** |
| Reunião realizada → oportunidade | 50% → **200 reuniões** |
| Contato efetivo → reunião | 20% → **1.000 contatos efetivos** |
| Lead trabalhado → contato efetivo | 25% → **4.000 leads trabalhados/mês** |
| Capacidade de 1 AE (ramped) | ~6–8 fechamentos/mês → **3 AEs** |
| Capacidade de 1 SDR | ~40–60 reuniões/mês → **4 SDRs** |

Com isso, a pergunta "quanto vou investir?" vira uma conta: headcount × custo + ferramentas + mídia, comparado ao MRR gerado (CAC e payback).

---

## 2. O que preciso de você (insumos)

### 2.1 Metas e finanças
- Metas da companhia para 12 meses (ARR/MRR, nº de clientes, receita de setup/implantação), idealmente quebradas por trimestre.
- MRR/ARR atual e nº de clientes por produto (WMS, Hub, ambos).
- Tabela de preços: mensalidade, setup/implantação, faixas/planos de cada produto.
- Churn mensal, NRR (expansão), margem bruta (se houver).
- Orçamento comercial disponível ou teto de CAC / payback aceitável pela diretoria.

### 2.2 Funil e histórico (do banco de dados comercial)
- Exportação do CRM/banco (CSV/Excel) com: lead, origem, segmento, porte, etapa, datas de entrada/mudança de etapa, valor, produto, motivo de perda, responsável.
- Definição das etapas do funil hoje usadas (e critérios de passagem).
- Ciclo médio de venda por produto e win rate histórico.
- Observação: não tenho acesso ao outro projeto do Claude. Você precisa **exportar o banco** (ou colar as tabelas) aqui neste repositório/conversa.

### 2.3 Base de leads planejada
- Volume total, segmentação (setor: e-commerce, indústria, distribuidor, 3PL, varejo), porte (faturamento, nº SKUs, nº pedidos/dia), região, ERP/marketplaces usados.
- Qualidade dos dados (telefone, e-mail, decisor, LinkedIn) e origem (comprada, inbound, eventos, parceiros).

### 2.4 Time e operação
- Time atual (funções, salários/OTE, comissões, tempo de casa) e quem você pretende contratar.
- Ferramentas atuais (CRM, discador, automação de e-mail, enriquecimento de dados, LinkedIn Sales Navigator).
- Parceiros existentes ou desejados (ERPs, marketplaces, transportadoras, consultorias logísticas, integradores).
- Principais concorrentes e diferenciais percebidos; principais motivos de perda.

### 2.5 Decisões de formato
- Público da apresentação (CEO, sócios, conselho, investidores) e periodicidade de reporte.
- Onde o acompanhamento deve viver: app web (dashboard), planilha (Google Sheets/Excel) ou documento + dashboard.

---

## 3. Estratégias e frameworks da literatura

### 3.1 Estrutura da máquina de vendas
- **Receita Previsível (Predictable Revenue)** — Aaron Ross & Marylou Tyler. Especialização de funções (SDR prospecta, Closer/AE fecha, CS retém/expande), *Cold Calling 2.0*, separação de seeds/nets/spears (indicação, marketing, outbound). Base do modelo de vendas SaaS no Brasil.
- **The Sales Acceleration Formula** — Mark Roberge (HubSpot). Vendas como processo científico: contratação por perfil, treinamento padronizado, coaching por métricas e geração de demanda previsível.
- **Blueprints for a SaaS Sales Organization / Bowtie Model** — Jacco van der Kooij (Winning by Design). Funil em "gravata-borboleta": aquisição + retenção/expansão; receita recorrente vem majoritariamente pós-venda.
- **Capacity planning e ramp-up**: cada novo vendedor leva ~3–6 meses para produtividade plena; contratar *antes* da necessidade.

### 3.2 Métricas e economia SaaS
- **SaaS Metrics 2.0** — David Skok (For Entrepreneurs): LTV:CAC ≥ 3, payback de CAC ≤ 12 meses, churn, NRR.
- **Pipeline velocity** = (nº oportunidades × win rate × ticket médio) ÷ ciclo de venda. Mostra as 4 alavancas que o plano pode mexer.
- **Cobertura de pipeline**: 3–4× a meta do período em pipeline qualificado.

### 3.3 Qualificação e metodologia de venda
- **BANT / GPCTBA-C&I** (HubSpot): qualificação para o Hub (venda transacional).
- **MEDDIC / MEDDPICC**: qualificação para WMS (venda complexa, múltiplos decisores: operações, TI, financeiro).
- **SPIN Selling** — Neil Rackham: perguntas de Situação, Problema, Implicação e Necessidade — ideal para quantificar dor logística (erros de separação, ruptura, retrabalho).
- **The Challenger Sale** — Dixon & Adamson: ensinar, adaptar e assumir o controle; trazer insight sobre a operação do cliente.
- **Solution / Value Selling**: business case de ROI (redução de erros de expedição, ganho de produtividade, prazo de entrega).

### 3.4 Estratégia de mercado
- **Crossing the Chasm** — Geoffrey Moore: escolher um nicho-cabeça-de-praia (ex.: e-commerce multicanal de médio porte) e dominá-lo antes de expandir.
- **Matriz de Ansoff**: penetração (base atual), desenvolvimento de produto (Hub + WMS), desenvolvimento de mercado (novos segmentos/regiões).
- **Land and Expand**: entrar com o Hub (ticket menor, ciclo curto) e expandir para WMS (cross-sell) — encaixa perfeitamente no portfólio Weesu.
- **Account-Based Marketing (ABM)**: contas tier A da base com abordagem personalizada multi-contato.
- **Canais e ecossistema (Partner/Channel Sales)**: parcerias com ERPs, marketplaces, transportadoras e consultorias logísticas como fonte de leads qualificados e menor CAC.
- **Forças de Porter / Proposta de Valor (Osterwalder)**: posicionamento frente a concorrentes.

### 3.5 Gestão e execução
- **OKRs** — John Doerr (*Measure What Matters*): objetivos trimestrais com resultados-chave mensuráveis.
- **4 Disciplinas da Execução (4DX)** — McChesney, Covey & Huling: foco em poucas metas crucialmente importantes, **medidas de direção (lead: atividades, reuniões)** × **medidas históricas (lag: fechamentos, MRR)**, placar visível e cadência de responsabilização.
- **Balanced Scorecard** — Kaplan & Norton: ligar metas comerciais a financeiro, cliente, processos e aprendizado.
- **PDCA**: ciclo mensal de revisão do plano.
- **Forecast ponderado por etapa** e acurácia de forecast como métrica de maturidade.

---

## 4. Indicadores que o app vai acompanhar

**Lag (resultado)**: novo MRR, nº fechamentos por produto, receita de setup, ticket médio, churn, NRR, CAC, payback, LTV:CAC.

**Lead (direção)**: leads trabalhados, tentativas de contato, contatos efetivos, reuniões agendadas/realizadas, oportunidades criadas, propostas enviadas, valor de pipeline, cobertura de pipeline.

**Conversão (ao longo do tempo, por coorte mensal)**: lead→contato, contato→reunião, reunião→oportunidade, oportunidade→proposta, proposta→ganho; ciclo médio; motivos de perda; tudo segmentado por produto, origem, segmento e vendedor.

**Visão Planejado × Realizado** por mês, com desvio (%) e ação corretiva.

---

## 5. Esqueleto do plano por horizonte

### Próximo mês (30 dias) — Fundação
- Baseline: importar e limpar a base, calcular conversões históricas reais.
- Definir ICP por produto e segmentar a base em tiers A/B/C.
- Padronizar etapas do funil e critérios de passagem no CRM.
- Playbook v1: pitch por produto, cadências (telefone + e-mail + LinkedIn + WhatsApp), roteiros SPIN, objeções.
- Lançar a primeira cadência sobre tier A; ligar o dashboard de acompanhamento.
- Abrir processo de contratação (se o funil reverso indicar gap).

### Próximos 3 meses — Tração
- Cadências rodando em toda a base; teste A/B de mensagens e canais.
- Contratações e onboarding (SDR/AE/pré-venda técnica para WMS).
- Oferta *land*: Hub como porta de entrada; piloto de cross-sell para WMS.
- 2–3 parcerias piloto (ERP/marketplace/consultoria).
- Revisão mensal (PDCA) de conversões e ajuste do funil reverso.

### Próximos 6 meses — Escala
- Time em produtividade plena; metas individuais e comissionamento ajustados.
- ABM nas contas tier A; cases de sucesso e conteúdo de prova (ROI).
- Canal de parceiros com comissionamento estruturado.
- CS/onboarding estruturado para reduzir churn e gerar expansão.
- Forecast ponderado com acurácia medida.

### Próximo ano (12 meses) — Máquina previsível
- Receita previsível: cobertura de pipeline 3–4×, LTV:CAC ≥ 3, payback ≤ 12 meses.
- NRR > 100% via expansão (Hub → WMS, novos módulos/integrações).
- Novos segmentos/regiões (Ansoff) e revisão de pricing.
- Planejamento do ano seguinte com base nos dados reais de conversão.

---

## 6. Estrutura do investimento (a ser preenchida)

| Categoria | Itens | Observação |
|-----------|-------|------------|
| Pessoas | SDR, AE/Closer, Pré-vendas/Engenheiro de soluções (WMS), CS/Onboarding, RevOps/analista | Salário + encargos + variável (OTE); considerar rampa |
| Ferramentas | CRM, sales engagement/discador, enriquecimento de dados, LinkedIn Sales Navigator | Custo por usuário/mês |
| Marketing/demanda | Conteúdo, mídia paga, eventos do setor (logística/e-commerce), materiais de ROI | Apoio ao outbound e ABM |
| Parcerias | Comissão de indicação/revenda, co-marketing | Variável sobre receita |
| Capacitação | Treinamento de metodologia, certificações | Pontual |

Saídas: investimento mensal e acumulado × novo MRR gerado, CAC por canal, payback e ponto de equilíbrio do investimento.
