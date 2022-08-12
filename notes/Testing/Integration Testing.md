<h1>Integration testing</h1>
	- Testing in which software components, hardware components or both combined are testing to evaluate the interaction among them.
	- Integration testing happens every milestone within the sprint
	- Types of #Integration-testing

<h2>Reason to Integration test</h2>
- Tests the arguments and parameters
- Test the communication between classes.
- Function name

<h2>Big bang</h2>
		- Left over from hardcore traditional waterfall methods
		- wait until all classes have been developed
		- now try to integrate them and test them
		- Issues
			- The testing occurs way to late in the SDLC
			- Unexpected behavior is difficult
<h2>Top-Down</h2>
	- Starts at the top of call hierarchy
	- Stub in next level down calls
	- Work our way to the bottom of call stack
	- Issues
		- Lots of Scaffolding (stubs)
		- Stubs restrict range of data for testing
		- Stubs may produce incorrect results

<h2>Bottom-Up</h2>
- Start at leaf nodes of the call hierarchy and work up
- Issues
	- Introduces "drivers" but they are easier than stubs



- Stub: These provide canned answers to calls during testing and record info about calls.