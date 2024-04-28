# TextReadabilityAnnotation

- Klassifizierung von Texten auf einer Skala von 0 bis 100 in Bezug auf ihren Lesbarkeitsindex (Readability) (0 für schwer, 100 für einfach).
- Einrodnung und Vergleich der Annotationen des LLMs mit dem [CommonLit Ease of Readability Corpus](https://github.com/scrosseye/CLEAR-Corpus) (CLEAR-Corpus). 

## Datenbasis
- Es werden die 4.724 Textpassagen des [CLEAR-Corpus](https://github.com/scrosseye/CLEAR-Corpus) verwendet. Diese setzen sich aus Texten zusammen, die
  - in Englisch verfasst sind,
  - aus der CommonLit-Datenbank, dem Project Gutenberg, von Wikipedia sowie weiteren frei zugänglichen Bibliotheken stammen (genaue Quellenangaben im Corpus),
  - zwischen 1791 und 2020 geschrieben wurden,
  - dem Genre der Sachtexte und literarischen Texte angehören,
  - eine Länge von 140 bis 200 Wörter aufweisen,
  - in ihrer Logik nicht unterbrochen wurden.

## Sprachmodell/Interface
- LLAMA 2
### 10 Ausgewählte Texte zusätzlich mit
- LLAMA 3 70B
- Claude 3
- Mixtral 8x22B
- ChatGPT 3.5

## Experimentdesign
- Ziel: Das Sprachmodell soll den Schwierigkeitsgrad verschiedener Texte annotieren.
- Fragen zur Beurteilung:
  - Kann das Modell ein Textniveau bestimmen?
  - Anhand welcher Faktoren bestimmt das LLM die Readability (Satzlänge, Fachterminologie, Syntax usw.)?
  - Inwieweit unterscheidet sich Bewertung mit den Flesch–Kincaid readability scores sowie der Beurteilung der Befragten des CLEAR-Corpus?
