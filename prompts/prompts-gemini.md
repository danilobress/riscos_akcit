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

## Criação analise.md
```
Atue como gerente de projetos e analista de riscos senior.
Contexto: O projeto foca em extrair dados de produção, qualidade e estoque de sistemas ERP (BAAN V) em plantas globais, consolidá-los em Cloud e visualizá-los via Tableau. Já identificamos 5 riscos principais: Sobrecarga e Indisponibilidade do Banco de Dados Operacional (ERP BAAN V), Inconsistência, Duplicidade e Desalinhamento de Master Data (Dados Mestres) Global, Instabilidade, Exposição de Informações Confidenciais por Falta de Segurança, Exposição de Informações Confidenciais por Falta de Segurança no Tráfego de Dados e Incompatibilidade Tecnológica e Obsolescência das Conexões Legadas do BAAN V
Objetivo: Realizar uma análise qualitativa estruturada para os 5 riscos identificados, detalhando os impactos, fatores condicionantes e classificando a probabilidade e o impacto de cada um. Além disso, deve elaborar uma Matriz Qualitativa de Riscos e definir as Zonas de Classificação com suas respectivas Ações Requeridas.
(Estilo): Analítico, direto e estruturado. Formato de relatório de gestão de riscos padrão do PMI/PMBOK. Utilize listas aninhadas e aplique negrito nos nomes dos parâmetros para clareza visual e tabelas em Markdown para a Matriz de Riscos e as Zonas de Classificação.
Tom: Profissional, crítico e pragmático. O tom deve refletir senioridade na avaliação de ameaças arquiteturais e de negócio em sistemas críticos.
Público-Alvo: Comitê de direção do projeto e arquitetos de dados, que buscam entender a gravidade e o porquê de cada risco.
Resposta: Dentro da pasta riscos, crie um arquivo chamado analise.md
A estrutura do arquivo deve seguir estritamente o formato abaixo:

# Etapa 2: Análise dos Riscos
## 1. Análise Estruturada
*(Repita a estrutura abaixo para os 5 riscos previamente mapeados no contexto)*
*   **Risco:** [Nome do risco]
    *   **Descrição:** [Detalhamento do risco]
    *   **Possíveis impactos no projeto:** [Impactos em prazo, custo, qualidade ou negócio]
    *   **Fatores condicionantes:** [Fatores que aumentam a chance de ocorrer]
    *   **Probabilidade:** [Alta / Média / Baixa]
    *   **Impacto:** [Alto / Médio / Baixo]
    *   **Justificativa:** [Explicação para as classificações dadas]

## 2. Matriz Qualitativa de Riscos
*(Crie uma tabela Markdown cruzando Probabilidade nos eixos verticais vs. Impacto nos eixos horizontais, distribuindo os 5 riscos mapeados dentro das células correspondentes)*

## 3. Zonas de Classificação e Ações Requeridas
*(Crie uma tabela Markdown definindo as zonas da matriz, contemplando: Zona/Cor [Ex: Crítico, Moderado, Baixo], Critério [Ex: Probabilidade Alta + Impacto Alto] e Ação Requerida [Ex: Plano de mitigação imediato, Monitoramento contínuo])*

*(Repita a estrutura acima para os 5 riscos previamente mapeados no contexto)*
```

## Criação respostas.md
```
Atue como gerente de projetos e líder técnico no projeto senior.
Contexto:  Na etapa anterior, mapeamos e analisamos 5 riscos: 1) Sobrecarga e Indisponibilidade do Banco de Dados Operacional (ERP BAAN V), 2) Inconsistência, Duplicidade e Desalinhamento de Master Data (Dados Mestres) Global, 3) Instabilidade, Exposição de Informações Confidenciais por Falta de Segurança, 4) Exposição de Informações Confidenciais por Falta de Segurança no Tráfego de Dados e 5) Incompatibilidade Tecnológica e Obsolescência das Conexões Legadas do BAAN V. Agora, é o momento de definir as estratégias de tratamento para esses riscos.

Objetivo: Elaborar planos de resposta definindo a melhor estratégia (Evitar, Mitigar, Transferir ou Aceitar) para cada um dos 5 riscos identificados, justificando a escolha e detalhando ações práticas.
Estilo: Acionável, estruturado e claro. Utilize tópicos (bullet points) para organizar as informações de forma hierárquica e facilite a leitura rápida. Destaque em negrito os rótulos de cada seção.
Tom: Estratégico, decisivo e executivo. O tom deve demonstrar controle sobre as soluções arquiteturais e maturidade em gerenciamento de projetos.
Público-Alvo: Stakeholders do projeto e engenheiros executores, que precisam saber exatamente qual direção o projeto vai tomar diante dos riscos.
Resposta: Dentro da pasta riscos, crie um arquivo chamado respostas.md
Siga a estrutura exata abaixo:

# Etapa 3: Definição de Estratégias de Resposta
*   **Risco:** [Nome do risco]
    *   **Estratégia Proposta:** [Evitar, Mitigar, Transferir ou Aceitar - escolha a mais adequada ou uma combinação]
    *   **Justificativa da escolha:** [Argumentação técnica/negócios do porquê essa estratégia é a ideal]
    *   **Possíveis ações associadas:** [Passos práticos/tarefas para aplicar a estratégia]

*(Repita a estrutura para os 5 riscos do contexto)*
```

## Criação status-stakeholders.md
```
Atue como gerente de projetos senior.
Contexto: Comunicar os riscos identificados e as decisões e o status geral aos patrocinadores e executivos do projeto de forma clara e não-alarmista.
Objetivo: Um relatório de status executivo (Status Report) que resume o mapeamento dos riscos e as estratégias adotadas, com o objetivo de dar visibilidade e segurança ao comitê diretivo de que o projeto está sob controle.
Estilo: Executivo, claro, conciso e visual. Evite jargões técnicos excessivos na explicação dos impactos (traduza problemas técnicos para impactos de negócio, como "parada de fábrica" ou "dados não confiáveis"). Utilize tabelas em Markdown e listas com marcadores (bullet points) para facilitar a leitura dinâmica.
Tom: Transparente, seguro, profissional e orientado a soluções. Deve transmitir senioridade e controle, garantindo que os riscos são conhecidos e estão sendo ativamente gerenciados.
Público-alvo: Stakeholders do projeto: C-Level (Diretores, Sponsors), gerentes de planta globais e líderes de negócios que precisam tomar decisões rápidas e não têm tempo para ler documentos longos.
Resposta: Dentro da pasta comunicacao, crie um arquivo chamado status-stakeholders.md
Siga a estrutura exata abaixo:

# Relatório de Status Executivo: Dashboard Global de Manufatura

## 1. Resumo Executivo
*(Escreva um parágrafo curto e direto resumindo o momento atual do projeto, destacando a conclusão bem-sucedida do mapeamento e planejamento de respostas aos riscos de arquitetura)*

## 2. Posição dos Riscos e Estratégias
*(Crie uma tabela em Markdown contendo as seguintes colunas: **Ameaça Identificada** | **Criticidade** | **Estratégia** | **Ação Principal de Negócio**. Preencha as linhas com o resumo dos 5 riscos mapeados nas etapas anteriores)*

## 3. Próximos Passos
*(Liste de 3 a 4 ações gerenciais que darão continuidade ao projeto, como aprovações de budget para as mitigações, início das provas de conceito (PoC) da arquitetura, etc.)*
```