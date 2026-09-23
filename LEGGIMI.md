# Sito personale: istruzioni

La tua pagina personale, pronta per **GitHub Pages**. È un file unico (`index.html`) più le foto.

```
Sito_web_personale/
├── index.html     ← il sito (testi, stile, animazioni)
├── favicon.svg    ← l'icona AF nella scheda del browser
├── LEGGIMI.md     ← questo file
└── img/
    ├── epfl.jpg        ← foto ridimensionate (le originali WhatsApp restano nella cartella)
    ├── lake.jpg
    └── mountains.jpg
```

## Cosa c'è nella pagina

1. **Hero**: logo AF disegnato come una piccola rete neurale, nome, una frase, e il carosello
   delle 3 foto (cambiano ogni 8 secondi, si fermano al passaggio del mouse). Sullo sfondo una
   rete neurale viva: i nodi si spostano col cursore e si colorano quando lo muovi, le parole
   dei tuoi temi galleggiano, e **cliccando parte un "segnale"** che si propaga nella rete.
2. **01 / the problem**: un mini‑esperimento interattivo. Il visitatore accende i 4 problemi
   dei dati clinici (sbilanciamento, confondenti, domain shift, modalità mancanti) e vede il
   modello "da manuale" andare in crisi; per ognuno c'è cosa hai fatto tu. Tutti e 4 → ADELAI.
3. **02 / about me**: la tua presentazione in forma di **model card** (come quelle di
   Hugging Face), con il pulsante *raw* che mostra la versione YAML/Markdown. È la tua
   versione "da ricercatrice" dell'idea JSON.
4. **03 / now**: una *now page* invece delle news: un'unica fotografia datata di cosa stai
   facendo + "Looking for my next lab". Non invecchia come una lista di news.
5. **04 / elsewhere**: link a GitHub, ADELAI, Scholar, ORCID, LinkedIn. Niente CV, niente elenco paper.

## Modificare i contenuti

Apri `index.html` e cerca in fondo il blocco **`const CONFIG = {`**:
- `photoSeconds`: secondi per foto (8 di default).
- `photos`: file, didascalie e `pos` (quale parte della foto resta visibile nel riquadro).
- `links`: GitHub, ADELAI, Google Scholar, ORCID, LinkedIn.
- `formEndpoint`: il modulo Formspree del pulsante **Write to me** (e della voce *contact* nel menu).
  I messaggi arrivano alla tua email, che non compare mai nel sito.
- `nowUpdated`, `now`, `lookingFor`: la sezione *now*. Aggiornala 2–3 volte l'anno.

Subito sotto ci sono **`CARD`** (i testi della model card) e **`TOY`** (i testi dell'esperimento).

## Pubblicare su GitHub Pages

Su GitHub hai (e avrai) tre repository, ognuno con un ruolo diverso:

| Repository | Cos'è | Indirizzo |
|---|---|---|
| `ariannafrancesconi` (esiste già) | Il README che compare sul tuo profilo GitHub (la landing) | github.com/ariannafrancesconi |
| `ADELAI` (esiste già) | Il sito dello studio | ariannafrancesconi.github.io/ADELAI/ |
| **`ariannafrancesconi.github.io`** (da creare) | Questo sito personale | **ariannafrancesconi.github.io** |

Il nome `ariannafrancesconi.github.io` è speciale: GitHub lo pubblica all'indirizzo principale.
ADELAI continua a funzionare su `/ADELAI/` senza toccare niente.

1. GitHub → **+ → New repository** → nome esatto `ariannafrancesconi.github.io` → **Public** →
   *non* spuntare "Add a README" → **Create repository**.
2. Terminale (una volta sola):
   ```
   cd ~/Downloads/Pagine_web_personali/Sito_web_personale
   git init
   git add .
   git commit -m "Personal site"
   git branch -M main
   git remote add origin https://github.com/ariannafrancesconi/ariannafrancesconi.github.io.git
   git push -u origin main
   ```
   (Il file `.gitignore` esclude le foto originali WhatsApp: vengono caricate solo quelle ridimensionate in `img/`.)
3. Di solito si pubblica da solo. Se dopo 2 minuti il sito non c'è: **Settings → Pages** →
   Source *Deploy from a branch* → `main` / `(root)` → **Save**.
4. Sul tuo profilo GitHub: matita **Edit profile** → campo **Website** → `https://ariannafrancesconi.github.io`.

**Aggiornamenti successivi** (quando cambi `index.html`):
```
cd ~/Downloads/Pagine_web_personali/Sito_web_personale
git add . && git commit -m "Update" && git push
```

## Note
- Chiaro/scuro automatico, con pulsante in alto a destra.
- Le animazioni si disattivano da sole se il sistema ha "riduci movimento".
- Pagina in inglese, pensata per le candidature ai postdoc internazionali.
