# Verificação das fontes

## 1. Metodologia utilizada

<p>
  A verificação das fontes foi feita realizando 5 perguntas, sobre diferentes tópicos, ao AnythingLLM. Para cada pergunta, foi exigido o fornecimento da fonte, para comparar a resposta do AnythingLLM à fonte fornecida e verificar se elas realmente sustentam o que foi afirmado. Após avaliar cada verificação, foi realizado o cálculo de cobertura de citações e a identificação de padrões.
</p>

## 2. Tabela de Verificação

| **Número** | **Afirmação analisada** | **Fonte apresentada** | **Resultado da verificação**
| --- | --- | --- | --- |
| 1 | Quais são os principais tipos de teste de software e qual a finalidade de cada um? Apresente fontes ou referências que comprovem as informações. | O AnythingLLM mencionou o ISTQB, livros técnicos, OWASP, Microsoft, TechTarget e Nielsen Norman Group, mas não forneceu links diretos nem páginas específicas. Na conferência complementar, foram localizados o syllabus do ISTQB, o guia da OWASP e o artigo do Nielsen Norman Group | Parcialmente sustentada. As fontes localizadas corroboram as definições gerais de testes de integração, sistema, aceitação, segurança e usabilidade. Entretanto, a resposta original não apresenta referências precisas para todas as afirmações, especialmente regressão e desempenho. Os livros citados também não foram identificados por edição ou página. |
| 2 | Quais são as principais características da qualidade de software segundo a norma ISO/IEC 25010? Cite a fonte utilizada e indique onde essas características podem ser consultadas. | O AnythingLLM indicou a ISO/IEC 25010:2011, mas forneceu apenas o domínio iso.org, sem link direto. Na verificação complementar, foi consultada a página oficial da edição de 2011, que confirma as oito características do modelo de qualidade do produto. Também foi consultada a edição de 2023. | Parcialmente sustentada. As oito características principais correspondem à edição de 2011. Contudo, a resposta contém uma classificação incorreta de subcaracterística de portabilidade, omite alguns elementos da usabilidade e não fornece um link direto para a norma original. |
| 3 | Quais são os benefícios e as limitações dos testes automatizados na garantia da qualidade de software? Apresente referências confiáveis que sustentem cada benefício e limitação. | A resposta citou livros de Lisa Crispin e Janet Gregory, Mark Fewster e Dorothy Graham, Paul C. Jorgensen, Martin Fowler, ISTQB, Google e Nielsen Norman Group, mas não forneceu links diretos para a maioria das referências. Na verificação complementar, foram consultados o syllabus do ISTQB, o artigo de Martin Fowler e o artigo do Google sobre testes instáveis. | Parcialmente sustentada. As fontes complementares confirmam benefícios como feedback rápido e redução de testes repetitivos, além de limitações relacionadas à manutenção, instabilidade e necessidade de testes manuais. Entretanto, parte das referências originais é genérica ou não foi identificada com precisão suficiente, especialmente nas alegações sobre retorno financeiro, interfaces dinâmicas e demanda por profissionais especializados. |
| 4 | O que é a cobertura de testes de software, como ela é calculada e quais são as suas limitações como métrica de qualidade? Inclua fontes que permitam verificar as definições e os cálculos apresentados. | O AnythingLLM mencionou o ISTQB, livros técnicos, Martin Fowler e a ISO/IEC 25010, sem apresentar links diretos para a maioria das referências. Na verificação complementar, foram consultados o syllabus do ISTQB, a documentação do JaCoCo, o artigo de Martin Fowler e as recomendações do Google. | Parcialmente sustentada. A definição geral, a fórmula de cobertura de ramificações e as principais limitações são corroboradas por fontes técnicas confiáveis. Contudo, a resposta simplifica a distinção entre linhas e instruções, apresenta uma fórmula limitada para cobertura de caminhos e não fornece referências precisas para todas as afirmações. |
| 5 | Como verificar se as respostas produzidas por um modelo de inteligência artificial são confiáveis e se as citações apresentadas realmente sustentam as afirmações? Indique métodos de verificação e fontes confiáveis. | A resposta menciona Google Scholar, IEEE Xplore, ACM Digital Library, ISO, NIST e outras instituições, mas não apresenta links específicos para fundamentar cada método. | Parcialmente sustentada. As orientações gerais são coerentes com as práticas de pesquisa e verificação. As fontes institucionais consultadas confirmam a relevância da conferência independente e disponibilizam meios para localizar literatura e normas. Entretanto, algumas recomendações são generalizações, e as referências foram apresentadas sem links diretos para comprovar cada orientação. |

## 3. Cobertura de citações

<p>Nas cinco respostas analisadas, observou-se que 100% mencionaram fontes, referências bibliográficas ou instituições reconhecidas. Entretanto, nenhuma apresentou links diretos para as fontes citadas originalmente, o que corresponde a uma taxa de 0% de respostas com referências diretamente acessíveis por meio de links. Apesar da presença de referências em todas as respostas, a verificação complementar indicou que elas sustentavam apenas parte do conteúdo ou apresentavam limitações de precisão e especificidade. Portanto, a presença de referências não foi suficiente para garantir que todas as afirmações estivessem devidamente fundamentadas.</p>

- <strong> Indicador 1: Respostas que apresentaram referências </strong><br>
ref = 5/5 x 100 = 100%

- <strong> Indicador 2: Respostas com links diretos nas referências originais </strong><br>
links = 0/5 x 100 = 0%

## 4. Padrões identificados

<p>A análise das cinco respostas permitiu identificar os seguintes padrões:</p>

- **Referências genéricas**: o modelo citou fontes reconhecidas, mas não apresentou links diretos para facilitar a verificação.
- **Informações parcialmente sustentadas**: as respostas apresentaram conteúdo geralmente coerente, mas algumas afirmações não foram totalmente confirmadas.
- **Imprecisões conceituais**: foram identificadas simplificações e erros pontuais, como na classificação de características da norma ISO/IEC 25010.
- **Necessidade de verificação**: foi necessário consultar fontes oficiais e documentação técnica para confirmar as informações apresentadas.

<p>Portanto, apesar de produzir respostas organizadas, o modelo apresentou limitações na rastreabilidade das referências, reforçando a importância da verificação independente.</p>
