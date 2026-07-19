# Etapa 2: Análise dos Riscos

## 1. Análise Estruturada

*   **Risco:** Sobrecarga e Indisponibilidade do Banco de Dados Operacional (ERP BAAN V)
    *   **Descrição:** Risco de exaustão dos recursos locais de processamento (CPU, memória e I/O) no servidor de banco de dados do ERP transacional BAAN V. A execução de varreduras analíticas massivas e concorrentes diretamente na base produtiva gera gargalos severos e travamento de tabelas críticas.
    *   **Possíveis impactos no projeto:** 
        *   *Prazo:* Atrasos na entrega de dados diários por conta da necessidade de abortar ou adiar cargas em momentos de sobrecarga.
        *   *Qualidade:* Relatórios apresentando informações incompletas ou defasadas temporariamente.
        *   *Negócio:* Interrupção de operações na fábrica (faturamento, notas fiscais, apontamento de produção física), resultando em perdas financeiras diretas e danos operacionais.
    *   **Fatores condicionantes:** Ausência de uma réplica de leitura (read replica) dedicada; falta de tecnologia de Change Data Capture (CDC) implementada; infraestrutura local obsoleta; execução de queries em horário comercial; ausência de índices nas tabelas transacionais legadas.
    *   **Probabilidade:** Alta
    *   **Impacto:** Alto
    *   **Justificativa:** Os servidores de banco de dados do BAAN V em plantas locais normalmente operam no limite de capacidade de sua infraestrutura on-premises legada. Como o processamento analítico requer queries pesadas de varredura histórica de tabelas extensas, a chance de locks concorrentes com transações diárias de produção é extremamente elevada, tornando a indisponibilidade fabril um cenário altamente provável.

*   **Risco:** Inconsistência, Duplicidade e Desalinhamento de Master Data (Dados Mestres) Global
    *   **Descrição:** Divergências e falta de conformidade em nomenclaturas, chaves de identificação, códigos e unidades de medida de produtos, fornecedores e clientes entre os diferentes sistemas BAAN V instalados geograficamente de forma descentralizada.
    *   **Possíveis impactos no projeto:** 
        *   *Qualidade:* Erros de agregação de dados e distorção dos indicadores unificados de Produção, Qualidade e Estoque exibidos no Tableau.
        *   *Custo:* Aumento do custo do projeto por retrabalho contínuo da equipe de dados tentando ajustar scripts ETL para tratar exceções locais.
        *   *Negócio:* Tomada de decisões errôneas por parte da diretoria corporativa e perda de credibilidade na plataforma de BI.
    *   **Fatores condicionantes:** Falta de regras de governança e saneamento unificados; gestão descentralizada das instâncias locais do ERP; ausência de uma ferramenta corporativa de MDM (Master Data Management).
    *   **Probabilidade:** Alta
    *   **Impacto:** Alto
    *   **Justificativa:** Plantas geograficamente dispersas costumam ter evoluído seus cadastros internos no ERP de forma isolada ao longo das décadas para atender especificidades regionais. A probabilidade de colisão de dados ao tentar mesclá-los diretamente em uma estrutura de DWH comum sem uma higienização prévia é quase total, comprometendo criticamente o valor gerencial esperado do Tableau.

*   **Risco:** Instabilidade, Perda de Conexão e Latência de Rede nas Plantas Globais
    *   **Descrição:** Instabilidade nos canais de comunicação de internet (alta latência ou queda de conexão) entre a infraestrutura on-premises de plantas isoladas e o ambiente Cloud de consolidação de dados.
    *   **Possíveis impactos no projeto:** 
        *   *Prazo:* Falhas no cronograma de atualização das cargas diárias, causando o atraso na entrega de relatórios e relatórios desatualizados.
        *   *Qualidade:* Ingestão de dados truncados ou fragmentados, exigindo execuções repetidas do pipeline.
    *   **Fatores condicionantes:** Localização das fábricas em áreas geográficas com infraestrutura de telecomunicação frágil; falta de canais de rede redundantes de backup; alto volume de arquivos extraídos sem compressão de dados.
    *   **Probabilidade:** Média
    *   **Impacto:** Médio
    *   **Justificativa:** Interrupções pontuais de rede em ambientes industriais globais são comuns, o que justifica a probabilidade média. O impacto é classificado como médio pois, embora as rotinas de carga fiquem temporariamente defasadas, os pipelines podem ser reiniciados de forma incremental assim que a conexão for reestabelecida, minimizando perdas permanentes.

*   **Risco:** Exposição de Informações Confidenciais por Falta de Segurança no Tráfego de Dados
    *   **Descrição:** Acesso não autorizado, roubo ou vazamento de informações industriais, margens financeiras e volumes confidenciais de estoque durante a transferência das plantas locais para o ambiente de nuvem pública.
    *   **Possíveis impactos no projeto:** 
        *   *Custo:* Multas por violações de conformidade de privacidade de dados (LGPD, GDPR) e custos com assessoria jurídica de crise.
        *   *Negócio:* Perda de vantagem competitiva estratégica no mercado caso dados de custos e eficiência sejam expostos a concorrentes; severo dano reputacional à marca da companhia.
    *   **Fatores condicionantes:** Trânsito de arquivos de dados via conexões HTTP abertas na internet sem VPN; senhas e chaves privadas expostas em código-fonte; falhas de configuração em gateways e políticas de controle de acesso de nuvem.
    *   **Probabilidade:** Baixa
    *   **Impacto:** Alto
    *   **Justificativa:** A probabilidade é baixa por conta das políticas globais rígidas de conformidade em segurança da informação de grandes corporações. No entanto, no cenário de uma quebra de segurança, o impacto financeiro, legal e regulatório decorrente do vazamento de dados críticos de negócio seria catastrófico e imediato.

*   **Risco:** Incompatibilidade Tecnológica e Obsolescência das Conexões Legadas do BAAN V
    *   **Descrição:** Limitação ou incapacidade técnica das ferramentas modernas de nuvem (como Azure Data Factory e AWS Glue) de se conectarem e extraírem dados diretamente do BAAN V devido a drivers proprietários ultrapassados, ausência de APIs nativas e esquemas de dados proprietários não documentados.
    *   **Possíveis impactos no projeto:** 
        *   *Prazo:* Extensão de prazos da fase inicial do projeto devido à necessidade de customização técnica.
        *   *Custo:* Aumento de horas de desenvolvimento especializado (geração de scripts locais em shell/python personalizados na ponta do cliente para exportar e fazer upload de arquivos flat).
    *   **Fatores condicionantes:** Inexistência de APIs modernas REST/SOAP no BAAN V; bancos de dados legados (Informix / Oracle antigos) sem suporte a ferramentas modernas de ETL; escassez de profissionais seniores que conheçam a fundo a arquitetura legada.
    *   **Probabilidade:** Média
    *   **Impacto:** Médio
    *   **Justificativa:** O obstáculo de integração tecnológica é uma constante em projetos envolvendo ERPs legados. A probabilidade é média devido à natureza fechada do BAAN V. O impacto técnico é médio porque, embora exija soluções complexas de integração híbrida (gateways locais e scripts customizados), não se trata de um impeditivo definitivo que inviabilize o fluxo do pipeline.

## 2. Matriz Qualitativa de Riscos

| Probabilidade \ Impacto | Baixo | Médio | Alto |
| :--- | :---: | :---: | :---: |
| **Alta** | — | — | **Risco 1:** Sobrecarga do DB BAAN V<br>**Risco 2:** Inconsistência de Master Data |
| **Média** | — | **Risco 3:** Instabilidade de Rede<br>**Risco 5:** Incompatibilidade de Conexão | — |
| **Baixa** | — | — | **Risco 4:** Exposição de Dados |

## 3. Zonas de Classificação e Ações Requeridas

| Zona / Cor | Critério de Classificação | Ação Requerida |
| :--- | :--- | :--- |
| **Crítico (Vermelho)** | Probabilidade Alta + Impacto Alto | - Definição mandatória de plano de mitigação e contorno técnico imediato.<br>- Revisão de design de arquitetura pelo comitê técnico.<br>- Aprovação formal da diretoria executiva para seguir ao Go-Live. |
| **Moderado (Amarelo)** | Probabilidade Média + Impacto Médio<br>OU Probabilidade Baixa + Impacto Alto<br>OU Probabilidade Alta + Impacto Médio | - Elaboração de plano de contingência e monitoramento preventivo de gatilhos.<br>- Alertas automatizados para identificar falhas em tempo de execução.<br>- Reporte mensal de status de riscos nas reuniões de governança. |
| **Baixo (Verde)** | Probabilidade Baixa + Impacto Baixo<br>OU Probabilidade Baixa + Impacto Médio<br>OU Probabilidade Média + Impacto Baixo | - Aceitação do risco sob monitoramento passivo das métricas básicas.<br>- Sem necessidade de alocação imediata de orçamento ou recursos adicionais. |
