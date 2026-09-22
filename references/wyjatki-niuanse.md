# Wyjątki i niuanse — sprawdź zawsze przed finalną decyzją

## E1 — Nie ufaj sztywno jednej etykiecie intencji

Intencja komercyjna/informacyjna to nie formalny element algorytmu Google — to uproszczenie (R14). Dotyczy to również etykiety `main_intent` zwracanej automatycznie przez DataForSEO: to dobry punkt startowy, nie wyrok.

**Zawsze skrzyżuj:**
- `main_intent` (raw label) ×
- `foreign_intent` (czy są sygnały więcej niż jednego typu) ×
- realny skład SERP (`item_types` z zapytania advanced) — jakie typy wyników RZECZYWIŚCIE tam są.

**Sygnał do zatrzymania się i pogłębienia analizy:** SERP pokazuje wyniki mieszane (np. część poradników, część stron produktowych) → nie wybieraj jednego typu treści automatycznie. Zapytaj: "czego użytkownik naprawdę szuka na TYM etapie", nie tylko jaką etykietę dostał keyword.

## E2 — Wysoki wolumen nie oznacza wysokiej wartości

Fraza może mieć duży wolumen wyszukiwań i jednocześnie przyciągać osoby, które nigdy nie zostaną klientem (R3). Przed rekomendacją "targetuj tę frazę" sprawdź, czy profil szukającego pasuje do oferty/marki, nie tylko czy fraza ma ruch.

## E3 — Nie kompresuj różnych etapów ścieżki klienta do jednej strony

Jeśli sieć zapytań (query network) pokazuje, że jedna "podobna" fraza w rzeczywistości reprezentuje inny etap ścieżki klienta niż fraza główna (R9) — nie próbuj adresować obu na jednej stronie tylko dla wygody. Lepiej rekomendować osobną stronę (supporting) niż nadmiernie rozciągniętą, jedną stronę próbującą odpowiedzieć na wszystko.

## E4 — Nie ściągaj się na frazy z nazwą marki konkurenta

Jeśli fraza/klaster zawiera nazwę konkretnej firmy/marki (np. "semcore", "webwave"), a nie generyczny opis usługi — nie rekomenduj jej jako celu contentowego. Strona nie wyprzedzi marki w wynikach na jej własną nazwę, niezależnie od jakości treści. Sprawdź to przy filtrowaniu related keywords, zanim przejdziesz do klasteryzacji (R2) — nazwy marek konkurencji odrzuć na starcie, nie licz ich do wolumenu klastra.

*(Dodane 21.09 po rozszerzonym pilocie — zaobserwowane jako jawna reguła w komparatorze "Search Intent Classifier", którego nasz skill wcześniej nie miał explicite.)*

## Kiedy zgłosić niską pewność (Confidence: Low)

- SERP pokazuje wyraźnie mieszane sygnały bez dominującego typu.
- Brak wystarczających danych rynkowych (DataForSEO niedostępny, user nie dostarczył SERP ręcznie).
- Reguły z `reguly-decyzyjne-slowik.md` wskazują na dwa różne, sensowne rozwiązania — w takim przypadku przedstaw obie opcje z warunkami, kiedy która ma sens, zamiast zgadywać jedną (zgodnie z filozofią z `AI + EXPERT ESCALATION.md` — lepiej przyznać niepewność niż udawać jednoznaczność).
