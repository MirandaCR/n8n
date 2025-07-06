# 🤖 Proyecto n8n - Chatbot IA Multimodal WhatsApp

Este flujo de trabajo permite la creación de un Asistente de IA que responde a mensajes de texto, imágenes o notas de voz recibidas a través de WhatsApp. El bot interpreta las entradas con IA generativa y responde en el mismo formato (texto o audio). Incluye análisis de imágenes mediante GPT-4o.

---

## 🚀 Funcionalidades principales

✅ Responde a mensajes de **texto** con IA generativa.  
✅ Transcribe notas de voz y responde en formato de texto o audio.  
✅ Analiza imágenes recibidas con IA y genera respuestas en texto.  
✅ Soporte para conversación contextual mediante memoria de IA.   

---

## 🛠️ Estructura del Flujo

### 📲 WhatsApp Trigger
- **Escucha mensajes entrantes** en WhatsApp (texto, audio o imagen).
- Identifica el tipo de contenido recibido (Switch):
  - `Audio` 🎙️
  - `Texto` 💬
  - `Imagen` 🖼️

---

## 💬 Procesamiento de Texto

1. **Set Fields**: Extrae el texto recibido.
2. **AI Agent**:
   - Modelo: GPT-4.1-mini (OpenAI Chat).
   - Mantiene contexto usando `Simple Memory`.
3. **Respuesta**:
   - Si la IA genera texto ➡️ envía mensaje de texto por WhatsApp.
   - Si la IA genera instrucción de audio ➡️ genera respuesta en audio.

---

## 🎙️ Procesamiento de Audio

1. **Obtener URL**: Descarga el audio recibido.
2. **Transcribe**: Convierte el audio a texto usando OpenAI.
3. **Generación de respuesta**:
   - El texto transcrito es interpretado por la IA (AI Agent).
4. **Respuesta**:
   - Si se define respuesta en texto ➡️ envía por WhatsApp.
   - Si se solicita respuesta en audio:
     - Genera el audio (OpenAI Text to Speech).
     - Ajusta formato MIME (Code Node).
     - Envía respuesta en formato de audio.

---

## 🖼️ Procesamiento de Imágenes

1. **Obtiene Imagen**:
   - Descarga la imagen recibida.
   - Extrae el texto del caption (si existe).
2. **Análisis IA (OpenAI Vision)**:
   - Analiza el contenido visual (modelo GPT-4o-mini).
3. **Respuesta**:
   - Envía texto interpretativo como respuesta en WhatsApp.

---

## 📚 Requisitos Previos

✅ Configurar credenciales:
- WhatsApp Business API.
- OpenAI API Key.
- Header Auth para descargas de medios.

✅ Tener acceso a los nodos:
- `n8n-nodes-base.whatsApp`
- `n8n-nodes-base.httpRequest`

---

## ⚙️ Tecnologías Utilizadas

- **n8n** - Automatización low-code.
- **OpenAI GPT-4.1-mini & GPT-4o-mini** - IA generativa.
- **WhatsApp API** - Comunicación bidireccional con usuarios.

---

## 💡 Posibles Mejoras

✅ Incluir validación de archivos multimedia.  
✅ Añadir procesamiento de documentos (PDF, Docs).  
✅ Incorporar generación de imágenes como respuesta.  
✅ Soporte multilenguaje.

---

## 🧩 Diagrama Simplificado

```plaintext
[WhatsApp Trigger]
        ↓
[Switch → Tipo de Mensaje]
        ↓
┌───────────── Texto ───────────────┐
│    [Set Fields → Extraer Texto]   │
│               ↓                   │
│      [AI Agent (Chat)]            │
│               ↓                   │
│      [If → ¿Respuesta en audio?]  │
│        ├─▶ [Generar Audio IA]     │
│        │         ↓                │
│        │    [Ajustar MIME]        │
│        │         ↓                │
│        │    [Enviar Audio]        │
│        └───▶ [Enviar Texto]       │
└───────────────────────────────────┘

┌───────────── Audio ───────────────┐
│   [Obtener URL del Audio]         │
│               ↓                   │
│   [Descargar Audio (HTTP)]        │
│               ↓                   │
│   [Transcribir Audio (OpenAI)]    │
│               ↓                   │
│   [Set Fields → Guardar Texto]    │
│               ↓                   │
│   [AI Agent (Chat)]               │
│               ↓                   │
│   [If → ¿Respuesta en audio?]     │
│        ├─▶ [Generar Audio IA]     │
│        │         ↓                │
│        │    [Ajustar MIME]        │
│        │         ↓                │
│        │    [Enviar Audio]        │
│        └───▶ [Enviar Texto]       │
└───────────────────────────────────┘

┌──────────── Imagen ───────────────┐
│   [Set Fields → Extraer Caption]  │
│               ↓                   │
│   [Obtener URL Imagen]            │
│               ↓                   │
│   [Descargar Imagen (HTTP)]       │
│               ↓                   │
│   [Analizar Imagen (GPT-4o-mini)] │
│               ↓                   │
│   [Enviar Respuesta Texto]        │
└───────────────────────────────────┘

```

![Flujo Bot](https://raw.githubusercontent.com/MirandaCR/n8n/refs/heads/main/Bot%20de%20Whatsapp/Images/Flujo_n8n_BotWhatsapp.png)