---
name: qa-conferir-screenshot-nao-so-assercao
description: Print de QA precisa ser de elemento (locator.screenshot) com assercao do texto-chave dentro dele, e ainda assim olhado
metadata:
  type: feedback
---

Prints de QA: use `locator.screenshot()` no elemento alvo, nunca print de viewport apos
`scrollTo`, e valide com uma assercao do tipo "este trecho de texto TEM de estar no
`innerText` do elemento" antes de salvar o arquivo. Depois **abra os prints**.

**Why:** o Elton cobrou porque numa ronda varios prints nomeados "hero" sairam com a secao
errada. Assercao sozinha tambem nao basta: numa ronda ela passou verde enquanto o print
mostrava alt text vazando por cima de um placeholder — o texto estava no DOM, so estava
desenhado no lugar errado.

**How to apply:** todo QA visual. Duas ressalvas ja pagas: (1) assercao com `innerText`
falha por caixa quando o CSS aplica `text-transform:uppercase` — compare case-insensitive
ou o hero da falso negativo; (2) print de elemento inclui o header fixo sobreposto, isso
e normal e nao e bug.
