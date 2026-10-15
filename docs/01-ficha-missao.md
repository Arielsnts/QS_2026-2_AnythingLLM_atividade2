# Ficha da Missão

## Identificação

Nome do Projeto: AnythingLLM
URL: https://github.com/Mintplex-Labs/anything-llm
Organização: Mintplex Labs
Licença: MIT
Missão Escolhida: D - Contexto sob Pressão

## Versão Testada

Data de Acesso: 21/10/26
Release: 

## Finalidade

Plataforma de RAG (Retrieval-Augmented Generation) que permite criar workspaces com documentos próprios e consultar um LLM com contexto recuperado desses documentos.

Para o recorte desta missão, a funcionalidade avaliada é a **resposta a partir de contexto recuperado de documentos do workspace**, incluindo o comportamento quando o contexto é correto, ausente, irrelevante ou conflitante.

## Usuários

- Usuário final que consulta documentos de um workspace
- Administrador que configura o workspace, os documentos e o provedor de modelo
- Equipe avaliadora, que executa os testes em ambiente controlado

## Modelo ou Provedor

Provedor de LLM: [Preencher, por exemplo: OpenAI, Anthropic, Ollama]
Modelo: [Preencher o nome exato, por exemplo: gpt-4o-mini]
Banco vetorial: [Banco configurado na instalação]

Os mesmos valores devem ser usados em todos os testes.

## Fluxo Avaliado

O fluxo abaixo representa o caminho de uma consulta, da entrada do usuário até a resposta com fontes e logs. <br />

>Usuário → Prompt/políticas (P1, P2 ou P3) → Contexto (RAG: busca vetorial nos chunks do workspace) → Modelo (LLM) → Resposta + fontes + logs


## Limitações

- O teste considera apenas a configuração padrão do workspace, com o provedor e modelo indicados acima.
- Os documentos são sintéticos e pequenos, não representam o volume real de uma base corporativa.
- Não há controle sobre a versão do modelo no provedor, que pode mudar sem aviso.
- Os resultados dependem de parâmetros de geração que podem variar entre execuções.
- Não foi avaliada a interface gráfica além do necessário para ver respostas e fontes.
- Não foram testados agentes, ferramentas externas ou múltiplos usuários simultâneos.
- Algumas informações da ficha dependem de verificação no repositório na data de acesso.
