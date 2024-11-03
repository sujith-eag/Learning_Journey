
Why? 
Does Something work as intended

Requirements - specifications
Respond correctly to inputs 
Respond within reasonable time
Installation and environment
Usability and Correctness


Static Vs Dynamic 

Static Testing: Code review, correctness proof
Dynamic Testing: Functional tests, apply suitable inputs

### Separation of concerns

#### White box testing
Detailed knowledge of implementation
Can examine internal variables, counters
Tests can be created based on knowledge of internal structure 
Pro: More detailed information available, better tets
Con: Focusing on less important aspects, doesn't abstract clean abstraction, Too much information

#### Blackbox testing
Only the interface is available, not the actual code, (ex: api , api specification is given)
Tests based on how it would look from outside
Pro: Closer to real usage scenario, encourages (enforces) clean abstraction of interface
Con: May miss corner cases that would have been obvious if internal structure was known, debugging is harder- even if it failed, or why it failed?

#### Grey box testing
Hybrid approach
Enforce interface as far as possible till a block is hit
Internal structure mainly used for debugging, examination variables etc


#### Regressions / Regressions testing
Maintain series of tests starting from basic development of code. Each test is for some specific feature or set of features.
Software is a continuous process, Something that was working stopped working,
Regression: loss of functionality introduced by some changes in the code.
Future modifications to code should not break existing code
Sometimes necessary - Update tests, update API version etc

Its great if a test can be run for this, regression suit that checks everything to see nothing broke.


### Coverage / Code coverage
How much of the code is covered by the tests
	> every line is executed at least once - 100% coverage
	> Does not guarantee "correctness" in all conditions
	> There may be more complex paths or other conditions that can cause failure
Branch coverage, condition coverage, function coverage

Full code coverage doesn't mean it got tested for all possible test cases, so its not a guarantee of bug free code.

Function coverage
Statement coverage
Branch coverage  
condition coverage

None of these by themselves cover the other coverages, only basic coverage is done.



______________
---

## Why Testing?

Testing ensures that a software application works as intended. It verifies that the software meets specified requirements and performs correctly under various conditions. Key aspects include:

- **Requirements Specification**: Confirm that the software meets all defined requirements.
- **Correctness**: The application should respond correctly to a wide range of inputs.
- **Performance**: Responses should occur within a reasonable timeframe.
- **Installation and Environment**: The software should install and function correctly in various environments.
- **Usability**: The application should be user-friendly and intuitive.

---

## Static vs. Dynamic Testing

- **Static Testing**: Involves examining the code without executing it. Common methods include:
  - Code reviews
  - Formal correctness proofs

- **Dynamic Testing**: Involves executing the code with various inputs. Types include:
  - Functional tests
  - Performance tests

---

## Separation of Concerns

### White Box Testing

- **Definition**: Testing with detailed knowledge of the internal implementation.
- **Capabilities**: Examines internal variables, data structures, and algorithms.
- **Pros**:
  - More detailed information available.
  - Tests can be tailored based on the internal structure.
- **Cons**:
  - May focus on less important aspects.
  - Can lead to overly complex tests.
  - Requires knowledge of the codebase.

### Black Box Testing

- **Definition**: Testing based solely on the software's external behavior, without knowledge of internal workings (e.g., API testing).
- **Capabilities**: Tests are based on requirements and specifications.
- **Pros**:
  - Closer to real-world usage scenarios.
  - Encourages clean abstraction of the interface.
- **Cons**:
  - May overlook corner cases that are evident with internal knowledge.
  - Debugging failures can be more challenging.

### Grey Box Testing

- **Definition**: A hybrid approach that combines aspects of both white box and black box testing.
- **Capabilities**: 
  - Enforces interface specifications while leveraging internal structure for debugging.
  - Useful for integration testing where both internal and external factors need to be considered.

---

## Regression Testing

- **Definition**: A testing process that ensures new code changes do not adversely affect existing functionalities.
- **Purpose**: Maintains a suite of tests throughout the development cycle. Each test is designed for specific features.
- **Importance**: As software evolves, functionalities that previously worked may break due to changes in the codebase. Regression testing helps identify these issues.
- **Approach**: Regularly update test cases to reflect changes in the code and ensure comprehensive coverage.

---

## Coverage / Code Coverage

- **Definition**: Code coverage measures how much of the source code is exercised by tests.
- **Types**:
  - **Statement Coverage**: Ensures every line of code is executed at least once.
  - **Branch Coverage**: Tests all branches in control structures (e.g., if statements).
  - **Function Coverage**: Ensures every function in the code is called.
  - **Condition Coverage**: Ensures all logical conditions in control structures evaluate to both true and false.

- **Limitations**:
  - Achieving 100% coverage does not guarantee that all possible test cases are covered.
  - Complex paths and edge cases may still lead to failures even with high coverage.

- **Conclusion**: While high coverage is important, it should be complemented with thorough testing strategies to ensure robustness and reliability of the software.

---
