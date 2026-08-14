---
name: qa-scroll-smooth-falseia-medicao
description: scroll-behavior:smooth do site faz boundingBox/scrollY do Playwright medirem em pleno voo e gerar falso negativo de drag e de scroll roubado
metadata:
  type: feedback
---

Em QA Playwright de site com `html{scroll-behavior:smooth}`, injete
`await p.addStyleTag({content:'html{scroll-behavior:auto !important}'})` logo apos o load,
e use `scrollIntoView({behavior:'auto'})`.

**Why:** com smooth ligado, `locator.boundingBox()` chamado logo apos um `scrollIntoView`
le a posicao com a pagina ainda em movimento. Num teste de slider drag isso fez o mouse
cair fora do elemento e o resultado foi "o arraste nao funciona" — sendo que funcionava
(script isolado deu 79,8%). O mesmo artefato inventou um "scroll roubado de 3456px" no
teste de touch, que era so `scrollY` lido em dois momentos do voo.

**How to apply:** todo script de QA que combine scroll programatico com medicao de
coordenada ou de `scrollY`. Antes de reportar "nao funciona", reproduza o gesto num
script isolado — falso negativo de harness e mais comum que bug de pagina.
