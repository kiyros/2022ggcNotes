#ai 
# Principles:
- Principle 1:
	- Write clear and specific instructions
	- CLEAR != Short
- Principle 2:
	- give the model time to think
### Tactics for principle 1:
- Tactic 1: Use Delimiters
	- Tipple quotes
	- Tipple backticks
	- Tipple dashes
	- Angle Brackets <>
	- XML tags
	- This stops prompt injections
- Tactic 2: Ask for a structured output
	- "Write the following with the following keys: book_ID, title, etc in JSON format"
- Tactic 3: Check weather conditions are salified check assumptions required to do the task
- Tactic 4: Few-shot prompting: Give successful examples of completing tasks then ask the model to perform the task
	- giving an example of a format for the prompt to use:
		- human: "This is a test format"
		- Bot 2: "This is a test answer"
		-------
		- Answer the prompt in this consistent style.
		- human: "What is 9 + 10"



### Tactics for principle 2:

- Specify the steps to complete a task:
	- Step 1:
	- Step 2:
	- Step N: .....
	- Example:
		- Perform the following actions:
		- 1 - Summarize the following text by triple \ backticks with 1 sentence.
		- 2 - Translate the summary into French.
		- 3 - List each name in the French summary.
		- 4 - Output a json object that contains the following \ keys: french_summary, num_names.
		- Separate your answers with line breaks.
- Instruct the model to work out its own solution before rushing to a conclusion
	- incorrect example: ![[Pasted image 20230501154559.png]]
	- correct example:
	- ![[Pasted image 20230501154741.png]]

## Model limitations:
- Makes statements that sound plausible but are not true: hallucination


# Iterative Prompt Development
![[Pasted image 20230501155323.png]]
- Prompt guidelines
	- Be clear and specific
	- analyze why the result does not give desired output
	- refine the idea and the prompt
	- Repeat
- Refine to avoid these issues:
	- The text is too long:
		- limit the words (Use at most X words)
	- Text focuses on the wrong details
		- Ask it to focus on the aspects that are relevant to the intended audience.
	- Description needs a table of dimensions
		- Ask it to extract information and organize it in a table.

# Summarizing
- Summarize with a word/sentence/character limit
- Focus on x/y and/or Z
	- prompt = f"""
	Your task is to generate a short summary of a product 
	review from an ecommerce site to give feedback to the 
	Shipping deparmtment. 
	
	Summarize the review below, delimited by triple 
	backticks, in at most 30 words, and focusing on any aspects 
	that mention shipping and delivery of the product. 

- try using "extract" instead of "Summarize"

# Inferring
- detect the type of sentiment of a prompt:
	- Needed a nice lamp for my bedroom, and this one had \
		additional storage and not too high of a price point. \
		Got it fast.  The string to our lamp broke during the \
		transit and the company happily sent over a new one. \
		Came within a few days as well. It was easy to put \
		together.  I had a missing part, so I contacted their \
		support and they very quickly got me the missing piece! \
		Lumina seems to me to be a great company that cares \
		about their customers and products!!
	- This indicates "happy, satified, greatful, impressed, content"
- What is the sentiment of the following product review, which is delimited with tripple backticks
 ![[Pasted image 20230501162142.png]]



# Expanding
- Turning short text into longer pieces of text. 
- Temperature: Increases randomness of the model
	- increase the temperature if you want the model to be more creative



# Content Creation
1. Find videos that are already successful
2. prompt: Can you make 10 video titles based on this video/script ? (copy transcript or general summary of the video)
3. Rework titles
4. prompt: Create a short script for the top 3 video titles.
	- Prompt: Create a script for each title, in the style of (X),  
5. prompt: based on the video and the script, Create description for each of the 3 video titles