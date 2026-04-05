# ClearClause (JasnaUmowa) — User Journey Map
> Framework: WF_User_Journey_Map | Data: 2026-04-05
> Zasada: *User Success = First Touch Value + Minimal Friction + Moment of Aha*

---

## Success Metric — „Co to jest sukces użytkownika?"

> **Użytkownik uzna ClearClause za warte 9 zł, jeśli:**
> → W ciągu 3 minut od wklejenia tekstu umowy otrzyma raport wskazujący konkretny ryzykowny zapis i zrozumie, co może stracić — zanim złoży podpis.

Mierzalne: *czas od rejestracji do pierwszego raportu < 5 min* | *ocena zrozumiałości ≥ 7/10* | *użytkownik zmienia decyzję lub negocjuje po analizie*.

---

## Persona (trigger journey)

**Kasia, 24 lata, studentka / młoda freelancerka**
Wynajmuje pierwsze mieszkanie. Wynajmujący wysyła PDF umowy — „podpisz do jutra". Kasia nie rozumie §8 (kaucja) i §12 (wypowiedzenie). Znajomi mówią „nie czytaj, daj znać jak chcesz podpisać". Kasia googla „co oznacza klauzula umowy najmu" → trafia na ClearClause.

---

## Stage 1 — Landing (0–30 sekund)

### Co widzi użytkownik

```
┌─────────────────────────────────────────────────────────┐
│  Headline:                                              │
│  "Dostałeś umowę do podpisania?                        │
│   Sprawdź ją w 30 sekund — zanim zgodzisz się na coś   │
│   czego nie rozumiesz."                                 │
│                                                         │
│  Sub-headline:                                          │
│  AI tłumaczy żargon prawniczy na ludzki język,          │
│  wskazuje ukryte kary i klauzule abuzywne.              │
│                                                         │
│  [CTA] → Sprawdź swoją umowę — 9 zł                    │
│                                                         │
│  Przykładowy raport (screenshot / live demo):           │
│  §8: 🔴 RYZYKO WYSOKIE — kaucja przepada bez ostrzeżenia│
└─────────────────────────────────────────────────────────┘
```

**Elementy krytyczne:**
- [ ] Headline mówi o jednej konkretnej sytuacji (umowa najmu/zlecenia), nie „AI Legal Assistant"
- [ ] Value prop widoczny BEZ scrollowania (above the fold)
- [ ] Przykładowy fragment raportu — użytkownik widzi, co dostanie, zanim zapłaci
- [ ] CTA z ceną wprost — brak niespodzianek przy kasie

**Friction Points i rozwiązania:**

| Problem | Ryzyko | Rozwiązanie |
|---|---|---|
| Zbyt ogólny headline „AI dla umów" | Kasia nie wie, czy to dla niej | Headline w 2 osobie + konkretna sytuacja |
| Brak demo / podglądu raportu | „Czy to działa? Nie wiem jak wygląda" → opuszcza stronę | Statyczny przykład raportu na landing page |
| Zbyt wiele opcji cenowych (Freemium vs Pro) | Paradoks wyboru → exit | Jedna cena, jeden CTA |
| „Zarejestruj się za darmo" bez informacji o płatności | Surprise przy kasie → porzucenie | „9 zł / analiza — bez subskrypcji" na landingu |

**Aha Moment (Stage 1):** Użytkownik myśli: *„To dokładnie moja sytuacja — mam umowę najmu i jutro deadline."*

**CTA:** `Sprawdź swoją umowę — 9 zł` (nie: „Dowiedz się więcej", nie: „Zacznij za darmo")

---

## Stage 2 — Sign-Up (1–2 minuty)

### Flow

```
[Klik CTA]
    ↓
[Formularz rejestracji — 2 pola]
    Email: ___________
    Hasło: ___________
    [Zarejestruj się]
    ↓
[Przekierowanie do Stripe Checkout]
    Produkt: Analiza dokumentu — 9 zł
    Karta / BLIK / Google Pay
    [Zapłać 9 zł]
    ↓
[Potwierdzenie płatności → przekierowanie do Analyzera]
```

**Elementy krytyczne:**
- [ ] Tylko 2 pola: email + hasło — zero pytań o branżę, stanowisko, cel
- [ ] Żaden survey onboardingowy przed pierwszym użyciem
- [ ] Rejestracja i płatność w jednym ciągłym flow (nie: „zarejestruj się → potwierdź email → zaloguj → dopiero kup")
- [ ] Jasna sekwencja kroków: `1. Konto → 2. Płatność → 3. Analiza`
- [ ] Po płatności: natychmiastowy dostęp, bez czekania na email

**Friction Points i rozwiązania:**

| Problem | Ryzyko | Rozwiązanie |
|---|---|---|
| Potwierdzenie emaila PRZED płatnością | Kasia nie sprawdza emaila od razu → porzuca | Potwierdzenie emaila PO pierwszej analizie (Clerk magic link opcjonalny) |
| Wymaganie numeru telefonu / 2FA | Zbędna bariera przy 9 zł zakupie | Email + hasło — wystarczy |
| Formularz „Powiedz nam o sobie" | Kasia chce analizy, nie ankiety | Usuń — dane zbieraj przez użycie produktu |
| Stripe — brak BLIK | Polska: BLIK jest dominującą metodą dla 18–30 lat | Aktywuj BLIK w Stripe Payments (natywne wsparcie) |
| Redirect po rejestracji do dashboardu zamiast do Analyzera | User szuka, gdzie zacząć | Redirect bezpośrednio: `/analyzer` |

**Email po rejestracji (max 5 min po płatności):**
> Temat: „Twoja analiza jest gotowa — zaloguj się by zobaczyć wynik"
> Treść: 2 zdania + przycisk `Wróć do analizy`

**Aha Moment (Stage 2):** Użytkownik widzi pole do wklejenia tekstu — natychmiast wie, co robić.

---

## Stage 3 — First Data Input (2–4 minuty)

### Flow

```
[Analyzer — strona po zalogowaniu]

┌─────────────────────────────────────────────────────────┐
│  Wklej fragment umowy lub cały paragraf:                │
│                                                         │
│  ┌─────────────────────────────────────────────────┐   │
│  │ [placeholder: np. §8. Wynajmujący ma prawo      │   │
│  │  zatrzymać kaucję w przypadku…]                 │   │
│  └─────────────────────────────────────────────────┘   │
│                                                         │
│  Typ umowy: [Najem ▼] [Zlecenie] [Pożyczka]            │
│                                                         │
│  [Analizuj →]                                           │
└─────────────────────────────────────────────────────────┘
```

**Elementy krytyczne:**
- [ ] Placeholder tekst — gotowy przykład do skopiowania, użytkownik widzi format
- [ ] Wybór typu umowy (dropdown) — kontekstuje system prompt, poprawia jakość raportu
- [ ] Max 3 000 znaków na MVP (komunikat live: „X/3000 znaków")
- [ ] Jeden guzik — zero opcji konfiguracyjnych
- [ ] Walidacja real-time: jeśli pole puste → „Wklej tekst, który chcesz przeanalizować"

**Friction Points i rozwiązania:**

| Problem | Ryzyko | Rozwiązanie |
|---|---|---|
| Użytkownik nie wie, co wkleić (ma PDF) | Frustracja → exit | Instrukcja 1 zdanie: „Skopiuj paragraf z umowy i wklej poniżej" + link „Jak otworzyć PDF?" |
| Brak wyboru typu umowy | Ogólny raport niskiej jakości | Dropdown: Najem / Zlecenie / O dzieło / Pożyczka / Inne |
| Formularz wygląda jak search bar | Użytkownik wpisuje 3 słowa zamiast paragrafu | Duże pole textarea (min 6 linii wysokości), placeholder z przykładem |
| Error message po submicie (pusty input) | Dezorientacja | Walidacja przed submitem + komunikat inline |

**Aha Moment (Stage 3):** System akceptuje tekst i pojawia się progress indicator — użytkownik czuje, że „coś się dzieje".

---

## Stage 4 — Processing (5–15 sekund)

### UX

```
[Po kliknięciu "Analizuj →"]

  ⏳ Analizuję zapisy umowy...
  ████████░░░░░░░░  Sprawdzam klauzule abuzywne (rejestr UOKiK)...

  Zwykle zajmuje to 5–10 sekund.
```

**Elementy krytyczne:**
- [ ] Animowany progress bar z opisowym tekstem (nie pusty spinner)
- [ ] Komunikat zmienia się co 3 sekundy: „Tłumaczę na ludzki język…" → „Szukam ukrytych kosztów…" → „Generuję raport…"
- [ ] Szacowany czas: „Zwykle zajmuje to 5–10 sekund"
- [ ] Jeśli czas > 15 sek.: pokaż komunikat „Jeszcze chwila — analizuję dłuższy dokument"

**Friction Points i rozwiązania:**

| Problem | Ryzyko | Rozwiązanie |
|---|---|---|
| Biały ekran ze statycznym spinner'em | Poczucie zawieszenia → zamknięcie karty | Animowany progress + opis kroków |
| Czas > 20 sekund bez komunikatu | „Strona się zawiesiła?" | Timeout fallback: „To trwa dłużej niż zwykle — nie zamykaj strony" |
| Brak obsługi błędu API | Crash bez komunikatu | Try/catch → user-friendly: „Ups, coś poszło nie tak. Spróbuj ponownie — analiza nie zostanie pobrana ponownie" |

---

## Stage 5 — First Output / AHA MOMENT (20–60 sekund od kliknięcia)

### Struktura raportu

```
┌─────────────────────────────────────────────────────────┐
│  RAPORT ANALIZY UMOWY NAJMU                             │
│  Przeanalizowany fragment: §8 Kaucja (245 znaków)      │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  📖 CO TO OZNACZA?                                      │
│  Wynajmujący może zatrzymać całą kaucję jeśli uzna,     │
│  że mieszkanie zostało „uszkodzone" — bez obowiązku     │
│  udowodnienia szkody ani podania kwoty.                 │
│                                                         │
├─────────────────────────────────────────────────────────┤
│  ⚠️ RYZYKA I HACZYKI                                    │
│  🔴 Brak definicji „uszkodzenia" — dowolna interpretacja│
│  🔴 Brak terminu zwrotu kaucji (standard: 30 dni)       │
│  🟡 Brak obowiązku protokołu zdawczo-odbiorczego        │
│                                                         │
├─────────────────────────────────────────────────────────┤
│  🛡️ OCENA BEZPIECZEŃSTWA                               │
│  ██████████░░░░░ 4/10 — RYZYKOWNE 🔴                   │
│                                                         │
│  Ta klauzula odbiega od standardu (art. 6a UoOL).      │
│  Możesz poprosić o zmianę zapisu.                       │
│                                                         │
├─────────────────────────────────────────────────────────┤
│  ⚠️ To narzędzie ma charakter edukacyjny i nie zastępuje│
│  porady prawnej. W razie wątpliwości skonsultuj się     │
│  z prawnikiem.                                          │
├─────────────────────────────────────────────────────────┤
│  [Skopiuj raport]  [Analizuj kolejny fragment]          │
└─────────────────────────────────────────────────────────┘
```

**Elementy krytyczne:**
- [ ] Raport podzielony na 3 sekcje (Znaczenie / Ryzyka / Ocena) — nie blok tekstu
- [ ] Sygnalizacja 🟢/🟡/🔴 przy każdym ryzyku — użytkownik natychmiast widzi priorytet
- [ ] Odwołanie do konkretnego artykułu prawa (art. X KC/UoOL) przy niestandardowych zapisach
- [ ] Score graficzny (progress bar) — wizualnie czytelny bez czytania całości
- [ ] Disclaimer prawny — stały, nieusuwany, po raporcie
- [ ] CTA: „Analizuj kolejny fragment" (nie „Kup więcej") — buduje wartość przed upsell

**Friction Points i rozwiązania:**

| Problem | Ryzyko | Rozwiązanie |
|---|---|---|
| Raport = ściana tekstu bez struktury | Użytkownik nie wie, gdzie patrzeć | 3 wyraźne sekcje + ikony + kolorowe badge |
| Zbyt ogólne tłumaczenie (mogłoby być o każdej umowie) | „To samo co ChatGPT. Nie widzę wartości." | System prompt wymusza: zawsze odnosić się do konkretnego fragmentu + cytować skan |
| Ocena „4/10" bez wyjaśnienia co znaczy | „To dobrze czy źle?" | Legenda: 1–3: ⛔ Unikaj / 4–6: 🔴 Negocjuj / 7–8: 🟡 Sprawdź / 9–10: 🟢 Standardowe |
| Brak opcji eksportu / kopiowania | Użytkownik nie może wysłać raportu wynajmującemu | Przycisk „Skopiuj raport" (plain text do wklejenia w WhatsApp/email) |
| Paywall na połowie raportu | Zaufanie spada drastycznie | Model Pay-Per-Doc — raport zawsze pełny po opłaceniu |

**Aha Moment (Stage 5 — KLUCZOWY):**
> *„Ten zapis jest naprawdę ryzykowny. Nie wiedziałam. Zadzwonię do wynajmującego i poproszę o zmianę."*

**Cel czasowy: Landing → Aha Moment w < 5 minut.**

---

## Stage 6 — Second Action (1–3 dni później)

### Scenariusze powrotu

**Scenariusz A (best case):** Użytkownik wraca samodzielnie — ma kolejny paragraf, który chce sprawdzić. Nie potrzebuje emaila.

**Scenariusz B (typowy):** Użytkownik dostaje email 24h po pierwszej analizie.

**Scenariusz C (nieudany):** Użytkownik nie wraca — Aha Moment był słaby lub problem rozwiązany jednorazowo (incydentalny use case).

### Email 24h po analizie

> **Temat:** „Twoja umowa: 3 rzeczy, które warto negocjować zanim podpiszesz"
>
> Cześć [imię],
>
> Przejrzałeś/aś §8 swojej umowy. Raport wykazał 2 ryzyka oznaczone 🔴.
>
> Jeśli nie wiesz, jak poprosić o zmianę tych zapisów — mamy gotowe szablony.
>
> [Wróć i sprawdź kolejny paragraf →]
>
> _ClearClause — zanim podpiszesz, zrozum co podpisujesz._

**In-app widget (po powrocie):**
```
💡 Masz więcej fragmentów do sprawdzenia?
   Poprzednia analiza: §8 Kaucja — 4/10 🔴
   [Analizuj kolejny fragment]
```

**Friction Points i rozwiązania:**

| Problem | Ryzyko | Rozwiązanie |
|---|---|---|
| Email po 24h jest zbyt ogólny | Użytkownik go ignoruje | Email personalizowany o konkretnym wyniku analizy (wynik z DB) |
| App wygląda identycznie jak przy pierwszej wizycie | Brak motywacji do powrotu | Widget „Kontynuuj analizę" z poprzednią historią na top |
| Brak historii poprzednich analiz | Użytkownik nie wie, co już sprawdził | Tier 2: prosta lista — data + fragment + ocena. Na MVP: tylko 1 analiza widoczna |

**Metryka:** Return rate Day 3 — cel ≥ 25% powracających użytkowników.

---

## Stage 7 — Conversion / Repeat Purchase (przy następnej umowie)

*Uwaga: Model Pay-Per-Document, nie subskrypcja. „Konwersja" = kupno kolejnej analizy.*

### Trigger konwersji

**Moment:** Użytkownik z nową umową (nowy najem po roku, nowy klient B2B, pożyczka).

**Trigger email (na podstawie daty rejestracji + sezonowości):**
> Temat: „Sezon wynajmu zbliża się — sprawdź umowę zanim podpiszesz"
> *(wysyłany sierpień–wrzesień: powrót studentów, czas szukania mieszkań)*

**In-product trigger (przy wyczerpaniu darmowego limitu):**
```
Twoja bezpłatna analiza została wykorzystana.
Kolejna analiza: 9 zł — bez subskrypcji, bez zobowiązań.
Pakiet 3 analiz: 20 zł (oszczędzasz 7 zł)
[Kup analizę — 9 zł]  [Kup pakiet 3 — 20 zł]
```

**Elementy krytyczne:**
- [ ] Cena wprost — „9 zł / analiza" (bez „od X zł")
- [ ] Opcja pakietu: 3 analizy za 20 zł (subtelny upsell bez presji)
- [ ] 1-click purchase jeśli wcześniej była karta w Stripe (Stripe Saved Payment Methods)
- [ ] Brak subskrypcji w CTA na tym etapie — subskrypcja dopiero po walidacji powtarzalności

**Friction Points i rozwiązania:**

| Problem | Ryzyko | Rozwiązanie |
|---|---|---|
| Konieczność ponownego wpisywania karty | Tarcie przy repeat purchase | Stripe saved cards — `customer.payment_methods` |
| Brak pakietów — tylko 9 zł/szt. | Niska percepcja wartości przy częstszym użyciu | Wprowadź pakiet 3 analiz za 20 zł od razu |
| Subskrypcja jako jedyna opcja | Segment incydentalny odrzuca (churn problem) | Pay-Per-Doc jako default, subskrypcja jako OPCJA „dla aktywnych" |

**Aha Moment (Stage 7):** *„Ostatnim razem zaoszczędziłam 1 500 zł kaucji. 9 zł za spokój ducha to tanio."*

---

## Mapowanie Krytycznych Friction Points (Full Journey)

| Stage | Friction Point | Wpływ na konwersję | Priorytet naprawy |
|---|---|---|---|
| Landing | Ogólny headline, brak demo raportu | ⛔ Krytyczny (exit przed sign-up) | P0 |
| Sign-Up | Potwierdzenie emaila przed płatnością | 🔴 Wysoki (porzucenie flow) | P0 |
| Sign-Up | Brak BLIK | 🔴 Wysoki (Polska: BLIK #1 metoda 18–30 lat) | P1 |
| Input | Użytkownik nie wie, co wkleić (ma PDF) | 🟡 Średni | P1 |
| Processing | Biały ekran / brak komunikatu | 🟡 Średni (poczucie błędu) | P2 |
| Output | Raport = ściana tekstu | ⛔ Krytyczny (Aha Moment się nie pojawia) | P0 |
| Output | Ogólne tłumaczenie bez konkretnych odniesień do prawa | 🔴 Wysoki („to samo co ChatGPT") | P0 |
| Second Action | Brak personalizowanego emaila | 🟡 Średni | P2 |
| Conversion | Ponowne wpisywanie karty | 🟡 Średni | P2 |

---

## Total Time: Landing → Aha Moment

| Etap | Czas |
|---|---|
| Landing (decyzja) | 20–30 sek. |
| Sign-Up (2 pola) | 30–60 sek. |
| Stripe Checkout | 30–60 sek. |
| Wklejenie tekstu | 30–90 sek. |
| Processing AI | 5–15 sek. |
| Raport (Aha Moment) | — |
| **ŁĄCZNIE** | **~2–4 minuty** ✅ |

Cel < 5 minut: **SPEŁNIONY** przy poprawnym flow.

---

## Summary Metrics (Cele MVP)

| Metryka | Cel |
|---|---|
| Landing → Płatność | ≥ 3% |
| Płatność → Raport (completion) | ≥ 90% |
| Ocena raportu (in-app, 1–10) | ≥ 7/10 |
| Return Rate Day 3 | ≥ 25% |
| Repeat Purchase (30 dni) | ≥ 15% |
| Support tickets / tydzień | < 2 |

---

## Quick Wins — Zmiany poprawiające konwersję w < 4 godziny

1. **Zmień headline landingu** z ogólnego na sytuacyjny: *„Dostałeś umowę najmu do podpisania? Sprawdź ją zanim złożysz podpis — 9 zł, wynik w 30 sekund."*
2. **Dodaj statyczny przykład raportu** na landing page (screenshot z prawdziwym wynikiem §8 🔴 Ryzykowne) — użytkownik widzi produkt przed zakupem.
3. **Skonfiguruj BLIK w Stripe** — 5 minut konfiguracji, krytyczne dla polskiej grupy docelowej 18–30 lat.
4. **Zmień placeholder w textarea** na konkretny przykładowy paragraf — użytkownik od razu rozumie format inputu.
5. **Dodaj ocenę in-app po raporcie** — 3 sekundy: `Czy raport był pomocny? 👍 👎` (dane do iteracji system promptu).

---

## Biggest Friction Point (jeden, który zabije konwersję)

> **Raport niskiej jakości = ściana ogólnego tekstu, która nie różni się od „wklejenia do ChatGPT".**

Jeśli użytkownik zapłaci 9 zł i otrzyma raport, który mógłby dostać bezpłatnie, nie wróci i zostawi negatywną recenzję. **Jakość systemu promptu jest jedynym prawdziwym moatem ClearClause** — inwestuj w nią przed UI.

---

## Powiązane dokumenty

- [Product Brief](./product-brief-clearclause.md) — koncepcja, moduły, model biznesowy
- [ICP + Problem Matrix](./icp-clearclause.md) — profil użytkownika (Kasia, Freelancer, Kredytobiorca)
- [Kill-the-Idea Audit](./kill-the-idea-clearclause.md) — ryzyka, Red Flags modelu subskrypcyjnego
- [MVP Scope](./mvp-scope-clearclause.md) — lista funkcji Tier 1/2/3, tech stack

---

*Dokument wygenerowany wg procedury `WF_User_Journey_Map` | ClearClause Pre-MVP | 2026-04-05*
