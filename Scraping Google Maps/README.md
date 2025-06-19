# 📬 Proyecto de Scraping de Contactos en Google Maps con n8n

## 🎯 Objetivo
Automatizar la obtención de **URLs** y **correos electrónicos** de las universidades de Monterrey listadas en Google Maps.  
Cada ejecución programada:

1. Visita la página de resultados de Google Maps.  
2. Extrae todos los enlaces externos de cada universidad.  
3. Filtra, deduplica e itera sobre cada sitio.  
4. Rastre de forma recursiva las páginas externas y extrae correos electrónicos.  
5. Devuelve un listado limpio y sin duplicados, listo para prospección o análisis.

---

## 🛠️ Herramientas y nodos clave

| Nodo n8n | Función principal | Comentario |
|----------|------------------|------------|
| **Schedule Trigger** | Lanza el flujo de forma recurrente (diario, horario, etc.). | Ajusta el intervalo en la pestaña *Rule*. |
| **HTTP Request – “Obtener elementos Maps”** | Descarga el HTML de `https://www.google.com/maps/search/universidades+monterrey/`. | Método **GET**. |
| **Code – “Extracción de Links”** | Regex `/(https:\/\/[^/]+)/g` → devuelve `{ urls }`. | Aísla los dominios externos. |
| **Split Out – “Split Out URLs”** | Separa cada URL en items individuales. | Facilita la filtración. |
| **Filter – “Filtro link”** | Elimina dominios de Google, gstatic, ggph t, schema, example. | `operator: notRegex` |
| **Remove Duplicates – “Quitar Duplicados URLs”** | Evita procesar el mismo dominio dos veces. | |
| **Split In Batches – “Iterar Páginas”** | Itera las URLs resultantes (batch size automático). | |
| **HTTP Request – “Obtener Contenido Web”** | Descarga el HTML de cada URL externa. | Método **GET**, `{{$json.urls}}`. |
| **Code – “Obtener Emails”** | Regex para emails: `\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b` → `{ emails }`. | Agrupa todos los matches. |
| **Split Out – “Split Out Emails”** | Separa cada email en un item. | |
| **Remove Duplicates – “Quitar Duplicados Emails”** | Entrega un listado final sin repeticiones. | |

---

## 🔄 Diagrama de flujo

```plaintext
[Schedule Trigger]
        ↓
[HTTP Request → Google Maps]
        ↓
[Code → Extraer URLs]
        ↓
[Split Out URLs]
        ↓
[Filter URLs]
        ↓
[Remove Duplicates URLs]
        ↓
[SplitInBatches → Iterar URL]
        ├─▶ [HTTP Request → Página externa]
        │         ↓
        │   [Code → Extraer Emails]
        │         ↓
        │   [Split Out Emails]
        │         ↓
        └───▶ [Remove Duplicates Emails] ──▶ (resultado)

```
![Flujo Scraping n8n](https://github.com/MirandaCR/n8n/blob/main/Scraping%20Google%20Maps/Images/Flujo_n8n_ScrapingMaps.png?raw=true)
