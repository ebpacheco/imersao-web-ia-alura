# 📖 Alura Album - Copa do Mundo Tech

O **Alura Album** é um álbum de figurinhas digital, interativo e moderno, projetado para celebrar grandes personalidades do mundo da tecnologia. Criado no contexto da **Imersão Alura**, o projeto reúne pioneiros e referências em áreas como Inteligência Artificial, Python, Banco de Dados, Sistemas Operacionais e Educadores/Criadores de Conteúdo de Tecnologia no Brasil.

---

## 🎯 Objetivo do Projeto

O objetivo principal é construir uma interface web imersiva e de alto padrão visual, simulando a experiência física de folhear um álbum de figurinhas. O projeto demonstra boas práticas de desenvolvimento web moderno, integrando:
1. Animações fluidas de virada de página em 3D.
2. Efeitos sonoros dinâmicos gerados em tempo real.
3. Consumo de uma API externa para carregamento dinâmico de imagens e dados das figurinhas.
4. Identidade visual premium com tema Dark Mode e detalhes futuristas/neon.

---

## 📂 Arquivos do Projeto e suas Funcionalidades

### 1. 📄 `index.html`
Responsável pela estrutura semântica e conteúdo do álbum de figurinhas.
- **Capa & Contracapa**: Páginas rígidas decoradas com elementos temáticos, incluindo efeitos de brilho 3D (Tech Sphere) e código de barras simulado.
- **Estrutura de Páginas e Slots**: Organiza o álbum em categorias bem definidas:
  - **Página 1 (IA)**: Pioneiros da Inteligência Artificial (ex: Alan Turing, Geoffrey Hinton).
  - **Página 2 (Python)**: Desenvolvedores e criadores da linguagem e ecossistema (ex: Guido van Rossum, Wes McKinney).
  - **Página 3 (Banco de Dados)**: Arquitetos de modelos e motores de banco de dados (ex: Edgar F. Codd, Salvatore Sanfilippo).
  - **Página 4 (Sistemas Operacionais)**: Criadores de sistemas fundamentais (ex: Linus Torvalds, Dennis Ritchie).
  - **Páginas 5 e 6 (Brasil Vol. 1 e Vol. 2)**: Professores, influenciadores e referências brasileiras em tecnologia (ex: Paulo Silveira, Gustavo Guanabara, Rafaela Ballerini e um slot especial para "Você").
- **Bibliotecas Externas**: Importa a biblioteca **PageFlip** via CDN para permitir a interação de livro/álbum.

### 2. ⚙️ `app.js`
Controla a lógica de interatividade, áudio e integração de dados.
- **Integração com API (`preencherFigurinhas`)**: Consome um backend FastAPI local (por padrão em `http://localhost:8000/figurinhas`) para recuperar dinamicamente as figurinhas disponíveis e exibi-las em seus respectivos slots (identificados por IDs como `#01`, `#02`, etc.).
- **Inicialização do `St.PageFlip`**: Configura as dimensões, sombras, comportamento de arraste (drag) e controle responsivo do álbum.
- **Controles de Navegação**: Mapeia as setas laterais no HTML, o arrastar do mouse/toque em dispositivos móveis, e as teclas direcionais do teclado (`ArrowLeft` e `ArrowRight`).
- **Sintetizador de Áudio (Web Audio API)**: Gera o som físico de papel virando em tempo real através da síntese de ruído branco filtrado dinamicamente com filtros passa-banda (*bandpass*) e passa-baixa (*lowpass*).
- **Controle de Som**: Permite ativar ou silenciar (*mute*) os efeitos sonoros da aplicação.

### 3. 🎨 `style.css`
Define todo o design visual e a experiência estética do usuário.
- **Estilo Geral & Tipografia**: Utiliza as fontes modernas *Inter* e *Outfit* do Google Fonts e uma paleta de cores escura e sofisticada.
- **Identidade por Categoria**: Cada categoria possui cores e badges personalizados (ex: verde para Python, azul para Banco de Dados, amarelo/verde para o Brasil).
- **Design de Slots de Figurinhas**: Slots vazios possuem silhuetas cinzas elegantes e textos descritivos que ganham cor e brilho assim que a imagem correspondente é preenchida pelo backend.
- **Efeitos Premium**: Inclui animações de brilho pulsante, efeitos de glitch no texto do título, rotações 3D simuladas e transições suaves de hover nos botões e páginas.

---

## 🚀 Como Executar o Projeto

Para visualizar o álbum completo com todas as figurinhas carregadas, você precisará executar o **frontend** (este repositório) e o **backend** da API.

### 1. Iniciar o Frontend
Você pode abrir o arquivo `index.html` diretamente no navegador ou iniciar um servidor estático local:
- Se estiver no VS Code, pode usar a extensão **Live Server**.
- Ou via terminal com Python:
  ```bash
  python3 -m http.server 3000
  ```
  Depois, acesse `http://localhost:3000`.

### 2. Iniciar o Backend (API)
O frontend tentará se conectar à API local em `http://localhost:8000`. Para rodar o backend correspondente:
1. Certifique-se de ter o Python e as dependências instaladas (FastAPI, Uvicorn).
2. Acesse a pasta do backend e execute o servidor:
   ```bash
   cd backend/dia-3
   uvicorn main:app --reload
   ```
3. Caso a API não esteja rodando, o álbum ainda funcionará para navegação e virada de páginas, exibindo mensagens de aviso no console do navegador indicando que as figurinhas dinâmicas não puderam ser carregadas.
