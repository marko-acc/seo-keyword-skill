# Taksonomia intencji wyszukiwania

Zgodna ze schematem, który zwraca DataForSEO (`search_intent_info.main_intent` / `foreign_intent`) — żeby dane z narzędzia i reguły skilla mówiły tym samym językiem.

| Typ | Co użytkownik naprawdę chce | Sygnały w SERP |
|---|---|---|
| **Informational** (informacyjna) | Odpowiedzi, wyjaśnienia, "jak to zrobić" | Dominują poradniki, definicje, featured snippet, people_also_ask |
| **Navigational** (nawigacyjna) | Konkretną stronę/markę, którą już znają | Dominuje 1 domena, brand name w zapytaniu |
| **Commercial** (komercyjna/porównawcza) | Porównanie opcji przed decyzją | Rankingi, "najlepsze X", recenzje, porównania |
| **Transactional** (transakcyjna) | Konkretną akcję — zakup, zapis, kontakt | Strony produktowe, koszyk, karty ofertowe, shopping units |

## Jak z tego korzystać w praktyce

1. `main_intent` z DataForSEO to **punkt startowy**, nie finalna decyzja (patrz `wyjatki-niuanse.md`, E1).
2. Sprawdź `foreign_intent` (array) — jeśli niepusty, SERP pokazuje sygnały **więcej niż jednego typu** — to jest właśnie sytuacja "mieszana" z reguły R14.
3. Skan realnego SERP (`item_types` z `serp/google/organic/live/advanced`) mówi więcej niż etykieta: obecność `people_also_ask` + `featured_snippet` + brak `shopping` → mocny sygnał informacyjny nawet jeśli etykieta mówi "commercial".
4. Jedna fraza może wyglądać podobnie na papierze i prowadzić do zupełnie innej potrzeby (R1/źródło 1) — etykieta nigdy nie zastępuje przeczytania realnych top 10 wyników.
