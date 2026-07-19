## Criação README.md

```
Atue como gerente de projeto e arquiteto de soluções senior.
Context: Estamos consolidando os artefatos de um projeto chamado "Dashboard Global de Manufatura". O projeto consiste em uma plataforma de Business Intelligence que extrai dados de um ERP legado (BAAN V) de múltiplas plantas globais, processa em um ambiente Cloud e exibe indicadores (Produção, Qualidade e Estoque) via Tableau. O foco atual do trabalho é a gestão avançada de riscos arquiteturais (como impactos no banco de dados da fábrica, inconsistência de Master Data e latência de rede).

Objective: Crie o conteúdo completo para o arquivo README.md que servirá como a página inicial e o guia do nosso repositório no GitHub. Ele deve contextualizar sobre o que é o projeto, qual é o objetivo desta entrega específica (focada no exercício de gestão de riscos) e mapear onde estão os demais arquivos criados.
Estilo: Utilize um estilo de escrita padrão de documentação de software open-source ou corporativo no GitHub. O texto deve ser estruturado, limpo, direto ao ponto e fazer uso de negritos e listas (bullet points) para facilitar a leitura dinâmica.
Tone: Mantenha um tom profissional, técnico, objetivo e gerencial. Transmita senioridade e clareza.
Publico-Alvo: Os avaliadores técnicos do exercício prático, engenheiros de dados, desenvolvedores e stakeholders (C-level) que acessarão o repositório para entender a documentação e as decisões arquiteturais tomadas.
Resposta: Crie um arquivo chamado README.md.
A estrutura obrigatória do arquivo deve conter os seguintes cabeçalhos:

Um H1 com o nome do projeto (Dashboard Global de Manufatura).
Um H2 chamado "Descrição do Projeto" (resumindo a arquitetura BAAN V -> Cloud -> Tableau).
Um H2 chamado "Objetivo do Exercício" (focado na mitigação de riscos arquiteturais).
Um H2 chamado "Organização do Repositório" exibindo uma estrutura de pastas/arquivos em formato de lista, contemplando:

README.md

riscos/identificacao.md
riscos/analise.md
riscos/respostas.md
comunicacao/status-stakeholders.md
```

## Criação identificacao.md
```
Atue como gerente de projetos e arquiteto de soluções senior.
Contexto: A arquitetura consiste em extrair dados de um ERP legado (BAAN V) de várias fábricas pelo mundo, processar e consolidar esses dados na Cloud, e exibi-los em dashboards gerenciais no Tableau. Etapa do processo de gestão de riscos do projeto.
Objetivo: Criar o conteúdo completo para o arquivo identificacao.md, que documenta a identificação inicial dos riscos do projeto. Você deve detalhar os principais riscos arquiteturais e de negócio mapeados para esta integração.
Estilo: Técnico, estruturado e analítico. Utilize listas e marcadores (bullet points) para facilitar a leitura. Use negrito para destacar os rótulos dos campos exigidos.
Tom: Profissional, objetivo e voltado para a governança de projetos de TI.
Público-Alvo: Avaliadores técnicos do exercício, stakeholders do projeto, arquitetos de dados e gerentes de TI que precisam entender rapidamente quais são as ameaças ao projeto.
Resposta: Dentro da pastas riscos, crie um arquivo chamado identificacao.md
A estrutura do documento deve ser:

Um H1 com o título "Etapa 1: Identificação de Riscos".
Uma lista numerada para cada um dos riscos identificados.
Dentro de cada item numerado, o título do risco em negrito, seguido por dois sub-tópicos obrigatórios:
Descrição: [Explicação breve do risco]
Contexto em que pode ocorrer: [Momento ou fase do projeto/operação em que o risco se materializa]
```