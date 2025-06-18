# 🧠 Proyecto de Scraping Inteligente con n8n: Estrategias de TradingView

## 🎯 Objetivo

Extraer automáticamente estrategias publicadas en la sección de scripts de [TradingView](https://www.tradingview.com/scripts/?script_type=strategies) utilizando flujos automatizados en **n8n** y aplicar procesamiento con **inteligencia artificial (IA)** para clasificar y analizar el contenido extraído.

---

## 🛠️ Herramientas Utilizadas

- ⚙️ [n8n](https://n8n.io/) - Plataforma de automatización de workflows (open source)
- 🌐 HTTP Request & HTML Extract - Para el scraping de datos HTML
- 🔄 Flujo de paginación automática hasta la página 5
- 🧩 OpenAI API - Para análisis semántico y clasificación de estrategias
- 📦 Google Sheets - Para almacenar los resultados

---

## 🧬 Flujo General del Proyecto

```plaintext
[Start]
   ↓
[Set: Paginación dinámica]
   ↓
[HTTP Request con paginación]
   ↓
[HTML Extract: Estratégia, Creador, descripción, Fecha, URL]
   ↓
[IA: Formato y análisis de contenido con OpenAI]
   ↓
[Guardar en Google Sheets]

```

![Flujo Scraping n8n](https://github.com/MirandaCR/n8n/blob/main/Scraping%20Estrategias%20de%20Trading/Images/Flujo_n8n_Scraping.png?raw=true)
