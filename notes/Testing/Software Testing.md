### Testing
- random walk
	- Might the user select arbitrary paths through the system?
	- Model user behavior as a random walk through the system's pages

- Stat: stochastic or Markov
	- Can we describe the likelihood of different transitions through the system.

- State machine
	- covers states, transitions, path, etc.

- Perception
	- if it pisses off the user, it's a bug

- Falsifiability
	- test something that might fail.
	- Don't create tests that will always pass
		- you will be wasting everyone time.
	- To be falsifiable, you must be able to devise an experiment with an observable outcome yield a different result than expected.

>Although #Bias can occur when making unit tests or test of any sorts, so keep that in mind.

<h2>Reasons for Testing</h2>
- Necessary, but not sufficient
- A holistic approach
- Testing MUST be intentional
	- there must be a reason that you should test.
- Everyone tests



<h2>Difficulties of testing</h2>
- Perception by some developers and managers
	- Testing is seen as a novice's job
	- Assigned to the least experienced team members.
	- Done as an afterthought (if at all)
		- "My code is good; it won't have bugs"
		- "I'll just find the bugs by running the client program"

<h2>limitations of testing </h2>
- Impossible to completely test a system
- Does not always directly reveal the actual bugs.
- does NOT prove the absence of errors in software.
- Testing code may also have bugs.


 [[Unit Test|Unit testing]]
- Unit testing: look for errors in a subsystem IN ISOLATION
- generally for a particular class
- JUnit provides "assert" commands to help us wrote tests.
	- The idea: put assertion calls in your test methods to check things you expect to be true. If they aren't, the test will fail.
- 