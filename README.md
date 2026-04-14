
# ClearClause (JasnaUmowa) — Master README
> Projekt zaliczeniowy z potencjałem komercyjnym | Legal-Tech / AI Utility SaaS | Stan: Pre-MVP | Data: 2026-04-05

---

## Spis treści

1. [Opis projektu](#1-opis-projektu)
2. [Struktura repozytorium](#2-struktura-repozytorium)
3. [Produkt — koncepcja i moduły](#3-produkt--koncepcja-i-moduły)
4. [ICP — Idealny Klient i Problem Matrix](#4-icp--idealny-klient-i-problem-matrix)
5. [Pre-Mortem Audit (Kill-the-Idea)](#5-pre-mortem-audit-kill-the-idea)
6. [MVP Scope](#6-mvp-scope)
7. [User Journey Map](#7-user-journey-map)
8. [Tech Stack](#8-tech-stack)
9. [Workflowy metodologiczne](#9-workflowy-metodologiczne)
10. [Roadmap](#10-roadmap)
11. [Metryki sukcesu](#11-metryki-sukcesu)

---

## 1. Opis projektu

**ClearClause** to inteligentny tłumacz i asystent umów, który niweluje asymetrię wiedzy między instytucjami (banki, korporacje, wynajmujący) a zwykłym obywatelem.

> **1-liner:** *„ClearClause tłumaczy żargon prawniczy na ludzki język i generuje bezpieczne umowy dla osób bez wykształcenia prawniczego."*

**Problem:** Przeciętna osoba podpisuje umowę najmu, zlecenia lub pożyczki „na wiarę" — nie rozumie legalese, a prawnik kosztuje 600–1 500 zł/godz.

**Rozwiązanie:** AI z zaszytymi instrukcjami opartymi na polskim prawie cywilnym (KC, UOPK, UOKK, rejestr klauzul abuzywnych UOKiK) analizuje umowy, wskazuje ryzyka i pomaga użytkownikowi działać — bez znajomości prawa.

**Model biznesowy:** Pay-Per-Document — 9 zł / jednorazowa analiza (nie subskrypcja).

---

## 2. Struktura repozytorium

```
Projekt webowy SaaS/
│
├── README.md                          ← Ten plik — master dokumentacja projektu
│
├── docs/                              ← Dokumentacja analityczna ClearClause
│   ├── Perosonalizacja                ← ICP Card + Problem Matrix
│   ├── product-brief-clearclause.md  ← Product Brief (koncepcja, moduły, model biz.)
│   ├── kill-the-idea-clearclause.md  ← Pre-Mortem Audit (5 filtrów, ryzyka, werdykt)
│   ├── mvp-scope-clearclause.md      ← MVP Scope (funkcje, tier, tech stack, czas)
│   └── user-journey-clearclause.md   ← User Journey Map (7 stadiów, Aha Moment)
│
└── kilocode/
    └── workflows/                     ← Workflowy metodologiczne (szablony)
        ├── README.md                  ← Metodologia Architekta SaaS
        ├── icp-persona.md             ← WF_ICP_Persona
        ├── job-to-be-done.md          ← WF_Job_To_Be_Done
        ├── kill-the-idea.md           ← WF_Kill_The_Idea
        ├── mvp-scope.md               ← WF_MVP_Scoping
        ├── Tech_Stack_Audit.md        ← WF_Tech_Stack_Audit
        └── User_Journey_Map           ← WF_User_Journey_Map
```

---

## 3. Produkt — koncepcja i moduły

> Źródło: [docs/product-brief-clearclause.md](docs/product-brief-clearclause.md)

### Trzy moduły produktu

| Moduł | Nazwa | Opis | Status |
|---|---|---|---|
| **Moduł 1** | The Decoder (Analiza) | Wklej paragraf → AI generuje: tłumaczenie + ryzyka + ocena 🟢/🟡/🔴 | ✅ MVP v1 |
| **Moduł 2** | The Architect (Kreacja) | Interaktywny generator umów przez wywiad AI | ⏳ Post-MVP |
| **Moduł 3** | The Counter (Negocjacja) | Generator kontrpropozycji + gotowy e-mail do drugiej strony | ⏳ Post-Launch |

### Decoder — struktura raportu

```
┌─────────────────────────────────────────────────────┐
│  📖 CO TO OZNACZA?      Tłumaczenie w 3 zdaniach    │
│  ⚠️ RYZYKA I HACZYKI   🔴🟡 lista konkretnych ryzyk │
│  🛡️ OCENA              ██████░░░░  4/10 🔴           │
│  ⚠️ Disclaimer         "Narzędzie edukacyjne..."     │
└─────────────────────────────────────────────────────┘
```

### Grupy docelowe

| Segment | Priorytet |
|---|---|
| Najemcy i wynajmujący (umowy najmu) | ⭐⭐⭐ Core |
| Pracownicy / zleceniobiorcy (UoP, B2B, dzieło) | ⭐⭐⭐ Core |
| Klienci instytucji finansowych (kredyty, pożyczki) | ⭐⭐ Secondary |
| Konsumenci (regulaminy, reklamacje) | ⭐ Later |

### Przewaga vs. ChatGPT

| Cecha | ChatGPT | ClearClause |
|---|---|---|
| Polskie prawo | Ogólna wiedza | System prompt z KC, UOKiK, UOPK |
| Kontekst | Użytkownik musi wiedzieć, o co pytać | System sam skanuje klauzule abuzywne |
| UX | Odpowiedź tekstowa | Strukturalny raport z oceną |
| Koszt | ~80 zł/mies. | 9 zł/analiza |

---

## 4. ICP — Idealny Klient i Problem Matrix

> Źródło: [docs/Perosonalizacja](docs/Perosonalizacja)

### ICP Card

| Pole | Opis |
|---|---|
| **Kto** | Młodzi dorośli (18–30 lat), studenci wynajmujący mieszkanie, freelancerzy (graficy, copywriterzy), osoby zaciągające pożyczki konsumenckie. Brak wykształcenia prawniczego, dochód 0–5 000 zł netto/mies. |
| **Co (Main Job)** | Podpisać umowę szybko i pewnie — bez ryzyka, że ukryty zapis wpędzi ich w kłopoty finansowe |
| **Ból** | Nie rozumieją paragrafów, boją się eksmisji i ukrytych kar, a na prawnika ich nie stać |
| **Decision Criteria** | Szybkie (< 5 min), zrozumiałe, tanie (9 zł), z wiarygodnego źródła |
| **Trigger** | Otrzymuje PDF umowy z 24–72 godz. na decyzję |

### Problem Matrix (Priority = Impact × Confidence × Ease)

| # | Problem | Impact | Confidence | Ease | **Priority** |
|---|---|---|---|---|---|
| 1 | Niezrozumienie kar umownych | 9 | 8 | 9 | **648** ⭐ Core |
| 2 | Lęk przed eksmisją (warunki wypowiedzenia) | 9 | 7 | 8 | **504** |
| 3 | Ukryte koszty kredytu / pożyczki (RRSO) | 8 | 8 | 7 | **448** |
| 4 | Prawa freelancera w umowie o dzieło (IP) | 8 | 6 | 8 | **384** |
| 5 | Brak bezpiecznego szablonu umowy | 7 | 6 | 7 | **294** |

**Core Problem do testu:** #1 — Kary umowne (Priority 648, Ease 9 → najłatwiej testować demo „wklej paragraf").

### Interview Script (7 pytań)

1. „Opowiedz o ostatnim razie, kiedy miałeś/aś umowę do podpisania — co to była za sytuacja?"
2. „Co dokładnie zrobiłeś/aś zanim ją podpisałeś/aś? Krok po kroku."
3. „Który fragment był najbardziej niejasny lub niepokojący?"
4. „Jak wyobrażasz sobie idealne podpisanie umowy? Po czym poznasz, że jest ok?"
5. „Ile czasu zajęło Ci zrozumienie tej umowy? Czy rezygnowałeś/aś z czegoś przez zawiłą umowę?"
6. „Gdyby aplikacja tłumaczyła całą umowę w 5 minut — ile byłbyś/abyś w stanie za nią zapłacić?"
7. „Czy próbowałeś/aś czegoś podobnego? ChatGPT, porady online? Co nie zadziałało?"

### Concierge MVP

```
[Użytkownik] → przesyła PDF umowy na WhatsApp/email/Typeform
      ↓
[Ty ręcznie] → analizujesz, opisujesz ryzyka (30–60 min)
      ↓
[Dostarczasz] → raport bullet list: "§3 znaczy X, ryzyko Y, kara Z zł"
      ↓
[Pytasz] → "Czy to było pomocne? Za ile byś to kupił/a?"
```

Sygnał minimalny: WTP > 0 zł u ≥ 60% testerów → buduj MVP.

---

## 5. Pre-Mortem Audit (Kill-the-Idea)

> Źródło: [docs/kill-the-idea-clearclause.md](docs/kill-the-idea-clearclause.md)

### Wyniki 5 Zabójczych Filtrów

| Filtr | Diagnoza | Status |
|---|---|---|
| Distribution Hell | CAC może przekroczyć LTV przy subskrypcji; jedyny bezpieczny kanał = organika (6–12 mies.) | ⚠️ ŻÓŁTA FLAGA |
| Feature, Not a Product | ChatGPT/Claude obsługuje 80% use case'u za darmo; moat technologiczny cienki | 🚩 CZERWONA FLAGA |
| Support Trap | Legal-Tech = ryzyko odpowiedzialności za błąd AI; jeden viralowy post może zniszczyć produkt | 🚩 CZERWONA FLAGA |
| Nice-to-Have Vitamin | Painkiller przy triggerze (umowa jutro), witamina bez triggera | 💊 WARUNKOWO |
| Zero-Moat | Wersję MVP można skopiować w 1–2 dni; system prompt + UX to jedyne bariery | ⚠️ ŻÓŁTA FLAGA |

### 🚩 Trzy Krytyczne Red Flags

1. **Model subskrypcyjny sprzeczny z incydentalnym use case** — churn 60–80% po 2–3 miesiącach
2. **Ryzyko odpowiedzialności prawnej** — disclaimer nie chroni przed reputacyjnym zniszczeniem
3. **Substytucja przez bezpłatne LLM** — ChatGPT Plus (80 zł/mies.) robi 80% tego samego

### Werdykt

> ## ⚠️ PROCEED WITH CAUTION — po zmianie modelu biznesowego

### Trzy Pivoty

| Pivot | Opis | Rekomendacja |
|---|---|---|
| **Pay-Per-Document** | 9–19 zł / jednorazowa analiza zamiast subskrypcji | ✅ **Rekomendowany** |
| **Wąska nisza: tylko najem** | Focus na umowach najmu + partnerstwo z OLX/Otodom | ✅ Równoległy |
| **B2B API** | Sprzedaj agencjom nieruchomości / platformom freelancerskim | ⏳ Post-PMF |

---

## 6. MVP Scope

> Źródło: [docs/mvp-scope-clearclause.md](docs/mvp-scope-clearclause.md)

### Hipoteza biznesowa

> *„Użytkownik z umową do podpisania zapłaci 9 zł jednorazowo za analizę AI tłumaczącą zapisy na ludzki język — w czasie < 5 minut."*

### Core Loop

```
Landing page → Rejestracja (2 pola) → Stripe Checkout (9 zł)
    → Textarea (wklej paragraf) → AI raport (< 30 sek.) → Disclaimer
```

### Tier 1 — Must-Have (~40–55 godz. budowy)

| Funkcja | Czas | Narzędzie |
|---|---|---|
| Landing page + CTA | 3 h | Next.js + Tailwind |
| Rejestracja (email + hasło) | 2 h | Clerk SDK |
| Textarea + walidacja (max 3 000 znaków) | 1 h | React form |
| OpenAI API call + system prompt prawny | 2 h | `openai` npm |
| Raport UI (3 sekcje + 🟢/🟡/🔴) | 3 h | shadcn/ui components |
| Disclaimer prawny (statyczny) | 0.5 h | React komponent |
| Stripe Checkout jednorazowy (9 zł) | 3 h | `stripe.checkout.sessions.create` |
| Webhook bramkujący dostęp | 2 h | Stripe webhook + Supabase update |
| Email potwierdzający | 1 h | SendGrid free tier |
| Deploy Vercel | 0.5 h | `vercel deploy` |

### Tier 2 — Post-feedback (4–8 tyg.)
Upload PDF, historia analiz, OAuth Google, analiza całego dokumentu (chunking).

### Tier 3 — Post-Launch
Generator umów (Architect), moduł negocjacji (Counter), eksport .docx/.pdf, B2B API.

### Co celowo wycinamy

| Funkcja | Powód |
|---|---|
| Upload PDF | Paste wystarczy na MVP; oszczędność ~8 h |
| Subskrypcja | Sprzeczna z incydentalnym use case |
| Generator umów | Osobna hipoteza, osobny flow |
| Moduł Counter | Zbyt złożony + ryzyko odpowiedzialności |
| OAuth, dark mode, admin panel | Tier 2/3 |

### Red Lines — czego NIE wolno ciąć

- ✅ Działający Decoder (bez tego nie ma produktu)
- ✅ Disclaimer prawny na każdym raporcie
- ✅ Walidacja + sanitizacja inputu (OWASP: injection)
- ✅ HTTPS + klucze API w zmiennych środowiskowych
- ✅ Weryfikacja podpisu webhooka Stripe
- ✅ Działająca płatność (bez niej nie walidujemy WTP)

---

## 7. User Journey Map

> Źródło: [docs/user-journey-clearclause.md](docs/user-journey-clearclause.md)

### Success Metric

> *„Użytkownik uzna ClearClause za warte 9 zł, jeśli w ciągu 3 minut od wklejenia tekstu umowy otrzyma raport wskazujący konkretny ryzykowny zapis."*

### 7 Stadiów Journey

| Stage | Czas | Aha Moment | Główny Friction Point |
|---|---|---|---|
| 1. Landing | 0–30 sek. | „To dokładnie moja sytuacja" | Ogólny headline, brak demo raportu → **P0** |
| 2. Sign-Up | 1–2 min | Widzi textarea — wie co robić | Potwierdzenie emaila przed płatnością → **P0** |
| 3. Data Input | 2–4 min | System akceptuje tekst | Użytkownik nie wie, co wkleić (ma PDF) → P1 |
| 4. Processing | 5–15 sek. | Progress bar — „coś się dzieje" | Biały ekran bez komunikatu → P2 |
| 5. Output ⭐ | < 30 sek. | „Nie wiedziałam — zadzwonię do wynajmującego" | Raport = ściana tekstu → **P0** |
| 6. Second Action | 1–3 dni | Wraca samodzielnie | Brak personalizowanego emaila → P2 |
| 7. Repeat Purchase | 30 dni | „9 zł za spokój ducha to tanio" | Ponowne wpisywanie karty → P2 |

### Total Time: Landing → Aha Moment

```
Landing (30 sek.) + Sign-Up (60 sek.) + Stripe (45 sek.)
    + Wklejanie (60 sek.) + AI Processing (10 sek.)
= ~2–4 minuty ✅ (cel: < 5 min — SPEŁNIONY)
```

### 5 Quick Wins (< 4 godz. każdy)

1. Sytuacyjny headline: „Dostałeś umowę do podpisania? Sprawdź ją zanim złożysz podpis — 9 zł, wynik w 30 sekund"
2. Statyczny przykład raportu na landing page (użytkownik widzi produkt przed zakupem)
3. Aktywacja BLIK w Stripe (dominująca metoda płatności 18–30 lat w Polsce)
4. Placeholder w textarea z konkretnym przykładowym paragrafem
5. Ocena in-app po raporcie: `Czy raport był pomocny? 👍 👎`

### Biggest Friction Point

> **Jakość raportu AI** — jeśli nieodróżnialna od „wklejenia do ChatGPT", użytkownik nie wróci i zostawi negatywną recenzję. Jakość systemu promptu = jedyny prawdziwy moat.

---

## 8. Tech Stack

> Źródło: [kilocode/workflows/Tech_Stack_Audit.md](kilocode/workflows/Tech_Stack_Audit.md)

### Stack (Solo-Dev Optimized, budżet $0–20/mies.)

| Warstwa | Technologia | Koszt MVP |
|---|---|---|
| Framework | Next.js 14 (App Router + Server Actions) | 0 zł |
| UI | Tailwind CSS + shadcn/ui | 0 zł |
| Auth | Clerk (free: 10k MAU) | 0 zł |
| AI | OpenAI gpt-4o API | ~0.10–0.30 zł/analiza |
| Database | Supabase PostgreSQL (free tier) | 0 zł |
| Płatności | Stripe Checkout + BLIK | 1.4% + 0.25 zł/transakcja |
| Email | SendGrid (free: 100/dzień) | 0 zł |
| Hosting | Vercel (free tier) | 0 zł |
| Monitoring | PostHog (free tier) | 0 zł |
| **ŁĄCZNIE (stałe)** | | **~0–20 zł/mies.** |

**Marża:** koszt AI 0.10–0.30 zł przy cenie 9 zł = **~97% marży brutto**.

### Zasada Tech Stack

> *„Najlepszy stack to ten, który pozwala uruchomić MVP w 4–8 tygodniach — nie ten, który jest najmodniejszy."*

---

## 9. Workflowy metodologiczne

> Źródło: [kilocode/workflows/](kilocode/workflows/)

Projekt zbudowany w oparciu o metodologię Architekta SaaS dla Solo-Deveów. Każdy workflow to powtarzalna procedura do uruchamiania na nowym pomyśle.

| Workflow | Plik | Zastosowanie w ClearClause |
|---|---|---|
| **WF_ICP_Persona** | [icp-persona.md](kilocode/workflows/icp-persona.md) | → [docs/Perosonalizacja](docs/Perosonalizacja) |
| **WF_Job_To_Be_Done** | [job-to-be-done.md](kilocode/workflows/job-to-be-done.md) | → sekcja JTBD w product-brief |
| **WF_Kill_The_Idea** | [kill-the-idea.md](kilocode/workflows/kill-the-idea.md) | → [docs/kill-the-idea-clearclause.md](docs/kill-the-idea-clearclause.md) |
| **WF_MVP_Scoping** | [mvp-scope.md](kilocode/workflows/mvp-scope.md) | → [docs/mvp-scope-clearclause.md](docs/mvp-scope-clearclause.md) |
| **WF_Tech_Stack_Audit** | [Tech_Stack_Audit.md](kilocode/workflows/Tech_Stack_Audit.md) | → sekcja Tech Stack |
| **WF_User_Journey_Map** | [User_Journey_Map](kilocode/workflows/User_Journey_Map) | → [docs/user-journey-clearclause.md](docs/user-journey-clearclause.md) |

### Kolejność uruchamiania workflowów

```
WF_ICP_Persona → WF_Job_To_Be_Done → WF_Kill_The_Idea
    → WF_MVP_Scoping → WF_Tech_Stack_Audit → WF_User_Journey_Map
```

---

## 10. Roadmap

### Faza 0 — Walidacja (teraz, 0–4 tyg. przed kodem)

- [ ] Concierge MVP: ręczna analiza 10 umów dla testerów (Typeform/email)
- [ ] 7 wywiadów z segmentem core (studenci, freelancerzy)
- [ ] Landing page z pre-signup (mierz: CTR → signup → WTP)
- [ ] **Cel:** WTP > 0 u ≥ 60% testerów → sygnał do budowania

### Faza 1 — MVP Decoder (4–8 tyg.)

- [ ] Rejestracja Clerk + Stripe Pay-Per-Doc (9 zł)
- [ ] Moduł Decoder: textarea → OpenAI → raport 3-sekcyjny
- [ ] System prompt v1 (KC + klauzule abuzywne UOKiK)
- [ ] BLIK w Stripe
- [ ] Deploy Vercel + PostHog
- [ ] **Cel:** 5 płatnych analiz w 2 tyg. od launchu

### Faza 2 — Wzrost (po sygnałach PMF)

- [ ] Upload PDF (pdf-parse / LangChain)
- [ ] Historia analiz (Supabase)
- [ ] Pakiet 3 analiz za 20 zł
- [ ] Rozszerzenie systemu prompt (zlecenie, dzieło, pożyczka)
- [ ] SEO content (blog „co oznacza klauzula X")

### Faza 3 — Rozszerzenie

- [ ] Moduł Architect (generator umów)
- [ ] Moduł Counter (kontrpropozycje)
- [ ] API B2B (agencje nieruchomości, platformy freelancerskie)
- [ ] Subskrypcja (dopiero po walidacji powtarzalności)

---

## 11. Metryki sukcesu

### Walidacja (Faza 0)

| Metryka | Cel |
|---|---|
| Umowy przesłane w Concierge MVP | ≥ 5 w 72 godz. |
| Ocena zrozumiałości raportu | ≥ 7/10 |
| WTP > 0 zł | ≥ 60% testerów |
| Zmiana decyzji po raporcie | ≥ 3/5 wskazuje zmianę |

### MVP (Faza 1 — po 3 miesiącach)

| Metryka | Cel |
|---|---|
| Registered users | ≥ 500 |
| Landing → Płatność | ≥ 3% |
| Time-to-first-value | < 5 min |
| Ocena raportu (in-app) | ≥ 7/10 |
| Return Rate Day 3 | ≥ 25% |
| Repeat Purchase (30 dni) | ≥ 15% |
| Support tickets / tydzień | < 2 |
| NPS | ≥ 40 |

---

## Ryzyki kluczowe (podsumowanie)

| Ryzyko | Poziom | Mitygacja |
|---|---|---|
| Substytucja przez ChatGPT/Claude | 🚩 Krytyczne | Jakość systemu prompt > UX; focus na PL-specyficzne prawo |
| Model subskrypcyjny → churn | 🚩 Krytyczne | Pay-Per-Doc jako default |
| Odpowiedzialność prawna za błąd AI | 🚩 Krytyczne | Disclaimer na każdym raporcie; język edukacyjny, nie poradniczy |
| Niska jakość raportu | 🔴 Wysokie | Testy systemu promptu przed launchu; iteracja po feedbacku |
| Brak ruchu organicznego | ⚠️ Średnie | Content SEO + grupy FB + partnerstwa (OLX, Useme) |

---

*Projekt ClearClause (JasnaUmowa) — dokumentacja wygenerowana na podstawie workflowów WF_ICP_Persona, WF_Job_To_Be_Done, WF_Kill_The_Idea, WF_MVP_Scoping, WF_Tech_Stack_Audit, WF_User_Journey_Map.*
