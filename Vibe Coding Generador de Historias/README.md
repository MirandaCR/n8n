# 📚 Proyecto: Loveable_GeneradorHistorias

Este flujo automatizado permite generar historias divertidas de 30 palabras para niños, utilizando un prompt personalizado que incluye un **nombre**, un **animal** y un **deporte**. El flujo está integrado con un frontend desarrollado en **Loveable (Vibecoding)**, y el backend se ejecuta en **n8n** con acceso a un modelo de lenguaje GPT.

---

## 🧠 Descripción General

- **Frontend:** Loveable (Vibecoding)
- **Backend:** n8n
- **Modelo de IA:** `gpt-4o-mini` de OpenAI
- **Funcionalidad:** Generación de historias creativas para niños basadas en entradas personalizadas

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
[Frontend recibe JSON con historia generada]
```

# Back - n8n
![Back GPT Loveable](https://raw.githubusercontent.com/MirandaCR/n8n/refs/heads/main/Vibe%20Coding%20Generador%20de%20Historias/Images/Flujo%20generador%20de%20historias.png)

# Front - Loveable
![Front GPT Loveable](https://raw.githubusercontent.com/MirandaCR/n8n/refs/heads/main/Vibe%20Coding%20Generador%20de%20Historias/Images/Generador%20de%20Historias.png)

