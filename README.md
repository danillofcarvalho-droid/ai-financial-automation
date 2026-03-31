Automação de Gastos com IA (Gemini + PostgreSQL)
Projeto de Engenharia de Dados e IA para captura, saneamento e análise preditiva de finanças pessoais em tempo real.

Este ecossistema utiliza Inteligência Artificial (Google Gemini API) para transformar descrições brutas de gastos em dados estruturados, armazenando-os em um banco de dados relacional e gerando insights automáticos mensais via Telegram.

Arquitetura do Sistema
O projeto é dividido em dois fluxos principais de automação:

1. Fluxo de Ingestão e Saneamento (Real-time)
Captura: O MacroDroid intercepta notificações de gastos no Android.

Transporte: Dados enviados via Webhook para o Make.com.

IA (Saneamento): O Google Gemini analisa a descrição (ex: "Posto Shell") e categoriza automaticamente (ex: "Transporte"), garantindo integridade no banco.

Persistência: Dados limpos são inseridos em uma tabela PostgreSQL hospedada no Supabase.

2. Fluxo de BI e Insights (Monthly)
Gatilho: Agendamento automático para o último dia de cada mês.

Agregação: Consulta SQL (Select Rows) que consolida todos os gastos do período.

IA (Análise): O Gemini atua como um Consultor Financeiro, identificando padrões de gastos e categorias críticas.

Entrega: O relatório final é enviado via Telegram Bot API.

🛠️ Stack Tecnológica
Orquestração: Make.com (iPaaS)

Banco de Dados: PostgreSQL (via Supabase)

Modelos de Linguagem (LLM): Google Gemini 1.5 Flash (via API)

Automação Mobile: MacroDroid

Interface de Notificação: Telegram Bot API

📂 Estrutura do Repositório
/blueprints: Contém os arquivos JSON (Blueprints do Make.com) para importação dos cenários.

/sql: Script de criação da tabela controle_gastos no PostgreSQL.

README.md: Documentação do projeto.

🚀 Como Replicar este Projeto
Banco de Dados: Execute o script SQL no seu console do Supabase para criar a tabela.

Make.com: Importe os arquivos .json da pasta /blueprints.

Configurações:

Conecte sua API Key do Google Gemini.

Configure as credenciais do seu banco PostgreSQL.

Adicione o Token do seu Bot do Telegram.

Mobile: Configure o Webhook no MacroDroid para apontar para a URL gerada no Make.

📈 Resultados Obtidos
Zero intervenção manual: O sistema categoriza 100% dos gastos sem necessidade de abrir apps financeiros.

Dados Estruturados: Banco de dados pronto para conexão com ferramentas de visualização como Looker Studio ou Power BI.

Insights Inteligentes: Recebimento de feedback financeiro baseado em dados reais, não apenas valores brutos.

👨‍💻 Autor
Danillo

Graduando em Análise e Desenvolvimento de Sistemas (ADS).

Foco em Automação, Integrações de API e Engenharia de Dados.
