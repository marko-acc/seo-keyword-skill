# Workflow: Konfiguracja marki (jednorazowo)

**Cel:** zebrać minimalny, niezbędny zestaw danych o marce usera, zanim skill oceni jakikolwiek keyword — bez tego reguły R3/E2/R15/R16 (dopasowanie odbiorcy i terytorium marki) oraz ocena kanibalizacji są zgadywaniem, nie analizą. Zapisać wynik do `brand-profile.md` w katalogu głównym, żeby nie pytać o to ponownie przy każdym kolejnym keywordzie.

**Uruchamiane:** automatycznie przez `SKILL.md`, gdy `brand-profile.md` nie istnieje, przy pierwszym użyciu skilla w danej sesji/projekcie.

## Krok 1 — Zapytaj o adres strony

*"Podaj adres swojej strony (URL) — spróbuję sam sprawdzić, czym się zajmujesz i jakie tematy już masz opisane."*

## Krok 2 — Jeśli URL podany: spróbuj odczytać stronę sam

1. Sprawdź stronę główną (WebFetch) — wyciągnij: czym firma się zajmuje, dla kogo, jaka jest oferta.
2. Spróbuj `{URL}/sitemap.xml` — jeśli istnieje, wyciągnij listę adresów blogowych/treściowych jako "istniejące tematy".
3. Jeśli sitemap niedostępny, spróbuj odnaleźć i sprawdzić stronę bloga (`/blog`, `/artykuly`, link w nawigacji).

**Jeśli odczyt się powiódł:** podsumuj to, co znalazłeś, i poproś o potwierdzenie/korektę — nie zakładaj, że automatyczny odczyt jest bezbłędny:

*"Na podstawie Twojej strony rozumiem, że zajmujesz się [X] dla [Y]. Znalazłem [N] istniejących artykułów o [tematy]. Czy to się zgadza, czy coś poprawić/dodać?"*

**Jeśli odczyt się nie powiódł** (strona niedostępna, blokuje boty, brak sitemap, user nie podał URL) — przejdź do Kroku 3.

## Krok 3 — Fallback: zapytaj wprost

*"Nie udało mi się (albo nie podałeś adresu) — opisz w 2-3 zdaniach, czym się zajmujesz, dla kogo, i wklej listę tematów/adresów artykułów, które już masz (jeśli są)."*

Jeśli user nie ma / nie chce podawać listy istniejących treści — kontynuuj bez niej, ale każdorazowo oznaczaj w dalszych analizach, że ocena kanibalizacji nie jest możliwa bez tych danych (nie zgaduj).

## Krok 4 — Zapisz profil

Zapisz do `brand-profile.md` w katalogu głównym:

```markdown
# Profil marki

## Oferta i grupa docelowa
[opis z Kroku 2 lub 3]

## Terytorium (R15 — core / forbidden / adjacent)
[jeśli user wskazał explicite — wypisz; jeśli nie, zostaw puste, niech się wypełnia z czasem przy kolejnych analizach]

## Istniejące treści
[lista tematów/URL z sitemap lub od usera — albo "brak danych, nie zbierane"]

## Źródło
[automatyczny odczyt strony / opis od usera / mix]

*Zaktualizowano: [data]*
```

## Krok 5 — Potwierdź i przejdź do właściwej analizy

*"Zapisałem to jako Twój profil marki — będę z niego korzystał przy kolejnych keywordach, nie będę pytał od nowa. Możesz go poprawić ręcznie w `brand-profile.md`, jeśli coś się zmieni."*
