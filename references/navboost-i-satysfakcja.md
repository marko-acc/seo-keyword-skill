# NavBoost i satysfakcja użytkownika — pogłębienie R6

> Materiał celowo wyszukany pod kątem treści **nietypowej, technicznej i sprzecznej z powszechnymi przekonaniami** (nie kolejnych ogólnych poradników) — w odpowiedzi na obserwację, że pierwsza runda ekstrakcji (`reguly-decyzyjne-slowik.md`, R1-R16) skupiła się głównie na dobrze wyjaśnionej, ogólnej dobrej praktyce, którą inteligentny model z dostępem do danych odtwarza samodzielnie. To jest próba dojścia do wiedzy trudniejszej do samodzielnego odtworzenia.

## Źródła

1. [NavBoost: why rankings slide when visitors bounce](https://www.szymonslowik.com/navboost/) — z żywym case study (grupa ubezpieczeniowa, rynek PL)
2. [Audyt treści — analiza contentu, która robi różnicę w SEO](https://www.szymonslowik.com/pl/audyt-contentowy-seo/)
3. [Jak pozycjonować się w AI Overviews oraz AI mode](https://www.szymonslowik.com/pl/jak-pozycjonowac-sie-w-ai-overviews-oraz-ai-mode/)

## R17 — Ranking to hipoteza, którą testują Twoi odwiedzający

Google (potwierdzone pod przysięgą przez VP Search w procesie antymonopolowym, październik 2023) re-rankuje wyniki na bazie kliknięć zbieranych w kroczącym oknie 13 miesięcy, dzielonych wg kraju/urządzenia/języka — rozróżniając kliknięcia kończące wyszukiwanie (goodClicks) od odbić z powrotem do wyników (badClicks). **Pozycja, pod którą narasta złe zaangażowanie, "wygasa" niezależnie od tego, jak stabilnie wygląda dziś** — korekta przychodzi zwykle cicho, czasem widocznie przy core update.

## R18 — Nie czas na stronie, tylko czy wyszukiwanie się kończy

Popularna rada "zwiększ czas spędzony na stronie" celuje w **niewłaściwą zmienną**. Udokumentowanym sygnałem jest `lastLongestClicks` — wynik, który *ostatecznie zaspokoił* szukającego — nie dwell time. To jest wprost kontra wobec powszechnej praktyki SEO.

## R19 — Reguły segmentowe (bezpośrednio do Kroku 6 workflow)

- **SaaS/B2B:** jeśli treść z góry lejka rankuje blisko fraz transakcyjnych z wysokimi wyświetleniami, ale niemal zerowymi kliknięciami na pozycji 5-10 → **przebuduj stronę pod realną potrzebę szukającego, albo usuń ją**. Nie zostawiaj martwej treści tylko dlatego, że rankuje.
- **E-commerce:** stabilna pozycja strony kategorii przy malejącym udziale w kliknięciach = użytkownicy odbijają się porównywać gdzie indziej. Rozwiązanie: **zrób ze strony kategorii "odpowiedź transakcyjną"** — widełki cenowe i argumenty decyzyjne **nad** siatką produktów, nie pod nią.
- **Usługi eksperckie:** top-5 na frazy cenowe, ale płaskie liczby leadów → brakuje konkretnej odpowiedzi → **opublikuj wprost stawki, harmonogram, co się dzieje na każdym etapie współpracy.**

## R20 — Kolejność audytu przed wydatkiem

"Sprawdź, czy Twoje rankujące strony kończą wyszukiwanie, czy je restartują, **zanim wydasz cokolwiek na cokolwiek innego**" — link budowanie, nowa treść, redesign. Pozycja z problemem zaangażowania pod spodem już wygasa, niezależnie od tego, co się na nią dołoży.

## R21 — Nie inwestuj w linki pod strony z problemem zaangażowania (kontrariańskie)

"To samo zachowanie, które podkopuje pozycję, podkopuje też nowe linki." Odwraca to typową priorytetyzację link buildingu — najpierw napraw satysfakcję, potem buduj autorytet, nie odwrotnie.

## R22 — Horyzont czasowy oceny (nowy wymiar Confidence)

Pełne osiadanie sygnału trwa **ponad rok** (rolling window 13 miesięcy), wczesne sygnały widać po **kwartale-dwóch**. Nie oceniaj sukcesu/porażki zmiany treści w miesiąc — pozycje "nie skaczą, tylko się stabilizują", zaczynając od przestania się osuwać przy kolejnych aktualizacjach.

## R23 — Spadek widoczności mimo aktywności contentowej to czerwona flaga

Kwestionuje założenie "więcej treści = lepiej". Jeśli widoczność spada mimo regularnych publikacji, to sygnał diagnostyczny, nie neutralny fakt do zignorowania.

## R24 — Centroid semantyczny jako filtr dryfu tematycznego

Treść oddalająca się od "centroidu semantycznego" głównej encji strony niesie ryzyko rozmycia autorytetu — **niezależnie od tego, czy ma dobry wolumen wyszukiwań**. To rozszerza R15 (terytorium core/forbidden/adjacent) o bardziej techniczne kryterium: nie tylko "czy to pasuje tematycznie", ale "jak daleko to jest od semantycznego centrum tego, czym się już jesteś rozpoznawany".

## R25 — Nawet strony transakcyjne zyskują na warstwie How-To/FAQ (kontrariańskie wobec E1)

Nawet dla biznesów lokalnych/usługowych o wyraźnie transakcyjnej intencji, dodanie ustrukturyzowanej treści How-To/FAQ zwiększa widoczność w AI Overviews. **To nie znaczy "buduj poradnik zamiast strony transakcyjnej"** (E1 nadal obowiązuje jako główna decyzja o formacie) — to znaczy: **warstwuj krótkie, ustrukturyzowane FAQ/How-To NA stronie transakcyjnej**, jako dodatek pod AI-widoczność, nie zamiennik głównego formatu.

## Jak z tego korzystać w workflow

- Krok 6 (decyzja o typie treści): przy typie "strona produktowa/kategoria" sprawdź R19 — czy to jest rzeczywiście "odpowiedź transakcyjna" (ceny/argumenty widoczne od razu), czy tylko lista produktów.
- Krok 7 (output, pole Confidence): dodaj realistyczny horyzont czasowy oceny wyniku (R22) — nie sugeruj oceny efektu w miesiąc.
- Przy każdej rekomendacji "usuń istniejącą treść" lub "zostaw jak jest" — sprawdź R19/R20 zamiast zgadywać.
