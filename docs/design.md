# Dokument projektowy moda (roboczy)

Mod do Hearts of Iron IV budowany na **vanilli**. Start w **2025**. Wydarzenia z prawdziwego świata,
ale **zhiperbolizowane**, ton **lekko satyryczny**. Dużo małych eventów ("evencików").

---

## 1. Tryby gry (reguła gry przy starcie)

| Element | Historyczny (kanon) | Niehistoryczny |
|---|---|---|
| Wybory w Niemczech 2026 | Wygrywa AfD | Wynik dynamiczny |
| Alzacja i Lotaryngia | Niemcy zajmują je po zwycięstwie AfD | Możliwe tylko gdy rządzi AfD (decyzja gracza / AI) |
| Unia Zachodnia | Neutralna | Neutralna |
| Francja po przekroczeniu Odry przez Rosję | Dołącza do Paktu Europejskiego, o ile pozwala ideologia | j.w. |
| Rewanż Francji ("La Revanche") | Tylko gdy wojnę domową wygra prorosyjski Front Odrodzenia | Dostępny dla każdego zwycięzcy |
| Rozpad NATO | Zawsze po wojnie bałkańskiej | Zawsze po wojnie bałkańskiej |

---

## 2. Oś czasu (tryb historyczny)

| Data | Wydarzenie |
|---|---|
| 2025 | Start: rząd CDU–SPD w Niemczech, rząd koalicyjny w Austrii, strajki we Francji |
| początek 2026 | Rozpad koalicji w Niemczech ("Budżet na Deutsche Bahn") |
| wiosna 2026 | Przedterminowe wybory w Niemczech, wygrywa AfD |
| 2026 | Strajk generalny we Francji wymyka się spod kontroli i przeradza w wojnę domową; rozpad Wielkiej Brytanii |
| 2026/2027 | Niemcy (AfD) zajmują Alzację i Lotaryngię |
| 2027 | Wojna bałkańska: Kosowo → Bośnia → Czarnogóra → podział Macedonii Północnej z Bułgarią |
| po wojnie bałkańskiej | Rozpad NATO → Pakt Pacyficzny (USA + Japonia) oraz Pakt Europejski |
| 2027 | Chiny zwiększają aktywność wokół Tajwanu, Rosja w Europie Wschodniej |
| koniec 2027 | FPÖ przejmuje władzę w Austrii → referendum → Anschluss 2.0 |
| początek 2028 | Rosja anektuje Białoruś i atakuje Ukrainę → mechanika "Za czy przeciw" |
| 2028+ | Jeśli Ukraina przegra → Rosja atakuje cały Pakt Europejski |
| po przekroczeniu Odry | Kraje neutralne (w tym Francja) dostają wybór: dołączyć do Paktu czy nie |

---

## 3. Niemcy

- Start 2025: rząd CDU–SPD.
- Początek 2026: satyryczny rozpad koalicji ("nie ma pieniędzy na pociągi, jest na komisję ds. punktualności pociągów").
- Wiosna 2026: przedterminowe wybory, w trybie historycznym wygrywa AfD (przed wojną domową we Francji).
- Wewnętrzna mechanika **Ostpolitik ↔ Festung Europa**: rosyjska presja na Polskę i Bałtów przesuwa Niemcy
  ku "Festung Europa" ("Deutschland zuerst, nicht Russland zuerst"). Event "Telefon z Moskwy, którego nikt nie odebrał".
- **Interwencja we Francji** (wymaga rządu AfD), łańcuch decyzji:
  1. "Ochrona Parlamentu Europejskiego" (Strasburg),
  2. "Korytarz humanitarny nad Renem",
  3. "Referendum w Alzacji" (trwa 3 godziny, wynik znany wcześniej),
  4. aneksja Alzacji i Lotaryngii → `set_global_flag = GER_annexed_alsace`.
- Po zajęciu Alzacji zwycięzca francuskiej wojny domowej, Belgia, Holandia, Luksemburg, Hiszpania i Węgry
  **nie wstępują** do Paktu Europejskiego.
- Bez interwencji: Zachód dołącza do Paktu, Niemcy dostają focus "Odpowiedzialny hegemon".
- Ewentualny rewanż Francji → wojna na dwa fronty, event "Déjà vu".

Uwaga: wyśmiewać sytuacje i instytucje, a nie konkretnych żyjących polityków.

---

## 4. Austria: "Neutralność do odwołania"

- Haki: żołnierze w Bośni (EUFOR Althea) i Kosowie (KFOR), duża diaspora serbska i bośniacka w Wiedniu.
- Mechanika **Barometr Neutralności** ("Ewige Neutralität" ↔ "Heim ins Reich 2.0"). Przesuwają go:
  eventy bałkańskie, presja Niemiec, rozpad NATO, boty i tabloid "Wiener Krone".
- Łańcuch kanoniczny:
  1. 2026 "Wiener Melange": kryzys koalicji,
  2. początek 2027 "EUFOR w ogniu": ewakuacja albo zostajemy,
  3. połowa 2027: referendum o końcu neutralności,
  4. rozpad NATO: "Allein in den Alpen",
  5. koniec 2027: FPÖ przejmuje władzę → "Referendum der Herzen" (paski TAK/NIE, decyzje kampanii) → Anschluss 2.0.
- Ścieżki w drzewku (gracz wybiera, AI zawsze Anschluss):
  - **Anschluss 2.0**: kanon,
  - **Alpenfestung**: wieczna neutralność, blok ze Szwajcarią i Liechtensteinem,
  - **Donaukonföderation**: federacja naddunajska jako przeciwwaga dla Niemiec.

---

## 5. Wojna bałkańska 2027

Fazy:
1. **Kosowo**: incydent na północy (wzór: Banjska 2023), Serbia atakuje Kosowo.
2. **Bośnia**: powstanie serbskich nacjonalistów, `start_civil_war` → tag Republiki Serbskiej, Bośnia wciągnięta w konflikt.
3. **Czarnogóra**: pretekst w postaci protestów prosierbskich i sporu o Cerkiew, Serbia atakuje.
4. **Macedonia Północna**: Serbia i Bułgaria dzielą kraj (Bułgaria wschód, Serbia północ), wspólny cel wojenny.

Nikt spoza Bałkanów nie może interweniować:
- spirit "Paraliż decyzyjny" dla wszystkich krajów spoza Bałkanów,
- decyzje interwencji istnieją, ale kończą się satyrą ("Parlament debatował 14 godzin...", "Wysłaliśmy stanowczy list"),
- zabezpieczenie: `on_declare_war` wymusza wycofanie kraju spoza Bałkanów.

Drzewko Serbii: "Kosovo je Srbija", "Braća iz Republike Srpske", Czarnogóra, "Macedoński tort z Bułgarią",
gospodarka wojenna, spirit "Propaganda turbo-folkowa". Po wojnie wybór patrona.

---

## 6. NATO: iluzja wpływu

- Widoczna zmienna `global.nato_trust`. Gracz może ją podbijać decyzjami (szczyty, ćwiczenia, zakupy broni).
- **Rozpad następuje zawsze** po wojnie bałkańskiej, niezależnie od zaufania. Event:
  "Zaufanie do NATO: 97%. Status NATO: rozwiązane. Wszyscy bardzo się starali."
- Żeby nie frustrować gracza, wysokie zaufanie w chwili rozpadu daje nagrody:
  lepszą pozycję w nowym bloku, bonus do spójności Paktu Europejskiego, ukryte osiągnięcie "Optymista".
- Powstają: **Pakt Pacyficzny** (USA + Japonia) i **Pakt Europejski**.

---

## 7. Atak Rosji (2028) i mechanika "Za czy przeciw"

- Aneksja Białorusi (`annex_country`), następnie wojna z Ukrainą (prawdziwa wojna, nie skrypt).
- Ukraina **nie** jest w Pakcie Europejskim; wniosek blokuje weto ("Wymagana jednomyślność. Jeden kraj ma pytania.").
- Każdy członek Paktu ma zmienną `war_stance` (−100 prorosyjska ... +100 proukraińska), Pakt ma pasek **Jedności**.

| Za Ukrainą | Przeciw (appeasement) |
|---|---|
| Wysłanie sprzętu | Kupno taniego rosyjskiego gazu |
| Ochotnicy i szkolenie | Weto wobec sankcji |
| Sankcje | Blokada transportu przez terytorium |
| Zamknięcie przestrzeni powietrznej | "Mediacja pokojowa" |

Rozstrzygnięcie:
- **Ukraina przegrywa** → event "Następni w kolejce", Rosja atakuje cały Pakt. Kraje proukraińskie mają bonusy
  przygotowania. Prorosyjskie dostają "Rosja dziękuje za współpracę" i i tak zostają zaatakowane
  (albo wybierają "finlandyzację" z karami).
- **Ukraina się utrzymuje** → zamrożony konflikt, kryzys wewnętrzny w Rosji.

---

## 8. Francja: wojna domowa 2026

Eskalacja (pasek "Grève Générale"): reforma emerytalna 2.0 → strajk rafinerii → blokady rond → strajk policji
→ podział w wojsku → wojna domowa (wzór: druga wojna secesyjna z TFR, unifikatorzy i separatyści).

| Frakcja | Typ | Postawa | Po przekroczeniu Odry |
|---|---|---|---|
| Rząd Tymczasowy Republiki | unifikator | proeuropejska | dołącza do Paktu (kanon) |
| Komitet Ocalenia Wojskowego | unifikator | pragmatyczna | dołącza, z warunkiem zwrotu Alzacji po wojnie |
| Komuna Cyfrowa | unifikator | antyfaszystowska | odmawia, zostaje neutralna |
| **Front Odrodzenia Narodowego** | unifikator | **prorosyjska**, rewanżystowska | odmawia + **La Revanche** (atak na Niemcy po Alzację) |
| Konfederacja Rond | separatyści / warlordowie | – | – |
| Korsyka, Bretania, Nowa Kaledonia | separatyści | – | – |

Mechanika **Force de frappe**: kontrola nad bazami atomowymi (m.in. Île Longue) zmienia globalne napięcie
i reakcje sąsiadów.

---

## 9. Unia Zachodnia (neutralna) i wybór krajów neutralnych

- Powstaje, gdy Niemcy zajmą Alzację: zwycięska Francja, Belgia, Holandia, Luksemburg, Hiszpania.
- Nie jest frakcją: członkowie dają sobie wzajemne gwarancje (obronna neutralność),
  wspólny spirit (bonus do handlu i produkcji cywilnej, kara do poparcia dla wojny ofensywnej).
- Węgry stoją osobno: neutralne i prorosyjskie (`war_stance` startuje z −60).
- **Wyzwalacz "przekroczenia Odry":** Rosja kontroluje którykolwiek stan będący rdzeniem Niemiec:
  `RUS = { any_controlled_state = { is_core_of = GER } }` (sprawdzane cyklicznie).
- Wtedy **każdy kraj neutralny** (Francja, Belgia, Holandia, Luksemburg, Hiszpania, Węgry) dostaje event
  "Barbarzyńcy nad Odrą" z wyborem:
  - dołączyć do Paktu Europejskiego,
  - zostać neutralnym,
  - (tylko Francja Frontu Odrodzenia / tryb niehistoryczny) La Revanche.
- Ograniczenia ideologiczne: Komuna Cyfrowa i Front Odrodzenia nie mogą wybrać "dołącz".
  Węgry domyślnie (AI) zostają neutralne.
- Unia Zachodnia rozpada się, gdy Francja dołączy do Paktu.

---

## 10. Drobne eventy (warstwa klimatu)

Trzy warstwy: **wielkie** (news_event dla wszystkich), **krajowe** (łańcuchy reakcji), **drobne** (losowe smaczki).

Przykłady drobnych: ceny prądu, deepfake prezydenta, fala uchodźców z Bałkanów, strajk rolników na granicy,
"Euro traci zaufanie", "Wspólna armia europejska?", chińskie drony nad Okinawą, wyciek danych z Pentagonu,
"Ostatni mecz Ligi Narodów przed wojną", "Stop ropy z Rosji", kryzys chipów po kryzysie tajwańskim.

Technicznie: `news_event` z `fire_only_once`, wyzwalanie przez `on_actions` z datą lub globalnymi flagami,
`mean_time_to_happen` dla losowych.

---

## 11. Zakres pierwszej wersji (MVP)

- Bookmark 2025 (historia krajów, stanów, OOB) dla kluczowych krajów, uproszczona reszta świata.
- Grywalne z drzewkami: Austria, Serbia, Francja (i frakcje), Polska, Niemcy, Rosja, Ukraina.
- Globalne łańcuchy eventów dla reszty świata.
- Kolejność prac: globalne flagi i oś czasu (`on_actions`) → wojna bałkańska + NATO → Niemcy/Alzacja
  → Francja → Austria → Rosja/Ukraina i "Za czy przeciw".

## Otwarte kwestie

- Rozpad Wielkiej Brytanii 2026: do rozpisania.
- Rola Polski jako państwa frontowego.
- Chiny–Tajwan i Pakt Pacyficzny: zakres.
