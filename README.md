# Curso Completo de Inteligencia Artificial (IA)

- Realizado por: Hedy Sánchez
- Profesora: Maillet Altube

Este repositorio contiene un curso completo de Inteligencia Artificial organizado por niveles: principiante, intermedio y experto. Incluye teoría didáctica dictada, ejemplos de código explicados, instrucciones de uso, enlaces a videos en español y modelos de IA gratuitos y descargables.

## Navegación
- [Guía del Curso](00-guia-del-curso.md)
- [Nivel Principiante](principiante/unidad1-introduccion-ia/pincipiante.md)
- [Nivel Intermedio](principiante/unidad1-introduccion-ia/intermedio.md)
- [Nivel Experto](principiante/unidad1-introduccion-ia/experto.md)
- [Modelos y recursos descargables](principiante/unidad1-introduccion-ia/modelos.md)
- [Recursos adicionales](principiante/unidad1-introduccion-ia/recursos.md)

---
Para dudas o colaboración: hwusjewJw194 (Hedy Sánchez)

---
## 🚨🚨Instrucciones Para Instalar Ollama

**Ollama** es una herramienta que te permite ejecutar modelos de IA grandes directamente en tu computadora, sin necesidad de internet o conexión a servidores externos.

---

## ✅ Requisitos del Sistema

Antes de comenzar, asegúrate de tener:

- **Computadora Windows, Mac o Linux** 🖥️
- **Al menos 8 GB de RAM** (16 GB recomendado) 🧠
- **Espacio en disco:** 10-50 GB según el modelo (depende del modelo que instales) 💾
- **Conexión a internet** (solo para la descarga) 🌐

Si tienes GPU (NVIDIA o AMD), Ollama la usará automáticamente para mejor rendimiento ⚡

---

## 🔧 Instalación por Sistema Operativo

### 📱 **En Windows**

1️⃣ **Descarga el instalador**
   - Ve a: `https://ollama.ai/download`
   - Descarga **Ollama-Windows.exe**

2️⃣ **Instala ejecutando el archivo**
   - Haz doble clic en `Ollama-Windows.exe`
   - Sigue el asistente de instalación
   - Ollama se agregará a tu menú de inicio

3️⃣ **Verifica la instalación**
   ```cmd
   ollama --version
   ```

---

### 🍎 **En macOS**

1️⃣ **Descarga Ollama**
   ```bash
   # O descárgalo directamente desde https://ollama.ai/download
   ```

2️⃣ **Instala usando Homebrew (recomendado)**
   ```bash
   brew install ollama
   ```

3️⃣ **Si lo descargaste manualmente**
   - Abre el archivo `.dmg`
   - Arrastra Ollama a la carpeta "Aplicaciones"

4️⃣ **Verifica la instalación**
   ```bash
   ollama --version
   ```

---

### 🐧 **En Linux**

1️⃣ **Instalación automática**
   ```bash
   curl https://ollama.ai/install.sh | sh
   ```

2️⃣ **O instalación manual:**
   ```bash
   # Descarga la última versión
   sudo wget https://github.com/jmorganca/ollama/releases/download/v0.1.32/ollama-linux-x86_64 -O /usr/local/bin/ollama
   
   # Dale permisos de ejecución
   sudo chmod +x /usr/local/bin/ollama
   ```

3️⃣ **Verifica la instalación**
   ```bash
   ollama --version
   ```

---

## 🎯 Primeros Pasos con Ollama

### **Inicia el servicio de Ollama**

**En Windows:** 
- Abre Ollama desde el menú de inicio (se ejecutará como servicio) 

**En macOS/Linux:**
```bash
ollama serve
```

✅ Verás: `Listening on 127.0.0.1:11434`

---

## 📥 Descargar tu Primer Modelo

### **Modelos Disponibles** 🤖

| Modelo | Tamaño | Velocidad | Memoria |
|--------|--------|-----------|---------|
| **Llama 2** | 3.5 GB | ⚡⚡ Rápido | 8 GB |
| **Mistral** | 4 GB | ⚡⚡ Rápido | 8 GB |
| **Neural Chat** | 4 GB | ⚡⚡⚡ Muy rápido | 8 GB |
| **Llama 2 13B** | 7 GB | ⚡ Moderado | 16 GB |
| **Mixtral** | 26 GB | ⚡ Moderado | 32 GB |

### **Descarga un Modelo** 📥

Abre **otra terminal/cmd** (mantén la primera ejecutando `ollama serve`) y escribe:

```bash
# Descargar Llama 2 (recomendado para comenzar)
ollama pull llama2

# O descarga Mistral
ollama pull mistral

# O descarga Neural Chat
ollama pull neural-chat
```

⏳ Esto puede tardar varios minutos dependiendo de tu conexión

---

## 💬 Comienza a Usar Ollama

### **Desde la Terminal/CMD**

```bash
ollama run llama2
```

Ahora puedes escribir preguntas:

```
>>> ¿Cuál es la capital de Francia?

La capital de Francia es París, una hermosa ciudad ubicada en el norte
central del país...

>>> Escribe una poesía sobre la programación

(El modelo escribirá una poesía...)

>>> /bye  # Para salir
```

---

## 🌐 Usa Ollama con una Interfaz Gráfica

### **Opción 1: Open WebUI** (🌟 Recomendado)

```bash
# Instala Open WebUI con Docker
docker run -d -p 3000:8080 --gpus all -v open-webui:/app/backend/data --name open-webui ghcr.io/open-webui/open-webui:latest
```

Luego abre: `http://localhost:3000` en tu navegador 🌐

### **Opción 2: Ollama Web**

Después de descargar un modelo, abre:

```
http://localhost:11434
```

---

## 🔗 Usa Ollama desde Python

```python
import requests
import json

# Conecta a Ollama
url = "http://localhost:11434/api/generate"

# Prepara tu pregunta
payload = {
    "model": "llama2",
    "prompt": "Escribe un haiku sobre la IA",
    "stream": False
}

# Envía la solicitud
response = requests.post(url, json=payload)
resultado = response.json()

print(resultado['response'])
```

---

## 🐍 Usa Ollama desde JavaScript/Node.js

```javascript
const fetch = require('node-fetch');

async function chatConOllama() {
    const response = await fetch('http://localhost:11434/api/generate', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
            model: 'llama2',
            prompt: '¿Qué es la programación?',
            stream: false
        })
    });
    
    const data = await response.json();
    console.log(data.response);
}

chatConOllama();
```

---

## 🆘 Solución de Problemas

### ❌ "Ollama no se reconoce como comando"
```bash
# Windows: Reinicia tu CMD o PowerShell
# Linux/Mac: Agrega a tu PATH
export PATH="/usr/local/bin:$PATH"
```

### ❌ "No hay espacio en disco"
Los modelos se guardan en:
- **Windows:** `C:\Users\[usuario]\.ollama\models`
- **Mac:** `~/.ollama/models`
- **Linux:** `~/.ollama/models`

### ❌ "Muy lento"
- Descarga un modelo más pequeño (Neural Chat, Mistral)
- Asegúrate de que tu GPU se esté usando
- Aumenta la RAM disponible

### ❌ "Error de conexión"
```bash
# Verifica que Ollama esté corriendo
ollama serve
```

---

## 📚 Comandos Útiles de Ollama

```bash
# Ver modelos descargados
ollama list

# Eliminar un modelo para liberar espacio
ollama rm llama2

# Ver estado del servicio
ollama ps

# Crear un modelo personalizado (avanzado)
ollama create mimodelo -f Modelfile
```

---

## 🎉 ¡Listo!

¡Has instalado **Ollama** exitosamente! 🚀 Ahora puedes ejecutar IA potente directamente en tu computadora, sin enviar datos a internet.
