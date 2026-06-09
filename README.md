# Construtor de Tutoriais LINCE

<div align="center">

![LINCE](https://img.shields.io/badge/D--LINCE-UFSM-185FA5?style=for-the-badge)
![Versão](https://img.shields.io/badge/versão-v15-22A355?style=for-the-badge)
![HTML](https://img.shields.io/badge/HTML-standalone-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![Licença](https://img.shields.io/badge/licença-CC%20BY--NC--SA-orange?style=for-the-badge)

**Ferramenta standalone para criação de tutoriais técnicos no padrão ABNT**

Exporta para `.docx` e `.pdf` · Pré-visualização em tempo real · Autosave automático · Integração com Google Drive

[⬇ Baixar última versão](#instalação) · [📖 Documentação completa](docs/README.md) · [🐛 Reportar problema](../../issues)

</div>

---

## O que é

O Construtor de Tutoriais LINCE é um único arquivo HTML que roda diretamente no navegador, sem instalação. Foi desenvolvido pela equipe do **D-LINCE** (Divisão de Suporte de Sistemas Educacionais e Redes Digitais) da UFSM para padronizar a produção de tutoriais técnicos no formato institucional.

```
construtor_tutorial_v15.html   ← tudo em um arquivo só
```

---

## Funcionalidades

| Funcionalidade | Descrição |
|---|---|
| **Editor por blocos** | Texto, Passos, Observações, Comandos, Imagens, Referências ABNT |
| **Pré-visualização em tempo real** | Split-view com atualização por patch (sem recarregar) |
| **Editor de imagens** | Seta, retângulo, texto, caneta livre, recorte (crop) |
| **Repositório de imagens** | Central de imagens reutilizáveis; suporte a `Ctrl+V` para prints |
| **Capa personalizada** | Logo, QR codes, imagem de fundo, CC license, cores e tipografia |
| **Exportar DOCX** | OOXML puro, Times New Roman 12pt, margens e espaçamento ABNT |
| **Exportar PDF** | Via `window.print()` com stylesheet dedicado |
| **Autosave** | localStorage a cada 30s; restauração automática ao reabrir |
| **Histórico de versões** | Até 10 snapshots locais com imagens preservadas; restauração com 1 clique |
| **Google Drive** | OAuth 2.0, pasta automática, diff de versões, autosave a cada 5min |

---

## Instalação

### Uso simples (sem Google Drive)

1. Baixe o arquivo da [última release](../../releases/latest)
2. Abra no navegador — funciona offline, sem instalação

### Com Google Drive

É necessário servir o arquivo via HTTP (restrição do OAuth):

```bash
# Na pasta onde está o arquivo
python3 -m http.server 8080
```

Acesse: `http://localhost:8080/construtor_tutorial_v15.html`

> **Windows:** crie um arquivo `iniciar.bat` com o conteúdo acima e clique duas vezes.

Para configurar a integração com o Drive, veja a [documentação completa](docs/README.md#12-google-drive).

---

## Uso rápido

```
1. Abra o arquivo no navegador
2. Preencha os metadados no painel esquerdo (título, autores, data)
3. Clique em "+ Nova Seção" e adicione blocos de conteúdo
4. Exporte com "Gerar DOCX" ou "Gerar PDF"
```

O construtor salva automaticamente a cada 30 segundos. Se fechar a aba acidentalmente, ao reabrir o arquivo aparece um prompt para restaurar o trabalho.

---

## Estrutura do repositório

```
.
├── construtor_tutorial_v15.html   # Ferramenta principal (arquivo único)
├── README.md                      # Este arquivo
├── docs/
│   └── README.md                  # Documentação completa de uso
└── exemplos/
    └── rascunho_exemplo.json      # Tutorial de exemplo para testar
```

---

## Histórico de versões

| Versão | Principais mudanças |
|---|---|
| **v15** | Histórico de versões local (10 snapshots, restauração, export por versão) |
| **v14** | Editor de imagens: crop · Repositório de imagens · Colar print com `Ctrl+V` |
| **v13** | Autosave localStorage 30s · Indicador de status na topbar · Restauração ao reabrir · Autosave Drive 5min |
| **v12** | Zoom via CSS `zoom` (sem deslocamento de tela) · `pvSetZoom` atualiza in-place |
| **v11** | Preview system v3: `iframe.onload`, highlight amarelo da seção/bloco ativo, scroll sem salto |
| **v10** | Correção do split-view: CSS duplicado removido, `_applyLayout` via `flex-basis %`, drag absoluto |
| **v9** | Preview em tempo real por patch `postMessage` (sem reload por keystroke) |
| **v8** | Split-view com divisor arrastável, modos editor/split/preview, atalho `Ctrl+\` |
| **v7** | Preview iframe real, notas internas por bloco, diff de versões no Drive |
| **v6** | Integração Google Drive (OAuth 2.0 implicit flow), pasta automática |
| **v5** | Editor de capa personalizada com preview live |
| **v4** | Correções críticas OOXML (`w:tcBorders`), botão mover em todos os blocos |

---

## Formato do arquivo de rascunho

Os tutoriais são salvos como `.json`:

```json
{
  "meta": {
    "titulo": "Windows 11 25H2",
    "subtitulo": "Instalação e Configuração",
    "autores": "João Silva, Maria Santos",
    "ano": "2025",
    "capa": true,
    "sumario": true
  },
  "sections": [
    {
      "id": "sec-001",
      "titulo": "INTRODUÇÃO",
      "blocos": [
        { "id": "blk-001", "tipo": "texto", "texto": "..." }
      ],
      "subsecoes": []
    }
  ],
  "imgs": {
    "blk-xyz": "data:image/png;base64,..."
  },
  "coverCfg": { "...": "..." },
  "_savedAt": "2025-03-31T12:00:00.000Z"
}
```

> As imagens são armazenadas em base64 dentro do JSON. Arquivos com muitas imagens de alta resolução podem ficar grandes (5–20MB).

---

## Padrões ABNT aplicados

| Parâmetro | Valor |
|---|---|
| Fonte | Times New Roman 12pt |
| Margens | Superior 3cm · Inferior 2cm · Esquerda 3cm · Direita 2cm |
| Espaçamento entre linhas | 1,5 |
| Alinhamento | Justificado |
| Recuo de parágrafo | 1,25 cm |
| Referências | NBR 6023, recuo deslocado |
| Idioma do documento | Português (Brasil) |

---

## Tecnologias

- **HTML5 + CSS3 + JavaScript (ES5/ES6)** — sem frameworks, sem dependências externas
- **OOXML puro** — geração de `.docx` sem bibliotecas
- **Canvas API** — editor de imagens e anotações
- **Google Drive API v3** — OAuth 2.0 implicit flow
- **localStorage** — autosave e histórico de versões

---

## Contribuindo

1. Faça um fork do repositório
2. Crie uma branch: `git checkout -b feature/minha-melhoria`
3. Faça as alterações no arquivo HTML
4. Commit: `git commit -m "Descrição clara da mudança"`
5. Push: `git push origin feature/minha-melhoria`
6. Abra um Pull Request

Para bugs, abra uma [issue](../../issues) descrevendo o comportamento esperado e o observado.

---

## Sobre

Desenvolvido pelo **D-LINCE** — Divisão de Suporte de Sistemas Educacionais e Redes Digitais  
Centro de Educação (CE) · UFSM · Prédio 16 · Santa Maria, RS

<a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">
  <img src="https://img.shields.io/badge/CC%20BY--NC--SA-4.0-lightgrey?style=flat-square" alt="CC BY-NC-SA 4.0">
</a>
