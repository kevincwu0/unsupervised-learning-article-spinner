# Article Spinner

Motivation:
- Very useful tool for internet marketers 
- Allows us to automate content-creation and generations to scale
- Can no longer just repeat 1000 times in invisble text for SEO
- Now duplicate content is heavily penalized (can't just copy your high ranking article 1000 times)
- Only way to keep up is to build unique and quality content
- Existing popular articles, doesn't match the original

What is article spinning?
- Take an article and slightly modify it (synonyms, replace phrases that have the same meaning)
- Results in a new article with different terms, but same meaning

Doesn't always work well in reality: 
"Airbnb is a platform or marketplace to rent or lease short-term lodging"
"Airbnb is a podium or forum to lo rent or lease limited shelter" (Makes no sense...)
Context is important!

Use surrounding words to influence the replacement word. So how can we model the probability of a word given the surrounding words?

Using Context:
- Label our words w(1), w(2), ..., w(N)
- Model w(i) using w(1), ...w(i-1) and w(i+1),...w(N)
- Probabilistic: P{ w(i) | w(1),... w(i-1), w(i+1), ...w(N) }
- But this wouldn't work: only this document has exactly w(1), w(2), ..., w(N) 
- That would give us only 1 data point to leanr from, not useful

Trigrams to accomplish something similar to Markov model:
- Specific instage of "N-gram", where N=3, three words (previous and next to predict)
- we'll model P{ w(i) | w(i-1), w(i+1) }
- How? Use a python dictionary with { previous w(i-1), next (w+1) } as the key and lookup w(i)
- Sort of like a Markov model where P{ w(i) | w(i-1) }
- Don't replace every single word in the document otherwise it won't make much sense. Let's replace each term with some probabiltiy p = 0.2 (can fine-tune this)
- This and LSA are unsupervised learning algorithms because there are no labels.
- Spam detection and sentiment analysis were "supervised learning" because we had labels - spam/no spam, positive/negative
