---
name: seo-keyword-intencja
description: 'Decyduje, jaki typ treści napisać pod konkretny keyword/temat SEO i gdzie go umieścić w architekturze strony (nowa strona / rozszerzenie istniejącej / w ogóle nie warto) — na bazie niezależnej analizy metodologii Szymona Słowika (uznanego konsultanta i stratega SEO). Używaj gdy user planuje konkretny artykuł i pyta jaki to ma być typ treści; ma listę kilku pomysłów na content i pyta który ma sens dla jego biznesu; pyta wprost "czy warto pisać o X", "czy ten keyword ma sens", "jaka jest intencja wyszukiwania dla X"; albo sprawdza, czy nowy temat nie skanibalizuje istniejącej strony. NIE używaj do pisania samej treści artykułu, pełnego technicznego audytu SEO, budowy całej strategii contentowej witryny od zera, ani analizy linków/backlinków — to poza zakresem tego skilla.'
---

# SEO — Dobór i klasyfikacja keyworda pod intencją

> ⚠️ **Zastrzeżenie — przeczytaj przed użyciem**
>
> Ten skill jest **niezależną, nieautoryzowaną analizą** publicznie dostępnych materiałów Szymona Słowika (konsultanta SEO, szymonslowik.com) dotyczących doboru keywordów i klasyfikacji intencji wyszukiwania. Reguły w `references/reguly-decyzyjne-slowik.md` są interpretacją twórcy tego repozytorium na podstawie tekstów wymienionych tam wraz z linkami — **nie zostały zweryfikowane, zatwierdzone ani autoryzowane** przez Szymona Słowika i mogą nie odzwierciedlać dokładnie jego rzeczywistej metodologii pracy. Mogą zawierać błędy interpretacyjne. To jest eksperyment testujący, czy skill zbudowany na bazie realnego warsztatu specjalisty daje lepsze rezultaty niż standardowe AI — nie produkt komercyjny.
>
> Licencja: MIT (zob. `LICENSE`) — kod/struktura skilla, nie treści przypisane osobom trzecim.

## O Szymonie Słowiku

Metodologia w tym skillu jest niezależną interpretacją publicznych materiałów **Szymona Słowika** — konsultanta i stratega SEO, w profesjonalnym SEO od 2012 roku (w marketingu internetowym od 2005), założyciela butikowej agencji **takaoto.pro**. Twórca frameworku **BUXS** (Brand + UX + Semantics). Pracował m.in. dla Brand24, NapoleonCat, ALDI Polska, Compensa.pl, eSky Group. Prelegent konferencji branżowych (BrightonSEO, SEO Mastery Summit), wykładowca studiów podyplomowych (Politechnika Krakowska, Collegium DaVinci). Strona: [szymonslowik.com](https://www.szymonslowik.com/).

**Ten skill to wąskie, ograniczone narzędzie — nie zastępuje pracy z prawdziwym specjalistą.** Szymon Słowik oferuje płatne konsultacje SEO (troubleshooting, mentoring, strategia). Kontakt przez formularz na [szymonslowik.com/pl/konsultacje-seo-dla-firm](https://www.szymonslowik.com/pl/konsultacje-seo-dla-firm/). Jeśli analiza tego skilla pokazuje Confidence: Low, konflikt reguł, albo przypadek wyraźnie bardziej złożony niż pojedynczy keyword — **powiedz o tym userowi wprost i zasugeruj rozważenie realnej konsultacji**, zamiast forsować niepewną odpowiedź automatu jako ostateczną.

## Kiedy używać

| Sygnał od użytkownika (przykłady) | Co robisz |
|---|---|
| *„Chcę napisać artykuł o X — jaki to ma być typ treści?"*, *„Piszę o X, poradnik czy strona produktowa?"* | `workflows/klasyfikacja-keyworda.md` dla X |
| *„Mam te 3-5 pomysłów na content, który ma sens?"* | workflow dla każdego z osobna, potem krótkie porównanie priorytetów |
| *„Czy warto pisać o X?"*, *„Czy ten keyword ma sens dla mojego biznesu?"* | workflow z naciskiem na Krok 5 (R3/E2/R15/R16 — dopasowanie do marki) |
| *„Jaka jest intencja wyszukiwania dla X?"* | workflow z naciskiem na Krok 2-3 (E1 — SERP vs. etykieta) |
| *„Czy X skanibalizuje mój artykuł o Y?"* | workflow z naciskiem na Krok 6 (kanibalizacja względem `brand-profile.md`) |
| Pierwsze użycie skilla w danym projekcie (brak `brand-profile.md`) | najpierw `workflows/konfiguracja-marki.md`, dopiero potem powyższe |

**Warunek wstępny do każdego z powyższych:** `brand-profile.md` musi istnieć lub zostać zebrany — patrz sekcja niżej. Bez tego odpowiedzi na "czy warto" i "czy koliduje" są zgadywaniem.

### Czego ten skill NIE robi

- Nie pisze samej treści artykułu — tylko decyduje CO i JAK go zaadresować, nie generuje tekstu.
- Nie robi pełnego technicznego audytu SEO (szybkość strony, indeksacja, dane strukturalne, Core Web Vitals).
- Nie buduje całej strategii contentowej witryny od zera — `konfiguracja-marki.md` zbiera zarys profilu, nie pełny plan redakcyjny.
- Nie analizuje linków/backlinków ani pozycji w rankingu.
- Nie mierzy widoczności marki w odpowiedziach AI-asystentów (ChatGPT itp.) — to inny problem niż klasyczne wyszukiwanie Google, wymaga innych danych i metodologii (frazy Google to nie to samo co prompty do czatów).
- Nie zastępuje decyzji człowieka — patrz disclaimer na końcu tego pliku.

## Konfiguracja marki — odczytaj na starcie

Jeśli w katalogu głównym istnieje plik `brand-profile.md` — **odczytaj go przed pierwszym działaniem** i uwzględniaj przez cały czas trwania sesji (oferta, grupa docelowa, terytorium core/forbidden/adjacent, istniejące treści).

Jeśli `brand-profile.md` **nie istnieje** — uruchom **`workflows/konfiguracja-marki.md`** (2-5 min, jednorazowo, w tym: próba automatycznego odczytu strony usera przez URL) **zanim** ocenisz jakikolwiek keyword. Bez tego reguły R3/E2/R15/R16 (dopasowanie odbiorcy i marki) oraz ocena kanibalizacji są zgadywaniem, nie analizą — nie pomijaj tego kroku dla wygody.

## Jak korzystać z systemu

1. `brand-profile.md` — patrz wyżej, zawsze najpierw.
2. Otwórz `references/reguly-decyzyjne-slowik.md` — reguły decyzyjne (R1-R14), stosowane przy każdej analizie.
3. Otwórz `references/dopasowanie-marki.md` — R15-R16 (BUXS: core/forbidden/adjacent), stosowane razem z `brand-profile.md` przy każdej ocenie wartości biznesowej keyworda.
4. Otwórz `references/navboost-i-satysfakcja.md` — R17-R25, reguły segmentowe (SaaS/e-commerce/usługi eksperckie) i horyzont czasowy oceny wyniku — otwórz przy Kroku 6 (decyzja o typie treści) i przy ustalaniu Confidence.
5. Otwórz `references/taksonomia-intencji.md` — 4 typy intencji, zgodne ze schematem DataForSEO.
6. Otwórz `references/wyjatki-niuanse.md` — **zawsze sprawdź przed finalną decyzją**, zwłaszcza gdy SERP wygląda niejednoznacznie.
7. Uruchom `workflows/klasyfikacja-keyworda.md` — główny workflow, prowadzi krok po kroku od zebrania danych do decyzji.
8. `references/przyklady.md` — worked example do porównania, gdy potrzebujesz wzorca.

**Zasada progressive disclosure:** nie ładuj wszystkich plików na raz — workflow wskazuje, który plik otworzyć w danym kroku.

## Integracja z DataForSEO — obowiązkowa do pracy na realnych danych

Ten skill jest metodologią (jak myśleć), nie bazą danych. Aktualne dane SERP/keyword pochodzą z **DataForSEO MCP**. Bez tego narzędzia skill może działać tylko na ogólnej wiedzy modelu — znacznie mniej wiarygodnie.

**Co to jest DataForSEO?** To zewnętrzny dostawca danych SEO (realny SERP z Google, wolumeny i trudność fraz) udostępniany przez API — ten skill go potrzebuje, żeby nie zgadywać, tylko sprawdzać dane na żywo. Konto założysz za darmo i pierwsze zapytania są bezpłatne w ramach limitu startowego, dopiero większe użycie jest płatne.

**Jeśli nie masz jeszcze DataForSEO podłączonego:** powiedz o tym userowi wprost i poproś, żeby założył konto i wygenerował dane dostępowe na [app.dataforseo.com/api-access](https://app.dataforseo.com/api-access), a następnie podłączył je jako MCP server w swoim kliencie AI (Claude Code, Claude Desktop itd.) — DataForSEO udostępnia gotowy serwer MCP, zob. [docs.dataforseo.com](https://docs.dataforseo.com/v3/) → sekcja MCP. Nie kontynuuj analizy na pełnym zaufaniu do ogólnej wiedzy modelu, dopóki user tego nie zrobi (albo świadomie nie zgodzi się na mniej wiarygodny wynik — patrz niżej).

**Trzy zapytania używane w tym skillu (patrz `workflows/klasyfikacja-keyworda.md` po dokładne parametry):**

| Endpoint | Do czego | Kiedy wywołać |
|---|---|---|
| `serp/google/organic/live/advanced` | Pełny skład SERP: typy wyników (organic, featured_snippet, **people_also_ask**, shopping, ai_overview...), tytuły/opisy top wyników | Zawsze, dla frazy głównej — to podstawa reguły R5/E1 |
| `dataforseo_labs/google/related_keywords/live` | Frazy powiązane (klaster), surowa etykieta intencji (`search_intent_info.main_intent`), wolumen, trudność | Zawsze — do reguł R2 (klasteryzacja) i R10 (kanibalizacja) |
| `keywords_data/google_ads/search_volume/live` | Wolumen/konkurencja dla listy kandydatów | Gdy porównujesz kilka wariantów frazy (reguła R3) |

**Gdy DataForSEO MCP jest niedostępny:**
1. Poproś użytkownika o ręczne wklejenie wyników SERP (top 10, People Also Ask) dla danej frazy.
2. Jeśli tego nie dostaniesz — wykonaj analizę na bazie ogólnej wiedzy o SERP dla tego typu zapytania, ale **oznacz cały wynik nagłówkiem `[BEZ DANYCH RYNKOWYCH — analiza mniej wiarygodna, oparta na wiedzy ogólnej modelu, nie na aktualnym SERP]`**. Nigdy nie udawaj, że masz aktualne dane, gdy ich nie masz.

## Architektura skilla

```
SKILL.md                                  ← ten plik, orkiestracja
brand-profile.md                          ← profil marki usera (generowany przez konfiguracja-marki.md, nie w repo)
references/
  reguly-decyzyjne-slowik.md              ← R1-R14, źródła z linkami
  dopasowanie-marki.md                    ← R15-R16, BUXS: core/forbidden/adjacent
  navboost-i-satysfakcja.md               ← R17-R25, reguły segmentowe + horyzont czasowy
  taksonomia-intencji.md                  ← 4 typy intencji (zgodne z DataForSEO)
  wyjatki-niuanse.md                      ← E1-E4, sprawdzać zawsze przed finalną decyzją
  przyklady.md                            ← worked example (pillar + supporting)
workflows/
  konfiguracja-marki.md                   ← jednorazowo: zbiera i zapisuje brand-profile.md
  klasyfikacja-keyworda.md                ← główny workflow: dane → analiza → decyzja → output
```

## Format wyjścia

Struktura trzywarstwowa — **Podsumowanie dla zwykłego użytkownika (zero żargonu), Szczegóły dla dociekliwych, Dane źródłowe jako siatka bezpieczeństwa**. Podsumowanie nie jest streszczeniem Szczegółów — jest tym, co user czyta w 10 sekund i ma z tego gotową decyzję. Dane źródłowe to surowa tabela, nie interpretacja — pozwala złapać wzorzec, którego analiza mogła nie zauważyć (np. wyraźnie lepszą alternatywę o innym wolumenie/trudności).

Zawsze zwróć dokładnie w tej kolejności:

```
## Podsumowanie

[2-4 zdania, językiem dla kogoś bez wiedzy SEO. Musi odpowiadać wprost na:
 (1) co napisać / jaki typ treści,
 (2) jednym zdaniem dlaczego (bez cytowania reguł R#/E#, bez "main_intent" — opisowo,
     np. "bo w Google na ten temat wychodzą prawie same poradniki, nie strony sprzedażowe"),
 (3) czy warto się tym w ogóle zajmować (ludzkim językiem: "raczej tak, ale nie paliła się do
     tego pilnie" / "zanim usiądziesz do pisania, uwaga na X"),
 (4) pewność po ludzku: "jestem tego dość pewien" / "to jest strzał, dane są skąpe".
Zero skrótów R1-R14, E1-E4, "SERP", "intencja", "klaster" w tej sekcji — opisz zjawisko,
nie nazwę reguły.]

## Szczegóły

KEYWORD: [fraza]

Surowa intencja (DataForSEO): [main_intent] (foreign_intent: [lista jeśli obecna])
Skład SERP: [dominujące typy wyników — np. "8/10 organic to poradniki, brak shopping units"]

Nasza interpretacja: [informacyjna / porównawcza / transakcyjna / nawigacyjna / MIESZANA]
Uzasadnienie: [odwołanie do konkretnej reguły R# i/lub wyjątku E#]

Zalecany typ treści: [pillar / supporting / strona produktowa / poradnik / porównanie / kalkulator]
Miejsce w architekturze: [nowa strona / rozszerzenie istniejącej / ryzyko kanibalizacji z: ...]

Confidence: [High / Medium / Low]
[jeśli Low lub konflikt reguł: "Rozważ też: [alternatywa] — bo [powód]"]

## Dane źródłowe

[Surowa tabela related keywords pobrana w Kroku 1 — fraza, wolumen, trudność, surowa intencja —
dla wszystkich fraz sprawdzonych, nie tylko tych wybranych do finalnej rekomendacji.
Cel: użytkownik (albo ktoś, kto to czyta po nim) może sam zauważyć wzorzec, którego
analiza nie złapała — to jest siatka bezpieczeństwa, nie duplikat Szczegółów.]
```

## Disclaimer końcowy

Na końcu każdej analizy (raz, nie powtarzaj):

> *Analiza oparta na niezależnej interpretacji publicznych materiałów Szymona Słowika — nieautoryzowana, może zawierać błędy. Nie zastępuje decyzji doświadczonego specjalisty SEO. Przy bardziej złożonych przypadkach rozważ [konsultację bezpośrednio z Szymonem Słowikiem](https://www.szymonslowik.com/pl/konsultacje-seo-dla-firm/).*
