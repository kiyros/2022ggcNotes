
in this course we will be using [[Python]]
<h2>ANI vs AGI</h2>
- ANI
	- Artificial intelligence
	- Virtual assistant, self-driving cars, web search, facial recognition. Machine Translation
	- Thriving in this field of AI
- AGI
	- Artificial General Intelligence
	- Do everything a human can
	- Not very much progress in this field



<h1> Knowledge-based AI(Symbolism) vs ML (Connectionism) </h1>
<h3>Knowledge-based</h3>
- A.K.A: Good Old-Fashioned AI
	- Classical AI
- Figure out how Humans can do it, store it in a knowledge base, then build systems for automatic reasoning and problem solving. 
- Changed in the late 1980s
- **Expert system** - a famous knowledge-based AI system
<h4>Limitations of Knowledge based AI</h4>
- AI systems like this fail to do the easiest tasks for humans such as recognizing a person's speech.
	- This is because the world is too complex, with too many variables and uncertainties.
	- Knowledge for real-world tasks, even the basic ones, is too hard to describe formally
- For example, can you articulate precisely how to drive a car safely?


<h3>Machine Learning</h3>
- The difficulty of hard-coding knowledge suggest that an AI system needs the ability to 
	- acquire it's own knowledge
	- By Extracting patterns from raw data.

- the arrow below is Pattern extraction
	- Data -> Knowledge



<h4>Supervised Learning</h4>
- By far the most mature & successful field of AI to date
- Creates almost all the economic values of AI
- Learn a desired, well-defined input-to-output mapping
	- x -> y
- We do this by giving them a training dataset. 
	- The Dataset is LABELED as to help the Computer to understand.
- an example would be spam filtering
	- x input would be: the email
	- y output would be sorted email(spam or not spam).


<h4>Unsupervised Learning</h4>
- An active field where significant progress has been made
- Further research is required. 
- Discover unknown Structures of an unlabeled dataset
- Clustering
	- Group a collection of unlabeled objects into cluster of "similar" ones
	- Image Clustering: Group unlabeled images into cluster of similar images
		- ex: All images of dogs into one cluster


Under-fiting
- when the model does not fit the data, even when the labels are given.