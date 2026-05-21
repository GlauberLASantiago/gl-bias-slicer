# GL Bias Slicer
**GL Bias Slicer** é uma aplicação web interativa e responsiva projetada para o ensino e prática de progressões harmônicas (cifras) integradas a partituras (MusicXML) e faixas de áudio (MP3). O projeto oferece uma interface moderna em camadas com suporte a temas claro e escuro, facilitando a edição rápida de acordes, manipulação de compassos e exportação em múltiplos formatos para plataformas como Moodle, editores de partitura (Finale, Sibelius, MuseScore) e reprodutores de mídia.
---
<img width="1889" height="931" alt="image" src="https://github.com/user-attachments/assets/be3476ea-cbcc-48bb-9f26-6c5f76654e41" />


## 🚀 Principais Funcionalidades
### 🎼 Visualização e Edição de Grade Harmônica
* **Suporte a MusicXML**: Carregue arquivos `.mxml`, `.musicxml` ou `.xml` para visualizar a melodia em tempo real através da biblioteca **OpenSheetMusicDisplay (OSMD)**.
* **Divisão de Compassos**: Dê dois cliques em qualquer compasso na grade para dividi-lo ao meio (permitindo dois acordes por compasso de 4 tempos) ou reverter para um acorde único.
* **Paleta de Acordes**: Interface rápida com botões clicáveis para selecionar a **Fundamental** (C, D, E, etc.) e o **Tipo de Acorde** (`maj7`, `9`, `7b9`, `m7`, `m7b5`, `dim7`).
### ⌨️ Reconhecimento de Acordes via Teclado (Sem Caixa de Texto)
Basta clicar em um slot de acorde (borda roxa) e digitar diretamente no teclado físico:
* **Notas Fundamentais**: Digite de `A` a `G`.
* **Acidentes**: Digite `b` para bemol, `#` ou `s` para sustenido.
* **Tipos**: Digite `m` para `m7`, `ma` para `maj7`, `d` para `dim7`, `7` para `9` / `7b9`.
* **Confirmação Inteligente**: Pressione `Espaço` ou `Enter` para preencher automaticamente com o melhor palpite, ou use o recurso de auto-inserção caso a digitação resolva para uma única opção exclusiva. Use `Backspace` para corrigir e `Esc` para cancelar.
### 📋 Copiar e Colar Compassos (Clipboard Inteligente)
* **Seleção por Faixa**: Clique em um compasso e use `Shift + Clique` em outro para selecionar um intervalo contínuo de compassos.
* **Seleção Não-Contígua**: Use `Ctrl + Clique` (ou `Cmd + Clique`) para selecionar múltiplos compassos específicos.
* **Atalhos de Teclado**: Copie o trecho com `Ctrl + C` e cole-o com `Ctrl + V` a partir do compasso de destino selecionado.
* **Visual Dinâmico**: Botões na interface atualizam seus estados ativados/desativados dinamicamente para orientar o fluxo de cópia.
### 🔊 Mixer e Player de Áudio Embutido
* **Mixagem em Tempo Real**: Ajuste volumes independentes para a **Base Harmônica** gerada eletronicamente e para o arquivo de áudio **MP3** de acompanhamento carregado pelo usuário.
* **Efeito Reverb**: Slider dedicado com processamento de convolução de áudio (Web Audio API) para criar ambiência no som sintetizado.
* **Controle de BPM**: Acelere ou desacelere a reprodução dinamicamente para se adequar ao tempo de estudo (entre 60 e 240 BPM).
---
## 📂 Formatos de Exportação e Importação (Central de Arquivos)
O botão **Exportar / Importar** abre o painel centralizado de arquivos, oferecendo suporte a:
1. **Projeto (.txt)**: Salve o progresso completo em um arquivo JSON local para continuar editando depois.
2. **Embed Moodle (HTML)**: Gera um bloco de código HTML independente contendo a tabela de acordes e o arquivo de áudio embutido diretamente como dados Base64 (WAV ou MP3 comprimido), pronto para colar no editor de páginas do Moodle.
3. **Áudio (.wav)**: Renderiza e baixa a faixa completa de acompanhamento consolidada em áudio WAV de alta qualidade.
4. **Grade Visual (.png)**: Exporta a sequência completa em uma grade de imagem de 8 colunas, incluindo título e autor, ideal para compartilhamento rápido e impressão.
5. **Tabela Markdown (.md)**: Gera a progressão harmônica formatada em tabelas simples do GitHub Markdown.
6. **MusicXML (.musicxml)**: Exporta a partitura de volta com a marcação de cifras nativa (`<harmony>`), facilitando a importação em softwares como MuseScore, Sibelius e Finale.
7. **Band in a Box (BIAB)**: Importa e exporta sequências textuais no formato padrão de cifras do software BIAB (ex: `| Ebmaj7 | Fm7 Bb7 |`).
---
## 🛠️ Como Executar o Projeto
O **GL Bias Slicer** é um aplicativo inteiramente *client-side* (roda direto no navegador). Não é necessário instalar servidores backend ou bancos de dados adicionais.
1. Baixe os arquivos do repositório.
2. Certifique-se de manter os arquivos de mídia padrão (`Melodia para II V.mxl` e `Melodia para II V Sax soprano.mp3`) no mesmo diretório do arquivo `index.html` para que sejam carregados de forma automatizada ao inicializar.
3. Dê um duplo clique no arquivo `index.html` para abrir diretamente no navegador ou utilize um servidor local estático para desenvolvimento (por exemplo: VS Code Live Server ou `python -m http.server`).
---
## ⚙️ Tecnologias Utilizadas
* **Estrutura e Lógica**: HTML5 & Vanilla JavaScript
* **Estilização**: Tailwind CSS (via CDN) & Font Awesome Icons
* **Renderização de Partituras**: [OpenSheetMusicDisplay (OSMD)](https://opensheetmusicdisplay.org/)
* **Geração de Arquivos Comprimidos**: [JSZip](https://stuk.github.io/jszip/)
* **Codificação de MP3**: [Lame.js](https://github.com/zhuker/lamejs)
* **Processamento de Áudio**: Web Audio API (OfflineAudioContext, ConvolverNode, GainNode)
