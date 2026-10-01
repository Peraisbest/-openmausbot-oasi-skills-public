---
name: verifica-progressivo-duplicati-verbale
description: Verifica in sola lettura progressivi, duplicati e anomalie dei verbali di recupero di un Comune confrontando Registro Verbali 2026, Google Drive e Gmail. Non genera documenti e non modifica le fonti.
---

# Verifica progressivo e duplicati verbale

## Scopo

Determinare, per un Comune e per l'anno richiesto:
- il massimo progressivo affidabilmente verificato;
- eventuali duplicati, conflitti e anomalie;
- il prossimo numero candidato;
- le evidenze che sostengono il risultato.

Opera esclusivamente in READ-ONLY. Non creare, modificare, spostare, eliminare, inviare, archiviare o correggere dati, file, email, bozze o registri.

## Principi

- Non inventare dati e non determinare il progressivo dalla memoria linguistica.
- Distingui dati letti, evidenze verificate, dati mancanti e anomalie.
- Non correggere silenziosamente alias, duplicati o conflitti.
- Non considerare una singola fonte automaticamente infallibile.
- Il numero risultante è solo candidato: non è assegnato, prenotato o consumato.
- Completa la paginazione delle fonti.
- Se una verifica necessaria non è completabile, dichiaralo.

## Input

Comune e anno di riferimento. Per il 2026 il formato ordinario è `NN/26`.

## 1. Comune e alias

Individua varianti ortografiche e alias plausibilmente riferiti allo stesso Comune senza fonderli o correggerli automaticamente. Usa gli alias per ampliare la ricerca, conservando sempre il nome esatto presente nella fonte.

## 2. Registro — tab `Comuni`

Cerca tutte le righe pertinenti. Acquisisci almeno: riga, nome esatto, cartella Drive, ID cartella, ID modello se presente, ultimo verbale, prossimo verbale, destinatario, stato e note.

Se esistono più righe riferibili allo stesso Comune, confronta cartelle, ID, destinatari e progressivi; segnala alias, duplicazioni e conflitti senza scegliere arbitrariamente.

## 3. Registro — tab `Verbali`

Esamina anche lo storico `Verbali`. Filtra sulla colonna `Comune`, non sulla semplice presenza testuale del nome in indirizzi, note o altri campi.

Acquisisci almeno progressivo, Comune, data, ora, indirizzo, ID evento se presente, link Word/PDF e stato.

Determina progressivi distinti, massimo, buchi, numeri ripetuti, stesso recupero associato a più numeri e stesso numero associato a recuperi differenti. Un progressivo ripetuto non equivale automaticamente a un recupero duplicato.

## 4. Collegamenti del Registro

Per i link a documenti verifica, quando possibile:
- accessibilità;
- appartenenza alla cartella operativa pertinente;
- progressivo del Registro;
- progressivo nel filename;
- progressivo interno al documento.

Segnala separatamente link non accessibile, file mancante/fuori cartella, e ogni conflitto Registro/filename/contenuto. Non correggere nulla.

## 5. Google Drive

Usa l'ID cartella risultante dal Registro. Se esistono ID divergenti, ispezionali separatamente e segnala il conflitto.

Esamina tutti i file pertinenti all'anno. Considera nome, ID/link, formato, progressivo nominale e numero interno quando verificabile.

DOCX, PDF e Google Doc dello stesso recupero non sono verbali distinti solo perché esistono in più formati.

Per il massimo non fermarti al filename: verifica internamente i documenti che costituiscono l'evidenza del massimo e confronta più formati quando disponibili.

Determina massimo nominale, massimo verificato internamente, buchi, versioni multiple, incongruenze nome/contenuto e presenza/assenza del candidato successivo.

## 6. Gmail

Controlla in sola lettura messaggi inviati e bozze. Usa Comune, alias e destinatario verificato per evitare ricerche troppo strette e completa la paginazione.

Acquisisci quando disponibile oggetto, data, destinatario, message/thread ID, progressivo, allegati e indicazioni di reinvio/rettifica/integrazione.

Determina separatamente massimo inviato, massimo nelle bozze e presenza/assenza del candidato. Un secondo messaggio non costituisce automaticamente un nuovo verbale.

## 7. Classificazione anomalie

Classifica quando applicabile:
- duplicato del recupero;
- duplicato del progressivo;
- progressivi multipli per lo stesso recupero;
- versione/formato multiplo;
- reinvio;
- rettifica;
- integrazione;
- conflitto Registro / filename / contenuto;
- collegamento Registro non valido;
- anomalia non risolta.

Non confondere versioni/formati con duplicati operativi.

## 8. Confronto fonti

Confronta separatamente:
- Registro `Comuni`;
- Registro `Verbali`;
- Drive nomi file;
- Drive contenuto verificato;
- Gmail inviate;
- Gmail bozze.

Non nascondere divergenze.

## 9. Massimo affidabile

Il massimo affidabile non coincide automaticamente col valore più alto di una singola fonte.

In presenza di anomalie storiche può essere determinato se il massimo è corroborato da almeno due evidenze indipendenti e coerenti, ad esempio contenuto verificato Drive, invio Gmail con allegato coerente, Registro coerente o altra evidenza operativa verificabile.

Due formati dello stesso documento non sono automaticamente due evidenze indipendenti.

Se il massimo non è stabilibile con affidabilità, non proporre il successivo: restituisci `BLOCCATO/DA VERIFICARE` e indica il conflitto.

## 10. Prossimo numero candidato

Dopo aver stabilito il massimo:
1. calcola l'immediato successivo;
2. cercalo nel tab `Verbali`;
3. cercalo nelle cartelle Drive pertinenti;
4. cercalo nelle email inviate;
5. cercalo nelle bozze;
6. verifica che non emerga come numero interno di un documento pertinente con filename diverso.

Se assente e il massimo è affidabile, restituisci `Prossimo numero candidato: NN/AA`, specificando che non è assegnato, prenotato o consumato e che nessuna fonte è stata modificata.

## 11. Anomalie storiche

Non correggerle. Non bloccano necessariamente il candidato se:
- il massimo corrente è corroborato indipendentemente;
- il candidato è stato cercato esplicitamente nelle fonti operative;
- nessuna evidenza lo attribuisce già a un altro recupero;
- l'anomalia storica non rende ambiguo il massimo corrente.

Se manca una condizione, blocca la determinazione.

## Output

Riporta: Comune/alias; esito `Comuni`; esito `Verbali`; Drive; Gmail inviate/bozze; anomalie classificate; confronto fonti; massimo affidabile o motivo del blocco; candidato solo se verificabile; evidenze principali; conferma di nessuna scrittura.

## Vincoli finali

Non generare verbali; non creare/modificare documenti o bozze; non inviare email; non modificare il Registro; non rinominare/spostare/eliminare file; non correggere anomalie; non trasformare il candidato in numero assegnato.

La funzione termina con verifica e report.
