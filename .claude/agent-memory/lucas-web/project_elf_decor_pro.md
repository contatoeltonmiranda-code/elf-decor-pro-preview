---
name: project-elf-decor-pro
description: LP Elf Decor Pro (Higgor Ferraz) - preview HTML estatico em higgor-ferraz, repo publico separado para GH Pages, memoria canonica no _brain do projeto
metadata:
  type: project
---

A LP da **Elf Decor Pro** (cliente Higgor Ferraz, mercado US, copy em ingles) tem
**duas pastas** e elas nao sao a mesma coisa:

- `2. wp-elementor/Projetos/higgor-ferraz/` — **fonte da verdade**. `index.html`,
  snapshots `index-vN.html`, `_brain/`, `qa/`, briefing, manual da marca.
- `2. wp-elementor/Projetos/elf-decor-pro-preview/` — **copia publica** que vai para o
  GitHub Pages. So `index.html` + `assets/`. Nunca editar aqui; sincronizar a partir da
  outra e dar push.

**Why:** o preview precisa de URL publica e o `_brain/` tem dado de cliente — nao pode ir
para repo publico. Cada alteracao aprovada exige re-sync, senao o link que o Elton manda
ao cliente fica velho.

**How to apply:** editar sempre em `higgor-ferraz/index.html`. Antes de editar, snapshot
`index-vN.html` (confirmar o proximo N com `ls`). A memoria detalhada — decisoes de
design, o que cada versao mudou, dados confirmados do cliente, o que ainda e
`[TO CONFIRM]` — fica em `higgor-ferraz/_brain/RESUMO.md` e `DECISOES.md`, que sao longos
e vale ler antes de qualquer ronda. Elton nao quer commit nem push aqui: ele sincroniza.
