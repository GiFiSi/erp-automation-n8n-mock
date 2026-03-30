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

O fluxo foi desenhado para eliminar processos manuais no setor financeiro e logístico, garantindo que a diretoria tenha acesso a dados em tempo real.

1. **Ingestão (Extract):** Scripts Python rodam de forma agendada consultando a API REST do ERP (ex: Bling) para extrair dados de faturamento, pedidos e impostos (DIFAL).
2. **Orquestração & Transformação (Transform):** Um servidor self-hosted do **n8n** (rodando em Docker) atua como o maestro do pipeline. Ele limpa os payloads JSON, cruza os dados logísticos e aplica as regras de negócio.
3. **Carga (Load):** Os dados tratados são enviados e estruturados automaticamente como um Data Lake em Google Sheets (via Google Apps Script/API).
4. **Visualização (Analytics):** O Looker Studio consome essas bases em tempo real, gerando painéis executivos para o C-Level.
5. **Notificação (IoT/Webhook):** O n8n dispara um resumo financeiro diário diretamente para o WhatsApp da diretoria corporativa.

## 🛡️ Segurança e Infraestrutura
Como a infraestrutura foi construída do zero (Self-hosted), as seguintes camadas de segurança foram aplicadas:
* **Isolamento:** Toda a stack (n8n, Python scripts) roda em contêineres **Docker** sobre um servidor Linux dedicado.
* **Redes:** Acesso externo seguro garantido através de **Cloudflare Tunnels**, eliminando a necessidade de expor portas do servidor para a internet.
* **Governança:** Mascaramento de dados sensíveis na camada de orquestração para alinhar as rotinas aos princípios da LGPD.

## 💡 Impacto de Negócios Simulado
* **Redução de OPEX:** Eliminação de R$ X/mês em licenças de plataformas de integração comerciais.
* **Eficiência Operacional:** Redução de processos manuais de exportação de planilhas de DRE que levavam horas para rodar em poucos minutos.
* **Democratização dos Dados:** Descentralização da inteligência de vendas para o time comercial operar com preços e fretes em tempo real.

---
*Desenvolvido por [Seu Nome/LinkedIn] - Focado em entregar inteligência de dados com eficiência de recursos.*
