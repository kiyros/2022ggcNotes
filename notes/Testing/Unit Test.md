



<h1>Structure of Unit Tests</h1>
<h3>Triple AAA Style</h3>
- Arrange : setup everything needed for the running test
- Act : Invoke the code under test.
- Assert : specify the pass criteria for the test.

<h3>When Given style</h3>
- Testing for exceptions


<h2>tips for [Testing]</h2>
- you can't test every possible input
- Think about boundary cases
	- positive, zero; negative numbers
- Think about null/empty and error cases
	- 0, -1, null;, an empty list or array
- Test behavior in combination
	- making multiple calls