# ClearClause (JasnaUmowa) — Product Brief
> Kategoria: Legal-Tech / AI Utility SaaS | Etap: Idea / Pre-MVP | Data: 2026-04-05

---

## 1. Concept Statement

**Problem:** Istnieje głęboka asymetria wiedzy pomiędzy instytucjami (banki, korporacje, wynajmujący) a zwykłym obywatelem. Przeciętna osoba podpisuje umowę najmu, zlecenia lub pożyczki „na wiarę", bo nie rozumie legalese, a prawnik kosztuje 600–1 500 zł/godz.

**Rozwiązanie:** ClearClause to inteligentny tłumacz i asystent umów — niweluje tę asymetrię, wyjaśniając zapisy prostym językiem, wskazując ryzyka i pomagając tworzyć bezpieczne alternatywy. Użytkownik nie musi wiedzieć, o co pytać — system sam wie, czego szukać.

**1-liner:** *„ClearClause tłumaczy żargon prawniczy na ludzki język i generuje bezpieczne umowy dla osób bez wykształcenia prawniczego."*

---

## 2. Trzy Filary Działania (Moduły produktu)

### Moduł 1 — The Decoder (Analiza)
Użytkownik wkleja tekst paragrafu lub przesyła zdjęcie/PDF dokumentu. AI generuje raport w czasie rzeczywistym:

| Komponent raportu | Opis |
|---|---|
| **Co to oznacza?** | Tłumaczenie paragrafu na język potoczny (max 3 zdania) |
| **Gdzie jest haczyk?** | Wskazanie kar umownych, ukrytych kosztów, terminów wypowiedzenia, klauzul abuzywnych |
| **Ocena bezpieczeństwa** | Skala 1–10 + sygnalizacja świetlna: 🟢 (bezpieczne) / 🟡 (uwaga) / 🔴 (ryzykowne) |

**System prompt:** Zaszyty zestaw instrukcji eksperckich opartych na polskim prawie cywilnym (Kodeks Cywilny, Ustawa o Ochronie Praw Konsumenta, Ustawa o Kredycie Konsumenckim), który automatycznie wyszukuje niedozwolone klauzule abuzywne (rejestr UOKiK).

---

### Moduł 2 — The Architect (Kreacja)
Interaktywny generator umów oparty na dynamicznym wywiadzie. Zamiast statycznego szablonu AI zadaje użytkownikowi celowane pytania o intencje:

> *„Czy chcesz móc wypowiedzieć umowę w dowolnym momencie?"*
> *„Czy lokal ma być podnajmowany?"*
> *„Jak długo ma trwać okres rozliczeniowy?"*

Na podstawie odpowiedzi system buduje spersonalizowany, profesjonalny dokument zgodny z polskim prawem. Typy generowanych umów (MVP scope):

- Umowa najmu mieszkania / pokoju
- Umowa o dzieło / zlecenie (dla freelancerów)
- Prosta umowa pożyczki między osobami fizycznymi

---

### Moduł 3 — The Counter (Negocjacja)
Generator gotowych odpowiedzi i kontrpropozycji do drugiej strony umowy. Użytkownik zaznacza zapis, który mu nie odpowiada, a system generuje:

- Gotowy e-mail do banku / właściciela mieszkania z prośbą o zmianę konkretnego zapisu
- Alternatywny zapis (redline) w stylu prawniczym
- Krótkie uzasadnienie prawne zmiany (np. powołanie na art. 385¹ KC — klauzule abuzywne)

---

## 3. Grupy Docelowe (Target Segments)

| Segment | Przykładowe use case'y | Priorytet |
|---|---|---|
| **Najemcy i wynajmujący** | Analiza umowy najmu przed podpisaniem, generowanie umowy dla podnajemcy | ⭐⭐⭐ Core |
| **Pracownicy i zleceniobiorcy (UoP / B2B / dzieło)** | Sprawdzenie zakazu konkurencji, praw autorskich do dzieła, kar za wypowiedzenie | ⭐⭐⭐ Core |
| **Klienci instytucji finansowych** | Tłumaczenie RRSO, ubezpieczeń do kredytów, warunków wcześniejszej spłaty | ⭐⭐ Secondary |
| **Konsumenci** | Analiza regulaminów usług cyfrowych, skomplikowanych umów subskrypcyjnych | ⭐ Later |

---

## 4. Przewaga Konkurencyjna

### vs. ChatGPT / ogólne modele AI
| Cecha | ChatGPT (ogólny) | ClearClause |
|---|---|---|
| Znajomość polskiego prawa | Ogólna, bez aktualnych rejestrów | Zaszyty system prompt z KC, UOPK, UOKK, rejestrem klauzul UOKiK |
| Kontekst zapytania | Użytkownik musi wiedzieć, o co pytać | System sam skanuje pod kątem znanych wzorców ryzyka |
| UX dla laika | Odpowiedź tekstowa → wymaga interpretacji | Strukturalny raport: tłumaczenie + ryzyko + ocena 1–10 |
| Generowanie umów | Brak ustrukturyzowanego flow | Interaktywny wywiad → gotowy dokument .docx / .pdf |
| Moduł negocjacji | Brak | Gotowy e-mail / redline do drugiej strony |

### vs. Kancelarie prawne
- Koszt: 0–29 zł/mies. vs. 600–1 500 zł/godz.
- Dostępność: 24/7, wynik w < 5 min vs. umówiona wizyta
- Skalowalność: nieograniczona liczba dokumentów

---

## 5. Model Biznesowy

### Freemium (Tier 0 — darmowy)
- Analiza pojedynczych zapisów (do **1 500 znaków**)
- 1 raport Decoder / dobę
- Brak eksportu, brak archiwum

### Subscription — SaaS (Tier 1 — płatny)
Proponowana cena: **19–29 zł / miesiąc** (lub 9 zł / jednorazowa analiza dokumentu)

| Funkcja | Freemium | Subscription |
|---|---|---|
| Analiza fragmentów tekstu | ✅ (1 500 znaków) | ✅ Bez limitu |
| Analiza pełnych PDF | ❌ | ✅ |
| Generator umów (The Architect) | ❌ | ✅ |
| Moduł negocjacji (The Counter) | ❌ | ✅ |
| Eksport .docx / .pdf | ❌ | ✅ |
| Archiwum umów w chmurze | ❌ | ✅ |
| Historia analiz | ❌ | ✅ |

### Potencjalne kanały przychodu (przyszłość)
- **B2B API** — agencje nieruchomości, platformy freelancerskie (np. No Fluff Jobs, Useme)
- **Partnerstwa** — linki afiliacyjne do e-prawników przy wykryciu złożonych spraw
- **White-label** — banki / SKOKi oferujące ClearClause jako wartość dodaną

---

## 6. JTBD — Job-to-be-Done (wg WF_Job_To_Be_Done)

### Summary
- **Hipoteza problemu:** Młodzi dorośli podpisują niekorzystne umowy, bo brak im wiedzy prawnej i środków na profesjonalną pomoc.
- **Target ICP:** 18–30 lat, student / freelancer / klient instytucji finansowej, Polsce, decyzje online.
- **Top insight:** Użytkownik nie chce zostać prawnikiem — chce wiedzieć „czy mogę to podpisać bez obawy, że wyląduję na ulicy lub stracę pieniądze".

### 5 Job Snapshotów (hipotezy — do weryfikacji wywiadami)

**Snapshot 1 — Student wynajmując pierwsze mieszkanie**
- **Context:** Wieczór przed planowanym podpisaniem umowy najmu, student na telefonie.
- **Motivation:** Boi się §12 „Kaucja przepada w przypadku…" — nie wie, czy to normalne.
- **Desired Outcome:** Potwierdzenie „ta klauzula jest standardowa" lub „to klauzula abuzywna, możesz żądać zmiany".
- **Current Solution:** Pyta rodziców / googla / pyta na Reddicie.
- **Barriers:** Rodzice nie wiedzą, Google daje nieaktualne wyniki, Reddit niepewny.
- **Trigger:** Deadline od wynajmującego na następny dzień.
- **Wartość:** Błąd = utrata kaucji 1 500–3 000 zł lub niekorzystne warunki przez 12 mies.
- **Confidence:** 7/10

**Snapshot 2 — Freelancer (grafik) podpisujący umowę o dzieło**
- **Context:** Nowy klient korporacyjny wysyła 6-stronicową umowę z §4 „Przeniesienie autorskich praw majątkowych".
- **Motivation:** Nie chce oddać praw do portfolio bezterminowo i za darmo.
- **Desired Outcome:** Zrozumieć, co traci; dostać gotową kontrpropozycję do klienta.
- **Current Solution:** Grupy FB dla freelancerów (porady laików), ewentualnie ignoruje.
- **Barriers:** Nie chce stracić zlecenia przez negocjacje; nie wie, co jest „normalne" w branży.
- **Trigger:** Wartość zlecenia > 2 000 zł — tym razem chce sprawdzić.
- **Wartość:** Prawa do pracy wartej dziesiątki tysięcy zł (prawa autorskie majątkowe).
- **Confidence:** 8/10

**Snapshot 3 — Osoba zaciągająca pożyczkę konsumencką**
- **Context:** W oddziale banku / SKOKu, doradca daje do podpisania 12-stronicową umowę.
- **Motivation:** Chce wiedzieć, ile naprawdę zapłaci za całe życie kredytu.
- **Desired Outcome:** „Łączny koszt = X zł, miesięczna rata = Y zł, wcześniejsza spłata kosztuje Z zł."
- **Current Solution:** Pyta doradcę (konflikt interesów), kalkulator RRSO na UOKiK (skomplikowany).
- **Barriers:** Presja czasu przy podpisaniu, żargon finansowy (RRSO, prowizja, PES).
- **Trigger:** Podpisanie umowy w banku.
- **Wartość:** Błąd = przepłacenie 5 000–30 000 zł na odsetkach lub opłatach.
- **Confidence:** 6/10

**Snapshot 4 — Najemca otrzymujący wezwanie do opuszczenia lokalu**
- **Context:** Wynajmujący wysyła pismo o rozwiązaniu umowy za „naruszenie regulaminu".
- **Motivation:** Nie wie, czy to legalne i jakie ma prawa (termin wypowiedzenia, tryb eksmisji).
- **Desired Outcome:** „Czy muszę się wyprowadzić w 7 dni? Co mi grozi jeśli zostanę?"
- **Current Solution:** Forum prawne (długi czas oczekiwania), bezpłatna porada miejska (kolejka 2–4 tyg.).
- **Barriers:** Pilność sytuacji vs. długi czas dostępu do porady.
- **Trigger:** Otrzymanie pisma z terminem.
- **Wartość:** Błąd = bezdomność lub postępowanie eksmisyjne.
- **Confidence:** 7/10

**Snapshot 5 — Pracownik podpisujący umowę B2B z pierwszym klientem**
- **Context:** Przejście z UoP na B2B — klient wysyła umowę z NDA, zakazem konkurencji i karami umownymi.
- **Motivation:** Nie wie, czy może jednocześnie pracować z innymi klientami.
- **Desired Outcome:** Lista rzeczy, które może/nie może robić przez czas trwania umowy i po jej zakończeniu.
- **Current Solution:** Pyta na grupach LinkedIn, płaci za jednorazową poradę prawną (300–500 zł).
- **Barriers:** Nie wie, co jest negotiable a co standardowe w B2B IT.
- **Trigger:** Pierwsza umowa B2B — nowy teren.
- **Wartość:** Kara umowna 10 000–50 000 zł za naruszenie NDA lub zakazu konkurencji.
- **Confidence:** 8/10

### Okazja: Core Job-to-be-Done
> **„Chcę szybko i pewnie zrozumieć umowę, którą mam podpisać — bez ryzyka, że ukryty zapis wpędzi mnie w poważne kłopoty finansowe lub prawne."**

### Minimum Success Criteria dla MVP
1. Użytkownik wkleja paragraf i w < 60 sekund dostaje zrozumiałe wyjaśnienie + ocenę ryzyka.
2. Użytkownik wie, co jest „niestandardowe" (czerwone flagi) bez znajomości prawa.
3. Użytkownik może wygenerować lub pobrać alternatywny zapis / e-mail do drugiej strony.

---

## 7. Stack Technologiczny (propozycja MVP)

| Warstwa | Technologia | Uzasadnienie |
|---|---|---|
| Frontend | Next.js 14 (App Router) + Tailwind CSS | SEO, SSR, szybki time-to-market |
| AI / LLM | OpenAI API (gpt-4o) z system promptem prawnym | Najlepsza jakość rozumowania prawniczego |
| Parsowanie PDF | `pdf-parse` / LangChain PDF loader | Ekstrakcja tekstu z przesłanych dokumentów |
| Auth | Clerk lub NextAuth.js | Szybki onboarding bez budowania od zera |
| Baza danych | Supabase (PostgreSQL) | Archiwum umów, historia analiz |
| Płatności | Stripe | Freemium → Subscription, jednorazowe płatności |
| Hosting | Vercel | Zero-config deployment dla Next.js |
| Eksport dokumentów | `docx` (npm) + `puppeteer` / `react-pdf` | Generowanie .docx i .pdf |

---

## 8. Roadmap (Fazy)

### Faza 0 — Walidacja (teraz, 2–4 tyg.)
- [ ] Concierge MVP: ręczna analiza 10 umów dla testerów, formularz feedbacku
- [ ] 7 wywiadów z segmentem core (studenci, freelancerzy)
- [ ] Landing page z pre-signup (mierz: CTR → signup → WTP)
- [ ] Cel: WTP > 0 u ≥ 60% testerów → sygnał do budowania

### Faza 1 — MVP (4–8 tyg. po walidacji)
- [ ] Moduł Decoder (wklejanie tekstu → raport)
- [ ] System prompt v1 (KC + klauzule abuzywne UOKiK)
- [ ] Auth + Freemium limit (1 500 znaków)
- [ ] Stripe — jednorazowa płatność za analizę PDF
- [ ] Metryki: time-to-first-value, % powracających użytkowników

### Faza 2 — Wzrost (po osiągnięciu PMF sygnałów)
- [ ] Moduł Architect (generator umów najmu + dzieło/zlecenie)
- [ ] Subskrypcja miesięczna (19–29 zł)
- [ ] Archiwum umów w chmurze
- [ ] Eksport .docx / .pdf

### Faza 3 — Rozszerzenie
- [ ] Moduł Counter (generator kontrpropozycji + redline)
- [ ] API B2B (agencje nieruchomości, platformy freelancerskie)
- [ ] Obsługa umów z sektora finansowego (RRSO, kredyty)

---

## 9. Ryzyka i Mitygacje

| Ryzyko | Prawdopodobieństwo | Wpływ | Mitygacja |
|---|---|---|---|
| **Odpowiedzialność prawna** — AI podaje błędną interpretację, użytkownik traci pieniądze | Średnie | Wysoki | Wyraźny disclaimer „nie jest poradą prawną", scoping tylko na edukację i zwiększenie świadomości |
| **Niska willingness-to-pay** — użytkownicy oczekują darmowego narzędzia (ChatGPT efekt) | Średnie | Wysoki | Freemium hook z wyraźną wartością płatnego tier; walidacja WTP w Concierge MVP |
| **Jakość AI w prawie** — gpt-4o hallucynuje odniesienia do artykułów | Niskie | Wysoki | System prompt z konkretnymi artykułami KC, testy regresjne przykładów dla każdego modułu |
| **Fragmentacja ICP** — każdy segment wymaga innego systemu prompt | Średnie | Średni | MVP skupiony na 1 typie umowy (najem) → iteracja po walidacji |
| **Kompetycja** — duże Legal-Tech (np. LegalZoom ekspansja do PL) | Niskie | Średni | Focus na polskim rynku i lokalnym prawie — bariera wejścia dla globalnych graczy |

---

## 10. Sukces produktu — Metryki

| Metryka | Cel po 3 mies. od MVP |
|---|---|
| Registered users | ≥ 500 |
| Activation rate (analiza ≥ 1 dokumentu) | ≥ 40% |
| Retention D7 | ≥ 25% |
| Free → Paid conversion | ≥ 5% |
| NPS (willingness to recommend) | ≥ 40 |
| Avg. time-to-first-value | < 2 min |

---

## Powiązane dokumenty

- [ICP Card + Problem Matrix](./icp-clearclause.md) — pełny profil ICP, priorytety problemów, Interview Script
- `WF_Job_To_Be_Done` — szablon zbierania Job Snapshotów
- `WF_MVP_Scoping` — kolejny krok: definicja minimalnego zakresu produktu

---

*Dokument wygenerowany na podstawie konceptu ClearClause | Projekt zaliczeniowy z potencjałem komercyjnym.*
