# ⚙️ Zero-Budget Data Pipeline & ERP Automation

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-FF6D5W?style=for-the-badge&logo=n8n&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=google-sheets&logoColor=white)
![Looker Studio](https://img.shields.io/badge/Looker_Studio-4285F4?style=for-the-badge&logo=looker&logoColor=white)

## 📌 Sobre o Projeto (Mock Architecture)
*Nota: Este repositório é uma demonstração arquitetural (Mock) de um ecossistema de dados real desenvolvido para o setor industrial/varejo. Por motivos de NDA e proteção de dados (LGPD), o código de produção e as credenciais reais não estão expostos. O objetivo aqui é demonstrar o raciocínio de engenharia e a arquitetura da solução.*

Este projeto demonstra a construção de um pipeline de dados ponta a ponta (ETL/ELT) e automação de processos utilizando a premissa de **Zero-Budget Tech** (custo zero de licenciamento de software). A solução orquestra a comunicação entre um ERP corporativo, bancos de dados e painéis de Business Intelligence, rodando 100% em infraestrutura local conteinerizada.

## 🏗️ Arquitetura da Solução

O fluxo foi desenhado para eliminar processos manuais no setor financeiro e logístico, centralizando a inteligência e garantindo que a diretoria tenha acesso a dados em tempo real.

1. **Orquestração e Ingestão (Extract):** Um servidor self-hosted do **n8n** (rodando em contêiner Docker) atua como o maestro central do pipeline. Através de *workflows* agendados (Triggers), o n8n utiliza *Nodes* de execução de código nativo (**Python**) para consultar a API REST do ERP corporativo (ex: Bling), extraindo dados de faturamento, pedidos e impostos.
2. **Transformação (Transform):** Dentro do próprio fluxo do n8n, os payloads JSON complexos são manipulados e limpos. É nesta etapa que os dados logísticos são cruzados e as lógicas tributárias (como o cálculo de DIFAL) são aplicadas em memória.
3. **Carga (Load):** Os dados tratados são enviados e estruturados automaticamente como um Data Lake em planilhas do Google Sheets (via Google Apps Script / Google API).
4. **Visualização (Analytics):** O Looker Studio consome essas bases estruturadas em tempo real, gerando painéis executivos de Business Intelligence para o C-Level.
5. **Notificação (IoT/Webhook):** O workflow do n8n é finalizado disparando um resumo financeiro diário diretamente para o WhatsApp da diretoria corporativa via API.

## 🛡️ Segurança e Infraestrutura
Como a infraestrutura foi construída do zero (Self-hosted), as seguintes camadas de segurança foram aplicadas:
* **Isolamento:** Toda a stack (n8n, Python scripts) roda em contêineres **Docker** sobre um servidor Linux dedicado.
* **Redes:** Acesso externo seguro garantido através de **Cloudflare Tunnels**, eliminando a necessidade de expor portas do servidor para a internet.
* **Governança:** Mascaramento de dados sensíveis na camada de orquestração para alinhar as rotinas aos princípios da LGPD.

## 💡 Impacto de Negócios Simulado
* **Redução de OPEX:** Eliminação de custos recorrentes com licenças de plataformas iPaaS (Zapier/Make) e infraestrutura Cloud, economizando aproximadamente R$ 1.000,00/mês em custos diretos de software.
* **Eficiência Operacional:** Automação total de processos de exportação e cruzamento de dados tributários (DIFAL), reduzindo o tempo de processamento manual de horas para segundos.
* **Democratização dos Dados:** Centralização da inteligência de faturamento e frete, permitindo tomada de decisão baseada em dados em tempo real pela diretoria.

---
**Desenvolvido por [Guilherme Ferreira Santos](https://www.linkedin.com/in/guilherme-ferreira-santos-94619b23a/)** *Focado em entregar inteligência de dados com máxima eficiência de recursos.*
