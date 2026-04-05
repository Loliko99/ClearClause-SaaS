# docs/ — Dokumentacja analityczna ClearClause (JasnaUmowa)

Ten katalog zawiera wszystkie dokumenty analityczne projektu ClearClause, wygenerowane na podstawie workflowów metodologicznych z `kilocode/workflows/`.

---

## Zawartość katalogu

| Plik | Workflow źródłowy | Opis |
|---|---|---|
| [Perosonalizacja](./Perosonalizacja) | `WF_ICP_Persona` | ICP Card, Problem Matrix (5 problemów, Priority = I×C×E), Interview Script, Concierge MVP |
| [product-brief-clearclause.md](./product-brief-clearclause.md) | `WF_Job_To_Be_Done` | Koncepcja produktu, 3 moduły (Decoder/Architect/Counter), grupy docelowe, model biznesowy, JTBD, tech stack, roadmap, ryzyka |
| [kill-the-idea-clearclause.md](./kill-the-idea-clearclause.md) | `WF_Kill_The_Idea` | Pre-Mortem Audit: 5 zabójczych filtrów, Red Flags, scenariusz śmierci, werdykt, 3 propozycje pivotu |
| [mvp-scope-clearclause.md](./mvp-scope-clearclause.md) | `WF_MVP_Scoping` | Scope MVP v1.0: audyt funkcji, Tier 1/2/3, feature cut table, red lines, tech stack, metryki |
| [user-journey-clearclause.md](./user-journey-clearclause.md) | `WF_User_Journey_Map` | Mapa ścieżki użytkownika: 7 stadiów, Aha Moments, friction points, quick wins, metryki |

---

## Kolejność czytania (rekomendowana)

```
1. Perosonalizacja         → Kim jest klient i jaki ma problem?
2. product-brief           → Co budujemy i dlaczego?
3. kill-the-idea           → Co może nas zabić? Jak się zabezpieczyć?
4. mvp-scope               → Co dokładnie budujemy w pierwszej wersji?
5. user-journey            → Jak użytkownik przejdzie przez produkt?
```

---

## Kluczowe decyzje produktowe (podsumowanie)

| Decyzja | Wybór | Powód |
|---|---|---|
| Model biznesowy | Pay-Per-Document (9 zł/analiza) | Subskrypcja sprzeczna z incydentalnym use case |
| Core moduł MVP | The Decoder (analiza tekstu) | Priority 648 — najwyższy, Ease 9 — najłatwiejszy do testu |
| Core segment | Najemcy + freelancerzy (18–30 lat) | Najwyższy trigger, najwyższa stawka finansowa |
| Stack | Next.js + Clerk + Stripe + OpenAI + Supabase + Vercel | Solo-Dev, 0–20 zł/mies. kosztów stałych |
| Przed kodem | Concierge MVP + 7 wywiadów | Walidacja WTP zanim zainwestujesz czas w infrastrukturę |

---

## Następny krok

> Przed pierwszą linią kodu: przeprowadź **Concierge MVP** (ręczna analiza 10 umów) + **7 wywiadów** z grupą docelową.
> Sygnał do budowania: WTP > 0 zł u ≥ 60% testerów.
