# 🎹 GL Bias Slicer

**GL Bias Slicer** é uma aplicação web interativa para o **ensino e prática de progressões harmônicas** integradas a partituras (MusicXML) e faixas de áudio (MP3). Roda inteiramente no navegador, sem instalação de servidor ou dependências locais.

Desenvolvido pelo **Professor Glauber Santiago — DAC/UFSCar**
🔗 [servidores.ufscar.br/glauber/](https://servidores.ufscar.br/glauber/) • [sites.google.com/view/glauberia](https://sites.google.com/view/glauberia)

---

## 🚀 Funcionalidades Principais

### 🎼 Grade Harmônica com Partitura
- **Carregamento de MusicXML** (`.mxml`, `.musicxml`, `.xml`, `.mxl`): visualize a melodia em tempo real via **OpenSheetMusicDisplay (OSMD)**, com a partitura fatiada acima de cada compasso da grade.
- **Divisão de Compassos**: dê duplo clique em qualquer compasso para dividi-lo ao meio (dois acordes por compasso) ou reverter para um acorde único.
- **Paleta de Acordes**: selecione rapidamente a **Fundamental** (C, D, E…) e o **Tipo de Acorde** (`maj7`, `9`, `7b9`, `m7`, `m7b5`, `dim7`) pelos botões laterais.

### ⌨️ Digitação Direta de Acordes (sem caixa de texto)
Com um slot de acorde selecionado (borda roxa), basta digitar no teclado físico:

| Tecla(s) | Ação |
|---|---|
| `A`–`G` | Seleciona a fundamental |
| `b` | Adiciona bemol |
| `#` ou `s` | Adiciona sustenido |
| `m` | Tipo `m7` |
| `ma` | Tipo `maj7` |
| `d` | Tipo `dim7` |
| `7` | Tipo `9` / `7b9` |
| `Espaço` / `Enter` | Confirma com o melhor palpite |
| `Backspace` | Corrige o último caractere |
| `Esc` | Cancela a entrada |

O acorde é inserido automaticamente quando a combinação digitada resolve para uma única opção.

### 📋 Copiar e Colar Compassos
- **Seleção por faixa**: `Shift + Clique` para selecionar um intervalo contínuo.
- **Seleção múltipla**: `Ctrl + Clique` (ou `Cmd + Clique`) para compassos não-contíguos.
- **Atalhos de teclado**: `Ctrl + C` para copiar e `Ctrl + V` para colar a partir do compasso de destino.

### 🔊 Mixer e Player de Áudio Embutido
- **Síntese FM interna** (Web Audio API): geração de acordes em tempo real com timbre de piano elétrico via síntese FM de 2 operadoras (Carrier 1:1, Modulator 1:14) com ADSR completo.
- **Voicing inteligente**: fundamental uma oitava abaixo, extensões distribuídas na faixa G3–B4 para evitar colisões de voz.
- **Volume escalado dinamicamente** para prevenir clipping em acordes com muitas notas.
- **Estilo de acompanhamento**: Bossa 1, Bossa 2, Samba, Jazz Swing e Balada.
- **Controles independentes de volume**: Base Harmônica (síntese) e MP3 de acompanhamento.
- **Reverb**: convolução de áudio (Web Audio API) com slider dedicado.
- **BPM**: controle de andamento de 60 a 240 BPM.

---

## 📂 Exportação e Importação (Central de Arquivos)

Clique em **Exportar / Importar** para acessar todos os formatos disponíveis:

| Formato | Descrição |
|---|---|
| **Projeto (.txt)** | Salva o estado completo em JSON para continuar editando depois |
| **Embed Moodle (HTML)** | Bloco HTML independente com áudio Base64 embutido (WAV ou MP3), pronto para colar no Moodle |
| **Áudio (.wav)** | Renderiza e baixa a faixa completa de acompanhamento em WAV de alta qualidade |
| **Grade Visual (.png)** | Exporta a grade em imagem com título, autor, partitura fatiada acima de cada acorde e 8 colunas por linha |
| **Tabela Markdown (.md)** | Progressão harmônica formatada em tabelas GitHub Markdown |
| **MusicXML (.musicxml)** | Exporta a partitura com cifras nativas `<harmony>`, importável em MuseScore, Sibelius e Finale |
| **Band in a Box (BIAB)** | Importa e exporta no formato padrão de cifras do BIAB (ex: `\| Ebmaj7 \| Fm7 Bb7 \|`) |

---

## 🛠️ Como Executar

O **GL Bias Slicer** é um app totalmente *client-side*. Não requer servidor backend.

**Opção 1 — Abrir direto no navegador:**
```
Dê duplo clique em index.html
```

**Opção 2 — Servidor estático local (recomendado para evitar restrições CORS):**
```bash
# Python 3
python -m http.server 8080

# Node.js (npx)
npx serve .

# VS Code: extensão "Live Server"
```

Depois acesse `http://localhost:8080` no navegador.

> **Nota:** para carregar os arquivos padrão de demonstração (`Melodia para II V.mxl` e `Melodia para II V Sax soprano.mp3`) automaticamente, mantenha-os no mesmo diretório do `index.html`.

---

## ⚙️ Tecnologias

| Tecnologia | Uso |
|---|---|
| HTML5 + Vanilla JavaScript | Estrutura e lógica da aplicação |
| Tailwind CSS (CDN) | Estilização responsiva com suporte a dark mode |
| Font Awesome | Ícones da interface |
| [OpenSheetMusicDisplay (OSMD)](https://opensheetmusicdisplay.org/) | Renderização de partituras MusicXML |
| [JSZip](https://stuk.github.io/jszip/) | Geração de arquivos comprimidos |
| [Lame.js](https://github.com/zhuker/lamejs) | Codificação de áudio MP3 no navegador |
| Web Audio API | Síntese FM de acordes, reverb por convolução, mixagem e renderização offline |

---

## 📸 Interface

A interface conta com:
- **Modo Escuro/Claro** com alternância pelo botão no cabeçalho
- **Partitura sincronizada**: cada compasso da grade exibe o trecho correspondente da partitura acima do acorde
- **Feedback visual**: o tipo de acorde selecionado fica destacado em roxo na paleta lateral
- **Layout responsivo** para desktop e telas médias

---

## 📄 Licença

Uso educacional livre. Desenvolvido no contexto do **Departamento de Artes e Comunicação (DAC)** da **Universidade Federal de São Carlos (UFSCar)**.

---

*Desenvolvido pelo Professor Glauber Santiago — DAC/UFSCar*
*[servidores.ufscar.br/glauber/](https://servidores.ufscar.br/glauber/) • [sites.google.com/view/glauberia](https://sites.google.com/view/glauberia)*
