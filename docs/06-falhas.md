# Achados e Plano de Melhoria

## Introdução

Este documento apresenta a análise de falhas identificadas durante a avaliação da aplicação AnythingLLM sob a missão **Contexto sob Pressão**.

Os achados foram classificados por categoria, severidade e impacto. Para cada um, foi identificada a causa provável, os testes relacionados e as evidências que o fundamentam. Os achados vêm dos testes de execução (05-testes), do laboratório de contexto e prompts (02-lab-contexto-prompts) e da verificação de fontes (03-verificacao-fontes).

O plano de melhoria prioriza os três achados mais críticos, propondo ações específicas, viáveis e com critérios de sucesso verificáveis.

---

## Classificação de Falhas

### Achado 1: Fontes não aparecem no texto da resposta

**ID:** ACV-01

**Categoria:** Rastreabilidade

**Severidade:** Baixa

**Descrição:** Nos testes CT-01, CT-02 e CT-06, o documento de origem aparece apenas no painel de Fontes da interface. O texto das respostas não indica documento, seção, página ou trecho de apoio. O mesmo padrão aparece nas respostas com documento do laboratório (B01, B03 e B05), e a verificação de fontes registrou 0% de respostas com links diretos para as referências.

**Evidência:**
- Teste CT-01: [ct01-resposta-com-fonte.png](../evidencias/testes-execucao/ct01-resposta-com-fonte.png)
- Teste CT-02: [ct02-plano-de-saude.png](../evidencias/testes-execucao/ct02-plano-de-saude.png)
- Teste CT-06: [ct06-prompt-reformulado.png](../evidencias/testes-execucao/ct06-prompt-reformulado.png)
- Laboratório, tabela de resultados: [02-lab-contexto-prompts.md](02-lab-contexto-prompts.md)

**Testes Relacionados:**
- CT-01: Extração direta de metas financeiras (fonte apenas no painel)
- CT-02: Coparticipação e custeio do plano de saúde (fonte apenas no painel)
- CT-06: Paráfrase do NPS (fonte apenas no painel na versão reformulada)

**Impacto:**
- O usuário não consegue verificar uma afirmação específica a partir do texto da resposta.
- A comprovação depende de a interface exibir o painel corretamente, o que torna o registro frágil quando a resposta é copiada ou exportada.
- O RQ-01 é atendido apenas em parte: a fonte existe, mas não está vinculada à afirmação.

**Causa Provável:**
- A interface apresenta as fontes como metadado separado da resposta.
- O prompt de sistema não exige citação inline (documento, seção ou trecho) junto a cada afirmação.
- Não há mecanismo que associe cada afirmação gerada ao chunk recuperado que a sustenta.

**Requisito Violado:**
- [RQ-01 - Indicar fontes em respostas documentais](../info/requisitos-qualidade.md)

---

### Achado 2: Saída estruturada fora do schema definido

**ID:** ACV-02

**Categoria:** Formato

**Severidade:** Alta

**Descrição:** No teste CT-10, os três indicadores vieram com valores corretos, mas a saída não cumpre o schema. O campo `meta_2026` foi retornado como texto (ex.: "R$ 55 milhões", "15%") e não como número. O campo `unidade` veio como "R$ milhões", fora dos valores previstos ("R$" ou "%"). Também há suspeita de aspas tipográficas, que tornariam o JSON inválido para `json.loads`, mas isso ainda depende da verificação do texto bruto.

**Evidência:**
- Teste CT-10: [CT10-saída-em-json.png](../evidencias/testes-execucao/CT10-saída-em-json.png)

**Testes Relacionados:**
- CT-10: JSON com schema definido

**Impacto:**
- A saída não passa na validação e não pode ser consumida diretamente por outro sistema.
- Quem integrar a resposta precisa de pós-processamento manual ou com regras improvisadas.
- A interface não formata o JSON, o que dificulta a leitura.

**Causa Provável:**
- O prompt pede um JSON, mas não define tipos e unidades de forma restritiva.
- O modelo gera texto que se parece com JSON, sem validação posterior.
- Não há etapa de validação de schema no fluxo da aplicação.

**Requisito Violado:**
- [RQ-01 - Indicar fontes em respostas documentais](../info/requisitos-qualidade.md)
- [RQ-02 - Recuperar informações relevantes dos documentos](../info/requisitos-qualidade.md)

**Observações Adicionais:**
- Os valores e as fontes da saída estão corretos. A falha é de formato, não de conteúdo.

---

### Achado 3: Respostas sobre fontes externas parcialmente sustentadas

**ID:** ACV-03

**Categoria:** Factualidade

**Severidade:** Alta

**Descrição:** Na verificação de fontes com cinco perguntas gerais, todas as respostas foram classificadas como parcialmente sustentadas. Entre os problemas encontrados estão a indicação da edição de 2011 da ISO/IEC 25010 com classificação incorreta de subcaracterística, referências a livros sem edição ou página, e ausência de links diretos. O sistema citou fontes de memória, sem indicar que a resposta não tinha base em documentos do workspace.

**Evidência:**
- Tabela de verificação das cinco respostas: [03-verificacao-fontes.md](03-verificacao-fontes.md)

**Testes Relacionados:**
- Verificação de fontes (perguntas 1 a 5 de 03-verificacao-fontes.md)

**Impacto:**
- O usuário pode usar uma referência que não sustenta a afirmação e confiar nela.
- Em contextos de estudo ou decisão, o risco é de propagação de erros conceituais.
- A presença de referências dá impressão de fundamentação que nem sempre existe.

**Causa Provável:**
- Perguntas sem documento no workspace são respondidas com conhecimento do modelo, e as citações são geradas de memória.
- Não há mecanismo que diferencie resposta fundamentada em documento de resposta de conhecimento geral.
- Não há instrução para indicar incerteza quando a fonte não pode ser verificada.

**Requisito Violado:**
- [RQ-01 - Indicar fontes em respostas documentais](../info/requisitos-qualidade.md)
- [RQ-03 - Indicar insuficiência de informação](../info/requisitos-qualidade.md)

**Observações Adicionais:**
- Este achado vem da verificação de fontes, e não dos testes CT-01 a CT-10. Por isso, ele não tem status A/P/R próprio na tabela de testes.
- A cobertura de citações de 100% usada em 05-testes mede a presença de fonte, enquanto a verificação de 03 mede a sustentação. Os dois números não devem ser apresentados como equivalentes.

---

## Ranking dos Achados Críticos

| Ranking | ID | Achado | Severidade | Categoria | Impacto |
|---------|----|--------|-----------|-----------|---------|
| 1º | ACV-03 | Respostas sobre fontes externas parcialmente sustentadas | Alta | Factualidade | Alta |
| 2º | ACV-01 | Fontes não aparecem no texto da resposta | Alta | Rastreabilidade | Baixa |
| 3º | ACV-02 | Saída estruturada fora do schema definido | Média | Formato | Alta |

Os três achados acima receberão plano de melhoria na seção seguinte.

---
