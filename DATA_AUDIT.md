# Data-revisjonsrapport – REKSTAD Fantasy Guide
**Revidert: 11. juni 2026 (før deadline R1 kl. 21:00)**

## Hovedfunn
Spillergrunnlaget var allerede komplett i datakilden (API-et), men nettsiden *skjulte* store deler av det:
filteret «kun startere» var slått PÅ som standard, slik at spillere med modellert startsannsynlighet under 70 %
(bl.a. Mohamed Hany, Leroy Sané og Enner Valencia) aldri ble vist. Dette er nå fikset – standard er å vise alle.

## 1. Spillerliste vs. TV 2 VM Fantasy (hovedkilde)
Sammenlignet 1:1 mot TV 2s offisielle prisliste (CSV fra vmfantasy.tv2.no/stats):

| Sjekk | Resultat |
|---|---|
| Antall spillere før | 1249 (i datakilden – men mange skjult i UI) |
| Antall spillere etter | 1249 – alle vises nå |
| Manglende spillere | 0 (Hany, Sané, Valencia m.fl. fantes, men var filtrert bort) |
| Spillere som ikke finnes i spillet | 0 |
| Duplikater | 0 |
| Prisavvik mot TV 2 | 0 av 1249 |
| Posisjonsavvik mot TV 2 (KEE/FOR/MID/ANG) | 0 av 1249 |
| Feil landslag | 0 av 1249 |
| Alle 48 nasjoner, 26 (27 POR*) spillere per tropp | OK (*TV 2 lister 27 for Portugal) |

## 2. Kampprogram
Alle 72 gruppekamper (24 per runde) verifisert mot offisiell VM-kalender.
Stikkprøver bekreftet eksternt: IRQ–NOR og FRA–SEN 16/6 (gruppe I), BRA–MAR 13/6, GER–CUR 14/6, NED–JPN 14/6.

## 3. Expected Points-modellen (endringer 11. juni)
- **Keepermål rettet:** modellen ga +10, TV 2 gir +8.
- **Ny: full kamp-bonus** (+1-poenget for MID/ANG som spiller hele kampen) er nå priset inn.
- **Ny: minuspoeng for baklengsmål** (−1 per 2. baklengsmål) trekkes nå fra for keeper/forsvar.
- **Ny: skader regnes per runde** – «Out R1» gir ~0 xP i runde 1 og normal xP fra runde 2 (f.eks. Neymar).
- Som før: xP = startsannsynlighet × (oppmøte + mål/assist-potensial + clean sheet + redninger − baklengs),
  per runde mot faktisk motstander, med rotasjonsjustering i R3 for trolig kvalifiserte lag.
- xP vises fortsatt per runde (R1/R2/R3), totalt og som verdi per million.

## 4. Skadeliste (oppdatert 11. juni, kilder: ESPN/theScore/beIN m.fl.)
- Neymar (BRA): ute i R1, trolig retur i R2 mot Haiti
- Jurriën Timber (NED): ute av hele VM (erstattet av Geertruida – ikke kjøpbar i spillet)
- Wesley (BRA): ute av hele VM → byttet ut av «Differensial»-troppen
- Lennart Karl (GER): ute av VM
- Alphonso Davies (CAN): mister åpningskampen
- Abde Ezzalzouli (MAR): mister minst R1
- Julio Enciso (PAR): sikter mot R3
- Giorgian de Arrascaeta (URU): tvilsom til R1
- Saka, Richards, Saliba: ventes å spille (merket «Monitor»)

## 5. Optimal Squads
- Alle 7 tropper re-validert mot TV 2-reglene: 100M budsjett, 2 KEE / 5 FOR / 5 MID / 3 ANG, maks 3 per land. 0 brudd.
- OPT_R1 og OPT_TOTAL er regnet helt på nytt med eksakt LP-optimalisering (CBC) på oppdatert xP.
- «Differensial»: Wesley (ute av VM) erstattet med Pau Cubarsí.
- Squad-kortene henter xP live, så alle tall reflekterer den nye modellen.

## 6. Kilder
- TV 2 VM Fantasy (vmfantasy.tv2.no): spillerliste, priser, posisjoner, eierandeler, regler, kampprogram (hovedkilde)
- Offisiell VM-kalender (FIFA/ESPN/Sky) for kryssjekk av kamper
- ESPN/theScore/beIN/Goal skadetrackere (10.–11. juni 2026)

## 7. Fortsatt usikkert
- **Startsannsynligheter** er modellestimat (pris/eierandel/«sikker starter»-liste), ikke offisielle laguttak. Sjekk laguttak 1–2 t før avspark.
- Styrkeratinger (lagets angreps-/forsvarsstyrke) er kalibrert skjønn, ikke hentet fra oddsmarkedet i sanntid.
- R3-rotasjon er en heuristikk for de 8 antatt sterkeste lagene.
