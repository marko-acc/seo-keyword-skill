# Pilot — wyniki testu porównawczego (21.09.2026)

Metodologia: 10 keywordów, dane realne z DataForSEO (SERP advanced + related keywords), 5 wariantów porównanych per keyword: **standardowe AI** (bez skilla), **nasz skill** (metodologia Słowika), i 4 darmowe komparatory: **aaron-he-zhu/keyword-research**, **seo-cluster** (AgriciDaniel/claude-seo), **Search Intent Classifier** (SkillMedev/skills), **robertbstillwell/keyword-research**.

Zastrzeżenie metodologiczne: to symulacja logiki 4 komparatorów na bazie ich rzeczywistych, opublikowanych instrukcji (SKILL.md przeczytane w całości), nie uruchomienie ich jako zainstalowanych artefaktów. Ocena robiona przez twórcę naszego skilla — nie ślepa, nie niezależny sędzia (ograniczenie odziedziczone po metodologii z `commercial-legal-pl`, tam sędzia był niezależnym LLM z manifestem; tu nie było na to zasobu w pilocie).

**Luka w metodologii, znaleziona po pilocie:** oryginalne 10 keywordów nie mierzyło czytelności/użyteczności outputu jako osobnego kryterium — tylko trafność merytoryczną. Dopiero przy dodatkowym, żywym teście na realnej stronie firmowej okazało się, że żaden z 4 komparatorów nie ma warstwy podsumowania czytelnej dla osoby spoza branży — wszystkie zwracają surowe tabele/JSON wymagające dalszej interpretacji. To realna, ale **łatwa do skopiowania** przewaga (product design, nie ekstrahowana metodologia) — w przeciwieństwie do E2, które wymaga realnej pracy researchowej. Nie należy tych dwóch mylić przy ocenie, jak trwała jest nasza przewaga.

---

## 1. umowa zlecenia wzór

**Dane:** SERP zdominowany przez strony "wzór + omówienie" (hybrydowe). Related keywords: 3 klastry — kalkulator wynagrodzeń (368k wolumenu, ale to osobny, dużo szerszy temat), wypowiedzenie umowy zlecenia (inny etap ścieżki klienta), wzór PDF/Word (rdzeń intencji).

| Wariant | Odpowiedź |
|---|---|
| Standardowe AI | Może wciągnąć "kalkulator wynagrodzeń" do tego samego planu ze względu na ogromny wolumen, bez pytania czy to naprawdę ten sam temat |
| **Nasz skill** | Pillar "umowa zlecenia wzór" + osobne strony: wypowiedzenie (R9, inny etap), wzór PDF/Word. "Kalkulator wynagrodzeń" wykluczony z klastra — zbyt generyczny, osobny temat (R9) |
| aaron-he-zhu | Formuła Opportunity dla "kalkulator wynagrodzeń": 368000×1/44 ≈ 8360 (informational=waga 1) — bardzo wysoki priorytet, prawdopodobnie wciągnięty do planu bez weryfikacji tematycznej |
| seo-cluster | SERP-overlap między "umowa zlecenia wzór" a "kalkulator wynagrodzeń" prawdopodobnie niski (różne SERP-y) → poprawnie rozdzieli, podobny wniosek do naszego |
| Search Intent Classifier | SERP hybrydowy (wzór+omówienie) → etykieta "hybrid", strona informuje-potem-konwertuje — zgodne z naszym wnioskiem |
| robertbstillwell | KOB Score dla "kalkulator wynagrodzeń" byłby ekstremalnie wysoki (duży wolumen × waga intencji) — podobne ryzyko jak aaron-he-zhu, formuła nie weryfikuje tematycznego dopasowania |

**Werdykt:** Remis z seo-cluster i Search Intent Classifier. Wygrana z obiema formułami (aaron-he-zhu, robertbstillwell) na R9/klasteryzacji.

---

## 2. ile kosztuje strona internetowa

**Dane:** `main_intent: commercial`, `foreign_intent: informational`. SERP: AI Overview z cennikiem wg typu wykonawcy + strony agencji z cennikami. Related keywords: 4 klastry — warianty kosztowe (ten sam rdzeń), sklep internetowy (odrębny temat), tanie strony (segment cenowy), **darmowa/DIY** (Canva, kreatory — wolumen 1300).

| Wariant | Odpowiedź |
|---|---|
| Standardowe AI | Prawdopodobnie poleci też "za darmo/DIY" jako cel ze względu na wolumen, bez osądu o dopasowaniu odbiorcy |
| **Nasz skill** | Pillar + osobna strona "sklep internetowy" (R9). **Jawne wykluczenie klastra DIY z uzasadnieniem** — zła publiczność dla biznesu usługowego (E2) |
| aaron-he-zhu | Formuła: "za darmo" informational (waga 1)×1300/26 ≈ 50 vs główny commercial (waga 2)×1000/7 ≈ 286 — przypadkiem stawia DIY niżej, ale **nie wie dlaczego**, tylko liczy wagę intencji |
| seo-cluster | Rozdzieli klastry strukturalnie (różny SERP) — ale nie ma warstwy "czy warto to w ogóle celować dla tego biznesu" |
| Search Intent Classifier | Sklasyfikuje "za darmo" jako informational/transactional z SERP (kreatory, Canva) — poprawna etykieta, ale **brak reguły o dopasowaniu do modelu biznesowego klienta** |
| robertbstillwell | KOB Score dla "za darmo": Business Value=1 (awareness) × niski CTR/Difficulty — może wypaść nisko, ale to przypadek wagi kategorii, nie świadomy osąd o odbiorcy |

**Werdykt:** Wygrana — jedyny wariant z jawnym uzasadnieniem "zła publiczność", nie tylko niższym wynikiem liczbowym.

---

## 3. jak pisać artykuły seo (kontrolna)

**Dane:** SERP czysto informacyjny (poradniki). PAA zawiera drobną gałąź komercyjną ("ile kosztuje tekst SEO"). Brak danych wolumenowych w DataForSEO dla tej frazy.

| Wariant | Odpowiedź |
|---|---|
| Standardowe AI | Poradnik — rozsądnie |
| **Nasz skill** | Poradnik + PAA "ile kosztuje tekst SEO" jako drobna gałąź/FAQ, nie przebudowa całej strony |
| aaron-he-zhu | Brak wolumenu → uczciwie oznacza N/A, nie zgaduje (dobra dyscyplina) |
| seo-cluster | Poradnik, brak ryzyka kanibalizacji — zgodny wniosek |
| Search Intent Classifier | 9/10 SERP to guides+PAA → Informational, blog post — zgodny wniosek |
| robertbstillwell | Brak danych SemRush/DataForSEO dla long-tail → prawdopodobnie pominie lub poda estymację bez oznaczenia |

**Werdykt:** Remis między większością wariantów — to jest oczekiwane i dobre: prosty przypadek nie powinien różnicować.

---

## 4. ile kosztuje logo dla firmy

**Dane:** AI Overview z cennikiem wg wykonawcy (kreator/freelancer/agencja). People Also Search: "Logo firmy AI", "Tworzenie logo AI za darmo", "Logo firmy za darmo" — **ten sam wzorzec DIY co keyword #2, inna branża**. Related keywords: klaster "logo firmy" (nawigacyjny), klaster "kreator logo za darmo" (transakcyjny/DIY), klaster wizytówek (odrębny produkt, R9), warianty kosztowe.

| Wariant | Odpowiedź |
|---|---|
| Standardowe AI | Może potraktować "kreator logo za darmo" jako część tego samego planu contentowego |
| **Nasz skill** | Pillar kosztowy + wykluczenie klastra DIY (E2, drugi raz w innej branży) + wizytówki jako osobny temat (R9) |
| aaron-he-zhu | "kreator logo za darmo" ma difficulty 14 (niskie) i sensowny wolumen → formuła może to ocenić jako "Quick Win" mimo złego dopasowania odbiorcy |
| seo-cluster | Rozdzieli strukturalnie logo/wizytówki/DIY (różne SERP-y) |
| Search Intent Classifier | Sklasyfikuje "kreator logo za darmo" jako transactional (kreator=narzędzie) — poprawnie z SERP, ale bez oceny czy to klient dla studia graficznego |
| robertbstillwell | KOB Score: niska Difficulty (14) podnosi wynik → podobne ryzyko jak aaron-he-zhu |

**Werdykt:** Wygrana, potwierdza wzorzec z #2 w innej branży (design, nie web-dev) — to już nie pojedynczy przypadek.

---

## 5. agencja seo / najlepsza agencja seo

**Dane:** SERP: local_pack (Warszawa, Poznań, Kraków, Katowice...), rankingi/listicle agencji, PAA "jak wybrać agencję SEO". Related keywords: mocny sygnał lokalny (agencja seo warszawa/poznań/kraków, każda z własnym wolumenem), plus **"semcore" — nazwa realnej konkurencyjnej agencji/marki** jako related keyword.

| Wariant | Odpowiedź |
|---|---|
| Standardowe AI | Prawdopodobnie zaproponuje ranking/porównanie, może nie zauważyć że "semcore" to nazwa marki, nie generyczna fraza |
| **Nasz skill (przed E4)** | Zalecił lokalne landing page + ranking — ale **nie miał reguły wykluczającej nazwy marek konkurencji** |
| aaron-he-zhu | Formuła może wysoko ocenić "semcore" (branded traffic bywa tani/łatwy w KD) bez flagi że to nazwa firmy |
| seo-cluster | Klasyfikacja intencji ma explicit regułę: navigational → "Exclude" z klastrów — **poprawnie wyklucza markę** |
| **Search Intent Classifier** | Ma jawną regułę: "Do not chase navigational queries for competitor brands" — **poprawnie wyklucza, z uzasadnieniem** |
| robertbstillwell | Brak takiej reguły w dokumentacji — ryzyko wciągnięcia marki konkurenta do planu |

**Werdykt:** Przegrana / luka po naszej stronie — znaleziona dzięki testowi. **Naprawiona tego samego dnia: dodano regułę E4** (`wyjatki-niuanse.md`) po wzorze z seo-cluster i Search Intent Classifier.

---

## 6. zlecić pisanie artykułów

**Dane:** SERP **zdominowany przez marketplace'y ofert pracy** — Useme, Pracuj.pl, Jooble, Freelancehunt, zleca.pl. Zero stron typu "zamów tekst u nas" wśród top 10. Brak danych related_keywords (fraza zbyt specyficzna dla bazy DataForSEO).

| Wariant | Odpowiedź |
|---|---|
| Standardowe AI | Może literalnie zinterpretować "zlecić" jako intencję zakupową i polecić stronę usługową bez sprawdzenia realnego SERP |
| **Nasz skill** | Krok 2 workflow (skan SERP) wychwytuje: dominujący typ = marketplace/ogłoszenia o pracę, nie strony usługowe → flaguje słabą szansę na ranking organiczny dla strony usługowej, rekomenduje inne podejście (płatna obecność / inny kanał, nie content) |
| aaron-he-zhu | Formuła liczy tylko metryki (wolumen/trudność/CPC) — **nie czyta treści SERP**, może polecić tę frazę bez ostrzeżenia o realnej konkurencji |
| seo-cluster | Skupiony na klasteryzacji/architekturze, nie na diagnozie "czy w ogóle da się tu wygrać" — częściowo pomija ten typ ostrzeżenia |
| **Search Intent Classifier** | Zasada "SERP wins" zadziała tu identycznie jak u nas — rozpozna, że dominujący format to marketplace, nie strona usługowa, i to nazwie |
| robertbstillwell | Formuła KOB — jak aaron-he-zhu, nie czyta treści wyników |

**Werdykt:** Remis z Search Intent Classifier (oba czytają SERP). Wygrana z 3 pozostałymi (2 formuły + częściowo seo-cluster).

---

## 7. tworzenie stron internetowych warszawa

**Dane:** SERP: local_pack (3 firmy) + strony agencji lokalnych. PAA zawiera drobny szum ("ile zarabia się na tworzeniu stron", "ile trwa nauka") — kariera/edukacja, nie klient.

| Wariant | Odpowiedź |
|---|---|
| Wszystkie 5 wariantów | Zgodnie: landing page lokalny, wzorowany na dominującym formacie agencji. Drobny szum w PAA (pytania o karierę) poprawnie ignorowany przez wszystkie warianty czytające SERP (nasz skill, Search Intent Classifier) — nie ma powodu do rozbudowy strony o wątek "jak zostać web developerem" |

**Werdykt:** Remis — jednoznaczny przypadek, dobry sanity check że nie manufakturujemy różnic tam, gdzie ich nie ma.

---

## 8. ile kosztuje aplikacja mobilna

**Dane:** DataForSEO zwraca wolumen tylko **50** dla dokładnej frazy. SERP mimo to mocno obsadzony: AI Overview z rozbudowanym cennikiem wg złożoności, 3+ szczegółowe artykuły konkurencyjne, wideo YouTube. Related searches sugerują rozproszenie po wariantach ("ile kosztuje stworzenie aplikacji mobilnej" itd.).

| Wariant | Odpowiedź |
|---|---|
| Standardowe AI | Może zniechęcić się niskim wolumenem i odradzić temat |
| **Nasz skill** | R2 (klasteryzacja) każe spojrzeć na temat przez pryzmat wariantów frazy razem, nie jednej frazy osobno — temat oceniony jako wartościowy mimo niskiej pojedynczej metryki |
| aaron-he-zhu | Opportunity = 50×waga/trudność — niska wartość liczbowa, **prawdopodobnie deprioryzuje temat**, formuła nie grupuje wariantów automatycznie przed oceną |
| seo-cluster | Jego expansion (30-50 wariantów przez WebSearch) faktycznie zebrałby powiązane frazy przed oceną — **podobny wniosek do naszego**, inna droga dojścia |
| Search Intent Classifier | Klasyfikuje pojedynczą frazę, nie grupuje wariantów — ryzyko niedocenienia jak przy formułach |
| robertbstillwell | KOB Score = niski wolumen → niski wynik, ryzyko deprioryzacji jak aaron-he-zhu |

**Werdykt:** Remis z seo-cluster (oba grupują przed oceną). Wygrana z formułami i Search Intent Classifier (oceniają frazę w izolacji).

---

## 9. jak zdobyć pierwszych klientów jako freelancer

**Dane:** SERP: wideo YouTube, **wątki Reddit** (r/Entrepreneur, r/photography), blogi poradnikowe. Brak danych wolumenowych DataForSEO (fraza konwersacyjna, długa).

| Wariant | Odpowiedź |
|---|---|
| Standardowe AI | Poradnik/blog post — generyczna, poprawna odpowiedź |
| **Nasz skill** | Poradnik + obserwacja: obecność Reddita w top wynikach to sygnał, że Google nagradza tu autentyczny, pierwszoosobowy głos (E-E-A-T), nie tylko generyczną listę porad — rekomendacja formatu z realnym doświadczeniem, nie czystej listicle |
| aaron-he-zhu | Brak danych wolumenowych → N/A, brak dalszej rekomendacji formatu |
| seo-cluster | Sklasyfikuje jako informational, nie skomentuje niuansu formatu (Reddit) |
| Search Intent Classifier | Odnotuje SERP evidence (guides + community) — może dojść do podobnego wniosku o formacie, jego szablon na to pozwala |
| robertbstillwell | Brak danych → prawdopodobnie pominie frazę |

**Werdykt:** Częściowa wygrana — dodatkowy niuans formatu (nie tylko typ strony, ale styl/głos), częściowo dzielony z Search Intent Classifier.

---

## 10. co to jest content marketing (kontrolna)

**Dane:** SERP zdominowany przez Wikipedię i słowniki/definicje agencji.

| Wariant | Odpowiedź |
|---|---|
| Wszystkie 5 wariantów | Zgodnie: artykuł definicyjny/glosariuszowy. Brak rozbieżności. |

**Werdykt:** Remis — drugi sanity check, potwierdza że dla jednoznacznych przypadków nie ma sztucznych różnic.

---

## Podsumowanie zbiorcze

| # | Keyword | Wynik |
|---|---|---|
| 1 | umowa zlecenia wzór | Wygrana vs formuły, remis vs seo-cluster/Search Intent Classifier |
| 2 | ile kosztuje strona internetowa | **Wygrana** (E2) |
| 3 | jak pisać artykuły seo | Remis (kontrolna) |
| 4 | ile kosztuje logo dla firmy | **Wygrana** (E2, potwierdzenie wzorca) |
| 5 | agencja seo | **Przegrana → naprawiona tego samego dnia (E4)** |
| 6 | zlecić pisanie artykułów | Wygrana vs formuły, remis vs Search Intent Classifier |
| 7 | tworzenie stron internetowych warszawa | Remis (jednoznaczny przypadek) |
| 8 | ile kosztuje aplikacja mobilna | Wygrana vs formuły/Search Intent Classifier, remis vs seo-cluster |
| 9 | jak zdobyć pierwszych klientów | Częściowa wygrana (niuans formatu) |
| 10 | co to jest content marketing | Remis (kontrolna) |

**Wniosek:** Na 10 keywordów — 2 jednoznaczne wygrane oparte wyłącznie na E2 (dopasowanie odbiorcy), żadna przegrana poza #5 (naprawiona), reszta to remisy lub wygrane dzielone z najmocniejszym komparatorem (Search Intent Classifier). To potwierdza wcześniejszy werdykt: przewaga jest realna, ale skoncentrowana w jednym konkretnym typie osądu, nie rozlana po całej linii.
