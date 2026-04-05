# ClearClause — WF_Kill_The_Idea (Pre-Mortem Audit)
> Framework: Sceptyczny Inwestor / 5 Zabójczych Filtrów | Data: 2026-04-05
> Domyślne założenie: *„Ten projekt upadnie w ciągu 6 miesięcy."*

---

## Analiza przez 5 Zabójczych Filtrów

---

### Filtr 1 — Distribution Hell (Piekło Dystrybucji)
**Pytanie:** Czy dotarcie do klienta będzie droższe niż zysk z subskrypcji?

**Diagnoza: ⚠️ ŻÓŁTA FLAGA**

Target — młodzi dorośli 18–30 lat, studenci, freelancerzy — to jeden z **najtrudniejszych do monetyzacji segmentów w polskim internecie**. Oto dlaczego:

- **Nieodczuwalna potrzeba w trybie pasywnym:** Użytkownik nie szuka „analizatora umów" regularnie. Trigger jest incydentalny (dostaje umowę raz na 12–18 mies.). To oznacza dramatycznie **niski organiczny intent w SEO i SEM** — frazy w rodzaju „co oznacza §12 umowy najmu" mają niski CPC, ale też niski wolumen transakcyjny.
- **CAC vs. LTV:** Przy cenie 19–29 zł/mies. i zakładanym churn 15–25%/mies. dla niszowego narzędzia, **LTV wynosi ~80–150 zł/użytkownik**. Jeśli Google Ads kosztuje 5–15 zł CPC w niszach „umowa najmu" lub „pożyczka konsumencka", a konwersja na płatnego użytkownika to 1–3%, **CAC może wynosić 150–500 zł** — przekraczając LTV.
- **Jedyny bezpieczny kanał to dystrybucja organiczna:** Grupy FB (Wynajem Mieszkań, Freelancerzy PL), TikTok/Reels z case studies „co ryzykujesz podpisując tę klauzulę", SEO contentowy (blogi + FAQ). Są tanie, ale **wolne** — 6–12 mies. do osiągnięcia krytycznej masy ruchu.

**Konkrety pytania:** Jak zamierzasz dotrzeć do użytkownika BEZ budżetu reklamowego, zanim ruch organiczny się nakręci?

---

### Filtr 2 — Feature, Not a Product (To tylko funkcja)
**Pytanie:** Czy ChatGPT / Google / Microsoft może to skopiować w jednym updacie?

**Diagnoza: 🚩 CZERWONA FLAGA**

To najpoważniejsze ryzyko egzystencjalne dla ClearClause.

- **OpenAI już to robi:** GPT-4o z Custom Instructions i GPTs pozwala każdemu stworzyć własną „wersję ClearClause" w 20 minut. Bariera wejścia dla użytkownika technicznego = zero. ChatGPT Plus kosztuje ~80 zł/mies. i robi 80% tego, co ClearClause (analizuje tekst, tłumaczy paragrafy).
- **Google NotebookLM:** Pozwala „pytać" dokument PDF. Bezpłatny. Coraz lepszy w dłuższych dokumentach.
- **Claude.ai:** Kontekstowe okno 200K tokenów — przeanalizuje całą 50-stronicową umowę naraz, bezpłatnie lub za ~80 zł/mies.
- **Ryzyko platform:** Jeśli OpenAI lub Anthropic uruchomi specjalizowane „Legal Assistant" jako wbudowaną funkcję (roadmap Q3–Q4 2026), cały produkt traci rację bytu overnight.

**Gdzie ClearClause NIE jest tylko funkcją (jedyne prawdziwe moaty):**
1. System prompt z rejestrem klauzul abuzywnych UOKiK (aktualizowany)
2. UX dopasowany do laika (nie wymaga wiedzy „co wkleić" — ogólne LLM wymagają)
3. Moduł Counter — generator kontrpropozycji z gotowym mailem (flow product-specific)

Ale te moaty są **cienkie** — wymagają ciągłej rozbudowy, żeby utrzymać przewagę.

---

### Filtr 3 — The Support Trap (Pułapka Wsparcia)
**Pytanie:** Czy produkt wygeneruje tsunami supportu, które zabije Solo-Deva?

**Diagnoza: 🚩 CZERWONA FLAGA (potencjalnie)**

Legal-Tech to **kategoria wysokiego ryzyka odpowiedzialności i zaufania**. Scenariusze supportowe:

- Użytkownik: *„Twoja aplikacja napisała, że klauzula jest bezpieczna, a wynajmujący właśnie zatrzymał mi kaucję — co teraz?"* → Żądanie odszkodowania, negatywna recenzja, potencjalny pozew.
- Użytkownik: *„Wygenerowałeś mi umowę, a okazało się, że zapis jest nieważny prawnie — co robić?"* → Odpowiedzialność za błędy AI w dokumencie prawnym.
- Użytkownik: *„AI napisało mi maila do banku z niepoprawnym odwołaniem do artykułu KC"* → Podobny scenariusz.

Każda firma Legal-Tech (nawet Rocket Lawyer, DocuSign) ma **armie prawników** do zarządzania tym ryzykiem. Solo-Dev nie ma.

**Mitygacja możliwa, ale wymagająca:**
- Disclaimer na każdym raporcie: „To nie jest porada prawna — narzędzie edukacyjne"
- Ograniczone sformułowania w module Counter (wskazówki, nie „oficjalne pisma prawne")
- Nie: „Ta klauzula jest nieważna". Tak: „Ta klauzula może budzić wątpliwości — porównaj z art. 385¹ KC i zapytaj prawnika"

**Ale disclaimer nie eliminuje ryzyka reputacyjnego** — jeden viralowy post „straciłem 3000 zł przez ClearClause" może zniszczyć produkt.

---

### Filtr 4 — The "Nice-to-Have" Vitamin
**Pytanie:** Czy to krwawiący ból (painkiller) czy witamina?

**Diagnoza: 💊 WITAMINA Z POTENCJAŁEM NA PAINKILLER**

Zależy od segmentu i momentu:

| Segment | Moment | Klasyfikacja |
|---|---|---|
| Student z umową najmu, jutro deadline | Trigger incydentalny, wysoka palącość | ✅ **Painkiller** |
| Freelancer z umową B2B (IP, zakaz konkurencji) | Trigger incydentalny, wysoka stawka finansowa | ✅ **Painkiller** |
| Osoba podpisująca kredyt | Incydentalny, ale decyzja wieloletnia | ✅ **Painkiller** |
| Użytkownik subskrypcji miesięcznej bez aktywnej umowy | Brak triggera | ❌ **Witamina** — **wysoce churnowalny** |

**Kluczowy problem:** Użytkownik potrzebuje produktu intensywnie przez 48 godzin, a potem **przez rok go nie potrzebuje**. To model „jednorazowy", nie „sticky SaaS". Subskrypcja miesięczna jest fundamentalnie sprzeczna z naturą problemu — użytkownicy zasubskrybują, użyją raz i odejdą.

**To jest strukturalny problem modelu biznesowego** — patrz Red Flags.

---

### Filtr 5 — Zero-Moat (Brak barier wejścia)
**Pytanie:** Czy ktoś może skopiować to w weekend?

**Diagnoza: ⚠️ ŻÓŁTA FLAGA**

- Wersja MVPv0 (wklej tekst → GPT API → raport) można zbudować w 1–2 dni. Technologia = zero barier.
- System prompt z polskim prawem nie jest „sekretny" — każdy copywriter z prawniczymi podstawami może go odtworzyć w tydzień.

**Rzeczywiste bariery (słabe, ale istniejące):**
1. **Jakość systemu prompt + rejestr klauzul abuzywnych** — wymagają ekspertyzy prawnej do budowy i aktualizacji. Zatrudnienie prawnika to koszt, nie każdy kopiujący to zrobi.
2. **Reputacja i trust** — w Legal-Tech recenzje i zaufanie marki budują się latami. Pierwszy niszowy gracz z dobrym NPS ma szansę na bycie „domyślnym wyborem".
3. **Dystrybucja** — kto pierwszy zbierze SEO i społeczność (grupy FB, poradniki), ten blokuje ruch.

---

## Raport Audytowy

---

### 🚩 RED FLAGS — Krytyczne

**1. Model subskrypcyjny sprzeczny z naturą problemu (Vitamin Trap)**
Umowy podpisuje się rzadko. Użytkownik, który zapłaci 19 zł/mies., w miesiąc po rejestracji zada pytanie: *„Po co mi ta subskrypcja, skoro nie mam teraz żadnej umowy?"*. Przewidywany churn po 2–3 miesiącach: 60–80%. Przy LTV 40–60 zł i jakimkolwiek CAC > 0, model jest deficytowy.

**2. Ryzyko odpowiedzialności prawnej i reputacyjnej (Single Bad Review Risk)**
Jeden błąd AI w interpretacji prawa, jeden użytkownik, który „poszedł za radą ClearClause i stracił", jeden viralowy post — i produkt jest martwy. W Legal-Tech disclaimer „nie jest poradą prawną" nie chroni przed reputacyjnym zniszczeniem. Solo-Dev nie ma zasobów na zarządzanie tym kryzysem.

**3. Substytucja przez bezpłatne LLM (Existential Platform Risk)**
ChatGPT, Claude, Gemini — wszystkie modele generalistyczne obsługują już 80% use case'u ClearClause za ~0–80 zł/mies. (cena ChatGPT Plus). Użytkownik, który raz sprawdzi umowę przez Claude.ai, nie zobaczy powodu, żeby płacić extra za ClearClause.

---

### ⚠️ YELLOW FLAGS — Ostrzegawcze

**4. Incydentalny intent = brak retention bez zmiany modelu**
SEO będzie działał (użytkownik googla „co oznacza klauzula X"), ale konwersja na subskrybenta będzie dramatycznie niska, bo po rozwiązaniu bieżącego problemu użytkownik znika.

**5. Wysokie koszty utrzymania jakości (Legal Ops)**
Rejestr klauzul abuzywnych UOKiK ulega zmianom. Polskie prawo się aktualizuje. Utrzymanie aktualności systemu prompta wymaga regularnych przeglądów przez osobę z wiedzą prawniczą — koszt, którego Solo-Dev nie pokryje z przychodów MVP.

**6. Fragment rynku, nie platforma**
Umowa najmu, umowa o dzieło, pożyczka — każdy typ wymaga osobnego kontekstu prawnego. Budowanie jednego spójnego produktu dla wszystkich segmentów jednocześnie = rozproszenie, które zabija jakość.

---

### 💀 The Death Scenario

**Miesiąc 1–2:** Solo-Dev buduje MVP (Decoder). Pierwsze 50–100 użytkowników z grup FB i Reddita. Feedback pozytywny, NPS wysoki. 15–20 płatnych subskrybentów.

**Miesiąc 3:** Churn uderza. 70% użytkowników z pierwszej kohorty odchodzi — mieli jedną umowę, przeanalizowali, nie potrzebują już narzędzia. Przychód nie rośnie bo nowych użytkowników brak (brak budżetu na ads, SEO potrzebuje 6–9 mies.).

**Miesiąc 4:** Użytkownik publikuje post na Reddicie: *„ClearClause napisało mi, że klauzula jest ok, a okazała się abuzywna — straciłem depozyt."* Negatywny PR. Nowe rejestracje spadają.

**Miesiąc 5:** OpenAI ogłasza „Legal Assistant" w ChatGPT (hipoteza, ale realne ryzyko na horyzoncie 12 mies.). Tech press pisze „po co płacić za ClearClause, skoro GPT robi to samo?". Traffic i konwersja spada o 60%.

**Miesiąc 6:** Przychód MRR: 200–400 zł. Koszty: OpenAI API (~150 zł) + Vercel (~50 zł) + Stripe fees + czas. Projektu nie opłaca się dalej prowadzić. Zamknięcie.

---

### 📉 Verdict

> ## ⚠️ PROCEED WITH CAUTION — po obowiązkowym Pivotcie modelu biznesowego

Pomysł jest **solidny problemowo** (realny ból, realna asymetria wiedzy, duży rynek) ale **słaby modelowo** (subskrypcja sprzeczna z incydentalnym use case'em, ryzyko odpowiedzialności, cienki moat technologiczny).

**Produkt NIE powinien być zabity** — ale wymaga zmiany 2 fundamentów przed startem.

---

## Procedura Wyjścia — Pivot Suggestions

### Pivot 1 (Rekomendowany) — Model Pay-Per-Document zamiast subskrypcji

Zamiast 19–29 zł/mies., sprzedaj **jednorazową analizę dokumentu za 9–19 zł**. Dlaczego to działa lepiej:
- Dopasowane do incydentalnego triggera — użytkownik płaci wtedy, kiedy ma problem
- Brak churnu (model transakcyjny, nie subskrypcyjny)
- Łatwiejszy „impuls zakupowy" — zapłać teraz, korzystaj teraz
- LTV budowany na powtarzalnych zakupach (1–3 x rok, przy różnych umowach)

### Pivot 2 — Wąska nisza: tylko umowy najmu, tylko Polska, tylko B2C

Zamiast „wszystkich umów", zostań **#1 narzędziem dla najemców mieszkań w Polsce**. Korzyści:
- Mniejszy zakres systemu prompta → niższe koszty utrzymania prawnego
- Precyzyjny kanał dystrybucji (grupy FB Wynajem, OLX, Otodom)
- Partnerstwo z OLX/Gratka/Morizon jako embedded tool przy ogłoszeniu wynajmu
- Jasny messaging: „Analizator umowy najmu — sprawdź zanim podpiszesz"

### Pivot 3 — B2B API zamiast B2C SaaS

Zamiast sprzedawać użytkownikom końcowym (wysoki CAC, niskie LTV), **sprzedaj API agencjom nieruchomości, platformom freelancerskim (Useme, No Fluff Jobs) i instytucjom finansowym** jako white-label. Korzyści:
- 1 kontrakt B2B = MRR 500–5 000 zł (vs. 19 zł/użytkownik B2C)
- Zero problemu z churn'em indywidualnych użytkowników
- Brak ryzyka reputacyjnego (odpowiedzialność przechodzi na partnera biznesowego)
- Bariera wejścia wyższa (relacje, integracje, SLA)

---

## Podsumowanie decyzyjne

| Aspekt | Ocena | Co zrobić |
|---|---|---|
| Problem (realność bólu) | ✅ Solidny | Potwierdź wywiadami (5–10 rozmów) |
| Model biznesowy (subskrypcja) | 🚩 Krytycznie słaby | **Zmień na Pay-Per-Doc** przed budowaniem |
| Moat technologiczny | ⚠️ Cienki | Inwestuj w jakość systemu prompt + aktualizacje prawa |
| Ryzyko odpowiedzialności | 🚩 Wysokie | Zdefiniuj disclaimery prawne PRZED MVP; skonsultuj z prawnikiem |
| Dystrybucja | ⚠️ Trudna bez budżetu | Organik-first: content SEO + grupy FB + partnerstwa |
| Substitucja przez LLM | 🚩 Egzystencjalna | Monitoruj roadmapy OpenAI/Anthropic; buduj moat w UX i fokusie |

**Następny krok:** Uruchom Concierge MVP (ręczna analiza 10 umów, Pay-Per-Doc w cenie 9–19 zł) → zmierz WTP i retention → dopiero wtedy inwestuj w infrastrukturę.

---

*Audyt przeprowadzony wg procedury `WF_Kill_The_Idea` | Postawy: Sceptyczny Inwestor | ClearClause Pre-MVP*
