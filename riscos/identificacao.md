# Etapa 1: Identificação de Riscos

1. **Sobrecarga e Indisponibilidade do Banco de Dados Operacional (ERP BAAN V)**
   - **Descrição**: Risco de exaustão de recursos de hardware (CPU, memória e I/O) e concorrência no banco de dados local do ERP BAAN V (comumente executado em servidores antigos ou bases de dados transacionais sensíveis). A execução de consultas analíticas complexas para extração de grandes volumes de dados históricos pode gerar bloqueios de tabelas (table locks), causando lentidão ou indisponibilidade no faturamento, emissão de notas fiscais e apontamento de produção nas plantas industriais.
   - **Contexto em que pode ocorrer**: Na fase de operação contínua do pipeline de dados, especificamente durante as janelas de extração diária ou em execuções de cargas completas de histórico (backfill), coincidindo com os turnos de pico de produção das fábricas.

2. **Inconsistência, Duplicidade e Desalinhamento de Master Data (Dados Mestres) Global**
   - **Descrição**: Divergência na parametrização, códigos de produto, unidades de medida (ex: metros vs. polegadas) e cadastro de fornecedores entre os ERPs BAAN V das diferentes plantas pelo mundo. A ausência de uma camada unificada de saneamento de dados causará distorções graves e duplicidade nos relatórios consolidados, gerando desconfiança sobre os KPIs de Produção, Estoque e Qualidade exibidos.
   - **Contexto em que pode ocorrer**: Nas etapas de modelagem de dados do Data Warehouse (DWH) e desenvolvimento dos relatórios no Tableau, estendendo-se para a fase de operação contínua do projeto caso não sejam estabelecidas regras rígidas de governança de dados (Master Data Management).

3. **Instabilidade, Perda de Conexão e Latência de Rede nas Plantas Globais**
   - **Descrição**: Degradação da banda de rede ou perda completa de comunicação entre os gateways locais instalados nas fábricas e os endpoints de ingestão da Cloud. Fábricas instaladas em regiões remotas ou de infraestrutura de telecomunicação instável sofrem com quedas intermitentes, atrasando a transferência diária de dados e furando as SLAs acordadas para a atualização de dados no Tableau.
   - **Contexto em que pode ocorrer**: Diariamente durante a fase de operação e sustentação do pipeline de dados, impactando a atualização dos painéis gerenciais e o monitoramento em quase tempo real (near real-time) das plantas mais distantes.

4. **Exposição de Informações Confidenciais por Falta de Segurança no Tráfego de Dados**
   - **Descrição**: Risco de interceptação ou vazamento de dados industriais, financeiros e comerciais sensíveis (como custos de produção e volume de estoque estratégico) durante a transmissão do ambiente on-premises das fábricas para o ambiente Cloud, devido ao tráfego de dados por canais não seguros ou sem criptografia forte.
   - **Contexto em que pode ocorrer**: Na fase de desenho e implantação da arquitetura de segurança física/lógica (infraestrutura de rede, chaves de API, túneis de VPN IPSec/ExpressRoute) e durante a operação contínua do fluxo de dados.

5. **Incompatibilidade Tecnológica e Obsolescência das Conexões Legadas do BAAN V**
   - **Descrição**: Limitações técnicas impostas por drivers JDBC/ODBC legados, ausência de APIs (REST/SOAP) ou falta de suporte moderno para extrações incrementais no banco de dados proprietário do BAAN V. Isso impede a integração direta com ferramentas de ETL nativas de nuvem, demandando a criação e manutenção de rotinas customizadas complexas e instáveis na ponta de cada fábrica.
   - **Contexto em que pode ocorrer**: Nas fases de infraestrutura e início de desenvolvimento do projeto, na tentativa de estabelecer a conectividade inicial entre a ferramenta de orquestração na nuvem e os bancos de dados locais.
