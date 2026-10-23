# Rede de Poder/Interesse — Partes Interessadas do Projeto FieldOps

> **Disciplina:** Gestão de Projetos — 4º semestre ADS
> **Professor:** Me. Deivison S. Takatu
> **Aula 08:** Aquisições e Partes Interessadas — Atividade de Partes Interessadas
> **Projeto:** FieldOps — Plataforma de Inspeção em Campo
> **Equipe:** 404 Not Found
> **Data:** 23/10/2026

---

## 1. Objetivo

Este documento apresenta a **matriz de Rede de Poder/Interesse do Projeto FieldOps**, elaborada conforme o processo de **Gerenciamento das Partes Interessadas** (PMBOK, área 13): identificar as partes interessadas, planejar o gerenciamento das partes interessadas, gerenciar o engajamento e controlar o engajamento.

As partes interessadas são classificadas segundo seu **poder** (capacidade de influenciar decisões e recursos do projeto) e seu **interesse** (grau de preocupação com os resultados do projeto), resultando em quatro estratégias de engajamento: **monitorar**, **manter informado**, **manter satisfeito** e **gerenciar com atenção**.

A análise toma como base os artefatos de planejamento já produzidos pela equipe — o TAP, o organograma, o plano de comunicação, a matriz RACI e o registro de riscos do projeto.

---

## 2. Identificação das Partes Interessadas

| # | Parte interessada | Tipo | Poder | Interesse | Principal expectativa |
|---|---|---|:--:|:--:|---|
| PI-01 | Fundação Toyota do Brasil (Patrocinador) | Externa | Alto | Alto | Retorno do investimento de R$ 204.000,00 e MVP entregue no prazo |
| PI-02 | Cliente / Product Owner | Externa | Alto | Alto | Valor entregue e aderência aos requisitos de negócio |
| PI-03 | Professor / Orientador | Externa | Alto | Alto | Evolução acadêmica, qualidade e cumprimento das entregas |
| PI-04 | Natália — Gerente de Projeto | Interna | Alto | Alto | Projeto dentro de prazo, custo e escopo; sucesso do MVP |
| PI-05 | Líderes de área (Marcela, Júlia, Natália) | Interna | Médio/Alto | Alto | Coordenação técnica e integração entre frentes |
| PI-06 | Equipe de desenvolvimento (Lucas, Andressa, Carol, Ian, Rodrigo, Felipe) | Interna | Baixo | Alto | Tarefas claras, dúvidas resolvidas e entregas concluídas |
| PI-07 | Técnicos de campo (usuários finais do app) | Externa | Baixo | Alto | App funcional, confiável e com bom uso offline |
| PI-08 | Administradores/Revisores (usuários do painel web) | Externa | Médio | Alto | Painel ágil para cadastro, revisão e aprovação de inspeções |
| PI-09 | Fornecedores de nuvem e serviços (AWS, Figma, etc.) | Externa | Médio | Baixo | Contratação dos serviços e pagamentos em dia |
| PI-10 | Órgãos regulamentadores | Externa | Alto | Baixo | Conformidade legal e de normas de inspeção |
| PI-11 | Instituição de ensino (SENAI) | Externa | Médio | Médio | Reputação acadêmica e aderência à metodologia PBL |
| PI-12 | Comunidade / demais colegas de turma | Externa | Baixo | Baixo | Acompanhamento do projeto como referência |

---

## 3. Matriz de Rede de Poder/Interesse

A matriz cruza **poder** (eixo vertical) com **interesse** (eixo horizontal), definindo a estratégia de engajamento de cada quadrante:

```
       ALTO  ┌──────────────────────────┬──────────────────────────┐
             │                          │                          │
             │     MANTER SATISFEITO    │   GERENCIAR COM ATENÇÃO   │
             │                          │                          │
    P        │  PI-10 Órgãos regul.     │  PI-01 Patrocinador       │
    O        │                          │  PI-02 Cliente / PO       │
    D        │                          │  PI-03 Professor          │
    E        │                          │  PI-04 Gerente (Natália)  │
    R        ├──────────────────────────┼──────────────────────────┤
             │                          │                          │
             │        MONITORAR         │     MANTER INFORMADO      │
             │                          │                          │
             │  PI-12 Comunidade        │  PI-05 Líderes de área    │
             │  PI-09 Fornecedores*     │  PI-06 Equipe de dev      │
             │  PI-11 Instituição*      │  PI-07 Técnicos de campo  │
             │                          │  PI-08 Admin/Revisores    │
       BAIXO └──────────────────────────┴──────────────────────────┘
              BAIXO                          ALTO
                             INTERESSE
```

> *\*PI-09 (Fornecedores) e PI-11 (Instituição) têm poder médio e interesse de médio a baixo; foram posicionados na faixa limítrofe entre "Monitorar" e "Manter satisfeito/informado" e são tratados com o esforço de engajamento correspondente ao quadrante mais próximo.*

### 3.1 Versão em diagrama

```mermaid
quadrantChart
    title Rede de Poder/Interesse - FieldOps
    x-axis Baixo Interesse --> Alto Interesse
    y-axis Baixo Poder --> Alto Poder
    quadrant-1 Gerenciar com atencao
    quadrant-2 Manter satisfeito
    quadrant-3 Monitorar
    quadrant-4 Manter informado
    Patrocinador (Toyota): [0.85, 0.92]
    Cliente / PO: [0.88, 0.85]
    Professor: [0.80, 0.82]
    Gerente (Natalia): [0.90, 0.88]
    Orgaos regulamentadores: [0.20, 0.80]
    Lideres de area: [0.82, 0.68]
    Equipe de dev: [0.78, 0.25]
    Tecnicos de campo: [0.85, 0.22]
    Admin / Revisores: [0.80, 0.45]
    Fornecedores: [0.25, 0.50]
    Instituicao (SENAI): [0.50, 0.52]
    Comunidade: [0.20, 0.20]
```

---

## 4. Estratégias de Engajamento por Quadrante

### 4.1 🔴 Gerenciar com atenção (Alto poder · Alto interesse)
> Partes interessadas mais importantes — devem ser plenamente engajadas e satisfeitas.

| Parte interessada | Estratégia de engajamento | Canal |
|---|---|---|
| PI-01 Patrocinador (Toyota) | Relatórios de status e demonstrações do valor entregue; alinhamento de investimento e prazo | Relatório quinzenal (e-mail) + demo por sprint |
| PI-02 Cliente / PO | Validação contínua das entregas, priorização do backlog e aprovação do MVP | Reunião + e-mail; demo de sprint (Meet) |
| PI-03 Professor / Orientador | Apresentação da evolução e das entregas acadêmicas | Reunião + repositório GitHub |
| PI-04 Gerente de Projeto (Natália) | Condução integral do projeto, coordenação das frentes e das cerimônias | Todos os canais |

### 4.2 🟠 Manter satisfeito (Alto poder · Baixo interesse)
> Pouco interesse no dia a dia, mas alto poder — manter satisfeitas sem sobrecarregar com detalhes.

| Parte interessada | Estratégia de engajamento | Canal |
|---|---|---|
| PI-10 Órgãos regulamentadores | Garantir conformidade legal/normativa das inspeções; acionar somente quando necessário | Comunicação formal pontual |

### 4.3 🟡 Manter informado (Baixo poder · Alto interesse)
> Muito interessadas, baixo poder — manter bem informadas e engajadas.

| Parte interessada | Estratégia de engajamento | Canal |
|---|---|---|
| PI-05 Líderes de área | Alinhamento técnico e de integração entre Backend, Web e Mobile | Coordenação técnica semanal (Meet/GitHub) |
| PI-06 Equipe de desenvolvimento | Backlog claro, dailies, resolução de dúvidas e revisão de código | WhatsApp + GitHub (Issues/PR) |
| PI-07 Técnicos de campo (usuários) | Coletar feedback de usabilidade do app e do fluxo offline | Testes de campo + demonstrações |
| PI-08 Administradores/Revisores | Feedback sobre o painel de cadastro, revisão e aprovação | Demonstrações + homologação |

### 4.4 🟢 Monitorar (Baixo poder · Baixo interesse)
> Acompanhar com esforço mínimo, sem comunicação intensa.

| Parte interessada | Estratégia de engajamento | Canal |
|---|---|---|
| PI-09 Fornecedores de serviços | Acompanhar contratos, SLA e pagamentos (ligado ao risco R02 e às aquisições) | Portais dos fornecedores |
| PI-11 Instituição de ensino (SENAI) | Manter aderência à metodologia PBL e disponibilizar o repositório | Repositório + entregas |
| PI-12 Comunidade / colegas | Compartilhar resultados ao final, sem comunicação dedicada | Repositório público |

---

## 5. Técnica Analítica — Nível de Engajamento

Classificação do engajamento **atual (C)** e **desejado (D)** das principais partes interessadas, conforme a técnica analítica das partes interessadas (desinformado, resistente, neutro, dá apoio, lidera):

| Parte interessada | Desinformado | Resistente | Neutro | Dá apoio | Lidera |
|---|:--:|:--:|:--:|:--:|:--:|
| PI-01 Patrocinador (Toyota) | | | | C | D |
| PI-02 Cliente / PO | | | C | D | |
| PI-03 Professor / Orientador | | | | C → D | |
| PI-04 Gerente (Natália) | | | | | C/D |
| PI-05 Líderes de área | | | | | C/D |
| PI-06 Equipe de desenvolvimento | | | | C/D | |
| PI-07 Técnicos de campo | C | | D | | |
| PI-08 Admin/Revisores | C | | D | | |

> **Legenda:** **C** = engajamento atual · **D** = engajamento desejado. As lacunas (ex.: técnicos de campo e revisores ainda desinformados) direcionam ações de engajamento, como demonstrações e coleta de feedback.

---

## 6. Considerações Finais

- Foram identificadas **12 partes interessadas** e posicionadas na **Rede de Poder/Interesse**, resultando em quatro estratégias de engajamento.
- O quadrante **"Gerenciar com atenção"** concentra Patrocinador, Cliente/PO, Professor e Gerente de Projeto — os atores de maior poder e interesse, que recebem comunicação mais frequente e formal.
- A matriz está **alinhada ao plano de comunicação do projeto**: cada estratégia de engajamento reutiliza os canais e frequências ali definidos (relatório quinzenal ao cliente, demos por sprint, coordenação técnica semanal, etc.).
- O engajamento dos **fornecedores** conecta-se diretamente ao **gerenciamento das aquisições** e ao risco **R02 (indisponibilidade de nuvem/API)** do registro de riscos do projeto.
- Este documento deverá ser **monitorado no processo 13.4 — Controlar o engajamento das partes interessadas**, ajustando a classificação e as estratégias conforme o projeto evolui.
