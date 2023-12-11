# TextReadabilityAnnotation

- Klassifizierung von Texten auf einer Skala von 1 bis 5 in Bezug auf ihren Lesbarkeitsindex (Readability) (1 für einfach, 5 für schwer).
- Beispiele:
  - Text: "Die Sonne scheint am Himmel, und die Vögel singen in den Bäumen."
    - Readability: 1
  - Text: "Sämtliche Konstellationen astronomischer Objekte sind von der Perspektive der Erde aus betrachtet einer kontinuierlichen Veränderung unterworfen, was die Präzision astronomischer Prognosen herausfordert."
    - Readability: 5
- Vergleich der Annotationen mit dem Flesch-Kincaid Readability Test, um die Genauigkeit des LLMs zu bewerten und Unterschiede zu analysieren.

## Datenbasis
- Textsorten: Nachrichtenartikel, Geschichten (Kurz- und Kindergeschichten, Märchen), Leichte Sprache-Texte, Wissenschaftliche Artikel, Amtsdeutsch.
- Sprache: Primär Deutsch, ggf. Englisch für höhere Präzision.
- Quellen: Gängige Nachrichtenportale, bpb, Ämter, ResearchGate, DSH, ACL Anthology, frei verfügbare literarische Texte.

## Sprachmodell/Interface
- ChatGPT || LLaMA
  - Ggf. Unterschiede feststellbar?

## Experimentdesign
- Ziel: Das Sprachmodell soll den Schwierigkeitsgrad verschiedener Texte annotieren.
- Fragen zur Beurteilung:
  - Kann das Modell ein Textniveau bestimmen?
  - Anhand welcher Faktoren bestimmt das LLM die Readability (Satzlänge, Fachterminologie, Syntax usw.)?
  - Inwieweit unterscheidet sich diese Bewertung von Flesch–Kincaid Readability tests?
