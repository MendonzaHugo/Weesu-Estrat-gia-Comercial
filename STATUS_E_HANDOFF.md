# Weesu · Estratégia Comercial: tudo o que foi gerado e o status em 06/11/2026

Documento de passagem para continuar o trabalho em outra conta do Claude. Ele reúne:

- o contexto do projeto;
- a lista de tudo o que foi produzido e onde está;
- o status atual de pipeline, metas, ações e pendências;
- as regras combinadas;
- como restaurar o painel numa conta nova.

Responsável: Hugo Mendonça, Coordenador de Vendas da Weesu.

---

## 1. Onde está cada coisa

| O quê | Onde | Observação |
|---|---|---|
| Repositório | GitHub `mendonzahugo/weesu-estrat-gia-comercial` | Todo o trabalho está na branch **`claude/wizu-strategic-sales-plan-io5l2p`**. Ela não foi integrada à `main` e não há pull request aberto. |
| Painel comercial (app) | `app/plano-comercial.html` | Publicado como artifact em https://claude.ai/artifact/YXhyhCJ9TkMeo1bT4edgnn, que pertence à conta atual. O link está aberto para quem o tiver, só para leitura. A edição e o banco de dados ficam nesta conta. |
| Tarefas dos próximos 30 dias | `app/tarefas-30-dias.html` | Página separada, sem banco de dados. Pode ser aberta direto no navegador ou impressa. |
| Termo de parceria de indicação | `parcerias/Parceria_Weesu_Standard_Termos_e_Condicoes.html` e `.pdf` | HTML editável, com painel de edição, botões "Baixar HTML" e "Salvar PDF". O PDF tem 11 páginas. |
| Retrato do CRM de 03/11 | `docs/03-retrato-crm-2026-11-03.md` | Resumo, ganhos, perdas, tabelas de preço, leitura estratégica e pendências. |
| Levantamento e diagnóstico iniciais | `docs/01-levantamento-estrategico.md`, `docs/02-diagnostico-inicial.md` | São de 12/10, anteriores às decisões atuais. Servem como histórico. |
| Base de leads e TAM/SAM/SOM | `dados/CONTEXTO_PROJETO.md`, `dados/resumo_indicadores.json` | Bases Omie RP, Omie MG, Senior e TOTVS: TAM 2.032, SAM 949, SOM 157. |
| Pipeline (cópia) | `dados/pipeline_seed.json` (124 negócios do CRM) e `dados/melixp_pipeline_seed.json` (leads MeliXP) | Sem dados de contato e sem CNPJs. |
| **Backup completo do banco do painel** | `dados/backup-banco-painel-2026-11-06.json` | Premissas, ações marcadas, decisões do WMS, acompanhamento (ainda vazio) e os 213 registros do pipeline. É o arquivo que restaura o painel em outra conta (seção 9). |

---

## 2. Contexto do projeto

- **Empresa:** Weesu, de Ribeirão Preto (SP). Nasceu dentro da Usee Brasil, uma operação de vendas em marketplace.
  - Produtos: **Seenc WMS** (gestão de armazém) e **Weesu HUB** (integração multicanal com marketplaces, ERPs e transportadoras).
  - O portfólio também tem Luwee e Weello, que ficam fora do foco comercial.
- **Ponto de partida:** a Weesu chegou a R$ 200 mil de MRR e 68 clientes sem área comercial estruturada, só com parceiros e indicações.
  - A operação comercial começou em agosto/2026.
  - De agosto a outubro vieram 8 clientes novos e 1 upsell, com R$ 41.099 de NMRR.
  - O plano parte de R$ 235 mil de MRR e 74 clientes.
- **Time:** 2 pessoas, o Hugo (liderança comercial, parceiros e fechamento) e 1 SDR.
  - Um Closer pode ser a 3ª contratação, decidida pelos gatilhos do funil (aba Rotina e indicadores).
  - O Hugo conduz o ritual de gestão.
- **Horizonte:** só os próximos 12 meses, de nov/26 a out/27. As projeções de longo prazo e a aba Time saíram por decisão do Hugo.
- **Histórico encerrado:** o plano começou como proposta de parceria Dixx–Weesu, com sociedade, repasse, réplica e tréplica.
  - O contrato foi concluído e todo o material dele foi removido.
  - A Dixx não é mais citada como responsável pelo time.
  - Ainda há resquícios no código: campos `taxaDixx` num registro e uma nota "confirmado pela Dixx" em duas decisões do WMS. Eles não aparecem como tema no painel.

---

## 3. Linha do tempo do que foi gerado

| Data | Entrega |
|---|---|
| 12/10 | Levantamento estratégico e diagnóstico inicial (`docs/01`, `docs/02`), com base nas bases de leads |
| 13 e 14/10 | Primeira versão do app, depois reestruturada como proposta de sociedade com a Dixx (repasse, 10 anos, abertura de canais, réplica e tréplica em HTML/PDF). **Tudo isso foi removido em 26/10.** |
| 14/10 | Fechamentos de ago/26 registrados como anteriores ao plano; leads MeliXP do e-commerce Puro entram como base; requisitos de WMS (FEFO, vários CDs) marcados como atendidos |
| 26/10 | Contrato removido e estratégia lapidada: ICP, prioridade de canais, funil reverso, rotina e plano 30/90/180 |
| 27/10 | Horizonte de 12 meses, time de 2 pessoas e Closer por gatilho; pipeline atualizado com o CRM de 27/10; Delta Comércio reprecificada; termo de parceria criado e mesclado com o modelo "Weesu Standard" |
| 03/11 | Pipeline atualizado com o CRM de 03/11; erro que travava o painel corrigido; Grupo Stockfacil reprecificado; Sul Distribuidora retirada; página das tarefas de 30 dias; meta de R$ 21 mil/mês |
| 06/11 | Este documento e o backup do banco |

---

## 4. O painel comercial

### Navegação
- **1. Estratégia**
  - Abertura
  - Canais e ICP
  - Metas e funil
- **2. Execução**
  - Plano 30/90/180
  - Rotina e indicadores
  - Pipeline
  - Acompanhamento
  - WMS e high ticket
- **Método e fontes**, fora dos blocos.

### Banco de dados do artifact
| Coleção | Conteúdo |
|---|---|
| `config/premissas` | Premissas editáveis na aba Metas. As atuais estão no backup. |
| `pipeline` | Um documento por negócio, com os campos `nome`, `etapa`, `produto`, `mrr`, `setup`, `prob`, `probCrm`, `chanceHugo`, `mes` (AAAA-MM), `status` (`aberto`, `ganho`, `perdido` ou `lead`), `proximaAcao`, `acaoData`, `pendencia`, `diagnostico`, `condicoes`, `motivo`, `perdidoEm`, `origem` (`puro` = e-commerce Puro), `preplano`, `noMrrInicial` e `upsell`. |
| `acoes` | Ações do plano marcadas como feitas (id da ação → `{feito:true}`). |
| `realizado` | Lançamentos mensais da aba Acompanhamento, ainda vazia. |
| `wms` | Decisões por requisito do Seenc. |

### Como o painel interpreta os dados
- A chance de cada negócio é a do Hugo (`chanceHugo`) quando foi definida. Nos demais, vale a probabilidade da etapa no CRM, guardada em `probCrm`.
- Os negócios com `status: ganho` e mês anterior a nov/26 são os fechamentos anteriores ao plano. Eles não contam para a meta.
- Quando esses fechamentos têm `noMrrInicial: false`, somam ao MRR de partida.

### Premissas atuais (as principais)
- **Meta e crescimento:**
  - Meta de NMRR de **R$ 21.000/mês**, sem crescimento no ano 1 (`cresc1 = 0`). Isso dá R$ 252 mil no ano e cerca de 78 contratos (ticket médio de R$ 3.211).
  - Do ano 2 em diante, os crescimentos são de 1%, 2%, 1% e 1% ao mês.
- **Base de partida:** MRR inicial de R$ 200.000, 68 clientes e churn de 1% ao mês.
- **Ticket e setup:** ticket low de R$ 3.000, ticket high de R$ 12.000 e setup médio de R$ 12.000.
- **Conversões:**

  | Origem | Conversão |
  |---|---|
  | Reunião → venda | 15% |
  | Indicação | 20% |
  | E-commerce Puro | 20% |
  | ERPs corporativos | 30% |
  | Inbound | 20% |
  | MeliXP (apresentação → contrato) | 20% |

- **Projeção do painel:** MRR de cerca de R$ 447 mil em out/27 (1,9 vez o atual), com 140 clientes.
- **Ponto a confirmar:** "21 mil por mês até o final do ano" foi aplicado ao ano inteiro do plano, até out/27, porque as premissas gravadas já tinham crescimento de 0% no ano 1. Se a meta deve voltar a crescer a partir de jan/27, basta ajustar o crescimento na aba Metas.

---

## 5. Status do pipeline (CRM de 03/11/2026)

**Resumo:**
- **Abertos:** 49 negócios (46 do CRM e 3 propostas fora dele), com R$ 144,9 mil de mensalidade e R$ 86,3 mil ponderados.
- **Novembro:**
  - 21 negócios, com R$ 49,6 mil ponderados.
  - Isso é 2,4 vezes a meta de R$ 21 mil.
- **Dezembro:**
  - 13 negócios, com R$ 26,3 mil ponderados.
- **Previsões vencidas:** 3 negócios com previsão em outubro ainda abertos (All Filmes, Confort Club Shoes e Shield), com R$ 5,9 mil ponderados.
- **Ganhos dos últimos 60 dias:**
  - 7 ganhos, com R$ 37.599/mês e R$ 95.000 de setup.
  - Os ganhos foram Trevisan R$ 13.499, Nutreline R$ 12.000, Ancora R$ 3.900, LS Ecomm R$ 2.700, Casa Eletro Marcon R$ 2.500, Gard R$ 1.500 e Leal R$ 1.500.
- **Perdas dos últimos 60 dias:** 64.
  - Por motivo: desqualificado 18, não respondeu 11, sem fit 10, preço 8 (R$ 43 mil/mês), sem urgência 8, projeto cancelado 3, concorrente 3, integração inviável 2 e sem orçamento 1.
  - A taxa de ganho sobre os encerrados é de 10%.

### Negócios mais próximos do fechamento
| Negócio | Etapa | Mensal | Chance | Previsão | Ponto de atenção |
|---|---|---|---|---|---|
| Delta Comércio | Contrato & Financeiro | R$ 7.000 | 99% | nov | Proposta: R$ 0,07 por pedido, 100 mil pedidos, excedente R$ 0,10, setup R$ 15.000, validade 30/11 |
| Grupo Stockfacil (seller + indústria) | Contrato & Financeiro | R$ 2.500 | 99% | dez | Ver abaixo |
| All Filmes | Contrato & Financeiro | R$ 2.500 | 90% | vencida | Estudo de kits; valor do Hub |
| Confort Club Shoes | Contrato & Financeiro | R$ 1.000 | 80% | vencida | Seenc na fase 2 |
| Tudo Limpinho | Negociação | R$ 6.450 | 80% | nov | — |
| Shield Equipamentos | Negociação | R$ 3.600 | 80% | vencida | Atualizar a previsão |
| Be Factory | Negociação | R$ 1.500 | 80% | nov | — |
| Mantycom | Negociação | R$ 1.000 | 80% | nov | Há um registro duplicado no CRM |
| Stoky | Negociação | R$ 15.000 | 25% (etapa: 75%) | nov | Custo da integração com o Sankhya |
| Pink Urban | Negociação | R$ 10.000 | 75% | dez | Caber em R$ 10 mil |
| Casa da Laurinha | Follow-up | R$ 6.000 | 55% | nov | API do ERP Times |
| Auto Speed | Follow-up | R$ 5.000 | 55% | nov | Prazo do Protheus; propostas de 03/11 com validade 17/11 |

**Grupo Stockfacil:**
- O cliente voltou atrás na contratação de ago/26 e pediu para incluir a indústria do grupo. O registro de agosto foi marcado como "Contratação revertida".
- Vale só a tréplica de 03/11:

  | Item | Valor |
  |---|---|
  | Seller | R$ 1.000/mês |
  | Indústria (até 4.000 SKUs) | R$ 1.200/mês |
  | 2 coletores | isentos por 3 meses, depois R$ 150 cada |
  | Total do grupo | R$ 2.200/mês nos meses 1 a 3 e R$ 2.500 depois |
  | Setup | R$ 5.000 |

- A tréplica depende da diretoria até 10/11. No painel, a ação n1m já está marcada como feita.

### Propostas emitidas fora do CRM (no painel com 55% de chance)
| Proposta | Valor considerado | Validade |
|---|---|---|
| AZP E-commerce (Vila Velha/ES) | Só o Seenc, banda de 70 mil pedidos: R$ 8.000/mês, setup R$ 15.000. A alternativa em combo Omie + Hub + Seenc, de R$ 16.650/mês, está registrada nas condições do negócio. | 17/11 |
| Seller de camisetas masculinas que usa UpSeller | Tabela A, 7 mil pedidos: R$ 3.300/mês, setup R$ 15.000 | 13/11 |
| Seller que usa UpSeller com 6 mil pedidos (nome a informar) | Tabela A: R$ 3.000/mês, setup R$ 15.000 | 13/11 |

### Fechamentos anteriores ao plano (no painel)
- **Somam ao MRR de partida:** Trevisan, Nutreline, Ancora, LS Ecomm, Gard e Leal, num total de R$ 35.099.
- **Já estavam no MRR de R$ 200 mil:** JGP (R$ 3.000), Casa Eletro Marcon (R$ 2.500) e o upsell da Campomar (R$ 500).
- **Saíram desta lista:**
  - Sul Distribuidora (R$ 2.900), a pedido do Hugo.
  - Stockfacil de agosto (R$ 1.000), por contratação revertida.

---

## 6. Regras de preço vigentes (base comercial de 03/11)

- **Tabela A, sellers (Seenc WMS):**
  - Mensalidade progressiva por pedido cross:

    | Pedidos | Mensalidade | Adicional por pedido |
    |---|---|---|
    | 1 a 2 mil | R$ 1.000 a 1.500 | R$ 0,60 |
    | 2 a 5 mil | R$ 1.500 a 2.700 | R$ 0,50 |
    | 5 a 10 mil | R$ 2.700 a 4.200 | R$ 0,40 |
    | 10 a 15 mil | R$ 4.200 a 5.450 | R$ 0,35 |
    | 15 a 20 mil | R$ 5.450 a 6.450 | R$ 0,25 |
    | Acima de 20 mil | R$ 6.450 + R$ 0,20/pedido | — |

  - Setup de R$ 15.000 à vista ou R$ 17.000 em 10x.
- **Full:** pedido enviado ao Full não entra na contagem. O cenário de cobrança é de 10% do preço do pedido cross.
- **Operador logístico, por bandas:**
  - Os pedidos de todos os clientes do operador somam na mesma banda.
  - Até 20 mil pedidos, vale o teto da Tabela A. Acima disso, o preço cai até R$ 0,10 por pedido em 100 mil.
  - Troca de banda com 15 dias de aviso.
  - Cliente novo do operador: R$ 1.000 de setup remoto.
- **Tabela B, indústrias e distribuidoras (aprovada em 27/10):**
  - Seenc por porte:

    | Porte | Mensalidade |
    |---|---|
    | Porte 1 (até R$ 10 mi de faturamento) | R$ 2.900 |
    | Porte 2 | R$ 4.500 |
    | Porte 3 | R$ 6.900 |
    | Porte 4 | R$ 9.900 |
    | Porte 5 | R$ 14.900 |

  - Hub: de R$ 1.500 a R$ 8.900.
  - Teto: as mensalidades de Seenc + Hub somadas ficam em até 0,6% do faturamento anual.
- **Integração de ERP:**

  | ERPs | Custo |
  |---|---|
  | Já integrados: Bling, Omie, Tiny, Limeweb e Protheus | Sem custo |
  | Estratégicos: Sankhya, BaseLinker, Magis5, Athon, Sysemp, UpSeller, Winthor, Senior e SAP Business One | R$ 3.000 |
  | Demais | R$ 7.000 |

- **Multi-CNPJ:** pronto desde 14/10, com saldos separados por CNPJ. O fiscal entre CNPJs fica no ERP do cliente.
- **Coletores:** a Weesu não fornece hardware por padrão. A locação já foi ofertada a R$ 135, 150, 180 e 190 por aparelho/mês.
- **Combo Omie ERP + Weesu Hub + Seenc WMS:** Omie pré-pago e sem fidelidade.
- **Lacunas em aberto:**
  - tabela do Hub para sellers;
  - preço padrão de locação de coletor;
  - custo interno de implantação;
  - regra de integração de ERP fora do operador logístico;
  - alçada para propostas abaixo da tabela.

---

## 7. Plano de ação: status das tarefas dos 30 dias (até 30/11)

| ID | Tarefa (resumo) | Responsável | Prazo | Status no painel |
|---|---|---|---|---|
| n1k | Limpar o CRM: previsões vencidas, 45 negócios com atividades antigas, follow-ups atrasados desde 28/10, Mantycom duplicada, 3 propostas fora do CRM | Hugo + SDR | 07/11 | aberta |
| n1l | Rituais na agenda: diária, revisão semanal e fechamento mensal | Hugo | 07/11 | aberta |
| n1m | Tréplica do Grupo Stockfacil na diretoria | Hugo + diretoria | 10/11 | **feita** |
| n1c | Política comercial e lacunas da tabela de preços | Sócios + comercial | 15/11 | aberta |
| n1d | Onda 1 da base: 157 contas Hot em cadência | SDR | 15/11 | aberta |
| n1g | MeliXP: desfechos, convites e ligações para tier A | SDR + Hugo | 15/11 | aberta |
| n1i | Programa de indicação de clientes ativos | Hugo + marketing | 15/11 | aberta |
| n1a | Fechamentos de novembro (NMRR ≥ R$ 21 mil) | Hugo | 30/11 | aberta |
| n1n | Qualificação no primeiro contato (desqualificados abaixo de 15% das perdas) | SDR + Hugo | 30/11 | aberta |
| n1o | Revisitar perdas por preço com a Tabela B e o combo Omie | Hugo | 30/11 | aberta |
| n1e | Bases de outros franqueados Omie | SDR + Hugo | 30/11 | aberta |
| n1f | Reativar contabilidades parceiras | Hugo | 30/11 | aberta |
| n1j | Frente de inbound com o marketing | Marketing + SDR | 30/11 | aberta |
| n1h | Conversas com canais de Sankhya, Senior e TOTVS | Hugo + sócios | 30/11 | aberta |

As ações de 90 dias, 180 dias e 12 meses estão no painel (aba Plano 30/90/180), definidas na constante `HORIZ` de `app/plano-comercial.html`.

### Decisões do WMS registradas no painel
| Requisito | Status | Decisão | Esforço / prazo |
|---|---|---|---|
| Lote e validade (FEFO) | Atende | Já atendido | — |
| Vários CDs e galpões | Atende | Já atendido | — |
| Kits e montagem | Atende | Já atendido | — |
| Reposição por mínimo | Atende em parte | Desenvolver | Pequeno · fev/27 |
| Integração com ERPs corporativos | — | Desenvolver | Médio · mar/27 |
| LPN e controle por pallet | Não atende | Não desenvolver | Grande |
| Granel e produto pesável | — | Não desenvolver | Médio |
| Integração com a produção (MES) | Não atende | A avaliar | Grande |
| Estoque entre CNPJs | Atende em parte (multi-CNPJ) | A avaliar | — |
| Expedição por carga, rota e doca | A levantar | A avaliar | — |

---

## 8. Termo de parceria de indicação

- **Modelo:** baseado no contrato de parceiros da Omie, mesclado com o "Parceria Weesu Standard – Termos e Condições" enviado pelo Hugo. Tem 11 páginas, com as fontes e cores da Weesu e do Seenc.
- **Remuneração:**
  - Opção A: 100% da 1ª mensalidade do cliente indicado.
  - Opção B: 10% ao mês durante o 1º ano do cliente.
- **Dados da Weesu no termo:**
  - Razão social e CNPJ: Weesu Consultoria e Sistemas Ltda., 37.219.704/0001-60.
  - Endereço: R. João Arcadepani Filho, 160 · Nova Ribeirânia · Ribeirão Preto/SP · CEP 14096-720.
  - Contato: WhatsApp (16) 99328-6681, contato@weesu.com.br e @weesutech.
  - Responsável pela parceria: Hugo Mendonça.
- **Em aberto no termo:**
  - "Mensalidade mínima: A definir".
  - E-mail financeiro da Weesu "[a preencher]".
  - Confirmar o endereço no cartão CNPJ: um cadastro público aponta Serrana/SP.

---

## 9. Como continuar em outra conta

1. **Repositório.** Dê acesso do GitHub à conta nova, ou continue usando a mesma conta do GitHub. Todo o material está na branch `claude/wizu-strategic-sales-plan-io5l2p`. Se preferir, integre-a à `main` antes.
2. **Painel.**
   - O artifact atual continua abrindo pelo link, só para leitura.
   - Para editar e gravar dados na conta nova, publique `app/plano-comercial.html` como um artifact novo nessa conta, com as capacidades `db` e `user`. O link será outro.
   - Em seguida, restaure o banco a partir de `dados/backup-banco-painel-2026-11-06.json`: grave `config/premissas`, `acoes`, `wms` e cada item de `pipeline` como documento da coleção de mesmo nome. Para o Claude, use lotes de até 50 escritas.
3. **Prompt sugerido para a conta nova:**

   > Sou o Hugo, Coordenador de Vendas da Weesu (Seenc WMS e Weesu HUB). Leia `STATUS_E_HANDOFF.md` na branch `claude/wizu-strategic-sales-plan-io5l2p` do repositório `mendonzahugo/weesu-estrat-gia-comercial`. Publique `app/plano-comercial.html` como artifact com banco de dados, restaure o banco a partir de `dados/backup-banco-painel-2026-11-06.json` e confirme que o pipeline mostra 49 negócios abertos e a meta de R$ 21 mil por mês. Depois, siga as regras da seção 10.

---

## 10. Regras combinadas (valem para qualquer continuação)

- **Dados pessoais:**
  - Nada de nomes de contatos, e-mails, telefones ou CNPJs de clientes no painel nem nos documentos.
  - Negócios em nome de pessoa física aparecem só com iniciais, por exemplo "Lead J.M.M. · pessoa física".
- **Escopo:**
  - A estratégia cobre só os próximos 12 meses, com o time atual de 2 pessoas.
  - Não projetar crescimento de equipe além do Closer por gatilho.
  - Nada de Dixx, sociedade ou contrato.
- **Chance dos negócios:** a do Hugo prevalece sobre a probabilidade da etapa no CRM.
- **Novo retrato do CRM:** atualize os negócios existentes pelo nome.
  - Perdidos ganham motivo e data.
  - Ganhos usam a data de ganho do CRM.
  - Propostas fora do CRM entram marcadas como tal.
- **Antes de publicar o painel:** verificar a sintaxe do script (`node --check`). Em 03/11, um parêntese faltando travou o painel inteiro.
- **Linguagem:** português, direto, com números conferidos.

---

## 11. Pendências e próximos passos

1. Decisão da diretoria sobre a tréplica do Grupo Stockfacil (validade 10/11).
2. Limpeza do CRM:
   - previsões vencidas (All Filmes, Confort Club Shoes e Shield);
   - follow-ups atrasados (Zeiq e 2 leads de pessoa física);
   - Mantycom duplicada;
   - registro das 3 propostas fora do CRM. A da UpSeller de 6 mil pedidos ainda precisa do nome da empresa.
3. Fechar as lacunas da tabela de preços e a alçada de desconto (ação n1c, até 15/11).
4. Confirmar se a meta de R$ 21 mil/mês vale até out/27 ou só até dez/26 (seção 4).
5. Em dezembro, lançar o realizado de novembro na aba Acompanhamento (leads, contatos, reuniões, propostas, vendas por canal, NMRR e setup).
6. Atualizar o pipeline a cada novo retrato do CRM.
7. Termo de parceria: definir a mensalidade mínima e o e-mail financeiro, e confirmar o endereço.
