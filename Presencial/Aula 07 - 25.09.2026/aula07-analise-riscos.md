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

A análise usa como base os artefatos já produzidos pela equipe — o **Termo de Abertura do Projeto (TAP)**, o **Cronograma**, o **Orçamento** (linha de base de R$ 204.000,00) e a **Análise da Qualidade** — em que a **sincronização offline** foi identificada como o ponto mais crítico do sistema.

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
| 4 | Alto | 0,40 | Atraso de 1 sprint | 7–15% do orçamento | Redução relevante do escopo |
| 5 | Muito alto | 0,80 | Inviabiliza a entrega | > 15% do orçamento | Produto final inutilizável |

### 2.3 Matriz de Severidade (Probabilidade x Impacto)

A severidade é calculada por **Probabilidade × Impacto** e classificada por faixa de cor:

| P \ I | 0,05 (MB) | 0,10 (B) | 0,20 (M) | 0,40 (A) | 0,80 (MA) |
|:---:|:---:|:---:|:---:|:---:|:---:|
| **0,90 (MA)** | 🟢 0,05 | 🟡 0,09 | 🟠 0,18 | 🔴 0,36 | 🔴 0,72 |
| **0,70 (A)** | 🟢 0,04 | 🟡 0,07 | 🟠 0,14 | 🔴 0,28 | 🔴 0,56 |
| **0,50 (M)** | 🟢 0,03 | 🟡 0,05 | 🟡 0,10 | 🟠 0,20 | 🔴 0,40 |
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

### R02 — Indisponibilidade de serviço de nuvem/API externa
- **Causa:** Dependência de infraestrutura de nuvem, banco PostgreSQL gerenciado e serviço de notificações push de terceiros.
- **Risco:** A API ou os serviços de nuvem podem ficar indisponíveis durante o desenvolvimento ou a demonstração.
- **Consequência:** Bloqueio dos testes integrados, atraso no cronograma e risco de falha na demo ponta a ponta (PBI-072).

### R03 — Falha de autenticação e gestão de sessão (token)
- **Causa:** Complexidade na implementação de JWT com refresh token e autorização por perfil (PBI-007, PBI-010, PBI-012).
- **Risco:** Usuários podem perder a sessão indevidamente ou acessar recursos sem permissão.
- **Consequência:** Falhas de segurança, bloqueio de uso pelos técnicos e retrabalho de correção.

### R04 — Subestimação de esforço nos pacotes de maior incerteza
- **Causa:** Estimativas de três pontos apontaram alta variação em sincronização offline, construtor de modelos e checklist dinâmico.
- **Risco:** O esforço real desses pacotes pode ultrapassar o estimado.
- **Consequência:** Estouro de horas, consumo da reserva de contingência (R$ 14.605,00) e pressão sobre o prazo das sprints.

### R05 — Indisponibilidade de membros da equipe
- **Causa:** Equipe acadêmica de 9 integrantes conciliando o projeto com outras disciplinas; concentração de conhecimento em poucas pessoas.
- **Risco:** Um ou mais integrantes podem ficar indisponíveis em momentos críticos das sprints.
- **Consequência:** Sobrecarga dos demais, atraso de PBIs dependentes e perda de conhecimento (bus factor).

### R06 — Defeitos em checklists com muitos itens
- **Causa:** Correlação positiva identificada na Aula 05 — quanto mais itens no checklist, mais defeitos por inspeção.
- **Risco:** Modelos de inspeção grandes podem apresentar mais falhas de validação e desempenho no mobile.
- **Consequência:** Não conformidades não detectadas, reprovação de inspeções e insatisfação do cliente.

### R07 — Falha no upload de evidências (fotos)
- **Causa:** Instabilidade de rede e ausência de tratamento robusto de foto pendente (PBI-044).
- **Risco:** Fotografias podem não ser enviadas ou ficar desvinculadas do item correto.
- **Consequência:** Inspeções sem comprovação de não conformidade, comprometendo a auditoria e a qualidade da entrega.

### R08 — Atraso na build/entrega para demonstração
- **Causa:** Concentração de tarefas de fechamento (seed, Docker, build APK, demo) no fim da Sprint 2, próximo aos marcos.
- **Risco:** Os builds de demonstração (APK Android e painel web) podem não ficar prontos a tempo.
- **Consequência:** Comprometimento dos marcos "MVP funcional P0" (28/09) e "Entrega final com P1" (02/10).

---

## 5. Análise Qualitativa e Quantitativa

Priorização por severidade (P × I), do maior para o menor:

| ID | Risco | Prob. | Impacto | Severidade (P×I) | Classificação |
|---|---|:---:|:---:|:---:|:---:|
| R01 | Perda na sincronização offline | 0,70 | 0,80 | **0,56** | 🔴 Crítico |
| R03 | Falha de autenticação/sessão | 0,50 | 0,40 | **0,20** | 🟠 Alto |
| R08 | Atraso na build para demo | 0,50 | 0,40 | **0,20** | 🟠 Alto |
| R02 | Indisponibilidade de nuvem/API | 0,30 | 0,40 | **0,12** | 🟠 Alto |
| R05 | Indisponibilidade da equipe | 0,30 | 0,40 | **0,12** | 🟠 Alto |
| R04 | Subestimação de esforço | 0,50 | 0,20 | **0,10** | 🟡 Moderado |
| R06 | Defeitos em checklists grandes | 0,50 | 0,20 | **0,10** | 🟡 Moderado |
| R07 | Falha no upload de evidências | 0,30 | 0,20 | **0,06** | 🟡 Moderado |

> **Análise:** o risco **R01 (sincronização offline)** é o único **crítico** e concentra a maior atenção — coerente com a Análise da Qualidade (Aula 05), em que essa categoria liderou o Diagrama de Pareto (35% dos defeitos). Os riscos **altos** (R02, R03, R05, R08) estão ligados a dependências externas, segurança, pessoas e ao fechamento do cronograma.

---

## 6. Plano de Respostas aos Riscos

| ID | Estratégia | Ações de resposta | Responsável | Gatilho de monitoramento |
|---|---|---|---|---|
| R01 | **Mitigar** | Garantir idempotência no reenvio (PBI-052), definir regras de conflito (PBI-055), fila outbox persistente (PBI-050) e testes automatizados dos fluxos críticos (PBI-065). | Lucas / Marcela / Felipe | Taxa de falha de sync > 16% (LSC do gráfico de controle) |
| R02 | **Transferir / Mitigar** | Usar serviços gerenciados com SLA; preparar ambiente de contingência local (Docker) para a demo (PBI-070). | Júlia / Marcela | Indisponibilidade > 1h em ambiente de homologação |
| R03 | **Prevenir** | Revisão de segurança do fluxo JWT + refresh; testes de autorização por perfil; renovação automática de sessão (PBI-010). | Lucas | Erros de sessão reportados nos testes |
| R04 | **Mitigar / Aceitar** | Monitorar horas por pacote; acionar reserva de contingência (R$ 14.605,00) somente para os pacotes de maior incerteza. | Natália (GP) | Consumo de horas > 110% do estimado no pacote |
| R05 | **Mitigar** | Programação em par, documentação (READMEs — PBI-067) e distribuição de conhecimento entre frentes. | Natália (GP) | Ausência não planejada > 2 dias |
| R06 | **Mitigar** | Testes de regressão para checklists com mais de 25 itens; validação e prévia antes de publicar (PBI-022). | Equipe QA / Web | Nº de defeitos por inspeção acima da tendência |
| R07 | **Mitigar** | Marcar foto como pendente e reenviar (PBI-044); associar fotografia ao item correto (PBI-043). | Natália / Rodrigo | Fotos pendentes acumuladas na outbox |
| R08 | **Prevenir** | Antecipar o congelamento de escopo P0; ensaiar a demo ponta a ponta (PBI-072) antes do marco de 28/09. | Equipe completa | Marco de MVP em risco na revisão de sprint |

---

## 7. Reserva de Contingência

Alinhada ao Orçamento (Aula 05), a **reserva de contingência de R$ 14.605,00 (~7,7% dos custos diretos e 7,2% do total geral)** cobre principalmente os riscos de maior incerteza:

| Risco coberto | Uso previsto da reserva |
|---|---|
| R01 — Sincronização offline | Retrabalho e testes adicionais de sincronização/idempotência |
| R04 — Subestimação de esforço | Horas extras nos pacotes de checklist dinâmico e construtor de modelos |
| R03 — Autenticação/sessão | Correções de segurança e ajustes de autorização |

---

## 8. Considerações Finais

- A análise identificou **8 riscos**, sendo **1 crítico** (R01 — sincronização offline), **4 altos** (R02, R03, R05, R08) e **3 moderados** (R04, R06, R07), todos descritos no formato **causa → risco → consequência**.
- O risco crítico converge com as conclusões da **Análise da Qualidade (Aula 05)**, reforçando a coerência entre os artefatos do FieldOps.
- As respostas priorizam **prevenção e mitigação** dos riscos de maior severidade, com **gatilhos de monitoramento** objetivos vinculados aos indicadores já definidos (ex.: LSC de falhas de sincronização).
- Este registro de riscos deverá ser **monitorado no processo 11.6 — Controlar os riscos** ao longo das sprints, revisando probabilidades, impactos e a eficácia das respostas, e registrando eventuais riscos residuais e novos riscos.
