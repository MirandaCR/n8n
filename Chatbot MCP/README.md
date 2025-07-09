# 🧠 MCP Client - Chat AI Workflow

Este flujo conecta un agente de inteligencia artificial con herramientas específicas a través de **n8n + Langchain**, utilizando la arquitectura **MCP (Model Context Protocol)**. Permite al agente conversar y ejecutar acciones sobre herramientas como Gmail, Airtable y workflows de scrapping, de forma dinámica e integrada.

---

## 📌 Objetivo

Permitir que el agente de IA entienda y responda a mensajes de chat, delegando operaciones a herramientas externas conectadas mediante el protocolo **MCP**, tales como:

- 📬 **Gmail**: gestión de correos.
- 📊 **Airtable**: consulta o edición de bases de datos.
- 🕸️ **Scrapping Trading**: ejecución de un flujo para obtener estrategias de trading de ViewTrading.

---

## 🔧 Estructura del Flujo

```plaintext
[When chat message received]
        ↓
       [AI Agent]
        ↓
  ┌────────────┬───────────────┬────────────┐
  │            │               │            │
[Gmail MCP] [Airtable MCP] [Scrapping Tool]
```

## Flujo MCP

## MCP Gmail

## MCP Airtable

## Flujo de Scrapping

![Scrapping](https://raw.githubusercontent.com/MirandaCR/n8n/refs/heads/main/Scraping%20Estrategias%20de%20Trading/Images/Flujo_n8n_Scraping.png)