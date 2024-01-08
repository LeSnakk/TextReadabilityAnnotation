# TextReadabilityAnnotation – Evaluation
Ziel war es, ein Large Language Model Texte anhand ihres Schwierigkeitsgrades annotieren zu lassen. Die Ergebnisse dieses Experimentes sollten dann im Anschluss gegenüber der Bewertungen des [CommonLit Ease of Readability Corpus](https://github.com/scrosseye/CLEAR-Corpus) eingeordnet werden.

## Umgebung
Als Datenbasis wurde der [CLEAR-Corpus](https://github.com/scrosseye/CLEAR-Corpus) benutzt, da die dort vorhandenen Texte bereits anhand ihrer Schwierigkeit bewertet wurden und die Texte darüber hinaus frei nutzbar sind.

Die Annotationen wurden vom LLM [Llama 2](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf) vorgenommen. Aus Performancegründen wurde die Version mit 7 Milliarden Parametern gewählt.

Die Kommunikation mit dem LLM fand mittels Python-Skript über ein Jupyter Notebook in Form eines [Kaggle-Notebooks](hhttps://www.kaggle.com/code/rundex/textreadabilityannotation) statt.

## Umsetzung

Zunächst wurden die Texte aus dem Datensatz extrahiert. Im Anschluss wurde für jeden Text einer Promt an das LLM gesendet; zusammengesetzt aus `"How would you rate the readability in percent of the following text 0% means hard to read, 100% means easy to read`, dem Text `"{excerpts[i]}"?` sowie einem Hinweis, wie die Antwort aufgebaut sein soll: `Your answer should look like this "Score", following the score, and "Explanation", why you rated it like this."` 

Das verwendete Skript befindet sich [hier](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/195739b6082a934c81cd8b296993ed240c6ca6df/project-files/llm-data/llm-prompts/TextReadabilityAnnotationKaggle.ipynb).

Anschließend wurde der `Score` und die `Explanation` aus dem Rückgabestring des LLM extrahiert und der jeweilige Texteintrag im Datensatz um diese Ergebnisse ergänzt. Der aktualisierte Datensatz wird [hier](https://github.com/LeSnakk/TextReadabilityAnnotation/blob/195739b6082a934c81cd8b296993ed240c6ca6df/project-files/llm-data/llm-results/CLEAR_Corpus_6.01_LLM-output.csv) gespeichert und kann in Form einer [Tabelle](https://docs.google.com/spreadsheets/d/1chTMqs1MWS1JJ-rLmyu_ZOP8uCpJcNvWnZaQIUPBs6c/edit?usp=sharing) betrachtet werden.

## Evaluation
Es war mit einer gewissen Schwierigkeit verbunden, einen Prompt auszuarbeiten, der sinnvolle Antworten bem LLM hervorrief, da das LLM nicht selten gar keine Antworten zurückgab. Zudem enthielten die Antworten häufig keine Annotationen sondern gaben lediglich die Aufgabenstellung in umformulierter Form oder etwas ganz anderes zurück zurück. Mit dem aktuellen Prompt habe ich versucht, diesen Problemen so gut es geht entgegenzuwirken; der aktuelle Prompt gibt jedoch leider noch immer häufig keine Annotationen zurück.

Wenn das LLM die Readability des Textes mit einem Score beziffert, liegt dieser leider ausschließlich zwischen 60% und 90% Readability, was einer mittelschweren bis einfacheren Leseschwierigkeit entspricht. Das LLM hat somit keinen Text als schwierig eingestuft, obwohl die Datenbasis Texte mit verschiedenen Schwierigkeitsstufen beinhaltet. Die durch das LLM ermittelten Werte lassen sich zudem nicht mit den sich im Datensatz bereits befindlichen Bewertungen vergleichen oder validieren, da sich dort kein sinnvoller Zusammenhang feststellen lässt.

Die Erklärungen, die das LLM für seine Bewertungen abgibt, sind sehr repetitiv und erwecken teilweise einen generischen Anschein, als seien sie nicht spezifisch für den jeweiligen Text ausgegeben worden. Teilweise wird die identische Erklärung mehreren Texten zugeordnet, unabhängig von der Bewertung der Texte. Die Erklärung beschränkt sich darüber hinaus auf Indikatoren wie Satzlänge und Wortwahl und vernachlässigt inhaltliche Komplexität. Ein aufgrunddessen scheinbar fehlende Verarbeitung der inhaltlichen Gesichtspunkte der Texte könnte das Scoring des LLMs erklären.

Insgesamt ist das Ergebnis dieses Experiments sehr ernüchternd, da sich bilanzieren lässt, dass die Annotation der Readability eines Textes durch das Llama 2-Sprachmodell nicht erfolgreich war. Das auf diese Anforderung nicht näher trainierte Modell war nicht in der Lage, belastbare Aussagen über den Schwierigkeitsgrad eines Textes zu treffen. Die Annotationen ließen sich nicht einheitlich mit den Bewertungen des Datensatzes vergleichen. Um die Ergebnisse des Modells zu womöglich zu verbessern, müsste es genauer für diesen Task trainiert werden.