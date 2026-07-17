# 🏆 Alura Album - Copa do Mundo Tech

[![Python Version](https://img.shields.io/badge/python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.14-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100.0%2B-009688.svg?style=flat&logo=FastAPI&logoColor=white)](https://fastapi.tiangolo.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

O **Alura Album** é um álbum de figurinhas digital, interativo e altamente imersivo projetado para celebrar grandes lendas e personalidades do mundo da tecnologia. Desenvolvido durante a **Imersão Alura**, o projeto recria a experiência de folhear um álbum físico diretamente no navegador, integrando efeitos 3D dinâmicos, síntese de som em tempo real e integração com API.

---

## 📸 Demonstração Visual
> *Insira aqui um GIF ou Screenshot do seu álbum em funcionamento!*

---

## ✨ Funcionalidades Principais

*   **📖 Interação 3D Imersiva (PageFlip):** Utiliza a biblioteca `St.PageFlip` com lógica customizada de arraste (*drag-and-drop*) e toque para simular a sensação física de virar páginas.
*   **🔊 Síntese de Áudio em Tempo Real (Web Audio API):** **Destaque técnico!** O som das páginas virando não é um arquivo estático (`.mp3` ou `.wav`). Ele é sintetizado via código em tempo real através da geração de ruído branco modulado por filtros passa-banda (*bandpass*) e passa-baixa (*lowpass*). Isso reduz o tempo de carregamento e demonstra uso avançado de APIs do navegador.
*   **🔌 Integração Dinâmica com API:** O frontend consome assíncronamente um backend local para preencher as figurinhas de forma dinâmica. Caso o backend esteja offline, a aplicação executa um *fallback* gracioso, permitindo a navegação normal.
*   **🎨 Design Premium (Dark & Neon Mode):** Estilização moderna e refinada utilizando variáveis CSS (custom properties), fontes premium do Google Fonts (*Inter* e *Outfit*), efeitos holográficos e animações neon.

---

## 🛠️ Tecnologias Utilizadas

### Frontend:
*   **HTML5 Semântico**
*   **CSS3 Avançado:** Variáveis nativas, Flexbox, CSS Grid, efeitos de Glassmorphism e Glow Neon.
*   **Vanilla JavaScript (ES6+):** Manipulação assíncrona do DOM e requisições HTTP (`fetch`).
*   **Web Audio API:** Síntese programática de áudio.
*   **PageFlip Library:** Engine para transição de páginas em 3D.

### Backend:
*   **Python:** Linguagem robusta e performática para construção da API.
*   **FastAPI:** Framework moderno, de alta performance e rápida codificação.
*   **Uvicorn:** Servidor ASGI ultrarrápido para execução do projeto.
*   **FastAPI StaticFiles:** Para servir as imagens das figurinhas localmente de forma otimizada.

---

## 📂 Arquitetura do Projeto

O projeto adota uma arquitetura desacoplada e limpa:

```text
/imersao-web-ia-alura
├── front/                   # Código-fonte do Frontend
│   ├── back/                # Código-fonte do Backend (API e Assets)
│   │   ├── figurinhas/      # Imagens estáticas das figurinhas
│   │   └── main.py          # Arquivo principal da API FastAPI
│   ├── app.js               # Lógica de interação, áudio e integração
│   ├── index.html           # Estrutura semântica e páginas do álbum
│   ├── style.css            # Estilos, variáveis de cores e efeitos visuais
│   └── .gitignore           # Ignora arquivos de ambiente virtual e cache (.venv/)
```

---

## 🚀 Como Executar o Projeto Localmente

### 1. Iniciar o Backend (FastAPI)
1. Certifique-se de que possui o Python instalado.
2. Abra o seu terminal e navegue até a pasta do backend:
   ```bash
   cd front/back
   ```
3. Ative o ambiente virtual:
   * **Linux/macOS:**
     ```bash
     source ../../back/.venv/bin/activate
     ```
   * **Windows:**
     ```cmd
     ..\..\back\.venv\Scripts\activate
     ```
     *(Caso prefira criar um ambiente virtual dedicado nessa pasta: `python -m venv .venv && source .venv/bin/activate && pip install fastapi uvicorn`)*
4. Inicie o servidor:
   ```bash
   uvicorn main:app --reload
   ```
   A API estará rodando no endereço: [http://localhost:8000](http://localhost:8000).

### 2. Iniciar o Frontend
Com o backend rodando:
1. Abra um **segundo terminal** na raiz da pasta `front`:
   ```bash
   cd front
   ```
2. Inicie um servidor HTTP local simples com Python:
   ```bash
   python3 -m http.server 3000
   ```
3. Abra seu navegador e acesse:
   [http://localhost:3000](http://localhost:3000)

---

## 🎯 Destaques para Recrutadores

*   **Separação de Responsabilidades (SPA/API):** Arquitetura moderna de microsserviços onde o Frontend interage com o Backend de forma totalmente assíncrona.
*   **Web Audio API:** Uso avançado de processamento de sinais digitais no navegador, evitando requisições desnecessárias por arquivos de áudio pesados.
*   **Resiliência (Fallback):** Tratamento de exceções e erros de conectividade de rede na comunicação com a API para que o site continue utilizável mesmo offline.
*   **Clean Code e Organização:** Diretórios limpos com arquivos organizados de forma semântica e arquivo `.gitignore` configurado.
