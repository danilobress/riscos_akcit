# Etapa 3: Definição de Estratégias de Resposta

*   **Risco:** Sobrecarga e Indisponibilidade do Banco de Dados Operacional (ERP BAAN V)
    *   **Estratégia Proposta:** Mitigar
    *   **Justificativa da escolha:** A extração dos dados é vital para a existência da plataforma analítica, tornando impossível *Evitar* (cancelar) a operação. A estratégia de *Mitigar* é a ideal pois protege o ambiente transacional da fábrica aplicando controles de arquitetura de banco de dados para minimizar o consumo de CPU/I/O, permitindo a extração de dados sem indisponibilizar o faturamento e o apontamento de produção física.
    *   **Possíveis ações associadas:**
        *   Configurar janelas de extração em lote (batch) exclusivamente fora do horário comercial local de cada planta.
        *   Criar um banco de dados de réplica de leitura (Read Replica) local para consultas analíticas pesadas, poupando a base transacional ativa.
        *   Implementar ingestão por Change Data Capture (CDC) baseado em logs de transação, evitando varreduras completas (full scans) nas tabelas transacionais.
        *   Definir limites rígidos de concorrência e timeout para queries analíticas locais.

*   **Risco:** Inconsistência, Duplicidade e Desalinhamento de Master Data (Dados Mestres) Global
    *   **Estratégia Proposta:** Mitigar
    *   **Justificativa da escolha:** As instâncias de ERP operam sob processos descentralizados e autônomos de cadastro de itens há décadas, impedindo que o risco seja *Evitado* sem um projeto paralelo massivo de migração. Ao *Mitigar* o risco, tratamos o problema na camada de processamento de dados na Cloud, aplicando regras rígidas de saneamento de dados e tabelas de conversão ("de-para"), garantindo a confiabilidade nos dashboards do Tableau.
    *   **Possíveis ações associadas:**
        *   Desenvolver e implementar uma camada centralizada de harmonização de dados no DWH que padronize unidades de medida, IDs de materiais e cadastros de fornecedores.
        *   Configurar rotinas automáticas de testes de qualidade de dados (utilizando ferramentas como dbt ou Great Expectations) para identificar registros fora de conformidade na entrada do pipeline.
        *   Definir um comitê corporativo de governança de dados e designar gestores de dados (data stewards) locais para sanear cadastros novos e existentes.
        *   Gerar relatórios de inconsistências de Master Data no Tableau para que os times locais corrijam os dados em suas respectivas instâncias do BAAN V.

*   **Risco:** Instabilidade, Perda de Conexão e Latência de Rede nas Plantas Globais
    *   **Estratégia Proposta:** Mitigar e Aceitar (Contingência)
    *   **Justificativa da escolha:** A infraestrutura de telecomunicações de regiões remotas não é controlada pelo projeto, logo, o risco não pode ser *Evitado*. Adotamos uma combinação de *Mitigar* (tornando os pipelines resilientes e tolerantes a interrupções) e *Aceitar* passivamente as flutuações, desde que os dados sejam reconciliados sem perda de integridade assim que o link for restabelecido.
    *   **Possíveis ações associadas:**
        *   Configurar mecanismos de retry automático com recuo exponencial (exponential backoff) nos pipelines de orquestração em nuvem.
        *   Implementar staging local nas plantas industriais (salvando arquivos compactados em servidores locais) para manter os dados seguros em caso de queda de link e transmiti-los automaticamente ao restabelecer a rede.
        *   Monitorar os tempos de transmissão de dados locais para a nuvem através de alertas automatizados no Slack ou Teams.
        *   Contratar links redundantes (por exemplo, internet via satélite ou rede celular 4G/5G corporativa) para plantas com taxas críticas de indisponibilidade de rede.

*   **Risco:** Exposição de Informações Confidenciais por Falta de Segurança no Tráfego de Dados
    *   **Estratégia Proposta:** Evitar (Eliminar)
    *   **Justificativa da escolha:** O vazamento de dados estratégicos de manufatura ou financeiros viola leis globais de proteção de dados e compromete o segredo industrial da companhia. Por ter consequências jurídicas, financeiras e reputacionais gravíssimas, a única estratégia aceitável é *Evitar* (eliminar a possibilidade de tráfego de dados inseguros) aplicando segurança de nível militar em todo o trânsito de dados.
    *   **Possíveis ações associadas:**
        *   Estabelecer conexões seguras dedicadas (túneis VPN IPSec ou links dedicados corporativos) entre a rede on-premises das fábricas e a rede virtual do provedor Cloud.
        *   Utilizar criptografia forte em trânsito (SSL/TLS 1.3) para todas as requisições e cargas de arquivos.
        *   Implementar criptografia em repouso (at-rest) nas camadas de staging, Data Lake e Data Warehouse em nuvem.
        *   Configurar políticas rígidas de IAM (Identity and Access Management) de menor privilégio e autenticação multifator (MFA) para todo o ecossistema analítico.

*   **Risco:** Incompatibilidade Tecnológica e Obsolescência das Conexões Legadas do BAAN V
    *   **Estratégia Proposta:** Mitigar
    *   **Justificativa da escolha:** A obsolescência do ERP BAAN V é um dado imutável para a linha do tempo do projeto analítico, não permitindo *Evitar* a integração. A estratégia de *Mitigar* foca em criar uma camada física/lógica híbrida de intermediação técnica para que orquestradores em nuvem se comuniquem perfeitamente com a base de dados do ERP sem a necessidade de migrar a base operacional local.
    *   **Possíveis ações associadas:**
        *   Configurar gateways locais de dados dedicados (como Microsoft Self-Hosted Integration Runtime ou agentes locais de dados) compatíveis com drivers JDBC/ODBC específicos da base do BAAN V.
        *   Desenvolver scripts em Python/Shell parametrizados locais que façam dump de dados locais para arquivos estruturados legíveis (como Parquet ou CSV) em caso de falha de conexão direta por driver de banco.
        *   Homologar de forma restrita e documentar a compatibilidade de drivers e sistemas operacionais de banco de dados de todas as fábricas no início do projeto.
        *   Treinar a equipe de engenheiros de dados para atuar no suporte dos drivers de bancos antigos das fábricas.
