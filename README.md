# **Automação de Gastos com IA (Gemini + PostgreSQL)**

> **Projeto de Engenharia de Dados e IA** para captura, saneamento e análise de finanças pessoais em tempo real.

Este ecossistema utiliza **Inteligência Artificial (Google Gemini API)** para transformar descrições brutas de notificações de pagamento em dados estruturados, armazenando-os em um banco de dados relacional e gerando insights automáticos mensais via Telegram.

---

### **Arquitetura do Sistema**

O projeto é dividido em dois fluxos principais de automação:

**1. Fluxo de Ingestão e Saneamento (Real-time)**
* **Captura:** O **MacroDroid** intercepta notificações de gastos no Android, seja por SMS ou pop-up do aplicativo do banco.
* **Transporte:** Dados enviados via **Webhook** para o **Make.com**.
* **IA (Saneamento):** O **Google Gemini** analisa a descrição bruta (ex: "Posto Shell") e categoriza automaticamente (ex: "Transporte"), garantindo a integridade e padronização dos dados.
* **Persistência:** Dados limpos são inseridos em uma tabela **PostgreSQL** hospedada no **Supabase**.

**2. Fluxo de BI e Insights (Monthly)**
* **Gatilho:** O sistema está configurado para gerar o fechamento mensal automaticamente no primeiro dia do mês subsequente, garantindo que todos os dados do período anterior tenham sido processados.
* **Agregação:** Consulta SQL (Select Rows) que consolida todos os gastos do período.
* **IA (Análise):** O Gemini atua como um **Consultor Financeiro**, identificando padrões de consumo, categorias críticas e sugerindo ajustes.
* **Entrega:** O relatório final é enviado diretamente para o usuário via **Telegram Bot API**.

---

### **Stack Tecnológica**

| Componente | Tecnologia |
| :--- | :--- |
| **Orquestração** | Make.com (iPaaS) |
| **Banco de Dados** | PostgreSQL (via Supabase) |
| **IA Generativa** | Google Gemini 2.5 Flash |
| **Automação Mobile** | MacroDroid |
| **Notificações** | Telegram Bot API |

---

### **Estrutura do Repositório**

* **/blueprints**: Arquivos JSON para importação dos cenários no Make.com.
* **/sql**: Script de criação da tabela controle_gastos no PostgreSQL.
* **README.md**: Documentação técnica do projeto.

---

### **Como Replicar este Projeto**

1. **Banco de Dados:** Execute o script SQL contido na pasta /sql no console do seu projeto Supabase.
2. **Make.com:** Importe os arquivos .json da pasta /blueprints.
3. **Configurações de API:**
    * Obtenha sua API Key no Google AI Studio.
    * Configure as credenciais de conexão do PostgreSQL no módulo do Make.
    * Crie um bot no Telegram via @BotFather para obter o Token.
4. **Mobile:** No MacroDroid, configure o envio de requisição HTTP (POST) para a URL do Webhook gerada no Make.

---

### **Resultados Obtidos**

* **Zero intervenção manual:** O sistema categoriza 100% dos gastos sem necessidade de interação humana.
* **Dados Estruturados:** Banco de dados normalizado e pronto para integração com ferramentas de visualização como Looker Studio ou Power BI.
* **Insights Inteligentes:** Feedback financeiro qualitativo baseado em dados reais, auxiliando na tomada de decisão.

---

### **Autor**

**Danillo**

* Graduando em Análise e Desenvolvimento de Sistemas (ADS).
* Foco em Automação, Integrações de API e Engenharia de Dados.
