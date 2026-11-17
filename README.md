# Hub pessoal

Ferramentas pessoais em HTML estático, sem build e sem servidor, publicadas no GitHub Pages:
**https://guivg.github.io/hub_pessoal/**

| Ferramenta | Pasta | O que faz |
|---|---|---|
| Meu menu | `ferramentas/menu/` | Monta o cardápio e a lista da semana |
| Investimentos | `ferramentas/investimentos/` | Rebalanceamento, patrimônio consolidado e aportes extras em BTC |

## Estrutura

```
index.html                 tela inicial: lista de ferramentas + backup dos dados
compartilhado/tema.css     tema grafite (tokens, claro/escuro, cabeçalho e abas padrão)
compartilhado/icones/      SVG-fonte dos ícones (hub e ferramentas)
ferramentas/<pasta>/       uma ferramenta por pasta, cada uma com seu index.html
```

## Dados

Cada ferramenta guarda os dados no `localStorage` do aparelho. Nada vai para o repositório.
A seção **Backup dos dados**, na tela inicial, copia todos os dados num texto só e restaura
a partir dele. Use para trocar de aparelho ou para levar os dados de um ícone da Tela de
Início para outro (no iPhone, cada ícone da Tela de Início tem o próprio armazenamento).

| Ferramenta | Chave(s) no `localStorage` |
|---|---|
| Meu menu | `meu-menu-v3` (e a antiga `cozinha_estado_v4`, lida só para migração) |
| Investimentos | `meus-investimentos:v1` |

## Adicionar uma ferramenta

1. Crie `ferramentas/<pasta>/index.html`. Comece pelo cabeçalho padrão:
   ```html
   <link href="https://fonts.googleapis.com/css2?family=Instrument+Sans:wght@400;500;600&display=swap" rel="stylesheet">
   <link rel="stylesheet" href="../../compartilhado/tema.css">
   ...
   <div class="pagina">
     <header class="topo">
       <h1><svg viewBox="12 12 76 76">…</svg>Nome</h1>
       <a class="voltar" href="../../">&larr; Hub</a>
     </header>
     <nav class="nav">  <!-- abas opcionais: botão ativo com aria-current="page" -->
   ```
2. Use só os tokens do tema (`--fundo`, `--papel`, `--tinta`, `--suave`, `--linha`, `--folha`,
   `--positivo`, `--alerta`, `--perigo`, `--fonte`). Assim o modo claro/escuro funciona sozinho.
3. Use uma chave de `localStorage` própria, com prefixo do nome da ferramenta (ex.: `minha-ferramenta:v1`).
4. Registre a ferramenta no array `FERRAMENTAS` do `index.html`: pasta, nome, descrição, ícone e `chaves`.
5. Ícone da Tela de Início: crie `compartilhado/icones/<pasta>.svg` (mesmo padrão: fundo `#1A1A1A`
   e anel `#ECECEA`) e exporte um PNG de 180×180 como `ferramentas/<pasta>/apple-touch-icon.png`.

## Rodar localmente

```sh
python3 -m http.server 8000   # abre em http://localhost:8000
```
