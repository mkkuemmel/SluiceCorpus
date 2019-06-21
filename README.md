# WhFinCor - wh-final corpus

"Ich habe sie genehmigt, aber ich kann nicht mehr genau sagen, wann."

36 search queries containing 36 german wh-phrases were run on the two source corpora (https://www.dwds.de/r)<br/>
Result: 479 german sentences with a final wh-word and period.<br/>
The corpus is in csv-format and can easily be browsed and manipulated (e.g. only show sluices) in Excel.<br/>

DATA:<br/>
- Genre (column A): contains the Genre of the document the hit is taken from
- Bibl (column B): bibliographic details about the document
- ContextBefore, Hit, and ContextAfter (columns C-E): one sentence before the hit, the actual wh-final
	sentence, and one sentence after the hit

MANUAL DATA ANNOTATION: <br/>
- Sluice or Non-Sluice (column G): The sentences in the corpus were annotated as sluice (‘y’) or non-sluice (‘n’)
- What Non-Sluice (column H): Non-Sluices were divided in four groups. Indefinite pronouns, elisions, interjections, 
	and frozen expressions.
- Embedding Verb and its Position (columns I and J): If a sentence turned out to be a sluice, the embedding verb 
	was annotated into column I. In the same step, the position of the embedding verb was annotated in column J: 
	if the embed-ding verb was the last verbal element before the final wh-phrase, column J contains ‘-1’, 
	if it was the penultimate verb, it contains ‘-2’ etc.
- Merger or Sprouting (column K): the sluices in the corpus were annotated with an ‘s’ in column K if they were 
	sprouting sluices and an ‘m’ for ‘merger’ if they had an overt antecedent. ‘bef’ was added if the antecedent 
	was found in the context before the hit.
- Negation (column L): Both, sluices and non-sluices were annotated with the information if the clause the 
	wh-word is related to, is negated (‘y’) or not (‘n’). If it is negated, the negating phrase was annotated in 
	the same column (e.g. ‘y, indefpron’ or ‘y, ohne’ (Engl.: without)).
	
COMPUTATIONAL DATA ANNOTATION: <br/>
- POS-tagged Hit and Context_before (columns N and O): Every Hit and the sentence before in the corpus were tagged
	by the TreeTagger.
- wh-Phrase and POS of wh-Phrase (columns F and P): The tagged material was subsequently used to fill column F with 
	the wh-phrase used in the sentence. The POS of the wh-phrase was put into column P.
- Sentence Length (column M)
- Last Verbal Element and Comparison to Embedding Verb (column Q and R): the last verbal element before the wh-remnant 
	was extracted and assigned to column P. If no verb could be found in the hit itself, the loop went through the 
	tagged sentence before the hit (‘ContextBefore’, column C). If it still could not find a verb, one exception 
	was hard coded: if the sequence ‘keine Ahnung’ (Engl.: no idea) was in the hit, the program ascribed ‘keine Ahnung 
	haben’ to the last verbal element. If that was not the case either, ‘\<none\>’ was put into the column. Subsequently, 
	the last verbal element was compared to the manually annotated embedding verb (column I) to see if they are the 
	same (‘y’/’n’).
- Prediction (column S): A specifically built Sluice-detector can make predictions about a sentence being a sluice 
	or not. (see readme above)
