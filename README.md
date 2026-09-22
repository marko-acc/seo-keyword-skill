# SEO — Keyword & Intent Skill (eksperyment)

Skill testowy dla Claude Code / Claude Desktop, budujący decyzję "jaki typ treści zbudować pod dany keyword" na bazie niezależnej analizy publicznie dostępnych materiałów Szymona Słowika (konsultanta SEO, szymonslowik.com).

## Status: eksperyment

To jest test hipotezy: czy skill zbudowany na bazie rzetelnie wyekstrahowanej metodologii pracy realnego specjalisty daje wyraźnie lepsze rezultaty niż standardowe AI i niż inne, generyczne skille SEO dostępne na marketplace'ach. Nie jest to gotowy, komercyjny produkt.

## Ważne — nieautoryzowane

Ten skill **nie został stworzony, zweryfikowany ani autoryzowany** przez Szymona Słowika. To niezależna interpretacja publicznych materiałów (linki w `references/reguly-decyzyjne-slowik.md`), może zawierać błędy. Zobacz pełny disclaimer w `SKILL.md`.

## Wymagania

- DataForSEO MCP podłączony do Twojego klienta AI (konto + credentials: [app.dataforseo.com/api-access](https://app.dataforseo.com/api-access)). Bez tego skill działa, ale ostrzega, że analiza jest mniej wiarygodna — patrz sekcja "Integracja z DataForSEO" w `SKILL.md`.

## Struktura

```
SKILL.md                                  — start tutaj (orkiestracja, o Szymonie Słowiku, format wyjścia)
brand-profile.md                          — Twój profil marki, generowany przy pierwszym użyciu (nie w repo)
references/
  reguly-decyzyjne-slowik.md              — R1-R14, reguły decyzyjne z linkami do źródeł
  dopasowanie-marki.md                    — R15-R16, framework BUXS (core/forbidden/adjacent)
  navboost-i-satysfakcja.md               — R17-R25, reguły segmentowe + horyzont czasowy
  taksonomia-intencji.md                  — 4 typy intencji wyszukiwania
  wyjatki-niuanse.md                      — E1-E4, wyjątki do sprawdzić przed finalną decyzją
  przyklady.md                            — worked example (pillar + supporting)
workflows/
  konfiguracja-marki.md                   — jednorazowo: zbiera i zapisuje brand-profile.md
  klasyfikacja-keyworda.md                — główny workflow: dane → analiza → decyzja → output
examples/
  pilot-wyniki.md                         — wyniki testu porównawczego vs. standardowe AI i inne skille
```

## Licencja

MIT — dotyczy struktury i sformułowań tego skilla. Nie oznacza to zgody osoby, na której publicznych materiałach oparto ekstrakcję reguł — zob. disclaimer w `SKILL.md`.
