# 💖 Proyecto: Loveable_GPT (n8n + Vibecoding)

Este flujo integra una interfaz web desarrollada en **Loveable (Vibecoding)** con un backend automatizado mediante **n8n**. Permite enviar prompts desde un frontend y recibir respuestas generadas por un modelo de lenguaje de OpenAI a través de una API tipo Webhook.

---

## 🧠 Descripción General

- **Frontend:** Loveable (Vibecoding)
- **Backend:** n8n
- **Modelo de IA:** `gpt-4o-mini` de OpenAI
- **Método de interacción:** Webhook (API REST)
- **Funcionalidad principal:** Recepción de un prompt, generación de respuesta textual y devolución al frontend en formato JSON limpio.

---

## 🔗 Flujo de datos

```plaintext
[Frontend (Loveable)]
        ↓ POST /webhook
[n8n: Webhook]
        ↓
[Langchain: AI Agent]
        ↓
[OpenAI Chat Model: GPT-4o-mini]
        ↓
[Respond to Webhook]
        ↓
[Frontend recibe JSON con respuesta]
```

# Back - n8n
![Back GPT Loveable](https://raw.githubusercontent.com/MirandaCR/n8n/refs/heads/main/Vibe%20Coding%20Bot%20de%20Gobierno/Images/Flujo_ChatGPT.png)

# Front - Loveable
![Front GPT Loveable](https://raw.githubusercontent.com/MirandaCR/n8n/refs/heads/main/Vibe%20Coding%20Bot%20de%20Gobierno/Images/Bot_ChatGPT.png)

