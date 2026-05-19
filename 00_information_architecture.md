# INFORMATION ARCHITECTURE

## Mappa gerarchica dell'app

```
GOAL APP
│
├── 🏠 HOME (Hub)
│   ├── Banner Lega corrente (Serie X, posizione)
│   ├── Daily Player card
│   ├── Grid del giorno card
│   ├── Duello card (con notifica se sfida pendente)
│   ├── Pronostici Live card (se match imminenti)
│   ├── Carriera card
│   └── Esplora card
│
├── 🏆 LEGA SETTIMANALE
│   ├── La mia posizione + 29 avversari (scrollable list)
│   ├── Punti del periodo
│   ├── Soglia promozione / retrocessione
│   ├── Cronologia settimane passate (5 più recenti)
│   └── Trofei Lega vinti
│
├── ⚔️ DUELLO (centro)
│   ├── Quick Match (matchmaking automatico)
│   ├── Sfida amico
│   ├── Inviti ricevuti (badge)
│   ├── Cronologia partite (10 più recenti)
│   └── Tornei attivi (se Premium)
│
├── 👤 PROFILO
│   ├── Header: avatar + nome calciatore + Caratura totale
│   ├── Squadra del cuore
│   ├── Filotto attuale + Freezer disponibili
│   ├── Statistiche complete (per categoria)
│   ├── Bacheca trofei (grid)
│   ├── Cronologia Carriera
│   ├── Settings
│   └── Goal Premium (upsell o gestione)
│
└── 🧭 MENU SECONDARIO (hamburger)
    ├── Amici (lista, ricerca, invito)
    ├── Leghe private
    ├── Esplora (quiz tematici free)
    ├── Notifiche history
    ├── Settings
    ├── Aiuto / FAQ
    └── About Goal
```

---

## Bottom navigation (5 tab fissi)

```
┌──────┬──────┬──────┬──────┬──────┐
│ Home │ Lega │ ⚔️    │ Carr.│ Prof.│
└──────┴──────┴──────┴──────┴──────┘
   1     2     3      4      5
```

Tab 3 (Duello) ha layout speciale: icona più grande, sopra-elevata. È il "play button" universale.

---

## Profondità di navigazione

Regola: **mai più di 3 tap dall'hub al qualsiasi azione di gioco**.

Esempi:
- Hub → Daily Player → Gioco (2 tap)
- Hub → Duello → Quick Match → Gioco (3 tap)
- Hub → Lega → Posizione (2 tap)
- Hub → Profilo → Settings → Notifiche (3 tap)

Se serve un 4° tap, c'è qualcosa di sbagliato nell'IA.

---

## Modali e overlay

Gli overlay si usano per:
- Onboarding (sequenziale)
- Promozione/retrocessione Lega (celebrative)
- Achievement unlocked
- Conferma azioni critiche
- Premium upsell (raramente, contestuale)

**NON** usiamo overlay per:
- Errori di sistema (sono toast/snackbar)
- Tutorial in-game (sono inline hints)
- Pubblicità (NO ads invasivi mai)

---

## Stato globale visibile

Sempre visibile in alto (status bar dell'app):
- Connessione (icona piccola se assente)
- Cambi rimanenti (5/5)
- Notifiche pendenti (badge)

---

## Search & discovery

L'app non ha una **search universale**. Le ricerche sono **contestuali**:
- Cerca giocatore (in Daily Player input)
- Cerca amico (in Amici)
- Cerca categoria (in Esplora)

Niente search bar top-level → meno overhead UX, più focus.

---

## Empty states

Ogni sezione ha un empty state intenzionale:
- Hub home post-onboarding: vuoto al 50% (le card non giocate sono "fresche")
- Bacheca trofei: stato "Bacheca vuota. Vinci la tua prima Lega."
- Cronologia: "Niente ancora. Apri un Duello."
- Amici: "Goal è meglio con amici. Invitane uno."

Tone of voice: vedi `../D_brand/02_tone_of_voice.md`.
