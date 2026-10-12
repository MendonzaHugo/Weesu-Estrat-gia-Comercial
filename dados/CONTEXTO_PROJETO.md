# Contexto do projeto: Prospecção WMS e Hub de Marketplaces

Exportado do projeto "Análise de Banco de Dados" em 12/10/2026. Este documento descreve tudo o que foi feito, com as regras, os números e as decisões em aberto, para que outro projeto continue o trabalho sem precisar das planilhas originais.

Arquivos que acompanham este documento:

| Arquivo | Conteúdo |
|---|---|
| `CONTEXTO_PROJETO.md` | Este documento: objetivo, metodologia, critérios, resultados e pendências |
| `base_consolidada_leads.csv` | Uma linha por empresa (2.032 linhas), com classificação, score, prioridade e contato |
| `resumo_indicadores.json` | Os números do funil e das quebras, em formato estruturado |

## 1. Objetivo

Empresa de SaaS que vende **WMS (gestão de estoque e armazém)** e **Hub de Integração com Marketplaces**. O trabalho foi analisar bases de clientes de ERPs, filtrar quem tem aderência aos produtos e priorizar leads para os SDRs/BDRs.

Regras de negócio definidas pelo usuário:

- **Foco em Comércio (atacado, varejo, e-commerce, distribuidoras) e Indústria.** Empresas de serviços são descartadas.
- **ERP de entrada (Omie, Bling, Tiny):** fit forte para Hub de Marketplaces e WMS leve a médio.
- **ERP corporativo (TOTVS, Senior, SAP, Linx):** fit forte para WMS avançado e integrações de alto volume.
- **Considerar apenas registros com status ativo** em todas as bases (instrução explícita do usuário).
- **Restrição de produto (informada pelo usuário):** o WMS hoje atende bem varejo e e-commerce; para indústria e atacado/distribuição ainda há funcionalidades a incrementar. Por isso o SAM foi dividido em duas frentes (seção 6).

## 2. Bases de origem

| Base | Linhas | Cada linha é | Filtro de ativo | Registros ativos | Ramo | Porte |
|---|---|---|---|---|---|---|
| Omie – Ribeirão Preto Centro | 1.176 | um aplicativo Omie contratado | Situação = ACTIVE | 618 | não traz; classificado pelo nome | mensalidade Omie e regime tributário |
| Omie – MG | 2.125 | um aplicativo Omie contratado | Situação = ACTIVE | 840 | não traz; classificado pelo nome | mensalidade Omie e regime tributário |
| Senior – Noroeste Paulista (CRM Senior) | 871 | uma conta do CRM | Status = Ativo | 817 | campo "Ramo de Atividade" do CRM | porte, funcionários e rating do CRM |
| TOTVS ("Lista Geralzão") | 225 | um parceiro cadastrado | Ativo = Sim | 225 | campo "Perfil" em 76 cadastros; o resto pelo nome | não traz |

As planilhas Omie foram emitidas em 02/07/2026. **Nenhuma base traz CNAE, faturamento, volume de pedidos ou canais de venda.**

Premissas sobre o ERP atual:

- **Omie:** todo registro ativo é cliente Omie. O plano (Omie completo, Start, Fit, BPO) fica em `erp_detalhe`.
- **Senior:** contas do tipo "Cliente" são usuárias do Senior. Contas "Prospect" e "Lead" não informam o ERP em uso e ficam como **"A confirmar"**.
- **TOTVS:** cliente ativo da lista é considerado usuário TOTVS. Cadastros com perfil "Fornecedor/Colaborador" ou "Prospect" ficam como **"A confirmar"**. Essa premissa ainda precisa ser confirmada pelo usuário.

## 3. Funil e definição de TAM, SAM e SOM

As bases não trazem faturamento nem ticket, então o mercado é medido em **número de empresas**, não em reais.

| Etapa | Empresas | Critério |
|---|---|---|
| Linhas nas planilhas | 4.397 | soma das quatro bases |
| Registros ativos | 2.500 | só status ativo |
| **TAM** | **2.032** | empresas únicas (CNPJ) com registro ativo nas quatro bases |
| **SAM** | **949** | TAM filtrado para comércio ou indústria |
| SAM com ERP conhecido | 614 | ERP = Omie, Senior ou TOTVS |
| **SOM** | **157** | ERP conhecido e score a partir de 85 (prioridade Hot) |

Na Omie, o CNPJ se repete a cada aplicativo: 1.458 linhas ativas viram 1.026 CNPJs. Depois, 36 CNPJs aparecem em mais de uma base e foram contados uma vez. Em 9 deles as bases apontam ERPs diferentes (marcados na coluna `observacao` como "ERP a confirmar").

Ordem de preferência ao remover repetidos: Omie Ribeirão Preto > Omie MG > TOTVS > Senior, e registro com ERP conhecido antes de registro "A confirmar".

**Decisão em aberto:** o SOM foi definido como os 157 Hot. A alternativa é SOM = 614 (todo o SAM com ERP conhecido), com os 157 como primeira onda dentro dele.

### Funil por base

| Base | Linhas | Ativos | TAM | SAM | SAM com ERP conhecido | SOM |
|---|---|---|---|---|---|---|
| Omie – Ribeirão Preto Centro | 1.176 | 618 | 499 | 218 | 218 | 74 |
| Omie – MG | 2.125 | 840 | 518 | 186 | 186 | 49 |
| Senior – Noroeste Paulista | 871 | 817 | 795 | 448 | 119 | 27 |
| TOTVS | 225 | 225 | 220 | 97 | 91 | 7 |
| **Total** | **4.397** | **2.500** | **2.032** | **949** | **614** | **157** |

O TAM de Omie MG é 518, e não 527, porque 9 CNPJs já estavam na base de Ribeirão Preto.

## 4. Classificação de ramo (do TAM ao SAM)

Ramos que entram no SAM: **Indústria, Atacado/Distribuição, Varejo, E-commerce**.

Ramos descartados (1.083 empresas):

| Motivo | Empresas |
|---|---|
| Serviços | 807 |
| Atividade não identificável pelo nome | 86 |
| Construção / Incorporação | 59 |
| Food service (restaurante, café, bar) | 50 |
| Agropecuária (produção rural) | 35 |
| Serviços – logística e transporte | 34 |
| Mineração / Combustíveis | 12 |

Como cada base foi classificada:

- **Omie (RP e MG):** leitura manual da razão social e do nome do aplicativo. Escritórios de BPO e contabilidade com vários aplicativos sob o mesmo CNPJ são serviços.
- **Senior:** ramo do CRM, ajustado pelo nome quando o ramo é genérico. Usinas de açúcar e álcool entram como Indústria. Cooperativas agropecuárias entram como Atacado/Distribuição (cooperativas de crédito saem). Empresas com "supermercado" no nome entram como Varejo. Em "Agricultura" e "Pecuária", só entram as que têm indício industrial ou comercial no nome (indústria, fertilizantes, usina, comércio, distribuidora, máquinas, peças, cereais etc.).
- **TOTVS:** perfil informado quando existe; 149 dos 225 cadastros estão sem perfil ou "a classificar" e foram classificados pelo nome.

A coluna `base_da_classificacao` diz de onde veio o ramo. **223 dos 949 do SAM estão com `validar_cnae = sim`** (ramo inferido ou ajustado pelo nome). 29 contas da Senior dentro do SAM não têm CNPJ preenchido.

Pontos de revisão do critério:

- **Logística e transporte (34 empresas)** foram descartadas pela regra de serviços, embora operador logístico seja comprador natural de WMS.
- **Cooperativas e usinas** foram mantidas no SAM por operarem armazém, loja de insumos e estoque industrial.

## 5. Produto recomendado

| Ramo | Produto padrão | Quando vira "WMS + Hub" |
|---|---|---|
| Indústria | WMS | fabrica bem de consumo vendável em marketplace (confecção, cosméticos, pet, alimentos de varejo, decoração, móveis, limpeza) |
| Atacado / Distribuição | WMS | distribui item de prateleira com giro em marketplace (autopeças, pneus, utilidades, limpeza, embalagens) |
| Varejo | Hub de Marketplaces | tem estoque relevante, depósito ou rede de lojas (no Senior e na TOTVS, o varejo em geral foi tratado como WMS + Hub) |
| E-commerce | WMS + Hub | regra geral (7 dos 8; 1 ficou só com Hub) |

SAM por produto: WMS 595 · WMS + Hub 253 · Hub de Marketplaces 101.
SOM por produto: WMS 84 · WMS + Hub 73.

## 6. SAM em duas frentes

| Frente | Status do produto | SAM | ERP conhecido | SOM |
|---|---|---|---|---|
| Varejo + E-commerce | oferta pronta | 241 (233 varejo, 8 e-commerce) | 185 | 30 |
| Indústria + Atacado/Distribuição | depende de evolução do WMS | 708 (467 indústria, 241 distribuição) | 429 | 127 |

**75% do SAM e 81% do SOM estão na frente em que o WMS ainda não está pronto.** Na frente de indústria e distribuição, 72 contas com ERP conhecido têm fit de Hub e podem ser abertas por ele.

## 7. Score (0 a 100)

O mesmo cálculo foi aplicado às quatro bases. Componentes:

| Componente | Pontos | Regra |
|---|---|---|
| Ramo | até 20 | Atacado/Distribuição 20 · E-commerce 20 · Indústria 18 · Varejo 14 |
| ERP conhecido e plano | até 30 | Omie completo 30 · Omie Start 22 · Omie Fit, BPO ou emissor 18 · cliente Senior 30 · cliente TOTVS 30 · ERP a confirmar 8 |
| Porte | até 20 | **Omie:** mensalidade ≥ R$ 2.000 → 15; ≥ 1.000 → 12; ≥ 500 → 8; ≥ 250 → 5; abaixo → 2; mais regime (Lucro Real/Presumido +5, Simples +3, MEI 0). **Senior:** porte Grande/Multinacional ou ≥ 250 funcionários → 20; ≥ 50 funcionários → 15; porte Pequena → 12; ≥ 10 funcionários → 10; Micro → 6; sem dado → 8; rating A +3, B +2 (teto 20). **TOTVS:** 12 fixo, porque a base não traz porte |
| Relacionamento | até 10 | **Omie:** último acesso ≤ 30 dias → 10; ≤ 90 dias → 5; acima → 0. **Senior e TOTVS, clientes:** rating A → 10; B → 9; demais → 8. **ERP a confirmar:** 0 |
| Grupo | 5 | mais de um CNPJ do mesmo grupo no SAM (mesma raiz de CNPJ, mesmo domínio de e-mail corporativo ou mesma matriz na TOTVS) |
| Fit para os dois produtos | 5 | produto recomendado = WMS + Hub |
| Contato preenchido | até 10 | e-mail 5 + telefone 5 |
| Penalidades | | −8 varejo de baixo fit com marketplace (veículos, piscinas, náutica, locação) · −5 ramo inferido · −10 contrato em cancelamento |

**Prioridade:** Hot = ERP conhecido e score ≥ 85 (é o SOM). Warm = demais empresas do SAM, incluindo todas com ERP a confirmar. Descartado = fora do SAM.

Resultado: 157 Hot, 792 Warm (457 com ERP conhecido e 335 a confirmar), 1.083 descartados.

**Ponto de atenção:** o score dá mais pontos a distribuição (20) e indústria (18) do que a varejo (14). A premissa foi definida antes da restrição do WMS (seção 6) e ajuda a explicar por que só 30 contas de varejo e e-commerce chegam ao SOM. Se a prioridade passar a ser a frente pronta, o peso do ramo deve ser revisto.

O score da base de Ribeirão Preto foi recalculado nessa régua comum. Numa versão anterior, só com Ribeirão Preto, ela tinha 73 Hot; na régua comum tem 74.

## 8. Resultados principais

SAM por ERP: Omie 404 · Senior 119 · TOTVS 91 · A confirmar 335.
SOM por ERP: Omie 123 · Senior 27 · TOTVS 7.
SOM por ramo: Atacado/Distribuição 64 · Indústria 63 · Varejo 24 · E-commerce 6.
Mensalidade Omie somada das 123 contas Omie no SOM: R$ 168,6 mil por mês (indicador de porte, não é faturamento do cliente).

Leitura por ERP:

- **Omie:** maior volume e melhor dado (uso e porte por contrato). Perfil de PME, com fit para Hub e WMS leve a médio.
- **Senior:** concentração em indústria de médio e grande porte (usinas, frigoríficos, metalmecânica, alimentos). Fit para WMS avançado; ticket maior e ciclo mais longo.
- **TOTVS:** base menor e sem dado de porte. Distribuidoras e redes de varejo com várias lojas (Armazém da Cerveja com 9 CNPJs, Track & Field, Mercadão dos Óculos).
- **A confirmar (335):** contas Prospect/Lead do CRM Senior e fornecedores da lista TOTVS. É o maior bloco de indústria da análise (208 indústrias, 71 distribuidoras, 56 varejos), com 52 empresas de grande porte.

Grupos com mais de um CNPJ: Armazém da Cerveja (9, TOTVS), Chico Rei (6, Omie), Milk Lat/2G (5, Omie), Origym, Quality Global e GIHF (4 cada, Omie).

## 9. Playbook resumido

- **Omie:** “Vocês já controlam o saldo no Omie. Quanto tempo a equipe leva para achar o item e conferir antes de faturar?” Oferta de Hub e WMS leve; time de SDRs de PME.
- **Senior:** “O ERP fecha o custo no centavo. A acuracidade do estoque físico acompanha?” Oferta de WMS avançado (lote, validade, vários armazéns); executivo de contas.
- **TOTVS:** “Quanto do estoque das lojas está disponível para vender online hoje?” Oferta de WMS + Hub omnichannel, com piloto em um CD ou uma loja.
- **ERP a confirmar:** primeira ligação só de qualificação: qual ERP usam, como controlam o armazém, se vendem em canal digital.
- **Por frente:** varejo e e-commerce recebem a oferta completa na primeira conversa. Em indústria e distribuição, a primeira reunião é de diagnóstico: levantar requisitos de armazém e conferir o que o WMS já cobre antes de propor; abrir com Hub onde houver fit.
- **Objeções:** “o ERP já controla meu estoque” → controla o saldo; o WMS controla onde está, quem separou e se o que saiu confere. “A Senior/TOTVS já tem módulo de WMS” → perguntar se está implantado no chão do armazém e posicionar como especialista integrado. “Vou ter que recadastrar tudo?” → não; produto, cliente e nota continuam no ERP.

## 10. Próximos passos e pendências

1. Validar CNAE do SAM, começando pelas 223 empresas com `validar_cnae = sim`, e depois as 86 de atividade não identificável.
2. Vender agora na frente pronta: 30 contas no SOM e 155 Warm com ERP conhecido em varejo e e-commerce.
3. Tratar as 127 contas de indústria e distribuição do SOM como pipeline de diagnóstico e levar os requisitos ao roadmap do WMS.
4. Confirmar o ERP das 335 contas "A confirmar" (56 de varejo, 279 de indústria e distribuição).
5. Resolver os 9 CNPJs com ERP conflitante entre bases.

Decisões que dependem do usuário:

- SOM = 157 (Hot) ou SOM = 614 (SAM com ERP conhecido).
- Rever o peso do ramo no score para favorecer varejo e e-commerce.
- Incluir logística e transporte como exceção à regra de serviços.
- Manter ou retirar cooperativas e usinas do SAM.
- Confirmar que a lista TOTVS é de clientes usuários do TOTVS.

## 11. Dicionário do `base_consolidada_leads.csv`

Codificação UTF-8, separador vírgula, uma linha por empresa, ordenado do maior para o menor score.

| Coluna | Descrição |
|---|---|
| `id` | identificador sequencial |
| `nivel_funil` | nível mais estreito que a empresa atinge: SOM, SAM ou TAM (TAM = descartada) |
| `prioridade` | Hot, Warm ou Descartado |
| `score` | 0 a 100; vazio para descartadas |
| `frente_sam` | Varejo + E-commerce ou Indústria + Atacado/Distribuição; vazio fora do SAM |
| `razao_social` | razão social como veio da base |
| `nome_fantasia_ou_aplicativo` | nome fantasia (Senior, TOTVS) ou nomes dos aplicativos Omie separados por " \| " |
| `cnpj` | CNPJ formatado; vazio em algumas contas da Senior que não têm CNPJ no CRM |
| `base_origem` | base de onde veio o registro mantido |
| `erp_atual` | Omie, Senior, TOTVS ou A confirmar |
| `erp_detalhe` | plano Omie ou tipo de conta na base de origem |
| `ramo` | ramo classificado |
| `base_da_classificacao` | de onde veio o ramo (nome da empresa, CRM Senior, perfil TOTVS, inferido) |
| `validar_cnae` | "sim" quando o ramo do SAM foi inferido ou ajustado pelo nome |
| `ramo_informado_na_origem` | ramo do CRM Senior ou perfil TOTVS, quando havia |
| `produto_recomendado` | WMS, WMS + Hub ou Hub de Marketplaces; vazio fora do SAM |
| `porte_informado` | porte do CRM Senior |
| `funcionarios` | número de funcionários do CRM Senior |
| `mensalidade_omie_rs` | soma das mensalidades dos aplicativos Omie ativos do CNPJ |
| `regime_tributario` | regime informado na Omie |
| `dias_sem_acesso_omie` | dias entre o último acesso ao Omie e 02/07/2026 |
| `cnpjs_mesmo_grupo` | quantos CNPJs do SAM pertencem ao mesmo grupo |
| `cidade`, `uf` | localização |
| `contato`, `email`, `telefone` | contato da base de origem (nas bases Omie é o contato financeiro) |
| `observacao` | outras bases em que o CNPJ aparece e conflitos de ERP |

## 12. Materiais produzidos no projeto original

Páginas privadas no claude.ai, do mesmo usuário:

- Relatório consolidado (cinco seções: resumo, ERP, matriz de priorização, playbook, próximos passos): https://claude.ai/artifact/GnwS1GZYqZ6dwyWbSbb2gV
- Apresentação interativa com TAM, SAM e SOM, as duas frentes do SAM e dashboard com filtros: https://claude.ai/artifact/AbUFMyKfv8xKzCSG33WD6u

Arquivos Excel entregues: `Leads_WMS_Hub_Consolidado.xlsx` (quatro bases), `Leads_WMS_Hub_Ribeirao_Preto_Centro_Ativos.xlsx` e `Leads_WMS_Hub_Ribeirao_Preto_Centro.xlsx` (versões anteriores, só Ribeirão Preto). O CSV deste pacote substitui a planilha consolidada e já inclui a coluna de frente do SAM, que a planilha não tem.

## 13. Instrução sugerida para o novo projeto

> Use `CONTEXTO_PROJETO.md` como referência de metodologia, definições e decisões, e `base_consolidada_leads.csv` como base de dados. TAM, SAM e SOM são contados em empresas. Ao recalcular qualquer número, parta do CSV e mantenha as regras das seções 3 a 7, salvo quando eu pedir outra regra. As decisões em aberto estão na seção 10.
