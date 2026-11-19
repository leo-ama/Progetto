# Sito per ricette

Web app per consultare e cercare ricette di cucina, ispirata a GialloZafferano.
Progetto scolastico realizzato da **Leonardo Amadini**, classe 5IB, paleocapa, a.s. 2026/2027.

## Descrizione

Il sito permette di trovare ricette, vederne le istruzioni e, dopo la registrazione,
lasciare recensioni.

## Funzionalità

**Visitatore (senza account)**
- Visualizzare la homepage
- Cambiare la lingua del sito
- Vedere le ricette suggerite
- Cercare ricette per ingredienti, con filtro per tipo di cibo
- Selezionare una ricetta e leggerne le istruzioni
- Registrarsi

**Utente registrato** (può fare tutto ciò che fa il Visitatore, più:)
- Effettuare il login e il logout
- Inserire recensioni sulle ricette

## Documentazione di progetto

- Diagramma dei casi d'uso: `docs/casi-d-uso.pdf`
- Diagramma delle classi: `docs/classi.pdf`
- Schema E-R (con dizionario dei dati e vincoli): `docs/er.pdf`
- Analisi SWOT: `docs/swot.pdf`

Classi principali: `Utente`, `Ricetta`, `Recensione`, `Ingrediente`,
`IngredienteRicetta`, `TipoCibo`.

## Modello dei dati

**Entità**

| Entità | Attributi | Identificatore |
|---|---|---|
| Utente | nomeUtente, email, password | nomeUtente |
| Ricetta | id, titolo, istruzioni, tempoPreparazione, difficolta | id |
| Recensione | id, voto, testo, data | id |
| Ingrediente | nome | nome |
| TipoCibo | nome | nome |

**Relazioni**

| Relazione | Entità coinvolte | Cardinalità | Attributi |
|---|---|---|---|
| Scrive | Utente - Recensione | (0,N) - (1,1) | / |
| Riguarda | Recensione - Ricetta | (1,1) - (0,N) | / |
| HaTipo | Ricetta - TipoCibo | (1,N) - (0,N) | / |
| Contiene | Ricetta - Ingrediente | (1,N) - (0,N) | quantita, unita |

**Vincoli principali**
- `email` univoca
- `voto` compreso tra 1 e 5
- `tempoPreparazione` e `quantita` maggiori di zero
- un utente può recensire la stessa ricetta una sola volta
- `votoMedio` di una ricetta è un dato derivato (media dei voti delle recensioni)

## Analisi SWOT in breve

- **Punti di forza:** interfaccia semplice, ricerca per ingredienti, multilingua, recensioni
- **Punti di debolezza:** poche ricette iniziali, risorse limitate, sito poco noto
- **Opportunità:** possibili estensioni (preferiti, filtri per dieta), riduzione degli sprechi
- **Minacce:** concorrenti noti, protezione dei dati (GDPR), diritti d'autore sui contenuti
