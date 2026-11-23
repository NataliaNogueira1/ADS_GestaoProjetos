# Análise de Riscos do Projeto — FieldOps

> **Disciplina:** Gestão de Projetos — 4º semestre ADS
> **Professor:** Me. Deivison S. Takatu
> **Aula 07:** Riscos — Atividade de Análise de Riscos
> **Projeto:** FieldOps — Plataforma de Inspeção em Campo
> **Equipe:** 404 Not Found
> **Data:** 25/09/2026

---

## 1. Objetivo

Este documento apresenta a **Análise de Riscos do Projeto FieldOps**, elaborada conforme o processo de **Gerenciamento dos Riscos do Projeto** (PMBOK, área 11): planejar o gerenciamento dos riscos, identificar os riscos, realizar as análises qualitativa e quantitativa, planejar as respostas aos riscos e controlar os riscos.

A análise usa como base os artefatos já produzidos pela equipe — o **Termo de Abertura do Projeto (TAP)**, a **EAP**, o **Cronograma**, o **Orçamento** (linha de base de R$ 204.000,00) e a **Análise da Qualidade** — em que a **sincronização offline** foi identificada como o ponto mais crítico do sistema. Os 12 riscos listados no TAP foram consolidados nos riscos deste registro (ver coluna "Riscos do TAP" na seção 5).

Para cada risco são descritos **causa, risco (evento) e consequência**, seguindo a orientação da aula de evitar registros genéricos como "o projeto pode atrasar".

---

## 2. Definição das Escalas

### 2.1 Escala de Probabilidade

| Nível | Classificação | Valor | Descrição |
|---|---|:---:|---|
| 1 | Muito baixa | 0,10 | Improvável de ocorrer no período do projeto |
| 2 | Baixa | 0,30 | Pode ocorrer, mas não é esperado |
| 3 | Média | 0,50 | Tão provável quanto improvável |
| 4 | Alta | 0,70 | Esperado que ocorra em algum momento |
| 5 | Muito alta | 0,90 | Quase certo de ocorrer |

### 2.2 Escala de Impacto

| Nível | Classificação | Valor | Prazo | Custo | Escopo/Qualidade |
|---|---|:---:|---|---|---|
| 1 | Muito baixo | 0,05 | Atraso desprezível | < 1% do orçamento | Impacto imperceptível |
| 2 | Baixo | 0,10 | Atraso de 1–2 dias | 1–3% do orçamento | Áreas secundárias afetadas |
| 3 | Moderado | 0,20 | Atraso de 3–5 dias | 3–7% do orçamento | Áreas principais afetadas |
| 4 | Alto | 0,40 | Atraso de 1–2 semanas | 7–15% do orçamento | Redução relevante do escopo |
| 5 | Muito alto | 0,80 | Inviabiliza a entrega | > 15% do orçamento | Produto final inutilizável |

> O nível de impacto de cada risco é definido pela dimensão **mais grave** entre prazo, custo e escopo/qualidade. Por isso, um risco pode ter impacto alto em escopo/qualidade e, ao mesmo tempo, um custo de resposta pequeno (seção 7).

### 2.3 Matriz de Severidade (Probabilidade x Impacto)

A severidade é calculada por **Probabilidade × Impacto** e classificada por faixa de cor:

| P \ I | 0,05 (MB) | 0,10 (B) | 0,20 (M) | 0,40 (A) | 0,80 (MA) |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **0,90 (MA)** | 🟢 0,05 | 🟡 0,09 | 🟠 0,18 | 🔴 0,36 | 🔴 0,72 |
| **0,70 (A)** | 🟢 0,04 | 🟡 0,07 | 🟠 0,14 | 🔴 0,28 | 🔴 0,56 |
| **0,50 (M)** | 🟢 0,03 | 🟢 0,05 | 🟡 0,10 | 🟠 0,20 | 🔴 0,40 |
| **0,30 (B)** | 🟢 0,02 | 🟢 0,03 | 🟡 0,06 | 🟠 0,12 | 🟠 0,24 |
| **0,10 (MB)** | 🟢 0,01 | 🟢 0,01 | 🟢 0,02 | 🟢 0,04 | 🟡 0,08 |

**Legenda:** 🟢 Baixo (≤ 0,05) · 🟡 Moderado (0,06–0,11) · 🟠 Alto (0,12–0,24) · 🔴 Crítico (≥ 0,25)

---

## 3. Estratégias de Resposta aos Riscos

Conforme o processo *11.5 — Planejar as respostas aos riscos*, adotam-se as estratégias:

**Para ameaças (riscos negativos):**
- **Prevenir (eliminar):** eliminar a causa ou proteger o projeto do impacto.
- **Transferir:** repassar o impacto a um terceiro (ex.: serviço gerenciado).
- **Mitigar:** reduzir a probabilidade e/ou o impacto a um nível aceitável.
- **Aceitar:** não agir preventivamente, tratando o risco caso ocorra (com ou sem reserva de contingência).

**Para oportunidades (riscos positivos):**
- **Explorar, Melhorar, Compartilhar, Aceitar.**

---

## 4. Registro de Riscos (Causa → Risco → Consequência)

### R01 — Perda/inconsistência de respostas na sincronização offline
- **Causa:** Falta de idempotência no reenvio e regras de conflito mal definidas entre o app mobile e a API; técnico atua em área sem cobertura de internet.
- **Risco:** As respostas registradas offline podem ser perdidas ou duplicadas ao sincronizar com o servidor.
- **Consequência:** Retrabalho de inspeção, inconsistência de dados e atraso na aprovação e na entrega do MVP.

### R02 — Indisponibilidade dos serviços de nuvem de terceiros
- **Causa:** Dependência de hospedagem em nuvem, banco PostgreSQL gerenciado, armazenamento de evidências e serviço de notificações push contratados de fornecedores externos.
- **Risco:** Os serviços de nuvem que hospedam a API do projeto podem ficar indisponíveis durante o desenvolvimento ou a demonstração.
- **Consequência:** Bloqueio dos testes integrados, atraso no cronograma e risco de falha na demo ponta a ponta (PBI-072).

### R03 — Falha de autenticação e gestão de sessão (token)
- **Causa:** Complexidade na implementação de JWT com refresh token e autorização por perfil (PBI-007, PBI-010, PBI-012).
- **Risco:** Usuários podem perder a sessão indevidamente ou acessar recursos sem permissão.
- **Consequência:** Falhas de segurança, bloqueio de uso pelos técnicos e retrabalho de correção.

### R04 — Subestimação de esforço nos pacotes de maior incerteza
- **Causa:** Estimativas de três pontos apontaram alta variação em sincronização offline, construtor de modelos e checklist dinâmico.
- **Risco:** O esforço real desses pacotes pode ultrapassar o estimado.
- **Consequência:** Estouro de horas, consumo da reserva de contingência (R$ 14.740,00) e pressão sobre o prazo das sprints.

### R05 — Indisponibilidade de membros da equipe
- **Causa:** Equipe acadêmica de 9 integrantes conciliando o projeto com outras disciplinas; concentração de conhecimento em poucas pessoas.
- **Risco:** Um ou mais integrantes podem ficar indisponíveis em momentos críticos das sprints.
- **Consequência:** Sobrecarga dos demais, atraso de PBIs dependentes e perda de conhecimento (bus factor).

### R06 — Defeitos em checklists com muitos itens
- **Causa:** Correlação positiva identificada na Aula 05 — quanto mais itens no checklist, mais defeitos por inspeção.
- **Risco:** Modelos de inspeção grandes podem apresentar mais falhas de validação e desempenho no mobile.
- **Consequência:** Não conformidades não detectadas, reprovação de inspeções e insatisfação do cliente.

### R07 — Falha no upload de evidências (fotos)
- **Causa:** Instabilidade de rede e ausência de tratamento de foto pendente (PBI-044).
- **Risco:** Fotografias podem não ser enviadas ou ficar desvinculadas do item correto.
- **Consequência:** Inspeções sem comprovação de não conformidade, comprometendo a auditoria e a qualidade da entrega.

### R08 — Atraso na build/entrega para demonstração
- **Causa:** Concentração de tarefas de fechamento (seed, Docker, build APK, demo) no fim da Sprint 2, e das funcionalidades P1 e da homologação final na Sprint 3.
- **Risco:** Os builds de demonstração (APK Android e painel web) podem não ficar prontos a tempo.
- **Consequência:** Comprometimento dos marcos "MVP funcional P0" (02/10/2026, fim da Sprint 2) e "Entrega final com P1" (24/11/2026, fim da Sprint 3).

### R09 — Alterações de escopo durante o desenvolvimento
- **Causa:** Inclusão de novas funcionalidades ou mudanças de requisitos sem passar pelo controle de mudanças.
- **Risco:** O escopo pode crescer além do backlog planejado para as sprints.
- **Consequência:** Aumento da complexidade e atraso das funcionalidades prioritárias (P0) do MVP.

### R10 — Falhas de integração e dependência entre frentes
- **Causa:** Backend, Web e Mobile são desenvolvidos em paralelo e dependem do mesmo contrato de API e modelo de dados.
- **Risco:** Divergências entre o contrato da API e o que Web e Mobile consomem, ou o atraso de uma frente, podem bloquear as demais.
- **Consequência:** Retrabalho de integração e impossibilidade de testar o fluxo completo da inspeção no prazo.

### R11 — Incompatibilidade de dispositivos e recursos indisponíveis
- **Causa:** Diferenças entre versões e modelos de Android e permissões negadas de câmera, QR Code ou geolocalização.
- **Risco:** O aplicativo pode se comportar de forma diferente entre dispositivos ou perder funções de evidência.
- **Consequência:** Falhas na captura de fotos, leitura de QR Code ou registro de localização durante a inspeção.

### R12 — Baixa qualidade das informações coletadas
- **Causa:** Interface pouco clara para o uso em campo ou validações insuficientes nos componentes de resposta.
- **Risco:** Os técnicos podem registrar respostas incompletas ou incorretas.
- **Consequência:** Reprovação de inspeções, retrabalho em campo e perda de confiança nos dados pelos supervisores.

---

## 5. Análise Qualitativa (Probabilidade × Impacto)

Priorização por severidade (P × I), do maior para o menor:

| ID | Risco | Riscos do TAP | Prob. | Impacto | Severidade (P×I) | Classificação |
|---|---|:---:|:---:|:---:|:---:|:---:|
| R01 | Perda na sincronização offline | 1, 2, 3 | 0,70 | 0,80 | **0,56** | 🔴 Crítico |
| R03 | Falha de autenticação/sessão | 8 | 0,50 | 0,40 | **0,20** | 🟠 Alto |
| R08 | Atraso na build para demo | 12 | 0,50 | 0,40 | **0,20** | 🟠 Alto |
| R10 | Integração e dependência entre frentes | 4, 10 | 0,50 | 0,40 | **0,20** | 🟠 Alto |
| R02 | Indisponibilidade da nuvem de terceiros | — | 0,30 | 0,40 | **0,12** | 🟠 Alto |
| R05 | Indisponibilidade da equipe | — | 0,30 | 0,40 | **0,12** | 🟠 Alto |
| R04 | Subestimação de esforço | 12 | 0,50 | 0,20 | **0,10** | 🟡 Moderado |
| R06 | Defeitos em checklists grandes | 11 | 0,50 | 0,20 | **0,10** | 🟡 Moderado |
| R09 | Alterações de escopo | 9 | 0,50 | 0,20 | **0,10** | 🟡 Moderado |
| R07 | Falha no upload de evidências | 5 | 0,30 | 0,20 | **0,06** | 🟡 Moderado |
| R11 | Incompatibilidade de dispositivos/recursos | 6, 7 | 0,30 | 0,20 | **0,06** | 🟡 Moderado |
| R12 | Baixa qualidade das informações coletadas | 11 | 0,30 | 0,20 | **0,06** | 🟡 Moderado |

> **Análise:** o risco **R01 (sincronização offline)** é o único **crítico** e concentra a maior atenção — coerente com a Análise da Qualidade (Aula 05), em que essa categoria liderou o Diagrama de Pareto (35% dos defeitos). Os riscos **altos** (R02, R03, R05, R08, R10) estão ligados a dependências externas, segurança, pessoas, integração entre frentes e ao fechamento do cronograma.

---

## 6. Análise Quantitativa (Valor Monetário Esperado)

Conforme o processo *11.4 — Realizar a análise quantitativa dos riscos*, cada risco recebeu um **custo estimado caso ocorra**, calculado em horas de retrabalho ao custo-hora de desenvolvimento do orçamento (R$ 50,00). O **Valor Monetário Esperado (VME)** é a probabilidade multiplicada por esse custo:

```
VME = Probabilidade × Custo se ocorrer
```

| ID | Probabilidade | Horas de retrabalho | Custo se ocorrer (R$) | VME (R$) |
|---|:---:|:---:|---:|---:|
| R01 | 0,70 | 160 h | 8.000,00 | 5.600,00 |
| R02 | 0,30 | 40 h | 2.000,00 | 600,00 |
| R03 | 0,50 | 60 h | 3.000,00 | 1.500,00 |
| R04 | 0,50 | 80 h | 4.000,00 | 2.000,00 |
| R05 | 0,30 | 60 h | 3.000,00 | 900,00 |
| R06 | 0,50 | 20 h | 1.000,00 | 500,00 |
| R07 | 0,30 | 30 h | 1.500,00 | 450,00 |
| R08 | 0,50 | 30 h | 1.500,00 | 750,00 |
| R09 | 0,50 | 30 h | 1.500,00 | 750,00 |
| R10 | 0,50 | 40 h | 2.000,00 | 1.000,00 |
| R11 | 0,30 | 20 h | 1.000,00 | 300,00 |
| R12 | 0,30 | 26 h | 1.300,00 | 390,00 |
| **Total** | | | **29.800,00** | **14.740,00** |

> **Análise:** o VME total de **R$ 14.740,00** é o valor da reserva de contingência do orçamento (Aula 05). Só o R01 responde por 38% do VME, o que confirma a priorização da análise qualitativa.

---

## 7. Plano de Respostas aos Riscos

| ID | Estratégia | Ações de resposta | Responsável | Gatilho de monitoramento |
|---|---|---|---|---|
| R01 | **Mitigar** | Garantir idempotência no reenvio (PBI-052), definir regras de conflito (PBI-055), fila outbox persistente (PBI-050) e testes automatizados dos fluxos críticos (PBI-065). | Lucas / Marcela / Felipe | Taxa diária de falha de sync > 13,7% (LSC do gráfico de controle da Aula 05) |
| R02 | **Transferir / Mitigar** | Usar serviços gerenciados com SLA; preparar ambiente de contingência local (Docker) para a demo (PBI-070). | Júlia / Marcela | Indisponibilidade > 1h em ambiente de homologação |
| R03 | **Prevenir** | Revisão de segurança do fluxo JWT + refresh; testes de autorização por perfil; renovação automática de sessão (PBI-010). | Lucas | Erros de sessão reportados nos testes |
| R04 | **Mitigar / Aceitar** | Monitorar horas por pacote; acionar a reserva de contingência (R$ 14.740,00) quando o esforço de um pacote ultrapassar o estimado. | Natália (GP) | Consumo de horas > 110% do estimado no pacote |
| R05 | **Mitigar** | Programação em par, documentação (READMEs — PBI-067) e distribuição de conhecimento entre frentes. | Natália (GP) | Ausência não planejada > 2 dias |
| R06 | **Mitigar** | Testes de regressão para checklists com mais de 25 itens; validação e prévia antes de publicar (PBI-022). | Júlia / Andressa (Web) e Rodrigo (testes mobile — PBI-065) | Nº de defeitos por inspeção acima da tendência |
| R07 | **Mitigar** | Marcar foto como pendente e reenviar (PBI-044); associar fotografia ao item correto (PBI-043). | Natália / Rodrigo | Fotos pendentes acumuladas na outbox |
| R08 | **Prevenir** | Congelar o escopo P0 antes do fim da Sprint 2; ensaiar a demo ponta a ponta (PBI-072) antes do marco de 02/10; na Sprint 3, reservar o período de homologação antes da entrega de 24/11. | Equipe completa | Marco em risco na revisão de sprint |
| R09 | **Mitigar** | Manter os itens P1 como opcionais (conforme a EAP); toda mudança de escopo passa pela gerente antes de entrar no backlog. | Natália (GP) | PBI novo adicionado fora do planejamento da sprint |
| R10 | **Mitigar** | Contrato OpenAPI primeiro, com dados simulados para os frontends (PBI-006); coordenação técnica semanal entre os líderes. | Marcela / Júlia / Natália | Endpoint divergente do contrato ou frente bloqueada > 2 dias |
| R11 | **Mitigar** | Testar em 2 dispositivos Android diferentes (orçamento D1); tratar permissões negadas com mensagem que oriente o técnico. | Rodrigo / Felipe | Falha de câmera, QR Code ou GPS em algum dispositivo de teste |
| R12 | **Mitigar** | Validação de obrigatórios no mobile (PBI-040), componentes de resposta por tipo de item (PBI-036) e revisão do supervisor (PBI-057). | Natália / Rodrigo (Mobile) e Carol (Web) | Inspeções reprovadas por dados incompletos |

---

## 8. Reserva de Contingência

A **reserva de contingência de R$ 14.740,00** do Orçamento (Aula 05), equivalente a **~7,8% dos custos diretos e 7,2% do total geral**, é igual ao VME total calculado na seção 6. Os riscos que mais pesam na reserva são:

| Risco | VME (R$) | Uso previsto da reserva |
|---|---:|---|
| R01 — Sincronização offline | 5.600,00 | Retrabalho e testes adicionais de sincronização/idempotência |
| R04 — Subestimação de esforço | 2.000,00 | Horas adicionais nos pacotes de checklist dinâmico e construtor de modelos |
| R03 — Autenticação/sessão | 1.500,00 | Correções de segurança e ajustes de autorização |
| R10 — Integração entre frentes | 1.000,00 | Retrabalho de integração entre API, Web e Mobile |
| Demais riscos (R02, R05–R09, R11, R12) | 4.640,00 | Retrabalho pontual caso ocorram |
| **Total** | **14.740,00** | |

---

## 9. Considerações Finais

- A análise identificou **12 riscos**, sendo **1 crítico** (R01 — sincronização offline), **5 altos** (R02, R03, R05, R08, R10) e **6 moderados** (R04, R06, R07, R09, R11, R12), todos descritos no formato **causa → risco → consequência** e cobrindo os riscos registrados no TAP.
- O risco crítico converge com as conclusões da **Análise da Qualidade (Aula 05)**, reforçando a coerência entre os artefatos do FieldOps.
- A análise quantitativa (VME) dimensiona a reserva de contingência do orçamento, ligando riscos e custos.
- As respostas priorizam **prevenção e mitigação** dos riscos de maior severidade, com **gatilhos de monitoramento** objetivos vinculados aos indicadores já definidos (ex.: LSC de falhas de sincronização).
- Este registro de riscos deverá ser **monitorado no processo 11.6 — Controlar os riscos** ao longo das sprints, revisando probabilidades, impactos e a eficácia das respostas, e registrando eventuais riscos residuais e novos riscos.
