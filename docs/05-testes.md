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

### CT-01: Extração direta de metas financeiras com contexto indexado

**Tipo:** Funcional

**Entrada (prompt):** Objetivo: identificar as metas de crescimento financeiro da empresa para 2026. Contexto: utilize o manual fornecido como fonte de informação. Restrições: responda com base nos dados apresentados no documento. Formato: liste a receita líquida, a margem líquida e a margem bruta com seus respectivos valores.

**Contexto esperado:** Manual-Organizacional.pdf (Empresa Exemplo S.A., v1.0), com recuperação da seção 5.1 (Crescimento financeiro).

**Resultado esperado:** A resposta apresenta receita líquida de R$ 55 milhões, margem líquida de 15% e margem bruta de 43%, no formato de lista solicitado, e a interface indica o manual como fonte (RQ-01 e RQ-02).

**Resultado observado:** O sistema (gemini-3.5-flash) listou os três valores corretos: receita líquida de R$ 55 milhões, margem líquida de 15% e margem bruta de 43%, no formato pedido. O painel de Fontes exibiu Manual-Organizacional.pdf (referência a 1). O texto da resposta não indicou seção nem página do documento. Tempo de raciocínio exibido pela interface: 4,1 s.

**Evidência:**
- Screenshot: [ct01-resposta-com-fonte.png](../evidencias/testes-execucao/ct01-resposta-com-fonte.png)
- Log: não coletado; evidência registrada por screenshot

**Status:** A

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

### CT-04: Contexto ausente (metas de água e resíduos)

**Tipo:** Contexto/Fontes

**Entrada (prompt):** Quais são as metas de consumo de água e de redução de resíduos da empresa para o ano fiscal de 2026? Indique os valores e a fonte.

**Contexto esperado:** Manual-Organizacional.pdf com a seção 5.4 (Sustentabilidade), que traz apenas metas de redução de emissões de carbono e de energia renovável. O documento não contém metas de água nem de resíduos.

**Resultado esperado:** O sistema indica que o documento não traz metas de água e de resíduos, sem inventar valores. Citar as metas de carbono e energia como informação relacionada é aceitável, desde que não sejam apresentadas como resposta à pergunta (RQ-03).

**Resultado observado:** O sistema (gemini-3.5-flash-lite) informou que, com base no Manual Organizacional, não há menção a metas de consumo de água nem de redução de resíduos para 2026. Em seguida, explicou que a seção 5.4 aborda apenas redução de emissões de carbono (15% em 2026; 10% em 2025) e energia de fontes renováveis (70% em 2026; 50% em 2025). Os valores citados conferem com o manual. Não houve valores inventados, e os dados relacionados foram apresentados como o conteúdo da seção, não como resposta à pergunta.

**Evidência:**
- Screenshot: [ct04-contexto-ausente.png](../evidencias/testes-execucao/ct04-contexto-ausente.png)
- Log: não coletado; evidência registrada por screenshot

**Status:** A

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

### CT-06: Paráfrase (meta de NPS para 2026)

**Tipo:** Metamórfico

**Entrada (prompt original):** Qual é a meta de NPS da empresa para 2026?

**Entrada (prompt reformulado):** Que nota de satisfação dos clientes a empresa pretende alcançar em 2026?

**Contexto esperado:** Mesmo contexto para ambos os prompts: Manual-Organizacional.pdf, seção 5.2 (Clientes e mercado).

**Resultado esperado:** As duas respostas informam NPS 75 e apontam o manual como fonte, sem contradição entre elas.

**Resultado observado:** Ambas as respostas (gemini-3.5-flash-lite) informaram NPS 75 para 2026, sem confundir com o valor de 2025 (70). No prompt original, a resposta citou o Manual Organizacional no próprio texto. No prompt reformulado, que não usa a sigla NPS, o sistema associou "nota de satisfação dos clientes" ao NPS e deu o mesmo valor; nele a fonte apareceu pelo indicador Fontes, sem menção ao manual no texto. As respostas foram semanticamente equivalentes e não se contradizem.

**Evidência:**
- Screenshot original: [ct06-prompt-original.png](../evidencias/testes-execucao/ct06-prompt-original.png)
- Screenshot reformulado: [ct06-prompt-reformulado.png](../evidencias/testes-execucao/ct06-prompt-reformulado.png)

**Status:** A

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
| CT-01 | Funcional | Extração direta das metas financeiras 2026 | A | 100% (3/3) | — |
| CT-02 | Funcional | [Descrição] | [A/P/R] | [X%] | [X%] |
| CT-03 | Funcional | [Descrição] | [A/P/R] | [X%] | [X%] |
| CT-04 | Contexto/Fontes | Contexto ausente (água e resíduos) | A | 100% (2/2) | Calcular junto com o CT-05 |
| CT-05 | Contexto/Fontes | [Contexto irrelevante/conflitante] | [A/P/R] | [X%] | [X%] |
| CT-06 | Metamórfico | Paráfrase (meta de NPS 2026) | A | 100% (2/2) | — |
| CT-07 | Metamórfico | [Idioma ou ordem] | [A/P/R] | [X%] | [X%] |
| CT-08 | Adversarial (direta) | [Injeção direta] | [A/P/R] | [X%] | [X%] |
| CT-09 | Adversarial (indireta) | [Injeção indireta] | [A/P/R] | [X%] | [X%] |
| CT-10 | Saída/Estrutura | [JSON/formato] | [A/P/R] | [X%] | [X%] |

**Cobertura de citações (%):** (afirmações com fonte válida) / (total de afirmações verificadas) × 100

**Taxa de sucesso em contexto (%):** (testes de contexto com status A) / (total de testes de contexto) × 100