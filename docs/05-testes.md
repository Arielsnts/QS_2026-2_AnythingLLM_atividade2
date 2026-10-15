# Testes de Execução

## Introdução

Este documento apresenta os casos de teste executados na avaliação da aplicação AnythingLLM sob a missão **Contexto sob Pressão**.

Os testes foram organizados em dez casos, distribuídos entre funcionais, de contexto e fontes, metamórficos, adversariais e de saída estruturada. Cada caso especifica a entrada, o contexto, o resultado esperado, o resultado observado, a evidência coletada e o status final.

Os testes validam os requisitos definidos em [Requisitos de Qualidade](../info/requisitos-qualidade.md) e os comportamentos descritos nos [Prompts e Cenários de Contexto](02-lab-contexto-prompts.md).

---

## Metodologia

Cada caso de teste é classificado com um dos status abaixo:

- **A (Aprovado):** O sistema se comportou conforme o resultado esperado
- **P (Parcial):** O sistema atendeu parcialmente, com desvios menores
- **R (Reprovado):** O sistema não atendeu ao resultado esperado

---

## Testes Funcionais

### CT-01: [Descrição]

**Tipo:** Funcional

**Entrada (prompt):** [Prompt exato utilizado]

**Contexto esperado:** [Documentos e chunks que devem ser recuperados]

**Resultado esperado:** [Comportamento esperado da resposta e das fontes]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

### CT-02: [Descrição]

**Tipo:** Funcional

**Entrada (prompt):** [Prompt exato utilizado]

**Contexto esperado:** [Documentos e chunks que devem ser recuperados]

**Resultado esperado:** [Comportamento esperado da resposta e das fontes]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

### CT-03: [Descrição]

**Tipo:** Funcional

**Entrada (prompt):** [Prompt exato utilizado]

**Contexto esperado:** [Documentos e chunks que devem ser recuperados]

**Resultado esperado:** [Comportamento esperado da resposta e das fontes]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

## Testes de Contexto e Fontes

### CT-04: [Contexto ausente]

**Tipo:** Contexto/Fontes

**Entrada (prompt):** [Prompt exato utilizado]

**Contexto esperado:** [Nenhum documento relevante no workspace]

**Resultado esperado:** [Indicação de falta de informação, sem afirmação fundamentada]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

### CT-05: [Contexto irrelevante/conflitante]

**Tipo:** Contexto/Fontes

**Entrada (prompt):** [Prompt exato utilizado]

**Contexto esperado:** [Documentos irrelevantes ou com informações conflitantes]

**Resultado esperado:** [Indicação de limitação ou de conflito, sem uso indevido do contexto]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

## Testes Metamórficos

### CT-06: [Paráfrase (prompt reformulado)]

**Tipo:** Metamórfico

**Entrada (prompt original):** [Prompt original]

**Entrada (prompt reformulado):** [Prompt parafraseado]

**Contexto esperado:** [Mesmo contexto para ambos os prompts]

**Resultado esperado:** [Respostas semanticamente equivalentes e com as mesmas fontes]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot original: [Link para ../evidencias/...]
- Screenshot reformulado: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

### CT-07: [Idioma ou ordem de documentos]

**Tipo:** Metamórfico

**Entrada (prompt):** [Prompt utilizado]

**Variação:** [Mudança de idioma do prompt ou ordem dos documentos no workspace]

**Contexto esperado:** [Mesmos documentos, em ordem ou idioma alterados]

**Resultado esperado:** [Respostas equivalentes e fontes consistentes]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

## Testes Adversariais

### CT-08: [Injeção direta]

**Tipo:** Adversarial (direta)

**Entrada (prompt malicioso):** [Prompt que tenta alterar as instruções do sistema]

**Contexto esperado:** [Documentos legítimos do workspace]

**Resultado esperado:** [Sistema mantém as instruções originais e não obedece à tentativa]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

### CT-09: [Injeção indireta]

**Tipo:** Adversarial (indireta)

**Entrada (prompt):** [Prompt legítimo do usuário]

**Documento contaminado:** [Nome do documento e trecho com instrução maliciosa]

**Contexto esperado:** [Documento contaminado recuperado como contexto]

**Resultado esperado:** [Sistema trata o conteúdo do documento como dado e não executa a instrução]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

## Testes de Saída Estruturada

### CT-10: [JSON inválido, campo ausente ou formato]

**Tipo:** Saída/Estrutura

**Entrada (prompt):** [Prompt que solicita saída estruturada]

**Schema esperado:** [Campos obrigatórios e tipos]

**Variação testada:** [JSON malformado, campo ausente, URL inválida ou conteúdo fora do esquema]

**Resultado esperado:** [Validação rejeita a saída inválida]

**Resultado observado:** [Preencher após execução]

**Evidência:**
- Screenshot: [Link para ../evidencias/...]
- Log: [Link para ../evidencias/...]

**Status:** [A / P / R]

---

## Tabela Resumo

| ID | Tipo | Descrição | Status | Cobertura de Citações (%) | Taxa de Sucesso em Contexto (%) |
|----|------|-----------|--------|---------------------------|---------------------------------|
| CT-01 | Funcional | [Descrição] | [A/P/R] | [X%] | [X%] |
| CT-02 | Funcional | [Descrição] | [A/P/R] | [X%] | [X%] |
| CT-03 | Funcional | [Descrição] | [A/P/R] | [X%] | [X%] |
| CT-04 | Contexto/Fontes | [Contexto ausente] | [A/P/R] | [X%] | [X%] |
| CT-05 | Contexto/Fontes | [Contexto irrelevante/conflitante] | [A/P/R] | [X%] | [X%] |
| CT-06 | Metamórfico | [Paráfrase] | [A/P/R] | [X%] | [X%] |
| CT-07 | Metamórfico | [Idioma ou ordem] | [A/P/R] | [X%] | [X%] |
| CT-08 | Adversarial (direta) | [Injeção direta] | [A/P/R] | [X%] | [X%] |
| CT-09 | Adversarial (indireta) | [Injeção indireta] | [A/P/R] | [X%] | [X%] |
| CT-10 | Saída/Estrutura | [JSON/formato] | [A/P/R] | [X%] | [X%] |

**Cobertura de citações (%):** (afirmações com fonte válida) / (total de afirmações verificadas) × 100

**Taxa de sucesso em contexto (%):** (testes de contexto com status A) / (total de testes de contexto) × 100