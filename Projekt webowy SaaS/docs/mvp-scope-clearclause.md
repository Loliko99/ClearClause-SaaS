# ClearClause (JasnaUmowa) — MVP Scope
> Framework: WF_MVP_Scoping | Data: 2026-04-05
> Zasada: MVP to nie "wersja 0.1 marzenia" — to najmniejsza instancja odpowiadająca na pytanie: *„Czy ludzie zapłacą za rozwiązanie tego problemu?"*

---

## Hipoteza biznesowa do walidacji

> **„Użytkownik, który otrzymał umowę do podpisania (najmu / zlecenia), zapłaci 9–19 zł jednorazowo za analizę AI, która tłumaczy jej zapisy na ludzki język i wskazuje ryzyka — w czasie < 5 minut."**

Model: **Pay-Per-Document** (nie subskrypcja — rekomendacja z WF_Kill_The_Idea).

---

## Audyt Funkcji przez 4 Pytania WF_MVP_Scoping

### Pytanie 1: "Czy ta funkcja jest niezbędna do dostarczenia Wartości #1?"
Wartość #1 = *użytkownik rozumie ryzykowne zapisy umowy przed podpisaniem*.

| Funkcja | Niezbędna? | Decyzja |
|---|---|---|
| Wklejanie tekstu → raport AI (tłumaczenie + ryzyko + ocena) | ✅ TAK | **MUST-HAVE** |
| Upload PDF → ekstrakcja tekstu → raport | TAK, ale działa bez (paste) | Post-MVP |
| Sygnalizacja świetlna 🟢/🟡/🔴 per paragraf | ✅ TAK — bez niej użytkownik nie wie, gdzie patrzeć | **MUST-HAVE** |
| Rejestracja użytkownika | TAK — do bramkowania płatności | **MUST-HAVE** (email+hasło) |
| Płatność jednorazowa (9–19 zł/dokument) | ✅ TAK — to walidacja WTP | **MUST-HAVE** |
| Generator umów (The Architect) | NIE — osobna wartość, osobny modul | **POST-MVP** |
| Moduł negocjacji (The Counter) | NIE — zbyt złożone na start | **POST-MVP** |
| Archiwum umów w chmurze | NIE | **POST-MVP** |
| Eksport .docx / .pdf raportu | NIE — wynik na ekranie wystarczy | **POST-MVP** |
| OAuth (Google / Facebook login) | NIE | **POST-MVP** |
| Dashboard administratora | NIE | **POST-MVP** |
| Historia analiz użytkownika | NIE | **POST-MVP** |
| Dark mode / responsywne mobile UI | NIE | **Nigdy (MVP)** |

### Pytanie 2: "Czy mogę to zbudować w < 4 godziny?"

| Funkcja | Szac. czas | Hack / alternatywa |
|---|---|---|
| Formularz wklejania tekstu (textarea + submit) | 1 h | Czysty HTML/CSS + Next.js form |
| Wywołanie OpenAI API + system prompt | 2 h | `openai` npm SDK, jeden POST endpoint |
| Parsowanie odpowiedzi → strukturalny raport | 3 h | Prompt zwraca JSON (`{ translation, risks[], score }`) |
| Sygnalizacja świetlna (UI badge) | 1 h | Komponent warunkowy na score |
| Auth (email + hasło) | 2 h | Clerk (gotowy komponent, bez budowania od zera) |
| Stripe Checkout (jednorazowa płatność) | 3 h | Stripe Payment Link lub `stripe.checkout.sessions.create` |
| Bramkowanie dostępu po płatności (webhook) | 2 h | Stripe webhook → update field `hasPaidAnalysis` w DB |
| Disclaimer prawny na każdym raporcie | 0.5 h | Statyczny tekst pod raportem |
| Prosty landing page + CTA "Sprawdź swoją umowę" | 3 h | Next.js + Tailwind |
| Deploy (Vercel) | 0.5 h | `vercel deploy` |

### Pytanie 3: "Czy bez niej tracę klienta w momencie onboardingu?"

| Funkcja | Utrata klienta bez niej? |
|---|---|
| Analiza tekstu → raport | ✅ TAK — to jest produkt |
| Sygnalizacja świetlna | ✅ TAK — bez niej raport jest ścianą tekstu |
| Płatność | ✅ TAK — bez niej nie walidujemy WTP |
| Disclaimer | ✅ TAK — bez niego ryzyko prawne i reputacyjne |
| Upload PDF | ❌ NIE — paste tekstu wystarczy na MVP |
| Historia analiz | ❌ NIE |
| Generator umów | ❌ NIE |

### Pytanie 4: "Czy mogę to zwalidować BEZ budowy?"

| Hipoteza | Jak walidować bez kodu |
|---|---|
| Czy ludzie potrzebują analizy umowy? | Concierge MVP: ręczna analiza 10 umów przez email/WhatsApp |
| Czy zapłacą 9–19 zł? | Typeform z pytaniem WTP po Concierge lub "Pay to unlock" landing page |
| Czy Decoder jest czytelny? | Mockup PDF raportu → feedback od 5 osób przed budowaniem UI |

**Rekomendacja:** Przed pierwszą linią kodu — przeprowadź 7 wywiadów + Concierge MVP (opisane w `icp-clearclause.md`).

---

## 🎯 MVP Scope: ClearClause v1.0

### Target Metrics (Co walidujemy?)
- [ ] ≥ 5 użytkowników zapłaci 9–19 zł/analizę w ciągu pierwszych 2 tygodni od launchu
- [ ] Time-to-first-value < 5 minut (od wklejenia tekstu do raportu)
- [ ] Ocena zrozumiałości raportu ≥ 7/10 (ankieta po analizie)
- [ ] ≥ 1 użytkownik wraca z drugą umową w ciągu 30 dni

### Core Loop (User Journey MVP)

```
[Landing page]
    ↓ CTA: "Sprawdź swoją umowę — 9 zł"
[Rejestracja]
    ↓ Email + hasło (Clerk) — 60 sek.
[Stripe Checkout]
    ↓ Płatność 9 zł jednorazowo — 30 sek.
[Analyzer]
    ↓ Użytkownik wkleja tekst umowy lub pojedynczy paragraf
[Raport AI]
    ↓ Tłumaczenie + ryzyka + ocena 🟢/🟡/🔴 — < 30 sek.
[Disclaimer]
    ↓ "To narzędzie edukacyjne, nie zastępuje porady prawnej"
[Feedback prompt]
    "Czy raport był pomocny? (1–10)" + pole na opinię
```

---

## Tier 1 — Must-Have (0–4 tygodnie)

- [ ] **Rejestracja** — Email + hasło (Clerk), bez OAuth
- [ ] **Landing page** — 1 screen: headline + opis + CTA + przykładowy fragment raportu
- [ ] **Formularz analizy** — textarea (wklejanie tekstu umowy / paragrafu, max 3 000 znaków)
- [ ] **Core AI feature** — wywołanie OpenAI gpt-4o z system promptem prawnym → JSON response
- [ ] **Raport UI** — 3 sekcje: "Co to znaczy" / "Ryzyka" / "Ocena 🟢🟡🔴"
- [ ] **Disclaimer prawny** — na każdym raporcie, nieusuwany
- [ ] **Stripe Checkout** — jednorazowa płatność 9 zł / analiza (nie subskrypcja)
- [ ] **Webhook bramkowanie** — dostęp do raportu dopiero po potwierdzeniu płatności
- [ ] **Prosty email potwierdzający** — po płatności (SendGrid basic template)
- [ ] **Deploy** — Vercel + zmienne środowiskowe (OPENAI_API_KEY, STRIPE_SECRET, DB)

**Szacowany czas budowy Tier 1: ~40–55 godzin roboczych**

---

## Tier 2 — Should-Have (4–8 tygodni, po zebraniu feedbacku)

- [ ] Upload PDF → ekstrakcja tekstu (pdf-parse lub LangChain PDF loader)
- [ ] Historia analiz użytkownika (Supabase — tabela `analyses`)
- [ ] Analiza całego dokumentu paragraf po paragrafie (chunking + batch calls)
- [ ] OAuth (Google login) — Clerk konfiguracja
- [ ] Ekspansja systemu prompt — więcej typów umów (zlecenie, dzieło)
- [ ] Podstawowy dashboard użytkownika (lista poprzednich analiz)

---

## Tier 3 — Post-Launch / Nice-to-Have

- [ ] Generator umów — The Architect (Moduł 2)
- [ ] Moduł negocjacji — The Counter (Moduł 3)
- [ ] Eksport raportu do PDF / .docx
- [ ] Archiwum umów w chmurze
- [ ] Subskrypcja miesięczna (po walidacji powtarzalności użycia)
- [ ] API B2B (agencje nieruchomości, platformy freelancerskie)
- [ ] Mobile-responsive UI
- [ ] Multi-język (ukraiński — duża diaspora w Polsce)

---

## 🚨 Co celowo wycinamy z MVP

| Funkcja | Powód cięcia |
|---|---|
| Upload PDF | Paste tekstu wystarczy do walidacji Core Job; PDF → +20 h, ryzyko błędów OCR |
| Subskrypcja miesięczna | Sprzeczna z incydentalnym use case (WF_Kill_The_Idea: Red Flag #1) |
| Generator umów (Architect) | Osobna wartość, osobny flow — nie waliduje Core Hypothesis |
| Moduł negocjacji (Counter) | Zbyt złożony; ryzyko odpowiedzialności za treść pism |
| Historia analiz | Baza danych + UI read — zbędne przy MVP transakcyjnym |
| OAuth | +4 h, nie blokuje onboardingu |
| Dark mode | Nigdy w MVP |
| Admin dashboard | Loguj bezpośrednio do Supabase / Stripe Dashboard |
| Advanced analytics | PostHog free tier na start; custom dashboardy — Post-Launch |

---

## Mapa Techniczna — Feature Cut Table

| Funkcja | Tier | Szac. czas (h) | Cut? | Hack / Alternatywa |
|---|---|---|---|---|
| Landing page | 1 | 3 | ❌ | Next.js + Tailwind |
| Clerk Auth (email+hasło) | 1 | 2 | ❌ | Clerk SDK — bez budowania od zera |
| Textarea input + walidacja | 1 | 1 | ❌ | `maxLength=3000`, sanitizacja input |
| OpenAI API call + system prompt | 1 | 2 | ❌ | `openai` npm, jeden server action |
| JSON response parsing → raport UI | 1 | 3 | ❌ | Prompt returnuje `{ translation, risks[], score }` |
| Sygnalizacja 🟢/🟡/🔴 | 1 | 1 | ❌ | Warunkowy Tailwind badge |
| Disclaimer komponent | 1 | 0.5 | ❌ | Statyczny komponent React |
| Stripe Checkout (jednorazowy) | 1 | 3 | ❌ | `stripe.checkout.sessions.create` |
| Stripe webhook + access gating | 1 | 2 | ❌ | Supabase update po `checkout.session.completed` |
| SendGrid email potwierdzający | 1 | 1 | ❌ | Free tier, 1 template |
| Vercel deploy + env vars | 1 | 0.5 | ❌ | `vercel` CLI |
| Upload PDF | 2 | 6 | ✅ CUT | Post-MVP |
| Historia analiz (DB + UI) | 2 | 8 | ✅ CUT | Post-MVP |
| OAuth (Google) | 2 | 4 | ✅ CUT | Post-MVP |
| Generator umów | 3 | 30+ | ✅ CUT | Post-Launch |
| Moduł Counter | 3 | 25+ | ✅ CUT | Post-Launch |
| Eksport .pdf raportu | 3 | 8 | ✅ CUT | Post-Launch |
| Mobile responsive | 3 | 10 | ✅ CUT | Funkcjonalne desktop wystarczy |
| Admin dashboard | 3 | 15 | ✅ CUT | Supabase Table Editor + Stripe Dashboard |

---

## Red Lines — Czego NIE wolno ciąć z MVP

1. ✅ **Działający Decoder** — bez niego nie ma produktu
2. ✅ **Disclaimer prawny na każdym raporcie** — bez niego ryzyko odpowiedzialności
3. ✅ **Walidacja inputu** — sanitizacja tekstu przed wysłaniem do API (OWASP: injection)
4. ✅ **HTTPS + zmienne środowiskowe** — klucze API nigdy w kodzie (secret leakage)
5. ✅ **Stripe webhook secret** — weryfikacja podpisu webhooka (OWASP: integrity failure)
6. ✅ **Działająca płatność** — bez niej nie wiesz, czy ktoś zapłaci

---

## Tech Stack (Solo-Dev Optimized)

| Warstwa | Wybór | Koszt (MVP) |
|---|---|---|
| **Framework** | Next.js 14 (App Router + Server Actions) | 0 zł |
| **UI** | Tailwind CSS + shadcn/ui | 0 zł |
| **Auth** | Clerk (free tier: 10k MAU) | 0 zł |
| **AI** | OpenAI gpt-4o — API calls | ~0.10–0.30 zł/analiza |
| **Database** | Supabase (PostgreSQL, free tier) | 0 zł |
| **Płatności** | Stripe Checkout | 1.4% + 0.25 zł/transakcja |
| **Email** | SendGrid (free: 100 mails/dzień) | 0 zł |
| **Hosting** | Vercel (free tier) | 0 zł |
| **Monitoring** | PostHog free tier | 0 zł |
| **ŁĄCZNIE (stałe)** | | **~0–20 zł/mies.** |

Koszt zmienne: ~0.10–0.30 zł koszt AI per analiza. Przy cenie 9 zł/analiza → **marża ~97%**.

---

## 80/20 Question — Uproszczenia

| Zamiast... | Zrób... | Oszczędność |
|---|---|---|
| Zaawansowanego systemu ról i uprawnień | Każdy zalogowany użytkownik po płatności ma dostęp | ~15 h |
| Pięknego mobile UI | Funkcjonalny layout desktop; max-width 800px | ~10 h |
| Custom auth od zera | Clerk SDK | ~12 h |
| Parsowania PDF | Pole textarea — użytkownik wkleja tekst sam | ~8 h |
| Dashboardu admina | Supabase Table Editor / Stripe Dashboard | ~15 h |
| Zaawansowanych analityk | PostHog snippet (1 linijka) | ~20 h |

---

## Checklist Gotowości do Startu

- [ ] Całkowity czas budowy Tier 1 < 200 h → **TAK (~40–55 h)**
- [ ] ≥ 60% czasu na Core Feature → **TAK (~15 h / 55 h = ~27% — uwaga, dodać funkcje raportu)**
- [ ] Plan pozyskania 10–20 beta-testerów bez budżetu → **TAK (grupy FB Wynajem, Reddit, znajomi freelancerzy)**
- [ ] Produkt w 1 zdaniu → **„Wklej fragment swojej umowy — AI wyjaśni Ci w 30 sekund, czy możesz to bezpiecznie podpisać."**
- [ ] Wiem, za co ludzie zapłacą → **9–19 zł jednorazowo za analizę dokumentu**
- [ ] Plan B jeśli hipoteza nie potwierdzona → **Pivot na B2B API (agencje nieruchomości); lub pivot na generator umów jako core**

---

## Procedura Monitorowania Post-Launch

| Metryka | Jak mierzyć | Próg „idź dalej" |
|---|---|---|
| **Time-to-first-value** | PostHog: czas od rejestracji do wygenerowanego raportu | < 5 min |
| **Konwersja (landing → płatność)** | Stripe + PostHog funnel | ≥ 3% |
| **Ocena raportu** | In-app: „Czy raport był pomocny? 1–10" | ≥ 7/10 |
| **Powracający użytkownicy (30 dni)** | Supabase: `COUNT(analyses) WHERE user = X AND days_since_first < 30` | ≥ 15% |
| **Support load** | Liczba emaili/tydzień wymagających odpowiedzi | < 2/tydzień |
| **Churn transakcyjny** | Brak zakupu drugiej analizy przez użytkownika | Mierz, nie optymalizuj na MVP |

**Decyzja:**
- Metryki zielone → Dodaj Tier 2 (PDF upload, historia), rozważ pakiet 3 analiz za 20 zł
- Konwersja < 1% → Zmień messaging na landing page lub cenę
- Ocena < 5/10 → Iteruj system prompt (jakość raportu), nie UI

---

## Powiązane dokumenty

- [Product Brief](./product-brief-clearclause.md) — koncepcja, moduły, model biznesowy
- [ICP + Problem Matrix](./icp-clearclause.md) — profil klienta, priorytety problemów, Interview Script
- [Kill-the-Idea Audit](./kill-the-idea-clearclause.md) — ryzyka, Red Flags, rekomendacja Pay-Per-Doc

---

*Dokument wygenerowany wg procedury `WF_MVP_Scoping` | ClearClause Pre-MVP | 2026-04-05*
