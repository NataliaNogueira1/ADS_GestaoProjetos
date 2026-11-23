# Gerenciamento das Aquisições do Projeto — FieldOps

> **Disciplina:** Gestão de Projetos — 4º semestre ADS
> **Professor:** Me. Deivison S. Takatu
> **Aula 08:** Aquisições e Partes Interessadas — Atividade de Aquisições
> **Projeto:** FieldOps — Plataforma de Inspeção em Campo
> **Equipe:** 404 Not Found
> **Data:** 23/10/2026

---

## 1. Objetivo

Este documento apresenta o **Gerenciamento das Aquisições do Projeto FieldOps**, elaborado conforme o processo de **Gerenciamento das Aquisições do Projeto** (PMBOK, área 12): planejar o gerenciamento das aquisições, conduzir as aquisições, controlar as aquisições e encerrar as aquisições.

A tabela de aquisições detalha **o que precisa ser contratado ou adquirido**, apresentando para cada item: urgência, motivo, fornecedores em potencial, quantidade, custo unitário, custo total e o responsável pela aquisição. As estimativas têm como base o Orçamento do Projeto, cuja linha de base autorizada é de **R$ 204.000,00**, e os demais artefatos já produzidos pela equipe.

---

## 2. Planejamento das Aquisições

Antes de conduzir as aquisições, foram observadas as seguintes etapas do processo (PMBOK 12.1):

- **Detalhar as características** da solução a ser contratada para cada item.
- **Preparar uma estimativa** de custo para compor o orçamento.
- **Divulgar a oportunidade** de contratação e identificar fornecedores qualificados.
- **Receber e avaliar propostas** dos fornecedores em potencial.

### 2.1 Escala de urgência

| Nível | Classificação | Descrição | Momento necessário |
|:--:|---|---|---|
| **5** | Muito Alta | Item bloqueador crítico — sem ele o sistema/demonstração não funciona. | Antes/no início da Sprint 1 |
| **4** | Alta | Necessário logo no início de uma frente de desenvolvimento. | Início da Sprint 1 |
| **3** | Média | Necessário ao longo do desenvolvimento, mas com alternativa temporária. | Durante a Sprint 1 / início da Sprint 2 |
| **2** | Baixa | Necessário apenas em fases finais (demonstração/entrega). | Sprint 2 / fechamento |
| **1** | Muito Baixa | Item acessório, sem impacto no andamento do projeto. | Quando conveniente |

---

## 3. Tabela de Gerenciamento das Aquisições — FieldOps

> Estrutura conforme o modelo da disciplina. **Cód. EAP** = pacote de trabalho ou subentrega da [EAP](../Aula%2003%20-%2021.08.2026/aula03-EAP.pdf) (Aula 03) atendido pelo item. **Cód. orçamento** = item correspondente no [Orçamento](../Aula%2005%20-%2004.09.2026/aula05-orcamento-custos.md) (Aula 05): **B** = Infraestrutura e Nuvem · **C** = Ferramentas e Licenças · **D** = Equipamentos e Materiais. Legenda de período em Qtde: **mês** = assinatura mensal durante os ~2 meses do projeto · **un** = unidade · **lic** = licença por integrante.

| ID | Cód. EAP | Cód. orçamento | Item a ser adquirido | Urgência | Motivo da Decisão de Compra | Fornecedores potenciais | Qtde | Custo unitário | Custo total | Previsão entrega | Observações |
|:--:|:--:|:--:|---|---|---|---|:--:|---:|---:|---|---|
| 1 | 4.1.1 | B1 | Servidor de aplicação (hospedagem da API Spring Boot) | 5-Muito Alta | Necessário para hospedar a API e viabilizar os testes integrados e a demo ponta a ponta. | AWS, Google Cloud, Render, Railway | 2 mês | R$ 180,00 | R$ 360,00 | Sprint 1 | Responsável: Júlia (PBI-070, PBI-072) |
| 2 | 4.1.2 | B2 | Banco de dados PostgreSQL gerenciado | 5-Muito Alta | Necessário para persistir os dados de usuários, clientes, equipamentos e inspeções. | AWS RDS, Supabase, Neon, Railway | 2 mês | R$ 150,00 | R$ 300,00 | Sprint 1 | Responsável: Marcela (PBI-004) |
| 3 | 4.1.3 | B3 | Armazenamento de objetos (evidências/fotos) | 3-Média | Necessário para guardar as fotografias de evidência e de não conformidades. | AWS S3, Cloudflare R2, Backblaze B2 | 2 mês | R$ 90,00 | R$ 180,00 | Sprint 1 | Responsável: Júlia (PBI-042, PBI-043) |
| 4 | 4.1 | B4 | Domínio e certificado SSL | 3-Média | Necessário para acesso seguro (HTTPS) ao painel web e à API. | Registro.br, GoDaddy, Cloudflare | 1 ano | R$ 120,00 | R$ 120,00 | Sprint 1 | Responsável: Júlia |
| 5 | 4.1 | B5 | Serviço de notificações push | 2-Baixa | Necessário para notificar técnicos de nova atribuição e de prazos (funcionalidade P1). | Firebase Cloud Messaging, Expo Push, OneSignal | 2 mês | R$ 60,00 | R$ 120,00 | Sprint 3 | Responsável: Marcela (PBI-075) |
| 6 | 4.2.1 | B6 | Pipeline CI/CD (build e deploy) | 3-Média | Necessário para automatizar build, testes e publicação. | GitHub Actions, GitLab CI, CircleCI | 2 mês | R$ 80,00 | R$ 160,00 | Sprint 1 | Responsável: Júlia (PBI-005, PBI-069) |
| 7 | 4.1.4 | B7 | Ambiente de homologação/testes | 3-Média | Necessário para validar a integração antes da demo e reduzir o risco de indisponibilidade. | AWS, Google Cloud, Render | 2 mês | R$ 120,00 | R$ 240,00 | Sprint 1 | Responsável: Marcela (risco R02) |
| 8 | 2.1 / 3.1 | C1 | Licença Figma (design/protótipo) | 4-Alta | Necessário para prototipar a UI/UX e as telas antes do desenvolvimento. | Figma | 2 mês | R$ 75,00 | R$ 150,00 | Sprint 1 | Responsável: Andressa |
| 9 | 4.2.4 | C2 | Conta Expo (Expo Build/EAS) — plano gratuito | 4-Alta | Necessária para gerar o APK Android de demonstração pelo Expo Build. O plano gratuito inclui até 15 builds Android por mês. | Expo | 1 conta | R$ 0,00 | R$ 0,00 | Sprint 1 | Responsável: Rodrigo (PBI-002, PBI-068); fila de baixa prioridade, disparar builds com antecedência |
| 10 | 5.3.1 | C3 | Ferramenta de gestão de projeto (board/backlog) | 4-Alta | Necessário para acompanhar o backlog e os cards (PBIs) como fonte única da verdade. | GitHub Projects, Jira, Trello | 2 mês | R$ 50,00 | R$ 100,00 | Sprint 1 | Responsável: Natália |
| 11 | 1 / 2 / 3 | C4 | IDEs e plugins premium | 3-Média | Necessário para a produtividade no desenvolvimento das três frentes. | JetBrains, VS Code, Cursor | 9 lic | R$ 40,00 | R$ 360,00 | Sprint 1 | Responsável: Equipe completa |
| 12 | 1.1.2 / 1.1.3 | C5 | Ferramenta de testes de API | 3-Média | Necessário para validar os endpoints e o contrato OpenAPI. | Postman, Insomnia, Bruno | 2 mês | R$ 60,00 | R$ 120,00 | Sprint 1 | Responsável: Lucas (PBI-006, PBI-071) |
| 13 | 3.4 / 4.3.1 | D1 | Dispositivo Android para testes de campo | 4-Alta | Necessário para testar o app mobile, QR Code, GPS e o fluxo offline em campo. | Samsung, Motorola, Xiaomi | 2 un | R$ 900,00 | R$ 1.800,00 | Sprint 1 | Responsável: Equipe Mobile (PBI-041, PBI-045, PBI-048) |
| 14 | 3.4.1 | D2 | Impressão de etiquetas QR Code para equipamentos | 3-Média | Necessário para a identificação única de equipamentos na inspeção. | Gráfica local, Pimaco | 100 un | R$ 1,20 | R$ 120,00 | Sprint 1 | Responsável: Natália (PBI-016) |
| 15 | 4.3.3 | D3 | Material de transporte para visita de campo (demo) | 2-Baixa | Necessário para o deslocamento à validação e demonstração em campo. | Uber, transporte próprio | 2 visita | R$ 50,00 | R$ 100,00 | Sprint 2 | Responsável: Equipe |
| 16 | 5.4 | D4 | Impressão de documentação e material de apresentação | 2-Baixa | Necessário para o material impresso da entrega final. | Gráfica local | 1 pacote | R$ 80,00 | R$ 80,00 | Sprint 3 | Responsável: Natália |
| | | | | | | | | **TOTAL** | **R$ 4.310,00** | | |

---

## 4. Resumo das Aquisições

| Categoria | Total (R$) | Nº de itens |
|---|---:|:--:|
| Infraestrutura e Nuvem | 1.480,00 | 7 |
| Ferramentas e Licenças | 730,00 | 5 |
| Equipamentos e Materiais | 2.100,00 | 4 |
| **TOTAL DAS AQUISIÇÕES** | **4.310,00** | **16** |

> O total de aquisições externas (**R$ 4.310,00**) corresponde a cerca de **2,1%** da linha de base de custos de R$ 204.000,00, coerente com o orçamento do projeto, em que os Recursos Humanos concentram 90,7% do investimento.

---

## 5. Condução das Aquisições

Na seleção de fornecedores e na adjudicação dos contratos, serão avaliados os seguintes elementos (PMBOK 12.2):

- **Preços e condições de pagamento** — priorizar planos mensais sem fidelidade longa, dado o prazo de ~2 meses.
- **Critérios de inspeção, qualidade e aceitação** — SLA de disponibilidade para serviços de nuvem (mitiga o risco R02).
- **Garantia e suporte futuro ao produto** — suporte técnico dos serviços gerenciados.
- **Incentivos e penalidades** — créditos por indisponibilidade (SLA).
- **Seguros e obrigações de realização** — não aplicável ao contexto acadêmico.
- **Cláusula de rescisão** — preferência por serviços canceláveis a qualquer momento.

---

## 6. Controle das Aquisições

Após contratar os fornecedores, o desempenho de cada um será monitorado em relação ao contrato (PMBOK 12.3):

- Acompanhar o **consumo e os custos** dos serviços de nuvem ao longo das sprints, comparando com o orçado.
- Verificar o **SLA de disponibilidade** dos ambientes de aplicação, banco e homologação (gatilho do risco R02: indisponibilidade > 1h em homologação).
- Validar que as **licenças e ferramentas** adquiridas estão ativas para toda a equipe.
- Registrar mudanças e correções de contrato quando necessário.

---

## 7. Encerramento das Aquisições

Ao final do projeto (PMBOK 12.4):

- **Cancelar as assinaturas mensais** de nuvem e ferramentas após a entrega final (marco de 24/11/2026, fim da Sprint 3).
- **Confirmar o encerramento** de cada contrato e a quitação de pagamentos.
- **Arquivar** os comprovantes e documentar as aquisições realizadas na pasta `docs/` do repositório do projeto FieldOps (pacote 5.4.2 da EAP).

---

## 8. Considerações Finais

- Foram mapeadas **16 aquisições** externas, distribuídas em 3 categorias, totalizando **R$ 4.310,00**, em total aderência ao orçamento do projeto.
- As aquisições de **urgência muito alta (nível 5)** — servidor de aplicação e banco PostgreSQL — são as únicas **bloqueadoras**: sem elas o sistema não funciona, e por isso devem ser providenciadas antes ou no início da Sprint 1.
- As aquisições de **urgência alta (nível 4)** — Figma, conta Expo, board de gestão e dispositivos Android — não bloqueiam o sistema, mas são necessárias logo no início das frentes de desenvolvimento, na Sprint 1.
- A escolha por **serviços gerenciados com SLA** apoia diretamente a resposta ao risco **R02 (indisponibilidade dos serviços de nuvem de terceiros)** do registro de riscos do projeto.
- Este documento constitui o **plano de aquisições** do FieldOps e deverá ser monitorado nos processos *12.3 — Controlar as aquisições* e *12.4 — Encerrar as aquisições* ao longo e ao final do projeto.
