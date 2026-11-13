# Pedale per chitarra: compressore a OTA + auto-wah

Progetto open source di un pedale per chitarra analogico che combina in un'unica scheda un **compressore** (OTA con *current stealing*) e un effetto **auto-wah** (filtro a due poli OTA-C con risonanza). Tutti i componenti sono a foro passante (THT), così da poter essere saldati a mano.

Il progetto nasce come tesi di laurea (Università degli studi di Trento, Dipartimento di ingegneria industriale: Robotica e Meccatronica, a.a. 2025/2026, autore Nicolò Ozretić, relatore Lucio Pancheri).

> ## ⚠️ Stato del progetto: NON ancora concluso
>
> - Il progetto è alla **fase di progettazione e simulazione**: il pedale **non è stato ancora costruito né misurato**.
> - I risultati riportati (guadagno, soglia, consumi, distorsione) vengono da simulazioni LTspice, non da misure.
> - Le schede **non sono state ordinate né verificate**: se le ordini, lo fai a tuo rischio.
> - È nota almeno una modifica da introdurre al prototipo: un **resistore di shunt (circa 680 Ω)** tra l'ingresso invertente dell'OTA del VCA e V<sub>bias</sub>, che realizza nel circuito reale l'attenuazione d'ingresso assunta nelle simulazioni. Non è ancora nello schema KiCad (vedi la tesi, Capitolo 5 e Conclusioni).
> - Questo repository verrà aggiornato man mano che il lavoro prosegue. Controlla la sezione *Cronologia* per le novità.

## Caratteristiche (da simulazione)

| | |
|---|---|
| Alimentazione | solo alimentatore da muro a 9 V (nessuna batteria) |
| Consumo | 19–23 mA senza LED, 26–30 mA con LED (233–271 mW) |
| Compressore | guadagno ≈ 10 dB sotto soglia, soglia ≈ 250 mV, rapporto ≈ 2,6:1, attacco ≈ 4 ms, rilascio ≈ 200 ms |
| Auto-wah | picco di risonanza ≈ 13 dB (Q ≈ 4,5), frequenza di picco da ≈ 235 Hz a ≈ 2,6 kHz, comandata dall'inviluppo |
| Componenti attivi | 2 × LM13700, 2 × TL074, TLE2426 (massa virtuale 4,5 V) |
| Controlli | SUSTAIN, DECAY, SENS, MASTER, trimmer di livello |
| Footswitch | 3PDT (serie FS5700) |

## Contenuto del repository

```
hardware/   progetto KiCad (schema, circuito stampato, librerie)
produzione/ file Gerber, distinta componenti (BOM) e posizioni, per ordinare la scheda
simulazioni/ file LTspice e script
tesi/       sorgenti LaTeX e PDF della tesi
docs/       tutorial (acquisto, montaggio, prove)
```

*(La struttura potrà cambiare: i file si aggiungeranno man mano.)*

## Tutorial: ordinare e costruire il pedale

> Il tutorial completo sarà pubblicato qui in `docs/` quando il progetto sarà verificato su un prototipo. Questa è la traccia di ciò che conterrà.

1. **Strumenti necessari**: saldatore a stagno, stagno, tronchesine, multimetro, cacciaviti, alimentatore da muro a 9 V (centro negativo, come la maggior parte dei pedali), cavi jack.
2. **Ordinare il circuito stampato**: caricare i file Gerber della cartella `produzione/` su un servizio di produzione di PCB (JLCPCB, PCBWay o simili) e scegliere le opzioni indicate nel tutorial (spessore, finitura, numero di strati).
3. **Ordinare i componenti**: dalla distinta componenti (BOM) in `produzione/`, presso un distributore di componenti elettronici (Mouser, Farnell, Digi-Key, RS o simili). Il tutorial indicherà le alternative equivalenti per i componenti più difficili da reperire.
4. **Montaggio**: ordine di saldatura consigliato (resistori, diodi, zoccoli per i circuiti integrati, condensatori, transistor, componenti ingombranti, potenziometri, connettori, footswitch), con attenzione alla polarità dei condensatori elettrolitici, dei diodi e dei circuiti integrati.
5. **Prima accensione e prove**: controllo della tensione di alimentazione e di V<sub>bias</sub> (4,5 V) prima di inserire i circuiti integrati, verifica dei consumi, prova con una chitarra e regolazione del trimmer.
6. **Contenitore**: forature, montaggio dei controlli e del footswitch.

### Preventivo indicativo

Un preventivo del costo di scheda e componenti **non è ancora disponibile**: verrà aggiunto qui quando saranno disponibili i prezzi di un fornitore di PCB e di un distributore di componenti (con la data di consultazione).

## Sorgenti della tesi

La cartella `tesi/` contiene il progetto LaTeX (compilabile con `pdflatex`, ad esempio su Overleaf) e il PDF.

## Licenza

*Da definire.* Per un progetto di hardware aperto si prevede una licenza CERN-OHL per i file di progetto e una licenza Creative Commons (CC BY) per la documentazione. Fino a quando non sarà aggiunto un file `LICENSE`, valgono i diritti d'autore dell'autore.

## Cronologia

- **novembre 2026**: prima pubblicazione del repository (progetto in fase di progettazione e simulazione).

## Contatti e contributi

Per segnalazioni, errori o miglioramenti apri una *Issue* in questo repository. I contributi sono benvenuti, in particolare le misure sul prototipo, se lo costruisci.
