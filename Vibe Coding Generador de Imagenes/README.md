# 🎨 Proyecto: Bolt_Imagenes

Este proyecto permite generar imágenes a partir de un texto descriptivo utilizando **OpenAI DALL·E** desde un backend en **n8n**, integrado con un frontend visual desarrollado en **Bolt (Vibecoding)**. Ideal para apps creativas, interfaces educativas o herramientas de diseño.

---

## 🧠 Descripción General

- **Frontend:** Bolt (Vibecoding)
- **Backend:** n8n
- **Modelo de IA:** `OpenAI - Image (DALL·E)`
- **Funcionalidad:** Generación de imágenes desde texto (text-to-image)

---

## 🔗 Flujo del proceso

```plaintext
[Frontend (Bolt)]
        ↓ POST /webhook
[n8n: Webhook]
        ↓
[OpenAI: Generate an image]
        ↓
[Respond to Webhook (binary)]
        ↓
[Frontend renderiza la imagen generada]
```

# Back - n8n
![Back GPT Loveable](https://raw.githubusercontent.com/MirandaCR/n8n/refs/heads/main/Vibe%20Coding%20Generador%20de%20Imagenes/Images/Flujo%20generador%20de%20Imagenes.png)

# Front - Loveable
![Front GPT Loveable](https://raw.githubusercontent.com/MirandaCR/n8n/refs/heads/main/Vibe%20Coding%20Generador%20de%20Imagenes/Images/Generador%20de%20Imagenes.png)

