# TextReadabilityAnnotation – Evaluation
Aufbauend auf den [Ergebnissen des ursprünglichen LLM-Experiments](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/195739b6082a934c81cd8b296993ed240c6ca6df/evaluation/Evaluation.md), die eher ernüchternd ausfielen, befasst sich das folgende, daran anschließende Experiment mit der Performance anderer Sprachmodelle als LLaMA 2 bei gleichbleibender Fragestellung. 

## Umgebung
Als Datenbasis wurde eine [kurierte Auswahl](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/main/project-files/llm-data/llm-results/MP-llm-results/MP_CLEAR_Corpus_6.01_curated_LLM-output.csv) von 10 Texten aus den [CLEAR-Corpus](https://github.com/scrosseye/CLEAR-Corpus) benutzt, die einen Querschnitt aus den verschiedenen Schwierigketsstufen an Texten darstellt.

Die Readability der Texte wurden von folgenden Sprachmodellen annotiert:
- LLaMA 3 70B
- Claude 3
- Mixtral 8x22b
- ChatGPT 3.5
- (LLaMa 2)

## Ergebnisse & Evaluation
Die Annotationsergebnisse der Sprachmodelle fielen insgesamt besser als bei dem vorherigen Experiment mit LLaMA 2 aus. Die Antworten von [LLaMA 3](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/main/project-files/llm-data/llm-results/MP-llm-results/results-llama-3-70b.txt), [Claude 3](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/main/project-files/llm-data/llm-results/MP-llm-results/results-claude-3.txt), [Mixtral](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/main/project-files/llm-data/llm-results/MP-llm-results/results-mixtral-8x22b.txt) und [ChatGPT 3.5](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/main/project-files/llm-data/llm-results/MP-llm-results/results-gpt-3.5.txt) sind in der [Ergebnistabelle](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/main/project-files/llm-data/llm-results/MP-llm-results/MP_CLEAR_Corpus_6.01_curated_LLM-output.csv) zusammengetragen.

Da die Ergebnisse sehr unterschiedlich sind, ist es schwierig, die Ergebnisse der LLMs objektiv miteinander zu vergleichen. Allerdings lässt sich verglichen mit den vorherigen Ergebnissen von LLaMA 2 die Tendenz einer Verbesserung erkennen:
- LLaMA 3 gab wesentlich differenziertere Antworten als beim vorherigen Experiment. Verglichen zu seinem Vorgänger waren auch die Erklärungen individueller auf die Texte zugeschnitten. Darüber hinaus schienen die Readability-Scores im Gegensatz zu den LLaMA 2-Ergebnissen tatsächlich mit der Schwierigkeit der jeweiligen Texte zu korellieren.
- Mixtral konnte insbesondere die schwierigen Texte gut von den einfacheren Texten abgrenzen. Das Sprachmodell hat die gesamte zur Verfügung stehende Bewertungsskala genutzt und ebenfalls plausible Erklärungen produziert. 
- Claude 3 produzierte ähnliche Ergebnisse; die Werte sind zwischen denen von Mixtral und LLaMA 3 zu verorten.
- Auffällig ist es, dass ChatGPT 3.5 scheinbar dazu tendiert, die Lesbarkeit der Texte bevorzugt positiv als negativ einzuschätzen. Verglichen mit den anderen LLMs schließt es nach LLaMa 2 am schlechtesten ab.

Abschließend lässt sich bilanzieren, dass LLMs – wenn mit LLaMA 2 verglichen wird – erfolgreicher annotiert haben. Die von den LLMs gegebenen Erklärungen legen belegen jedoch, dass die Einschätzung der Readability ausschließlich durch Bewertung der Parameter wie Satzlänge, Satzbau, Grammatik und Vokabular erfolgt. Inhaltliche Faktoren wie die kognitive Komplexität, die durch den Text entsteht und entscheident für dessen Verständnis ist, werden nicht berücksichtigt.