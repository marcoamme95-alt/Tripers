# TRIPERS — MASTER PROMPT PER CODEX

**Destinatario:** Codex, agente di sviluppo software.  
**Obiettivo:** creare un prototipo full-stack realmente eseguibile e poi sviluppare Tripers per release progressive.  
**Lingua:** interfaccia e documentazione utente in italiano; codice e convenzioni tecniche in inglese, ove opportuno.

---

## ISTRUZIONI OPERATIVE NON NEGOZIABILI

Agisci come un team senior composto da product manager, UX/UI designer, tech lead full-stack, database architect, security engineer, QA engineer e specialista travel-tech. Sei incaricato di **progettare e implementare** software, non soltanto proporre idee o produrre slide.

Lavori nel repository aperto. Se è vuoto, inizializza il progetto. Se contiene già codice, **analizzalo prima di modificarlo** e riutilizza ciò che è valido: non riscrivere inutilmente. Prima di eseguire modifiche distruttive chiedi conferma.

**Importante:** il progetto completo è ampio. Procedi per release verticali verificabili, senza fingere che una funzione futura sia già operativa. La prima consegna deve essere un **MVP realmente avviabile** sul computer locale, con database, autenticazione demo sicura, ruoli, percorsi utilizzabili, dati dimostrativi e test. Implementa quindi le altre funzioni una release alla volta. Non considerare il lavoro concluso con una homepage estetica o mockup statici.

Prima di lavorare:
1. Ispeziona repository, ambiente e strumenti disponibili; leggi eventuali allegati (Masterplan Tripers, piano ibrido, documenti Agenzia/Cliente). Se non sono allegati, usa rigorosamente i requisiti qui sotto.
2. Crea `AGENTS.md` con regole del progetto, `docs/ARCHITECTURE.md`, `docs/ROADMAP.md`, `docs/FEATURE_MATRIX.md` e `TASKS.md` con attività e progressi.
3. Produci un breve piano tecnico, quindi **inizia a sviluppare subito**, salvo blocchi reali. Non fermarti per chiedere preferenze estetiche secondarie.
4. Al termine di ciascuna release esegui installazione, lint, typecheck, test e build; correggi i problemi; dimostra il funzionamento. Se uno strumento non è disponibile, dichiara esplicitamente cosa non hai potuto verificare.
5. Non inventare API, prezzi aggiornati, disponibilità di voli, accordi con partner, commissioni o certificazioni. Funzioni non collegate a sistemi reali devono essere etichettate chiaramente `DEMO`, `DATI ESEMPLIFICATIVI` o `DA INTEGRARE`.
6. Non usare marchi, testi, foto, database o codice dei concorrenti senza autorizzazione. Ispirati soltanto a problemi, pattern funzionali e modelli di business generali.

## VISIONE E MODELLO TRIPERS

**Tripers è una piattaforma di viaggi B2C-first con marketplace multi-operatore e gestionale B2B.** Offre un'unica esperienza del viaggiatore prima, durante e dopo il viaggio, senza eliminare il valore della consulenza umana. È un prodotto digitale originale, con design proprio e ottimizzato per mobile.

Tre interfacce, **un solo core dati**:
- `Tripers Cliente` / `My Tripers`: persone che organizzano viaggi autonomamente oppure acquistano attraverso agenzie, tour operator o DMC.
- `Tripers Agenzia` / `Tripers OS`: agenzie di viaggio, tour operator e DMC, con ruoli e permessi di organizzazione.
- `Tripers Admin`: amministrazione piattaforma, partner, offerte, contenuti, qualità, lead, commissioni, analytics e supporto.

**Modello ibrido deciso:** FASE 1: Tripers mostra offerte, raccoglie richieste e invia clienti ai partner; il pacchetto viene contrattualizzato e pagato **direttamente al partner**. FASE 2: eventuale checkout integrato solo dopo accordi, valutazioni legali, pagamenti, rimborsi e compliance. **Non sviluppare né simulare come reale un checkout del pacchetto turistico nella FASE 1.** Tripers potrà incassare propri canoni e prodotti digitali secondo configurazione, inizialmente in sandbox.

Il valore totale dei pacchetti venduti dai partner **non è il fatturato Tripers**. Traccia GMV separatamente dai ricavi propri; registra commissioni soltanto quando fondate su un contratto e su una prenotazione attribuita e confermata. Non addebitare fee di acquisizione su clienti portati autonomamente dall'agenzia, salvo accordo separato.

## IDENTITÀ VISIVA E UX

Progetta un brand premium ma accessibile e amichevole. Palette orientativa Tripers: arancione `#F28C2E`, corallo `#EC653F`, rosa `#D92D5A`, bordeaux `#330C17`, fondo crema/bianco. Usa una sfumatura arancione→corallo→rosa solo dove utile. Design originale, luminoso, elegante, leggibile, non clone di Vela, TourRadar, Evaneos, WeRoad o altre piattaforme.

Interfaccia in italiano, responsive mobile-first, navigazione semplice, layout coerente, skeleton/loading, empty states, error states, feedback azioni, ricerca e filtri, accessibilità WCAG 2.2 AA dove applicabile. Realizza componenti riutilizzabili, tipografia accurata e iconografia consistente. Il marchio Tripers può essere rappresentato come wordmark tipografico se manca il file del logo, senza spacciare il wordmark temporaneo per logo ufficiale.

La navigazione pubblica deve includere: `Scopri viaggi`, `Viaggi di gruppo`, `Viaggi su misura`, `Come funziona`, `Tripers Cliente`, `Per agenzie e partner`, `Accedi`.

## FUNZIONI RICHIESTE — TRIPERS CLIENTE

1. Dashboard personale con viaggi futuri, in corso e passati; home contestuale prima/durante/dopo il viaggio.
2. Creazione viaggio manuale con destinazione, periodo, passeggeri, preferenze e budget. Gestione tappe e agenda giorno per giorno, mappe e documenti.
3. `Booking Importer`: caricamento privato PDF/voucher/email inoltrata, parse e bozza dati, verifica e conferma umana, controllo duplicati/date/fusi orari; predisporre adapter AI opzionale senza promettere estrazione accurata senza API. Nella demo usare dati fixture esplicitamente etichettati.
4. `Trip Sharing`: invito partecipanti, ruoli, autorizzazioni granulari, commenti, proposte di modifica e spese condivise. Nessun partecipante vede passaporti, dati sanitari o documenti privati degli altri per impostazione predefinita.
5. `Tripers Wallet`: budget, spese in più valute, pagante, quote, split e saldi; non è un conto bancario o sistema di pagamento.
6. `Country Kit`: app e trasporti locali, requisiti documentali come informazioni orientative con fonte e data verifica, valuta, prese, emergenze, connettività.
7. `Daily Experience`: programma del giorno, suggerimenti contestuali, photo spots, mappe, trasporti, meteo solo se collegato a provider, attività pertinenti.
8. Outfit completamente **facoltativi e disattivati di default**: aggiunta/modifica manuale, suggerimenti su richiesta, privati di default e condivisibili con scelta esplicita.
9. `Tripers Care`: guida in caso di volo cancellato, hotel, bagagli, questioni sanitarie e assicurazione; procedure e contatti ufficiali; ticket/escalation al partner quando autorizzati. Non dichiarare assistenza d'emergenza reale 24/7 se non esiste.
10. `Travel Readiness`: checklist documenti, visti/ESTA/eTA, scadenze e link al check-in; **un link al check-in non significa check-in effettuato**. Nessun rilascio automatico di autorizzazioni o biglietti senza provider abilitato.
11. Piani B2C configurabili: Lite gratuito, Premium software ipotetico 5,99 €/mese, Trip Pass ipotetico 9,90 €/viaggio, consulenze Check 49 €, Route 149 €, Premium consulenza 299 € (prezzi proposti e da validare, IVA e condizioni da configurare). Non confondere Premium software e Premium consulenza.

## FUNZIONI RICHIESTE — TRIPERS AGENZIA

1. Account organizzazione, agenti, responsabili, permessi per tenant, profili clienti, pratiche e assegnazioni.
2. CRM leggero con richieste marketplace, brief, stati lead, note, preventivi, follow-up e storico eventi.
3. `Tripers Preview`: proposta visiva ispirazionale prima dell'acquisto (città, notti, highlights, foto lecite, budget/prezzi esplicitamente stimati o verificati). Approvazione finale dell'agente.
4. Pratiche confermate con voli, hotel, transfer, partecipanti, allegati, timeline, scadenze e documenti; invito clienti a My Tripers.
5. `AI Planner + Route Validator`: itinerari da brief, calendario con vincoli, luoghi con fonti, controllo tempi di spostamento con provider cartografico, conferma umana. Non presentare un prezzo inventato dall'AI come prenotabile.
6. `Agent Copilot`: dashboard priorità, attività e promemoria; notifiche stato pratica e follow-up; log eventi.
7. Supporto a Travel Readiness e Tripers Care con escalation, ruoli chiari e audit.
8. Report B2B: clienti e pratiche, tempo di risposta, lead, booking confermati, ricavi attribuiti, extra e commissioni verificati.
9. Canoni B2B proposti, IVA esclusa e **configurabili**, sulla media degli ultimi tre mesi delle **nuove pratiche confermate**: Start 0–20 a 59 €/mese, Growth 21–60 a 119 €, Pro 61–150 a 239 €, Network 151–300 a 399 €, Enterprise oltre 300 da accordare. Escludere preventivi, doppioni e vecchie pratiche importate.
10. **Migrazione da Vela**: percorso di importazione esclusivamente autorizzato (export/API/documenti), validazione 1:1, staging, error report, audit, rollback. Canone Tripers **zero durante tutta la migrazione** fino alla verifica delle pratiche concordate, approvazione finale dell'agenzia e cutover completato; non attivarlo dopo una scadenza temporale automatica.

## FUNZIONI RICHIESTE — MARKETPLACE E PARTNER

1. Catalogo multi-operatore originale con categorie `Viaggi di gruppo`, `Viaggi su misura`, `Tour organizzati`, `Esperienze`, filtri per destinazione, date, budget, durata, stile, età se pertinente e operatore.
2. Scheda offerta con organizzatore contrattuale chiaramente identificato, descrizione autorizzata, servizi inclusi/esclusi, prezzi con provenienza, data ultimo aggiornamento, disponibilità non falsamente live, condizioni di cancellazione, CTA `Richiedi preventivo` o `Vai al partner`.
3. Lead: form, consenso e informative, routing al partner, deduplica, stati, messaggi e follow-up; tracking referral con identificatore ed eventi verificabili.
4. Partner dashboard per tour operator, DMC e agenzie: pubblicare bozze offerte, aggiornarle, ricevere richieste e confermare l'esito della vendita. Pubblicazione amministrata e controllata.
5. Commissioni: modello configurabile per contratto e fonte lead; calcolo su booking **confermato** e commissionabile; gestire storni, annullamenti, storicizzazione e riconciliazione. Demo economica etichettata, nessuna commissione fittizia presentata come incassata.
6. Adapter provider astratti per cataloghi/link affiliati, senza scraping non autorizzato. Connettori futuri possibili: WeRoad, Utravel, TourRadar, Evaneos/DMC, GetYourGuide, Viator, Klook, eSIM, transfer, parcheggi, assicurazioni solo dove abilitati. Nessuna partnership presunta.
7. `Tripers Group Travel`: partenze, programma, posti dichiarati dal partner, profilo esperienza, coordinatore se previsto, link al partner e condivisione in My Tripers. Community avanzata in fase successiva.
8. `Tripers DMC Network`: richiesta viaggio su misura, brief, assegnazione all'esperto/agenzia autorizzata, preventivo e stato richiesta.

## MODULO FUTURO — TRIPERS MILES FINDER

Inserisci nell'architettura un `Loyalty Hub` con programmi fedeltà e saldi manuali, senza memorizzare password delle compagnie. Predisponi interfaccia demo per:
- Visualizzare saldi distinti e status dei programmi, senza sommare miglia eterogenee.
- Ricercare voli premio per tratta, date, classe e passeggeri.
- Confrontare denaro vs miglia + tasse, includendo condizioni e data verifica.
- Evidenziare una consulenza specializzata per l'agenzia, senza promettere commissioni sulle prenotazioni premio.
- Reindirizzare al programma/partner ufficiale per il riscatto nella prima fase.

API da valutare **solo dopo accordo commerciale**: AwardWallet, Seats.aero e altri provider. Nella demo usa un provider mock con etichette visibili. Non creare finti collegamenti a veri account, non memorizzare credenziali e non mostrare posti premio inventati come reali.

## ARCHITETTURA, DATI E QUALITÀ

Prediligi **un modular monolith** semplice e manutenibile per un team piccolo. Stack consigliato salvo motivazione tecnica documentata: Next.js App Router, TypeScript strict, React, Tailwind CSS, componenti accessibili stile shadcn/ui, PostgreSQL, Prisma o Drizzle, Zod per validazione, test Vitest e Playwright. Per login e storage privato scegli opzioni collaudate, spiegando i compromessi; le chiavi restano lato server. Usa Docker Compose per sviluppo locale se l'ambiente lo consente. Evita dipendenze superflue e microservizi prematuri.

Entità base: `User`, `Organization`, `Membership`, `PartnerProfile`, `TravelOffer`, `Departure`, `Lead`, `Proposal`, `ProposalVersion`, `Trip`, `TripParticipant`, `TravelSegment`, `ItineraryDay`, `ItineraryItem`, `Document`, `ImportJob`, `Expense`, `ExpenseSplit`, `Notification`, `Consent`, `AuditEvent`, `AffiliateEvent`, `Commission`, `LoyaltyProgram`, `LoyaltyAccount`, `AwardSearch`, `AssistanceCase`, `MigrationBatch`, `MigrationItem`, `AgencyBillingState`.

**Sicurezza imprescindibile:** multi-tenancy applicata lato server e query database, non solo filtri frontend; policy/RLS se stack Supabase. Test automatico che un'agenzia non acceda alle pratiche di un'altra; documenti privati con accessi e download autorizzati; RBAC, log audit, autorizzazione per ogni endpoint, protezione input e upload, rate limiting, gestione errori, eliminazione e retention dati, minimizzazione privacy, backup e ripristino documentati. Non usare mai dati personali veri nelle fixture o chiavi di produzione nel repository. Inserisci `.env.example`, escludi segreti da Git.

Gestisci timezone locali, EUR e valuta originale, date, localizzazione it-IT, prezzi IVA inclusa/esclusa distinti, fonti dei dati, versioni dei preventivi, idempotenza delle importazioni e della conferma prenotazioni.

Predisponi provider interfaces per AI, Maps, document parsing, email, pagamenti propri, meteo, flight status, booking/affiliate e miles. Dove le chiavi non esistono, implementa mock espliciti e un'architettura sostituibile. **Nessun checkout turistico, trasferimento fondi, emissione biglietti, ESTA automatica, assicurazione o check-in nativo simulato come realmente operativo.**

Documenta verifiche legali necessarie: Codice del Turismo/pacchetti, trasparenza marketplace, GDPR, ruoli nel trattamento dati, normative sui pagamenti, possibili intermediari assicurativi e contratti con i fornitori. Non affermare di aver ottenuto autorizzazioni.

## CONSEGNE IN SEQUENZA

### RELEASE 0 — Audit e progetto
- Analisi del repository; architettura e modello dati; backlog tracciato; mappa delle pagine e flussi. Se repository vuoto, inizializzazione completa.
- Setup comandi `install`, `dev`, `lint`, `typecheck`, `test`, `build`, `seed`.

### RELEASE 1 — MVP verticale realmente funzionante (priorità assoluta)
Implementa e rendi navigabile, con dati seed demo, questo percorso end-to-end:

**Un viaggiatore cerca un viaggio in Giappone → trova un'offerta autenticamente contrassegnata DEMO → richiede un preventivo → il partner riceve il lead in Tripers Agenzia → l'agente registra una proposta e una conferma demo → nasce un Trip condivisibile → il viaggiatore accede a My Tripers con itinerario e documenti dimostrativi.**

Da includere: homepage curata, catalogo/filtri, dettagli offerta, account viaggiatore, account agenzia, dashboard e gestione lead, approvazione proposta, trip core, condivisione essenziale, area admin base, ruoli sicuri, seed e test del flusso. Tutto deve funzionare localmente **senza API commerciali o credenziali reali**, con modalità demo dichiarata. Prevedi login demo o fixture per il test, ma nessuna scorciatoia di autenticazione abilitata in produzione.

### RELEASE 2 — Utilità dopo la prenotazione
Booking Importer con revisione manuale, Route editor, Wallet, Country Kit, notifiche/task, Daily Experience, Care guidato, preview e versioning. Test su permessi e date.

### RELEASE 3 — Distribuzione e monetizzazione
Gestione partner, DMC e viaggi di gruppo, affiliate tracking e commission ledger con stati, piani tariffari configurabili, billing sandbox per prodotti propri, migrazione Vela autorizzata, AI Planner con adapter/provider opzionali.

### RELEASE 4 — Fidelity e integrazioni
Loyalty Hub/Miles Finder demo e integrazioni live **soltanto quando esistono chiavi e accordi**; provider extra; analytics completi; ottimizzazione e hardening.

### RELEASE FUTURA NON IMPLEMENTARE NEL PRIMO MVP
Checkout travel integrato, booking engine voli/hotel, conferma live posti senza API autorizzate, biglietti premio emessi dentro Tripers, app native; mantenerli come milestone condizionate.

## CRITERI DI ACCETTAZIONE

- Avvio locale documentato in `README.md`, con comandi esatti e credenziali demo non sensibili.
- Almeno un flusso E2E automatizzato che copra visitatore → lead → agenzia → viaggio cliente.
- Due agenzie seed distinte; un test deve provare che l'agenzia A non può leggere o alterare dati dell'agenzia B, nemmeno tramite API.
- Distinzione chiara tra dati demo, dati reali e risultati da provider autorizzati.
- Mobile responsive, accessibile e usabile; caricamenti, errori e stati vuoti gestiti.
- Nessuna dipendenza da chiavi commerciali per l'avvio demo.
- Build e test eseguiti con esito riportato onestamente; correggi tutti i problemi bloccanti identificati.
- `docs/FEATURE_MATRIX.md` che distingua IMPLEMENTATO / DEMO / PARZIALE / NON IMPLEMENTATO; `docs/INTEGRATIONS.md` che indichi per ogni provider contratto, API, costi e permessi da verificare.
- Alla fine mostra: struttura del progetto, cosa è realmente pronto, come avviarlo, screenshot (se ambiente lo permette), risultati dei test, limiti e tre attività più importanti successive.

## COMANDO FINALE

**Non fermarti al piano: crea file, codice, migrazioni, seed, pagine, componenti, API, test e documentazione. Comincia subito dalla RELEASE 0 e prosegui fino alla RELEASE 1 completamente avviabile.** Se il lavoro supera i limiti della sessione, salva lo stato in `TASKS.md`, lascia il repository eseguibile e riprendi dal prossimo task al turno seguente. Non dichiarare completate le release 2–4 senza implementazione e test effettivi.
