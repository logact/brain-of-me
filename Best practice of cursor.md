# Core Principle
1. firstly, we should correct the previous wrong thought:  the developer don't need any knowledge of tech(pure vibe), the AI code assistants will work well with more detailed tech context(e.g the function implementation logic)
2. the developer should provide enough context including the "where the problem?" ,"how the data  flow","what's the basic implementation logic of some function "
3. so the developer should have a  [[#minimal understanding of a project]].
# process with AI 
follow the process in [[Solving Problems with AI]],and we set some setting in cursor("User rules", "Project rules", "User commands","Project commands") create the agent.md for cursor. [[cursor agent]]



# prompt template
### common setting of prompt
1. tech architecture
	1. what tech we use?
	2. the core component and how they interact?
2. constraint
	1. compatibility
3. alignment
	1. In each action confirm to me what you have got from my request.
	2. ask any thing if want get more detail or don't know
	3. if you have question need me to add anything, feel free to ask me.
4. test
	1. pass all auto test when we finish a request
		1. if some test case failed, tell me why, and provide the fix plan for me to confirm and adjust
5. other engineering suggestion.
6. add one 
	1. if we have some good practice suggest found in development add there
### add a new feature

1. current state
	1. what function exits now (how they implement).
2. requirements
	1. only on feature in 1 request
3. please(add one for specific task )
	1. firstly  feasibility analysis, research  is it available?
	2. if it's available? research best practice
	3. small proof-of-concept(if we stuck try to use this to figure out how the plan run)

### bug fix
1. current state
	1. in (where),in (when),(what you do) cause (what)
	2. what's current  implementation
2. environment
3. other debug information
	1. log
4. expectation
5. what have i tried and the result
6. please(add one for specific task)
	1. Analyze the root cause 
	2.  Research similar problems and solutions
	3. Provide a fix with explanation
	4. suggest how to prevent this in the future

# Appendix
## minimal understanding of a project

1. understand the architecture
	1. what tech dose the project use?
	2. what's the basic concept of the project's tech?
	3. what's the core component  and how they interact?
	4. how the core feature implement?
	5. how the project build and run?
2. how to use the specific tool of the project?
	1. how to read the log of the project?
	2. for some optimization issue we may need provide memory usage log.