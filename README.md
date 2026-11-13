# NexGest

Gestionale per **agenzie di intermediazione di prestiti e finanziamenti**: aziende convenzionate, clienti, operatori, campagne promozionali, pratiche con le diverse finanziarie (tra cui Agos) e promemoria di follow-up, con controllo delle performance degli operatori.

Progettato e sviluppato da me, versione 1.0 (maggio 2026), pronto per la demo al cliente con dati di prova e manuale utente.

> Il codice non è pubblicato: posso mostrare l'applicazione e il codice durante un colloquio.

**Stack:** PHP 8.2 · MySQL/MariaDB · PHPRunner (generazione) + libreria PHP scritta a mano · JavaScript · Chart.js · Bootstrap · PowerShell · hosting condiviso con cron

## Cosa fa
**Anagrafiche.** Aziende convenzionate, clienti con validazione del codice fiscale e consenso marketing, operatori con creazione e sincronizzazione automatica dell'account (username univoco, ruolo predefinito).

**Pratiche.** Contratti con le finanziarie e calcolo automatico di importo finanziato, TAN, IRR, rendimento e assicurazione (CPI); importazione da CSV con registro degli import; ricerche salvate.

**Promemoria.** Scadenze con priorità e stato, assegnazione a più operatori, ricorrenze, visibilità in base al ruolo, **email automatica giornaliera** dei promemoria in scadenza (script da cron con modalità di prova e senza invii doppi).

**Analisi.** Dashboard con grafici per periodo (finanziato, contratti, incidenza CPI), lista giornaliera, classifica degli operatori, estrazioni con filtri, assegnazione delle campagne in massa.

## Sicurezza e qualità
- **3 ruoli** (amministratore, supervisore, operatore) con **sicurezza a livello di riga**: ogni operatore vede solo le proprie pratiche; pagine di amministrazione bloccate lato server.
- Password con **bcrypt**, mai mostrate nelle liste.
- **Audit log** di ogni inserimento, modifica ed eliminazione, con i dati prima e dopo in JSON.
- **Eliminazione logica** (soft delete) su tutte le anagrafiche e le pratiche.
- **QA documentato** su due ruoli, con registro di bug e miglioramenti (severità, correzione, verifica).

## Lavoro oltre il generatore
PHPRunner genera le pagine, ma la logica è in una **libreria PHP di oltre 700 righe** scritta da me (ruoli, filtri di riga, audit, calcoli finanziari, ricorrenze, gestione utenti) più gli eventi delle singole tabelle e JavaScript per l'interfaccia. Siccome ogni nuova generazione sovrascrive i file, ho scritto uno **script PowerShell di ripristino post-build** e una checklist di 10 test da rifare a ogni build.

---
**Filippo Bonanno** · sviluppatore web (PHP, PrestaShop, Laravel, JavaScript) · altri progetti: [gestionale multi shop](https://github.com/FilippoBonanno/gestionale-multi-shop), [moduli PrestaShop](https://github.com/FilippoBonanno/prestashop-modules-showcase)
