# Bemanningsplan — infoskjermvisning

Dagsvisning av bemanningsplanen for Caverion avd. Tromsø, laget for infoskjerm
i 1920 × 1080 liggende. Viser kun dagens dato og bytter dag automatisk ved
midnatt, så kanalen kan stå åpen døgnet rundt.

**Alle data i dette repoet er eksempeldata.** Navn på ansatte og oppdrag er
byttet ut med oppdiktede navn. Strukturen — fag, grupper, fordeling av
oppdrag, kontor og fravær — er beholdt fra den virkelige planen, så visningen
ser ut og oppfører seg som i drift.

## Filer

| Fil | Hva det er |
| --- | --- |
| `index.html` | Ferdig visning i én selvstendig fil. Fonter, stiler og data ligger inne i filen. Dette er filen GitHub Pages publiserer. |
| `src/Bemanningsplan.dc.html` | Kildefilen for visningen. |
| `src/bemanningsplan-data-demo.js` | Eksempeldata: 45 ansatte i 14 faggrupper, alle 53 uker. |
| `src/support.js`, `src/_ds/` | Kjøretid og designsystem som kildefilen bruker. |

## Publisere med GitHub Pages

1. Legg filene i repoet, med `index.html` i roten.
2. *Settings → Pages*: velg branch `main` og mappe `/ (root)`, lagre.
3. Etter et par minutter ligger siden på `https://<brukernavn>.github.io/<repo>/`.
4. Lim URL-en inn som nettsidekanal i SmartSign.

Merk at GitHub Pages fra et privat repo krever GitHub Team eller Enterprise.
På en gratiskonto blir siden offentlig tilgjengelig — derfor eksempeldata.

## URL-parametere

| Parameter | Effekt |
| --- | --- |
| `?date=2026-08-20` | Viser en bestemt dato i stedet for dagens. Nyttig for testing. |
| `?data=https://.../plan.json` | Henter planen fra en JSON-fil ved oppstart og hvert 15. minutt i stedet for å bruke kopien i filen. Klokkeslettet for siste henting vises øverst til høyre. Feiler hentingen, fortsetter visningen med sist lagrede plan. |

## Fargekoder i visningen

- Hvit celle med grønn strek — oppdrag ute
- Lys grønn — kontor og prosjektering
- Skravert — fravær og permisjon
- Stiplet linje — ingen plan lagt inn
- «Ny»-merket og linjen nederst — oppdrag som er endret siden i går

## Data

Dataene kommer fra arket «Ukentlig timeplan» i `Bemanningsplan 2026.xlsx`.
Arket har 53 ukeblokker side om side: uke *n* starter i kolonne
`B + (n−1) × 15`, hver dag opptar to kolonner, og hjelpekolonnen `ADQ`
markerer om en rad er en faggruppe eller en ansatt.

For å oppdatere visningen må enten filen bygges på nytt fra Excel-arket,
eller planen legges ut som JSON og hentes med `?data=`-parameteren.
