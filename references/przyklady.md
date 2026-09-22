# Worked example — struktura pillar + supporting

Wzorowany na przykładzie z materiału źródłowego (temat "umowa zlecenia", źródło 4 w `reguly-decyzyjne-slowik.md`), przeniesiony na generyczny szablon.

## Sytuacja

Fraza główna: szeroki temat z wysokim wolumenem, np. **"[temat główny]"**. Query network (related keywords) pokazuje dziesiątki powiązanych fraz reprezentujących różne, konkretne pod-potrzeby.

## Obserwacja

- SERP dla frazy głównej: mieszane sygnały — częściowo poradniki ogólne, częściowo linki do konkretnych pod-tematów.
- Related keywords zawierają frazy z wyraźnie różnymi `main_intent`: część informacyjna ("co to jest X", "jak działa X"), część transakcyjna/narzędziowa ("kalkulator X", "wzór X"), część porównawcza ("X czy Y").

## Decyzja (wg R13)

1. **Strona pillar** — adresuje temat główny ogólnie, dotyka każdej istotnej kwestii jednym-dwoma akapitami, linkuje do stron supporting.
2. **Strony supporting** — osobne, szczegółowe artykuły na każdą wyraźną pod-intencję:
   - Artykuł wyjaśniający (informacyjna)
   - Wzór/szablon do pobrania (transakcyjna/narzędziowa)
   - Kalkulator/narzędzie interaktywne (transakcyjna)
   - Porównanie wariantów (komercyjna)

## Kryterium podziału (kiedy NIE robić jednej strony)

Jeśli related keywords pokazują ≥3 wyraźnie różne `main_intent` z realnym wolumenem każda → **nie kompresuj do jednej strony** (E3). Jedna strona próbująca odpowiedzieć na informacyjną, transakcyjną i porównawczą intencję naraz zwykle słabo satysfakcjonuje każdą z nich (R6, R11).

## Kryterium NIE dzielenia (kiedy jedna strona wystarczy)

Jeśli related keywords to głównie warianty tej samej intencji (synonimy, drobne różnice frazowania) — R2 (klasteryzacja) mówi: buduj JEDEN klaster/jedną stronę pokrywającą wszystkie te warianty, nie mnóż stron sztucznie.
