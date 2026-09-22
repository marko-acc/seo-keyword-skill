# Workflow: Klasyfikacja keyworda pod intencją

**Cel:** dla podanej frazy/tematu — zdecydować, jaki typ treści powinien ją adresować, z uzasadnieniem odwołującym się do konkretnych reguł.

**Triggery:** *„jaki typ treści zbudować pod X"*, *„sklasyfikuj intencję dla X"*, *„czy warto targetować X"*, *„sprawdź czy X i Y się nie kanibalizują"*.

## Krok 0 — Sprawdź profil marki

Sprawdź, czy `brand-profile.md` istnieje w katalogu głównym.

- **Jeśli tak** — odczytaj go i użyj przez całą analizę (oferta, grupa docelowa, terytorium core/forbidden/adjacent, istniejące treści).
- **Jeśli nie** — uruchom `workflows/konfiguracja-marki.md` **przed** kontynuowaniem (zbiera dane raz, w tym próbę automatycznego odczytu strony usera z URL, zapisuje do `brand-profile.md` na przyszłość — kolejne keywordy nie będą już wymagały tego pytania).

Bez tego kroku reguły R3/E2/R15/R16 (dopasowanie odbiorcy i marki) oraz ocena kanibalizacji są zgadywaniem, nie analizą. Jeśli mimo `konfiguracja-marki.md` user nie poda kompletu danych (np. brak listy istniejących treści) — kontynuuj, ale **wprost napisz w Podsumowaniu**, że to założenie/domysł w tym miejscu, zamiast cicho zgadywać i podawać to jako pewnik.

## Krok 1 — Zbierz dane (DataForSEO)

Wywołaj w tej kolejności:

1. `serp/google/organic/live/advanced` dla frazy głównej (location/language dopasowane do rynku, dla Polski: `location_code: 2616`, `language_code: pl`) → zapisz `item_types` (co dominuje: organic guides, featured_snippet, people_also_ask, shopping, ai_overview...) i treść top 10 (title+description).
2. `dataforseo_labs/google/related_keywords/live` (depth 1-2, `include_serp_info: true`) → lista fraz powiązanych z `search_intent_info.main_intent`, `foreign_intent`, `search_volume`, `keyword_difficulty`.
3. (opcjonalnie, jeśli porównujesz kilka wariantów frazy) `keywords_data/google_ads/search_volume/live` dla listy kandydatów.

**Jeśli DataForSEO MCP niedostępny:** poproś użytkownika o ręczne wklejenie top 10 SERP + People Also Ask. Jeśli i tego nie ma — kontynuuj, ale oznacz wynik `[BEZ DANYCH RYNKOWYCH]` (patrz SKILL.md).

## Krok 2 — Skan SERP (reguła R1, R5)

Przeczytaj tytuły/opisy top 10. Zapisz: ile pozycji to poradniki/definicje, ile to strony produktowe/ofertowe, ile to porównania/rankingi. To jest realny sygnał — ważniejszy niż sama etykieta `main_intent`.

## Krok 3 — Sprawdź etykietę vs. rzeczywistość (E1, `wyjatki-niuanse.md`)

Porównaj `main_intent` + `foreign_intent` z tym, co realnie widzisz w SERP (krok 2). Jeśli się zgadzają i SERP jest jednoznaczny → przejdź do kroku 4 z wysoką pewnością. Jeśli SERP jest mieszany lub `foreign_intent` niepusty → zanotuj to jako sygnał niepewności, kontynuuj analizę głębiej (nie zgaduj).

## Krok 4 — Klasteryzacja i kanibalizacja (R2, R8, R9)

Przejrzyj related keywords. Pogrupuj wg realnej intencji (nie tylko etykiety). Dla każdej grupy zadaj: czy to inny etap ścieżki klienta niż fraza główna (R9)? Jeśli tak — to sygnał do osobnej strony supporting, nie do wciskania w tę samą treść.

## Krok 5 — Ocena wartości biznesowej i terytorium marki (R3, R4, R15, R16, E2)

Nie odrzucaj automatycznie niskiego wolumenu (long tail, R4). Sklasyfikuj keyword względem `brand-profile.md` do strefy core/forbidden/adjacent (R15) **zanim** ocenisz wolumen — wolumen nie decyduje o strategii (R16). Odrzuć wysoki wolumen, jeśli profil szukającego nie pasuje do oferty — **na podstawie kontekstu z Kroku 0**, nie założenia. Jeśli kontekstu biznesowego nie znasz (user go nie podał), nie stawiaj tezy o "złej publiczności" ani o strefie terytorium jako pewnika — zaznacz to jako założenie wymagające potwierdzenia.

## Krok 6 — Decyzja o typie treści i architekturze (R11, R12, R13, E3, R17-R25)

Zdecyduj: pillar / supporting / strona produktowa / poradnik / porównanie / kalkulator. Jeśli related keywords pokazują ≥3 wyraźnie różne intencje z realnym wolumenem — rozważ strukturę pillar+supporting (patrz `przyklady.md`) zamiast jednej strony.

Jeśli decyzja to strona produktowa/kategoria — sprawdź `navboost-i-satysfakcja.md` R19: to nie wystarczy, że strona istnieje, musi być realną "odpowiedzią transakcyjną" (ceny/argumenty widoczne od razu, nie tylko lista produktów pod spodem). Jeśli rekomendujesz usunięcie lub przebudowę istniejącej treści zamiast tworzenia nowej — sprawdź R19/R20 (segmentowe kryteria: rankuje z wysokimi wyświetleniami, ale near-zero kliknięciami = przebuduj albo usuń, nie zostawiaj).

**Kanibalizacja — tylko na podstawie realnych danych z Kroku 0.** Jeśli masz URL/listę istniejących tematów usera: sprawdź wprost, czy któryś istniejący artykuł już pokrywa tę frazę lub blisko pokrewną — jeśli tak, rekomenduj rozszerzenie istniejącej strony, nie nową. Jeśli nie masz tych danych — nie pisz "brak ryzyka kanibalizacji" ani nie zgaduj ryzyka; napisz wprost, że tej oceny nie da się zrobić bez wglądu w istniejącą zawartość strony.

## Krok 6.5 — Sprawdź, czy istnieje wyraźnie lepsza alternatywa (obowiązkowe, nie opcjonalne)

Jeśli decyzja z Kroku 6 to "nie pisz na ten keyword" (albo "niski priorytet") — **zanim** to zapiszesz jako finalną rekomendację, przejrzyj dane z Kroku 1 (related keywords) pod kątem frazy o wyraźnie wyższym wolumenie i/lub wyraźnie niższej trudności, z podobną lub pokrewną intencją. To nie jest krok opcjonalny zależny od tego, czy "coś rzuci się w oczy" — zrób to za każdym razem, systematycznie, bo inaczej rekomendacja "nie pisz tego" bez wskazania co pisać zamiast tego jest niepełna. Jeśli taka fraza istnieje, staje się ona **główną częścią rekomendacji w Podsumowaniu**, nie dopiskiem na końcu w "Rozważ też".

**Zweryfikuj znalezioną alternatywę jednym dodatkowym sprawdzeniem SERP** (`serp/google/organic/live/advanced` dla tej alternatywnej frazy) — nie poprzestawaj na samej etykiecie `main_intent`/wolumenie/trudności z danych labs, tak jak to zrobiłeś dla frazy głównej w Kroku 1-2. To jest dokładnie ta różnica, która pokazała się przy realnym teście: alternatywa poparta żywym SERP jest wiarygodniejsza niż alternatywa oparta tylko na metrykach.

**Twardy limit — dokładnie jedno dodatkowe zapytanie SERP na tym etapie, nie więcej.** Nie szukaj rekurencyjnie "czy jest coś jeszcze lepszego niż ta alternatywa" ani nie weryfikuj kolejnych kandydatów w pętli — wybierz najlepszego kandydata z danych z Kroku 1 (najwyższy wolumen przy najniższej trudności i pasującej intencji), zweryfikuj **jego jednym** zapytaniem, i na tym zatrzymaj Krok 6.5, niezależnie od wyniku weryfikacji. Jeśli weryfikacja podważy tę alternatywę — zgłoś to wprost w Confidence/Podsumowaniu (np. "dane liczbowe wyglądały obiecująco, ale żywy SERP pokazuje X" — nie ukrywaj tego), zamiast szukać kolejnego kandydata.

## Krok 7 — Output

Zwróć wynik w formacie z `SKILL.md` (sekcja "Format wyjścia"). Jeśli reguły wskazują na dwa sensowne rozwiązania lub dane są niepełne — Confidence: Low/Medium i przedstaw alternatywę z warunkiem, kiedy ją wybrać (nigdy nie zgaduj jednoznacznie, gdy dane na to nie wskazują).

**Horyzont czasowy (R22):** jeśli rekomendacja dotyczy zmiany/przebudowy istniejącej strony (nie nowej treści), dodaj w Podsumowaniu realistyczne oczekiwanie co do czasu — wczesne sygnały po kwartale-dwóch, pełne osiadanie po ponad roku. Nie sugeruj oceny efektu w miesiąc.

## Powiązania

- `workflows/konfiguracja-marki.md` — Krok 0, jednorazowo
- `references/reguly-decyzyjne-slowik.md` — R1-R14
- `references/dopasowanie-marki.md` — R15-R16
- `references/navboost-i-satysfakcja.md` — R17-R25
- `references/taksonomia-intencji.md` — typy intencji
- `references/wyjatki-niuanse.md` — E1-E4
- `references/przyklady.md` — worked example
