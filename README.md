# 📘 Construtor de Tutoriais LINCE

Ferramenta standalone em HTML para criação de tutoriais técnicos no padrão ABNT, com exportação para `.docx` e `.pdf`, pré-visualização em tempo real e integração com Google Drive.

---

## Índice

1. [Requisitos](#1-requisitos)
2. [Como abrir](#2-como-abrir)
3. [Interface](#3-interface)
4. [Criando um tutorial](#4-criando-um-tutorial)
5. [Tipos de bloco](#5-tipos-de-bloco)
6. [Editor de imagens](#6-editor-de-imagens)
7. [Personalizando a capa](#7-personalizando-a-capa)
8. [Mover e reordenar blocos](#8-mover-e-reordenar-blocos)
9. [Pré-visualização](#9-pré-visualização)
10. [Salvar e carregar rascunhos](#10-salvar-e-carregar-rascunhos)
11. [Google Drive](#11-google-drive)
12. [Exportar DOCX](#12-exportar-docx)
13. [Exportar PDF](#13-exportar-pdf)
14. [Atalhos de teclado](#14-atalhos-de-teclado)
15. [Perguntas frequentes](#15-perguntas-frequentes)

---

## 1. Requisitos

- Navegador moderno: **Chrome 90+**, **Edge 90+** ou **Firefox 88+**
- Nenhuma instalação necessária — o arquivo `construtor_tutorial_v11.html` é completamente autossuficiente
- Para integração com Google Drive: acesso à internet e um projeto configurado no Google Cloud (opcional)

---

## 2. Como abrir

1. Baixe o arquivo `construtor_tutorial_v12.html`
2. Abra-o diretamente no navegador (`Arquivo → Abrir` ou duplo clique)
3. O construtor carrega imediatamente, sem servidor ou instalação

> **Dica:** Para hospedar em um servidor local (necessário para o Google Drive funcionar), use:
> ```bash
> python3 -m http.server 8080
> ```
> Depois acesse `http://localhost:8080/construtor_tutorial_v11.html`

---

## 3. Interface

```
┌─────────────────────────────────────────────────────────────────┐
│ TOPBAR  [+ Nova Seção] [Exportar] [DOCX] [PDF] [Drive] [Layout] │
├──────────────┬──────────────────────────┬────────────────────────┤
│              │                          │                        │
│  PAINEL      │   EDITOR DE CONTEÚDO     │  PRÉ-VISUALIZAÇÃO      │
│  ESQUERDO    │                          │  (documento ABNT       │
│              │   Seções, subseções,     │   em tempo real)       │
│  - Metadados │   blocos de conteúdo     │                        │
│  - Capa      │                          │   ← zoom ajustável     │
│  - Sumário   │                          │                        │
│  - Lista de  │                          │                        │
│    seções    │                          │                        │
└──────────────┴──────────────────────────┴────────────────────────┘
```

### Topbar — botões principais

| Botão | Função |
|---|---|
| `+ Nova Seção` | Adiciona uma nova seção ao tutorial |
| `{} Exportar Config` | Salva o rascunho atual como `.json` |
| `📄 Gerar DOCX` | Exporta o documento Word (.docx) |
| `📷 Gerar PDF` | Abre pré-visualização para imprimir/salvar como PDF |
| `✦ Personalizar Capa` | Abre o editor de capa |
| `💾 Salvar local` | Salva rascunho `.json` no computador |
| `📁 Abrir local` | Carrega rascunho `.json` do computador |
| `☁ Google Drive` | Conecta ao Drive para salvar/abrir tutoriais |
| `▪ ▪▪ ▪` | Alterna entre os modos de layout |

---

## 4. Criando um tutorial

### Passo a passo básico

**1. Preencha os metadados** no painel esquerdo:
- **Título** — ex: `Windows 11 25H2`
- **Subtítulo** — ex: `Instalação e Configuração`
- **Autor(es)**, **Colaborador(es)**, **Orientador(es)**
- **Data** — ex: `31 de março de 2025`
- Marque `Capa` e `Sumário` conforme necessário

**2. Adicione seções** clicando em `+ Adicionar Seção` ou no botão da topbar.

**3. Nomeie a seção** no campo de título azul do editor.

**4. Adicione subseções** (opcional) clicando em `+ Subseção` dentro de cada seção.

**5. Adicione blocos** de conteúdo com os botões na barra inferior de cada seção:
`¶ Texto` · `☰ Passos` · `ℹ Obs.` · `>_ Cmd` · `📷 Imagem`

**6. Reordene seções** arrastando pelo ícone `⠿` na lista lateral esquerda.

**7. Exporte** clicando em `Gerar DOCX` ou `Gerar PDF`.

---

## 5. Tipos de bloco

### ¶ Texto
Parágrafo de texto com formatação rich text.

- **Negrito** (`Ctrl+B`), **Itálico** (`Ctrl+I`), **Sublinhado** (`Ctrl+U`)
- Tachado, Sobrescrito (x²), Subscrito (x₂)
- Botão `✕ₐ` limpa toda a formatação

> O texto é exportado justificado com recuo ABNT (1,25 cm) no DOCX.

---

### ☰ Passos
Lista numerada de passos, ideal para procedimentos sequenciais.

- Cada linha é um passo independente
- Botão `+ Adicionar passo` insere novo passo ao final
- Botão `✕` ao lado de cada passo remove-o (mínimo de 1)
- No DOCX, exporta como tabela com número do passo em destaque azul

---

### ℹ Obs. (Observações)
Caixa de destaque com 4 variações de cor:

| Tipo | Cor | Uso |
|---|---|---|
| **Obs.** | Âmbar | Observações gerais |
| **25H2** | Azul | Novidades da versão 25H2 do Windows |
| **Atenção** | Vermelho | Alertas e cuidados |
| **Dica** | Verde | Sugestões e boas práticas |

Selecione o tipo clicando na aba correspondente. Suporta formatação bold/italic.

---

### >_ Cmd (Comandos)
Blocos de linha de comando em fonte monospace.

- Cada linha é um comando independente
- Botão `+ Adicionar comando` insere novo comando
- Exportado com fundo cinza claro e fonte `Courier New`

---

### 📷 Imagem
Bloco para inserção de figuras.

- **Upload:** Clique na área pontilhada ou arraste um arquivo de imagem
- **Legenda:** Campo abaixo da imagem — será exportada como `Figura N — Legenda`
- **Anotar:** Botão `✏ Anotar` abre o editor de anotações
- **Mover:** Botão `⇋ Mover / Reordenar` para reposicionar entre seções
- Formatos suportados: PNG, JPG, JPEG, WebP, GIF

> A numeração das figuras é automática e global (percorre todas as seções em ordem).

---

### 📖 Referência
Bloco para referências bibliográficas no padrão ABNT NBR 6023.

- Suporta formatação bold/italic (necessária para o título da obra em itálico)
- Exportado com recuo deslocado (1,25 cm) conforme ABNT
- Formato recomendado:
  ```
  SOBRENOME, Nome. Título da obra. Local: Editora, Ano.
  ```

---

### 📝 Nota interna
Todo bloco possui um campo **📝 Nota** com fundo amarelo, visível apenas no editor.

- Não aparece no DOCX nem no PDF
- Útil para comentários de revisão, lembretes ou instruções de preenchimento

---

## 6. Editor de imagens

Clique em `✏ Anotar` em qualquer bloco de imagem para abrir o editor.

### Ferramentas disponíveis

| Ícone | Ferramenta | Como usar |
|---|---|---|
| `→` | **Seta** | Clique e arraste para criar uma seta direcional |
| `▭` | **Retângulo** | Clique e arraste para destacar uma área |
| `T` | **Texto** | Clique na imagem e digite a anotação |
| `✏` | **Caneta** | Desenho livre clicando e arrastando |

### Controles do editor

- **Cor:** Seletor de cor aplica-se à ferramenta ativa
- **Espessura:** Controla a largura de linhas e bordas
- **Tamanho da fonte:** Aplica-se somente à ferramenta Texto
- **↩ Desfazer:** Remove a última anotação
- **🗑 Limpar:** Remove todas as anotações
- **✓ Salvar:** Confirma as anotações e fecha o editor

> As anotações são aplicadas sobre a imagem original e salvas no rascunho `.json`.

---

## 7. Personalizando a capa

Clique em `✦ Personalizar Capa` na topbar para abrir o editor de capa. A pré-visualização atualiza em tempo real conforme você edita.

### Seções do editor

| Seção | O que você pode customizar |
|---|---|
| **Logo** | Padrão LINCE (pinguim), upload de imagem própria ou sem logo; altura e alinhamento |
| **Cores e Tipografia** | Cor do título, subtítulo, réguas e fundo; tamanho das fontes |
| **Réguas horizontais** | Ativar/desativar; estilo: dupla, simples ou grossa |
| **QR Codes** | Ativar/desativar; URL e rótulo de cada QR (esquerdo e direito) |
| **Imagem de fundo** | Upload de imagem com controle de opacidade (ideal para brasão em marca d'água) |
| **Imagem decorativa** | Banner ou figura entre as réguas e os autores; controle de largura |
| **Licença e Rodapé** | Creative Commons, texto livre no rodapé, cor do texto |

Clique em `✓ Aplicar e Fechar` para confirmar. As configurações são salvas no rascunho `.json`.

---

## 8. Mover e reordenar blocos

Todo bloco possui o botão `⇋ Mover / Reordenar`. Ao clicar, abre um modal com duas abas:

### Aba "Reordenar na seção"
- Lista todos os blocos da seção atual
- **Arrastar pelo ícone `⠿`** para reposicionar (drag-and-drop)
- Setas `▲▼` para ajuste fino de um passo por vez
- O bloco em edição aparece destacado

### Aba "Mover para outra seção"
- Lista todas as seções e subseções do tutorial
- Clique no destino para mover o bloco
- A seção atual aparece marcada como `atual`

---

## 9. Pré-visualização

O painel direito exibe o documento exatamente como será exportado, atualizado em tempo real.

### Modos de layout

Use os três botões no canto direito da topbar:

| Botão | Modo | Atalho |
|---|---|---|
| `▪` | **Só editor** — tela inteira para editar | `Ctrl+\` |
| `▪▪` | **Split** — editor e preview lado a lado | `Ctrl+\` |
| `▪` | **Só preview** — tela inteira para revisar | — |

### Ajuste de zoom

Use o slider `Zoom` acima do preview (40% a 130%).

### Indicadores visuais em tempo real

- **Barra amarela** na esquerda do cabeçalho da seção ativa
- **Contorno amarelo** no bloco sendo editado
- O preview rola automaticamente para manter o bloco editado visível

---

## 10. Salvar e carregar rascunhos

### Salvar localmente

Clique em `💾 Salvar local` — gera um arquivo `rascunho_tutorial.json` com todo o conteúdo, incluindo imagens embutidas em base64 e configurações de capa.

### Abrir rascunho local

Clique em `📁 Abrir local` — selecione um arquivo `.json` salvo anteriormente.

> **Atenção:** O rascunho `.json` substitui completamente o conteúdo atual. Salve antes de abrir um novo.

### Exportar configuração

O botão `{} Exportar Config` também gera um `.json` — funcionalidade equivalente ao `Salvar local`.

---

## 11. Google Drive

Permite salvar e versionar tutoriais diretamente no Drive sem sair do construtor.

### Configuração inicial (uma vez)

1. Acesse [console.cloud.google.com](https://console.cloud.google.com)
2. Crie um projeto → **APIs & Serviços → Credenciais**
3. Clique em **Criar credenciais → ID do cliente OAuth 2.0**
4. Tipo: **Aplicativo da Web**
5. Em *Origens JavaScript autorizadas*, adicione o domínio onde o construtor está hospedado (ex: `http://localhost:8080`)
6. Copie o **Client ID** gerado
7. Abra o `construtor_tutorial_v11.html` em um editor de texto, localize a linha:
   ```js
   var DRIVE_CLIENT_ID = '';
   ```
   e cole o Client ID entre as aspas
8. Ative a **Google Drive API** em `APIs & Serviços → Biblioteca`

### Uso diário

O indicador `☁ Google Drive` na topbar mostra o status da conexão:

| Cor | Estado |
|---|---|
| Cinza | Desconectado |
| Verde | Conectado |
| Amarelo piscando | Salvando/carregando |
| Vermelho | Erro |

**Conectar:** Clique no indicador → `Entrar com Google` → autorize no popup.

**Salvar:** No modal do Drive, ajuste o nome do arquivo e clique em `💾 Salvar no Drive`.

**Salvar como novo:** Cria uma nova versão com nome personalizado — útil para controle de histórico.

**Abrir:** Clique em qualquer arquivo da lista → `Abrir`. Se houver conteúdo no editor, o construtor mostra um **resumo das diferenças** antes de substituir:
- `＋` Seções adicionadas
- `－` Seções removidas  
- `~` Seções modificadas

**Excluir:** Ícone `🗑` ao lado de cada arquivo na lista.

> Os tutoriais são salvos na pasta **"Tutoriais LINCE"** criada automaticamente no Drive.

---

## 12. Exportar DOCX

Clique em `📄 Gerar DOCX`. O arquivo `.docx` é gerado e baixado automaticamente.

### O que está incluído

- **Capa** com logo, autores e licença CC (conforme configurado)
- **Sumário** com líderes pontilhados e numeração de página
- **Seções** com cabeçalho azul numerado ABNT (ex: `1  TÍTULO DA SEÇÃO`)
- **Subseções** com barra lateral azul (ex: `1.1  Título da Subseção`)
- **Todos os tipos de bloco** com formatação ABNT correta
- **Imagens** centralizadas com legenda `Figura N — Legenda`
- **Referências** com recuo deslocado NBR 6023

### Configurações ABNT aplicadas automaticamente

| Parâmetro | Valor |
|---|---|
| Fonte | Times New Roman 12pt |
| Margens | Superior 3cm · Inferior 2cm · Esquerda 3cm · Direita 2cm |
| Espaçamento | 1,5 linha |
| Alinhamento | Justificado |
| Recuo de parágrafo | 1,25 cm |
| Idioma | Português (Brasil) |

> **Observação:** O arquivo gerado segue o padrão ABNT. Para enquadramento fino de imagens ou ajustes de paginação, uma revisão rápida no Word ainda pode ser necessária.

---

## 13. Exportar PDF

Clique em `📷 Gerar PDF`. Um modal abre com a pré-visualização do documento em tamanho A4.

### Como salvar o PDF

1. Clique em `🖨 Imprimir / Salvar PDF`
2. No diálogo do navegador, selecione `Salvar como PDF` como destino
3. Recomendado no Chrome/Edge: em "Mais configurações", defina **Margens: Nenhuma** e desmarque cabeçalhos/rodapés do navegador

> O PDF usa o mesmo HTML gerado para a pré-visualização, garantindo fidelidade ao documento.

---

## 14. Atalhos de teclado

| Atalho | Ação |
|---|---|
| `Ctrl+B` | Negrito (dentro de bloco de texto) |
| `Ctrl+I` | Itálico (dentro de bloco de texto) |
| `Ctrl+U` | Sublinhado (dentro de bloco de texto) |
| `Ctrl+\` | Alternar entre modo Split e modo Editor |

---

## 15. Perguntas frequentes

**O arquivo `.json` é muito grande — por quê?**  
As imagens são armazenadas em base64 dentro do JSON. Para tutoriais com muitas imagens de alta resolução, o arquivo pode ficar grande. Considere redimensionar as imagens antes de importá-las.

**Posso usar o construtor offline?**  
Sim, completamente. Todas as funcionalidades (exceto Google Drive) funcionam sem internet. O arquivo HTML contém todos os recursos embutidos.

**O DOCX abre com erros no Word?**  
Verifique se está usando o Word 2016 ou superior. O arquivo usa OOXML com estilos `Heading1`/`Heading2` e configurações de compatibilidade para Word 15 (2013+).

**A pré-visualização não atualiza ao digitar.**  
Aguarde um momento — há um debounce de 150ms. Se continuar sem atualizar, verifique se o painel de preview está visível (modo Split ou Só Preview).

**Como adicionar uma seção de Referências Bibliográficas?**  
Crie uma seção com o título `REFERÊNCIAS` e adicione blocos do tipo `📖 Referência` para cada entrada.

**Os QR codes no PDF/DOCX são funcionais?**  
Os QR codes exibidos na capa são representações visuais geradas com base na URL informada. Para QR codes escaneáveis funcionalmente, edite a capa no Word após exportar e insira QR codes gerados por ferramentas dedicadas.

---

## Estrutura do arquivo de rascunho `.json`

```json
{
  "meta": {
    "titulo": "Nome do Tutorial",
    "subtitulo": "Subtítulo",
    "autores": "Nome, Nome",
    "colab": "Nome",
    "orient": "Nome",
    "ano": "2025",
    "capa": true,
    "sumario": true
  },
  "sections": [
    {
      "id": "...",
      "titulo": "Nome da Seção",
      "blocos": [ ... ],
      "subsecoes": [ ... ]
    }
  ],
  "imgs": {
    "<id-do-bloco>": "data:image/png;base64,..."
  },
  "coverCfg": { ... },
  "_savedAt": "2025-03-31T12:00:00.000Z"
}
```

---

## Sobre

Desenvolvido pelo **D-LINCE** — Divisão de Suporte de Sistemas Educacionais e Redes Digitais  
Centro de Educação (CE) — UFSM — Prédio 16

Licença: Creative Commons CC BY-NC-SA
