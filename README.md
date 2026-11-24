# SQ-2 ACIDPILOT

**Sequencer acid a due tracce per telefono Android, stile Korg Gadget.**
Riceve il MIDI clock dalla **Korg Electribe** e pilota **Behringer TD-3** e **Donner Essential B1** su due uscite o canali MIDI, con pattern, scene, preset e scale che seguono la tonalità scelta.

Fa parte della collezione **DocLAB**: un solo file HTML, nessuna dipendenza, funziona offline.

▶ **Apri l'app:** https://alessandrotemi.github.io/Acid-Lab/SQ-2_ACIDPILOT.html

---

## Funzioni

- **Clock esterno o interno:** si sincronizza col MIDI clock dell'Electribe (start, stop, continue, song position) oppure suona col clock interno da 60 a 200 BPM.
- **Due tracce indipendenti:** una per la TD-3 e una per il B1, ciascuna con porta, canale, ottava, velocity, accent, gate, swing, risoluzione (da 1/32 a 1/8) e offset in ms.
- **8 pattern per traccia**, fino a 32 step. Il cambio pattern va in coda e scatta a fine pattern o a fine battuta.
- **8 scene** per richiamare insieme i pattern delle due tracce.
- **Accent e slide stile 303:** l'accent passa con la velocity, lo slide con le note sovrapposte; uno slide sulla stessa nota diventa una nota tenuta.
- **36 preset acid** in 7 stili: classico, acidcore, mental, melodico, minimal, rave, basso.
- **25 scale**, tra cui modi, minori ed esotiche, pentatoniche, blues, hirajoshi, diminuita e cromatica.
- **Tutto segue la tonalità:** cambiando fondamentale o scala si adattano preset e pattern, anche mentre suona.
- **Tastiera GRADI** (solo note della scala) oppure **PIANO** (cromatica), con modalità REC passo-passo.
- **Strumenti sul pattern:** RND (linea casuale in scala), MUT, rotazione, sposta di un grado, copia/incolla, annulla.
- **Anteprima audio:** un synth 303 interno per ascoltare e correggere le melodie anche senza hardware.
- **Timing:** modalità DIRETTO oppure PREDITTIVO, che toglie il jitter del telefono e permette di anticipare una traccia per allinearla all'Electribe.
- **Sicurezza sul palco:** pulsante ALL OFF, chiusura automatica delle note se il clock sparisce, schermo sempre acceso, riconoscimento automatico dei dispositivi collegati a caldo.
- **Salvataggio automatico** nel browser, più esportazione e importazione del set in JSON.

## Requisiti

| | |
|---|---|
| Browser | **Chrome per Android** (o un altro browser con Web MIDI) |
| Indirizzo | **https** (GitHub Pages va bene). Web MIDI non funziona da file locale né dentro le anteprime |
| Collegamento | **Hub USB-C OTG alimentato, senza uscita HDMI** |
| Hardware | Korg Electribe (clock), Behringer TD-3, Donner Essential B1, oppure qualsiasi synth MIDI |

## Collegamento

1. Collega Electribe, TD-3 e B1 all'hub e l'hub al telefono. Collega anche il caricatore alla porta PD dell'hub.
2. Su OnePlus e simili attiva **Impostazioni → Impostazioni aggiuntive → Connessione OTG**: può spegnersi da sola dopo 10 minuti senza uso.
3. Apri l'app in Chrome, tocca **COLLEGA IL MIDI** e consenti l'accesso ai dispositivi MIDI.
4. Le porte con nome Electribe, TD-3 e B1 vengono assegnate da sole. Puoi cambiarle in **⚙ SETUP**, dove il pulsante **TEST** manda una nota di prova a ogni traccia.
5. Premi play sull'Electribe: l'app parte a tempo.

### Impostazioni dei synth

- **TD-3 (Behringer SynthTool):** imposta il canale MIDI. L'accent scatta con velocity sopra 100. Se lo slide non si sente, disattiva **Multi Trigger**.
- **B1 (Donner Control):** imposta il canale MIDI e porta **Accent Velocity Threshold** sotto il valore ACC della traccia (di default 127).
- **Electribe:** clock interno, con trasmissione del clock attiva sulla porta che usi (USB o MIDI OUT).

## Uso rapido

| Azione | Gesto |
|---|---|
| Cambiare pattern (in coda) e modificarlo | tocca il pad 1–8 |
| Modificare un pattern senza cambiare quello che suona | tieni premuto il pad |
| Salvare una scena | **STORE**, poi la scena S1–S8 |
| Selezionare uno step / accenderlo o spegnerlo | tocca / ritocca lo step |
| Scrivere note in sequenza | **REC→**, poi i tasti |
| Caricare un preset | **★ PRESET** |
| Cambiare tonalità per tutto il set | barra **TONALITÀ** (◀ ▶ e scala) |
| Ascoltare senza hardware | **🔊 ANTEPRIMA**, poi ▶ |
| Spegnere tutte le note | **ALL OFF** |

## Problemi comuni

- **Lo schermo diventa nero quando collego l'hub:** succede con gli hub che hanno l'uscita HDMI. Usa un hub senza HDMI.
- **Nessuna porta MIDI:** controlla che la pagina sia aperta da https, che l'OTG sia attivo e che i permessi MIDI del sito siano concessi in Chrome.
- **Note cortissime o perse:** in SETUP imposta **Invio MIDI → TIMER JS**.
- **Synth in ritardo rispetto all'Electribe:** imposta **Timing → PREDITTIVO** e dai un offset negativo alla traccia (⚙ sulla traccia).

## Tecnica

- Un solo file HTML/CSS/JS senza librerie esterne, basato su **Web MIDI API** e **Web Audio API** (per l'anteprima).
- Lo scheduling usa i timestamp MIDI con una coda annullabile: STOP e MUTE non lasciano partire note già programmate.
- Tempo e fase del clock esterno sono stimati con una regressione lineare sugli ultimi 24 tick.
- Le note sono salvate come gradi della scala, così fondamentale e scala si possono cambiare senza perdere le melodie.

---

**DocLAB** · strumenti audio per il browser
