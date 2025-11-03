# 📝 PPT-Translate

[![License](https://img.shields.io/github/license/QuantumNovice/ppt-translate)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.111+-green.svg)](https://fastapi.tiangolo.com/)
[![Transformers](https://img.shields.io/badge/🤗_Transformers-Enabled-orange.svg)](https://huggingface.co/docs/transformers)
[![Gradio](https://img.shields.io/badge/UI-Gradio%20App-lightgrey.svg)](https://gradio.app/)
[![Build](https://img.shields.io/github/actions/workflow/status/QuantumNovice/ppt-translate/main.yml?branch=main)](https://github.com/QuantumNovice/ppt-translate/actions)
[![Stars](https://img.shields.io/github/stars/QuantumNovice/ppt-translate?style=social)](https://github.com/QuantumNovice/ppt-translate/stargazers)

## 🌐 Overview

Translate PowerPoint presentations or plain text between **Korean ↔ English**.  
Built on FastAPI and Hugging Face Transformers, with an optional Gradio UI.

---

## 🚀 Quick Start

```bash
git clone https://github.com/QuantumNovice/ppt-translate.git
cd ppt-translate
pip install -r requirements.txt
uvicorn app:app --reload
```

Then open your browser at:  
👉 http://127.0.0.1:8000/docs

For the Gradio UI:

```bash
python app.py
```

---

## 🧩 API Endpoints

| Method | Endpoint               | Description                               |
| ------ | ---------------------- | ----------------------------------------- |
| `POST` | `/translate`           | Translate text between Korean and English |
| `POST` | `/ppt`                 | Upload a `.pptx` for translation          |
| `GET`  | `/download/{filename}` | Download the translated file              |

---

## 💡 Example Requests

### Python

```python
import requests
r = requests.post("http://127.0.0.1:8000/translate",
                  json={"text": "안녕하세요", "src_lang": "ko"})
print(r.json())
```

### JavaScript (Node)

```js
import fetch from "node-fetch";

const res = await fetch("http://127.0.0.1:8000/translate", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ text: "Hello world", src_lang: "en" }),
});
console.log(await res.json());
```

### cURL

```bash
curl -X POST "http://127.0.0.1:8000/translate"   -H "Content-Type: application/json"   -d '{"text": "안녕하세요", "src_lang": "ko"}'
```

---

## 🧠 Models Used

| Direction        | Model                                                              |
| ---------------- | ------------------------------------------------------------------ |
| Korean → English | `Helsinki-NLP/opus-mt-ko-en`                                       |
| English → Korean | `seongs/ke-t5-base-aihub-koen-translation-integrated-10m-en-to-ko` |

---

## 🛠 Stack

- FastAPI
- Transformers
- python-pptx
- Gradio
- Uvicorn

---

## 🧪 Development

### Run tests

```bash
pytest
```

### Run with Docker

```bash
docker build -t ppt-translate .
docker run -p 8000:8000 ppt-translate
```

---

## 📜 License

MIT License © [QuantumNovice](https://github.com/QuantumNovice)
