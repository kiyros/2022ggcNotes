
<h2> #Software Testing </h2>
<h3>happy case</h3>
1. constructor
2. Methods
3. conditions

<h3>unhappy cases</h3>
1. type errors (int as a string)
2. null values null cases
3. boundary tests
4. negative values

<h2>Tips for testing</h2>
- Think hard to break your code!
	- Think/Act like a hacker.
- Think about boundary cases
	- positive; zero
- when unit testing use an expected answer to minimize tests

<h2>Test Case "smells" </h2>
- Tests should be self-contained and not care about each other.
- "Smells" (bad things to avoid in tests):
	- Constrained test order: Test A must run before test B
- Tests call each other: Test A calls Test B's method
- Mutable shared state : test A/B both uses a shared object.
	- (If A breaks it, what happens to B?)




<h2>Testing overview</h2>
![[Pasted image 20220307160909.png]]

1. Requirement Elicitation
	1. user requirement
		- functional and non-functional requirements
2. analysis
	- UML diagrams
3. arch design
	- UML
4. component design
5. coding

<h2>Key Components for a Test case</h2>
* **Unique ID:** used as a reference for all kinds of things like defining a defect, reporting, results, cross references
* **Title**: indicating a purpose of the test
* **preconditions**: all constraints that must be satisfied to run the test and generate expected behavior
* **execution steps**: the sequence of actions to execute the test with specific data
* **expected result**: The result that is needed for the test to pass.
* **test case status**: passed/blocked/failed



<h2> definitions </h2>
- object/dummy:
	- Needs to exist, no real collaboration needed
- Test sub:
	- Used for passing some values to the SUT (indirect input)
- Test spy:
	- Used to verify the SUT calls specific methods of the collaborator
- mock objects
	- A simple mock:
		- Where does it take place?
			- in the Junit Test code