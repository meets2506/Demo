
# 📦 Qualcomm Nano LLM Packaging Architecture – Demo README

## Overview

This system delivers a lightweight, on-device AI-powered Q&A experience. It utilizes a compact language model (QwenNano LLM), a vector database for semantic search, and a BM25 database for keyword search. Integrated into an Android app, it enables real-time question answering with support for speech input and admin-level control via a web portal.

---

## ✅ Features

- 🤖 **Embedded LLM:** QwenNano LLM integrated via `libLlama.so`
- 🔍 **Hybrid Search:** Vector + BM25 keyword-based information retrieval
- 📱 **Android App:** Mobile interface to input and receive answers
- 🗣️ **Voice Support:** Speech-to-text using `libWhisper.so`
- 🛠️ **Admin Portal:** Manage users, repositories, devices, and versions
- 📂 **File Management:** Push/Pull file functionality for documents and data

---

## 📂 Architecture Summary

```
User Input | |---> Voice-to-Text (Whisper STT) |---> Embedded Inference Engine | | | +---> QwenNano LLM | |---> Backend Services | +---> Vector Search Engine +---> BM25 Document Search
```

---

## 🧠 LLM Model

- **Model Name:** QwenNano LLM
- **Version:** v1.0.3
- **Type:** Lightweight Transformer-based Language Model
- **Library:** Loaded through `libLlama.so` (aka `libInterplayInference.so`)
- **Core Functions:**
  - `load_model()`
  - `predict()`
  - `generate_vector()`

---

## 📦 Components & Shared Libraries

| Component          | Description                                           |
|-------------------|-------------------------------------------------------|
| `libLlama.so`      | Loads and runs the LLM model                         |
| `libAppServer.so`  | API communication layer between components           |
| `libWhisper.so`    | Speech-to-text processing module                     |
| `Vector Database`  | Stores vector embeddings for semantic search         |
| `Bm25 Database`    | Keyword-based document retrieval                     |
| `QwenNano LLM`     | Lightweight embedded language model                  |
| `Admin Portal`     | Manages access, users, and system configurations     |

---

## 🗂️ Admin Portal Features

- 🔐 Multi-user and multi-company support
- 🖥️ Company-wise device dashboards
- 📁 Repository creation and version control
- 📄 Support for BM25/VectorStore document types
- 🧩 Device targeting with control options
- 📂 Push/Pull files to/from portal
- 📊 Track versions of:
  - LLM (QwenNano)
  - Inference Engine (`libLlama.so`)
  - Vector Database
  - BM25 Database

---

## 🧪 Workflow (Step-by-Step)

1. Launch the Android Nano App.
2. Input a question via voice or text.
3. If voice, `libWhisper.so` converts it to text.
4. Text is converted to a vector and queried:
   - Through Vector Database
   - And BM25 for keyword matching
5. App calls `predict()` via `libAppServer.so`.
6. QwenNano LLM processes the query and returns the answer.

---

## 📌 Versioning Info

| Component         | Version        |
|------------------|----------------|
| QwenNano LLM     | v1.0.3         |
| libLlama.so      | v1.2.0         |
| libWhisper.so    | v1.0.0         |
| libAppServer.so  | v1.1.1         |
| Vector DB Schema | v1.0           |
| BM25 DB Engine   | v0.9-beta      |

---

## 🚀 Getting Started for Demos

1. Deploy the Nano Android App on your device.
2. Use voice/text input to generate questions.
3. Up to 50 questions per session supported.
4. Admins can log into the portal for backend control.
5. Monitor system logs and outputs in real time.

---

## 🔧 Customization Available

- 🧠 Custom Language Models (BYOM)
- 🗃️ Multiple document source integration (PDF, websites, etc.)
- 🏢 Company-branded Admin Portal
- 🎯 OEM-level device and feature targeting

---


---

> Empowering real-time, offline intelligence on the edge with Nano AI.
