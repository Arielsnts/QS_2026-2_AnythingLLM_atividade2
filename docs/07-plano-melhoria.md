## Plano de Melhoria

### Melhoria 1: Exigir fonte verificável por afirmação (ACV-03)

**Achado Relacionado:** ACV-03 (Respostas sobre fontes externas parcialmente sustentadas)

**Causa Provável:**
- Perguntas sem documento no workspace são respondidas com conhecimento do modelo, e as referências são geradas de memória
- Não há mecanismo que diferencie resposta fundamentada em documento de resposta de conhecimento geral
- Não há instrução para indicar incerteza quando a fonte não pode ser verificada

**Ação Proposta:**
1. Ajustar o prompt de sistema (P2) para exigir que cada afirmação factual venha acompanhada de documento e trecho de apoio do workspace
2. Instruir o modelo a declarar explicitamente "sem fonte no workspace" quando a resposta não puder ser sustentada pelos documentos disponíveis
3. Desativar, nos workspaces de teste, respostas com referências bibliográficas externas não verificáveis
4. Repetir a verificação de fontes com as mesmas cinco perguntas após o ajuste

**Prioridade:** Alta

**Dependências:**
- Acesso às configurações de prompt de sistema do workspace
- Workspace com documentos cobrindo os temas das perguntas (ou aceitação explícita de resposta sem fonte)

**Timeline Estimada:** 2-3 dias

**Evidência Esperada (após melhoria):**
- Tabela de verificação refeita com as cinco perguntas, com trecho de apoio para cada afirmação
- Respostas sem base documental identificadas como tal

**Plano de Reteste:**
- Repetir as cinco perguntas de 03-verificacao-fontes.md → esperado: cada afirmação com documento e trecho, ou declaração de ausência
- Re-executar CT-04 (contexto ausente) → esperado: manter status A, sem valores inventados


---

### Melhoria 2: Citação inline vinculada ao chunk recuperado (ACV-01)

**Achado Relacionado:** ACV-01 (Fontes não aparecem no texto da resposta)

**Causa Provável:**
- A interface apresenta as fontes como metadado separado da resposta
- O prompt de sistema não exige citação inline junto a cada afirmação
- Não há mecanismo que associe cada afirmação ao chunk que a sustenta

**Ação Proposta:**
1. Alterar o prompt P2 para exigir formato de citação no texto, como "(Documento, seção X)", após cada valor
2. Verificar se a configuração do workspace permite exibir os trechos recuperados junto à resposta
3. Reexecutar os casos CT-01, CT-02 e CT-06 e comparar com o registro atual

**Prioridade:** Baixa

**Dependências:**
- Melhoria 1 concluída, para que o prompt ajustado seja o mesmo
- Confirmação de quais configurações de exibição de fontes o AnythingLLM oferece na versão testada

**Timeline Estimada:** 1-2 dias

**Evidência Esperada (após melhoria):**
- Respostas de CT-01, CT-02 e CT-06 com documento e seção citados no próprio texto
- Captura do painel de Fontes e do texto, lado a lado

**Plano de Reteste:**
- Re-executar CT-01 → esperado: valores e seção citados no texto
- Re-executar CT-02 → esperado: documento v2.0 citado no texto
- Re-executar CT-06 (versão reformulada) → esperado: manter NPS 75 e citar o manual no texto


---

### Melhoria 3: Validação de schema antes do consumo da saída (ACV-02)

**Achado Relacionado:** ACV-02 (Saída estruturada fora do schema definido)

**Causa Provável:**
- O prompt pede JSON sem restringir tipos e unidades de forma explícita
- O modelo gera texto com aparência de JSON, sem validação posterior
- Não há etapa de validação de schema no fluxo da aplicação

**Ação Proposta:**
1. Verificar o texto bruto da resposta do CT-10 (via log ou exportação) para confirmar se as aspas tipográficas existem na saída real
2. Refazer o prompt com tipos explícitos: `meta_2026` como número, `unidade` restrita a "R$" ou "%"
3. Criar validador simples em Python (`json.loads` + verificação de campos e tipos) e aplicá-lo à saída
4. Se o validador rejeitar a saída, tratar a resposta como inválida e solicitar nova geração ou pós-processamento

**Prioridade:** Alta

**Dependências:**
- Verificação do texto bruto concluída (define se o achado é de formato do sistema ou de cópia)
- Script de validação disponível no repositório

**Timeline Estimada:** 1-2 dias

**Evidência Esperada (após melhoria):**
- Log do validador aceitando a saída principal
- Log do validador rejeitando as quatro variações inválidas

**Plano de Reteste:**
- Re-executar CT-10 → esperado: JSON válido, `meta_2026` numérico, `unidade` no padrão
- Executar as quatro variações inválidas no validador → esperado: rejeição em todas
