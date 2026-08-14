---
name: sondagem-arquivo-gera-404-console
description: Nao existe como checar por HTTP se um asset existe sem imprimir 404 no console; em preview de cliente usar chave booleana manual
metadata:
  type: feedback
---

Quando um componente precisa apontar para imagens que **ainda nao existem**, nao tente
detectar a existencia do arquivo em runtime. Use `data-src` + uma **chave booleana unica**
no JS (ex.: `var COMPARE_PHOTOS_READY = false`) e documente a virada num LEIA-ME ao lado
das imagens.

**Why:** toda forma de sondar por HTTP dispara um 404 que o Chrome imprime em vermelho no
console — `fetch HEAD` (que ainda gera `requestfailed` com `net::ERR_ABORTED`, porque HEAD
nao tem corpo), `new Image()`, `<link rel=preload>`. Testei o `fetch HEAD` achando que
seria o caminho limpo e o QA Playwright devolveu 4 erros de console + 4 requestfailed em
todas as 7 larguras. Em preview que vai ao cliente, console sujo custa mais que virar um
booleano a mao.

**How to apply:** qualquer slot de imagem/video pendente numa LP de preview. Combine com
`.slot img:not([src]){display:none}` — sem `src` o Chrome **desenha o alt text** por cima
do placeholder (so aparece no screenshot, nao em asserção de DOM). Ver
[[qa-conferir-screenshot-nao-so-assercao]].
