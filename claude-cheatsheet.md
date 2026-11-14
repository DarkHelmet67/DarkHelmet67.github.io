# Claude — Cheat Sheet dei comandi (aggiornato a novembre 2026)

> **Nota importante.** I *veri* slash command esistono in **Claude Code** (terminale, IDE, desktop, web).
> Nell'app Claude (web/mobile) la maggior parte delle funzioni passa da pulsanti e menu: lì i "comandi" sono **istruzioni in linguaggio naturale**, raccolte nella sezione 11.
> Digita `/` in Claude Code per la lista sempre aggiornata della tua versione: comandi, skill e plugin installati.

## Indice

1. [Avvio & sessione](#1-avvio--sessione)
2. [Contesto & memoria](#2-contesto--memoria)
3. [Modello & modalità](#3-modello--modalità)
4. [Codice & review](#4-codice--review)
5. [Automazione & agenti](#5-automazione--agenti)
6. [Integrazioni & estensioni](#6-integrazioni--estensioni)
7. [Permessi & configurazione](#7-permessi--configurazione)
8. [Consumi & diagnostica](#8-consumi--diagnostica)
9. [Esporta & condividi](#9-esporta--condividi)
10. [Comandi personalizzati (skill)](#10-comandi-personalizzati-skill)
11. [Prompt pattern (app Claude e ovunque)](#11-prompt-pattern-app-claude-e-ovunque)
12. [Scorciatoie e prefissi](#12-scorciatoie-e-prefissi)
13. [Esempi pratici](#esempi-pratici)

---

## 1. Avvio & sessione

| Comando | A cosa serve |
| :-- | :-- |
| `/init` | Analizza il progetto e genera un `CLAUDE.md` iniziale |
| `/clear` | Svuota la conversazione e riparte da zero |
| `/resume` | Riprende una sessione precedente |
| `/rewind` | Torna a un punto precedente, ripristinando i file modificati da Claude |
| `/add-dir` | Aggiunge una cartella alla sessione (e ne carica le skill) |
| `/cd` | Sposta la sessione in un'altra cartella |
| `/exit` | Chiude Claude Code |

## 2. Contesto & memoria

| Comando | A cosa serve |
| :-- | :-- |
| `/context` | Mostra quanto contesto è occupato e da cosa |
| `/compact` | Riassume la conversazione per liberare contesto |
| `/memory` | Apre i file di memoria (`CLAUDE.md`) per modificarli |
| `@percorso/file` | Inserisce un file o una cartella nel prompt |

## 3. Modello & modalità

| Comando | A cosa serve |
| :-- | :-- |
| `/model` | Cambia il modello in uso |
| `Shift+Tab` | Passa tra le modalità di permesso (normale, auto-accept, plan mode) |
| `/config` | Apre le impostazioni (tema, output, comportamento) |

## 4. Codice & review

| Comando | A cosa serve |
| :-- | :-- |
| `/code-review` (alias `/review`) | Review del codice modificato |
| `/security-review` | Revisione di sicurezza delle modifiche in sospeso |
| `/simplify` | Rilegge il codice modificato e lo semplifica (riuso, qualità, efficienza) |
| `/verify` | Compila e avvia l'app per confermare che la modifica funziona davvero |
| `/run` | Avvia e usa l'app per vedere la modifica in azione |
| `/run-skill-generator` | Registra come compilare e avviare il progetto in una skill `/run-<nome>` |

## 5. Automazione & agenti

| Comando | A cosa serve |
| :-- | :-- |
| `/agents` | Crea e gestisce i subagent |
| `/loop` | Ripete un prompt o un comando a intervalli |
| `/batch` | Applica in parallelo una modifica estesa su tutta la codebase |
| `/hooks` | Configura gli hook (azioni automatiche prima e dopo l'uso dei tool) |

## 6. Integrazioni & estensioni

| Comando | A cosa serve |
| :-- | :-- |
| `/mcp` | Gestisce i server MCP collegati |
| `/plugin` | Installa, abilita, disabilita e rimuove i plugin |
| `/skills` | Elenca le skill disponibili (anche quelle sincronizzate da claude.ai) |
| `/reload-skills` | Ricarica le skill dopo averne aggiunte |
| `/reload-plugins` | Applica le modifiche ai plugin (hook, MCP, agenti, stili) |
| `/claude-api` | Carica la documentazione Claude API per il linguaggio del progetto |

## 7. Permessi & configurazione

| Comando | A cosa serve |
| :-- | :-- |
| `/permissions` | Gestisce le regole su cosa Claude può fare senza chiedere |
| `/login` / `/logout` | Accede o esce dall'account |
| `/doctor` | Controlla installazione, `CLAUDE.md`, permessi e consumi, e propone correzioni |

## 8. Consumi & diagnostica

| Comando | A cosa serve |
| :-- | :-- |
| `/usage` (alias `/cost`) | Mostra i consumi del piano o della sessione |
| `/status` | Stato della sessione: account, modello, impostazioni attive |
| `/debug` | Analizza il log della sessione di Claude Code per capire cosa non va |
| `/skill-doctor` | Mostra quanto contesto occupa ogni skill e quanto viene usata |
| `/help` | Elenco dei comandi disponibili |

## 9. Esporta & condividi

| Comando | A cosa serve |
| :-- | :-- |
| `/export` | Esporta la conversazione in un file o negli appunti |
| `/copy` | Copia l'ultima risposta di Claude negli appunti |

## 10. Comandi personalizzati (skill)

| Percorso | Ambito |
| :-- | :-- |
| `~/.claude/skills/<nome>/SKILL.md` | Personale (tutti i progetti) |
| `.claude/skills/<nome>/SKILL.md` | Progetto (da committare per condividerla col team) |
| `<plugin>/skills/<nome>/SKILL.md` | Plugin, si invoca come `/plugin:nome` |
| `.claude/commands/<nome>.md` | Formato legacy, funziona ancora |

Variabili utili nel corpo: `$ARGUMENTS`, `$0` / `$1` (argomenti posizionali), `${CLAUDE_PROJECT_DIR}`.
Con `` !`comando` `` si inserisce l'output di un comando shell prima che Claude legga la skill.

## 11. Prompt pattern (app Claude e ovunque)

Nell'app Claude questi **non sono comandi**: sono formule che funzionano bene se scritte per esteso.

| Obiettivo | Cosa scrivere |
| :-- | :-- |
| Definire l'obiettivo | "L'obiettivo è… Il risultato deve servire a…" |
| Dare contesto | "Contesto: sono…, il pubblico è…, il vincolo è…" |
| Far fare domande | "Prima di iniziare fammi le domande che ti servono." |
| Confrontare | "Confronta A e B su costo, rischio e tempi, in tabella." |
| Mettere in dubbio | "Quali assunzioni sto dando per scontate? Contestale." |
| Riscrivere | "Riscrivi in metà parole, tono diretto, senza perdere i fatti." |
| Strutturare | "Trasforma in outline con 3 livelli." |
| Ricercare | "Cerca fonti recenti e citale; distingui fatti e opinioni." |
| Verificare | "Verifica queste affermazioni e segnala quelle non supportate." |
| Ottenere un file | "Fammi un documento / una presentazione / un foglio con…" |
| Ricordare | "Ricorda che preferisco risposte brevi." (con la memoria attiva) |

## 12. Scorciatoie e prefissi

| Tasto / prefisso | Effetto |
| :-- | :-- |
| `/` | Apre l'elenco di comandi e skill (filtra mentre scrivi) |
| `@` | Menziona file e cartelle |
| `!` | Esegue direttamente un comando shell |
| `Esc` | Interrompe Claude mentre lavora |
| `Esc` `Esc` | Apre il menu per tornare indietro (rewind) |
| `Shift+Tab` | Cambia modalità di permesso / plan mode |

---

# Esempi pratici

## 1. Avvio & sessione — esempi

**`/init`**
```text
> /init
# Claude esplora il repo e crea CLAUDE.md con stack, comandi di build/test e convenzioni.
```

**`/clear`**
```text
> /clear
# Nuovo task, contesto pulito: utile quando si cambia argomento.
```

**`/resume`**
```text
> /resume
# Scegli dalla lista la sessione "refactor player HLS" di ieri.
# Da terminale: claude --resume   oppure   claude -c (ultima sessione)
```

**`/rewind`**
```text
> /rewind
# Scegli il punto precedente al refactoring sbagliato: codice e conversazione tornano lì.
```

**`/add-dir`**
```text
> /add-dir ../shared-ui-components
```

**`/cd`**
```text
> /cd ~/projects/tado-widget
```

**`/exit`**
```text
> /exit
```

## 2. Contesto & memoria — esempi

**`/context`**
```text
> /context
# Mostra la ripartizione: system prompt, tool, file di memoria, messaggi, spazio libero.
```

**`/compact`**
```text
> /compact mantieni solo le decisioni sull'architettura e i TODO aperti
```

**`/memory`**
```text
> /memory
# Apre CLAUDE.md nell'editor. Esempio di contenuto:
## Convenzioni
- TypeScript strict, niente `any`
- Test con Vitest: `npm test`
```

**`@file`**
```text
> Spiega il flusso di @src/player/AdManager.ts e dimmi dove gestiamo gli errori VAST
```

## 3. Modello & modalità — esempi

**`/model`**
```text
> /model
# Seleziona il modello dalla lista, oppure passalo direttamente: /model opus
```

**`Shift+Tab` (plan mode)**
```text
[Shift+Tab fino a "plan mode"]
> Pianifica la migrazione da Webpack a Vite. Non modificare file.
# Claude propone un piano; lo approvi prima che tocchi il codice.
```

**`/config`**
```text
> /config
# Tema, editor, notifiche, stile di output...
```

## 4. Codice & review — esempi

**`/code-review`**
```text
> /code-review
# Review delle modifiche correnti: bug, leggibilità, casi limite.
```

**`/security-review`**
```text
> /security-review
# Cerca injection, segreti nel codice, gestione insicura di input e token.
```

**`/simplify`**
```text
> /simplify
# Dopo un'implementazione rapida: elimina duplicazioni e codice superfluo.
```

**`/verify`**
```text
> /verify il nuovo pulsante "skip ad" compare dopo 5 secondi
```

**`/run`**
```text
> /run
# Avvia l'app e la usa per mostrare la modifica funzionante.
```

**`/run-skill-generator`**
```text
> /run-skill-generator
# Crea /run-<nome>: le volte successive basta invocarla per avviare il progetto.
```

## 5. Automazione & agenti — esempi

**`/agents`**
```text
> /agents
# Crea un subagent "test-writer" con accesso solo a Read, Write e Bash(npm test *).
```

**`/loop`**
```text
> /loop 10m controlla se la pipeline CI è verde e riassumi gli errori
```

**`/batch`**
```text
> /batch sostituisci moment.js con date-fns in tutto il progetto
```

**`/hooks`**
```jsonc
// .claude/settings.json — formatta ogni file dopo che Claude lo modifica
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [{ "type": "command", "command": "npx prettier --write \"$CLAUDE_FILE_PATHS\"" }]
      }
    ]
  }
}
```

## 6. Integrazioni & estensioni — esempi

**`/mcp`**
```bash
# Da terminale: aggiunge un server MCP
claude mcp add github -- npx -y @modelcontextprotocol/server-github
# In sessione: /mcp per vederne lo stato e autenticarti
```

**`/plugin`**
```text
> /plugin
# Sfoglia i marketplace, installa un plugin, abilitalo o disabilitalo.
```

**`/skills`**
```text
> /skills
```

**`/reload-skills`** e **`/reload-plugins`**
```text
> /reload-skills
> /reload-plugins
```

**`/claude-api`**
```text
> /claude-api migrate
# Aiuta ad aggiornare il codice che usa l'SDK Anthropic.
```

## 7. Permessi & configurazione — esempi

**`/permissions`**
```jsonc
// .claude/settings.json
{
  "permissions": {
    "allow": ["Bash(npm run test *)", "Bash(git status)"],
    "deny":  ["Read(./.env)", "Bash(rm -rf *)"]
  }
}
```

**`/login`** / **`/logout`**
```text
> /login
> /logout
```

**`/doctor`**
```text
> /doctor
> /doctor prompt-audit   # controlla le istruzioni in CLAUDE.md e nelle skill
```

## 8. Consumi & diagnostica — esempi

**`/usage`**
```text
> /usage
```

**`/status`**
```text
> /status
```

**`/debug`**
```text
> /debug il server MCP di GitHub non si connette
```

**`/skill-doctor`**
```text
> /skill-doctor
# Individua le skill che occupano contesto e non usi mai.
```

**`/help`**
```text
> /help
```

## 9. Esporta & condividi — esempi

**`/export`**
```text
> /export sessione-refactor.md
```

**`/copy`**
```text
> /copy
```

## 10. Comandi personalizzati — esempio

```markdown
<!-- .claude/skills/fix-issue/SKILL.md -->
---
name: fix-issue
description: Risolve una issue GitHub seguendo gli standard del progetto
disable-model-invocation: true
allowed-tools: Bash(gh issue view *), Bash(npm test *)
---

Contesto della issue:
!`gh issue view $ARGUMENTS`

1. Riproduci il problema con un test che fallisce.
2. Correggi il codice.
3. Esegui `npm test` e riassumi la modifica.
```

Uso:
```text
> /fix-issue 123
```

## 11. Prompt pattern — esempi

**Obiettivo + contesto**
```text
Obiettivo: una mail di 5 righe per chiedere un rinvio della scadenza.
Contesto: destinatario = cliente storico, tono cordiale ma deciso.
```

**Domande prima di iniziare**
```text
Voglio un piano di onboarding per un junior frontend.
Prima di scriverlo fammi al massimo 3 domande.
```

**Confronto**
```text
Confronta Capacitor e Kotlin Multiplatform per portare un player web su mobile:
tabella con effort, performance, riuso del codice, rischi.
```

**Contestare le assunzioni**
```text
Ecco il mio piano: […]. Fai l'avvocato del diavolo: quali assunzioni sono fragili?
```

**Riscrivere / accorciare**
```text
Riscrivi questo paragrafo in metà parole, senza gergo: […]
```

**Strutturare**
```text
Trasforma questi appunti in un outline a 3 livelli, poi in una tabella delle azioni.
```

**Ricerca con fonti**
```text
Cerca le novità di HLS dell'ultimo anno, cita le fonti e separa annunci e funzioni già disponibili.
```

**Fact-check**
```text
Verifica queste 5 affermazioni e per ognuna indica: confermata / smentita / non verificabile.
```

**Ottenere un file**
```text
Fammi una presentazione di 8 slide sui risultati del trimestre a partire dal file allegato.
```

**Memoria**
```text
Ricorda: nelle risposte tecniche preferisco esempi in TypeScript.
```

## 12. Scorciatoie — esempi

```text
> !git log --oneline -5           # esegue il comando e ne mostra l'output a Claude
> Rivedi @src/ads/ e @README.md   # menziona più percorsi
[Esc]                             # ferma Claude mentre lavora
[Esc][Esc]                        # torna a un messaggio precedente
```

---

*Verificato sulla documentazione ufficiale di Claude Code ([code.claude.com/docs](https://code.claude.com/docs/en/slash-commands)) a novembre 2026. I comandi cambiano spesso: usa `/help` per la tua versione.*
