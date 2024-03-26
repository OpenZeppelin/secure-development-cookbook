## Test

There are three categories of tests, all of which should have a fully-fledged test suite with a unique set of quality criteria:

### 1. Functional testing

Ensures that every happy path through the software system works as intended. This encompasses both state changes and return values.

- **Unit tests**: Test one function invocation or multiple functions on a single contract (while optionally mocking other parts of the system).
- **Integration tests**: Evaluate the interactions between multiple contracts in the codebase and with already deployed external contracts. Establishing a forked blockchain state is essential for accurately simulating realistic integration states, allowing for the exploration of different scenarios, such as the failure of an oracle. Furthermore, mock versions of integrations can be employed for simplicity, according to one's preference.
- **Deployment tests**: Test the entire set of contracts to be deployed, including the
  deployment scripts, ensuring correct order and parameterization.

### 2. Security testing

Assures the absence of undesired functionality that could be misused to steal funds or bring the system into an undefined state.
**Negative testing**: Typically, a test case asserts that a certain transaction reverts.
**Authorization**: The test ensures that arbitrary senders cannot call the respective
function.
**Authentication**: Test ensures that the message sender is identified correctly.
**Re-entrancy**: The test ensures that re-entrancy cannot occur or is considered safe.
**Path equivalence**: If two different sets of state changes lead to the same semantic end state, the test case checks for technical equivalence (e.g., staking rewards).
Known exploits: Tests inspired by known exploits are adapted to the codebase.

### 3. Testing Processes: [Shift-Left Testing](https://en.wikipedia.org/wiki/Shift-left_testing)

**Test Suite Trigger**: Tests are automatically initiated by specific events in the CI/CD pipeline, such as commits, merges to the main branch, or other CI/CD-related occurrences. This ensures that testing is an integral, continuous part of the development process, facilitating early detection and resolution of issues. OpenZeppelin Defender’s code inspector provides code analysis on every PR, using dozens of detectors to enhance security, efficiency, and code quality.

**Test-Driven Development (TDD)**: Aligning with the Shift Left principle, tests are crafted prior to the development of code. This practice ensures that the system's intentions are thoroughly understood and addressed from the outset. Optionally, this process can be managed by a dedicated team, separate from the one responsible for development, to further ensure objectivity and comprehensive coverage of test cases.

**Behaviour-Driven Development (BDD)**: Following the principles of TDD, Behavior-Driven Development (BDD) takes a step further by integrating business and technical perspectives. BDD involves writing tests in a language that mirrors real-world scenarios, allowing non-technical stakeholders to participate actively in the development process. This approach not only clarifies the system's behavior from the user's viewpoint but also fosters collaboration across the team, ensuring the developed features precisely meet the project's requirements.

**Invariant & Spec Design**: Before the onset of implementation and testing phases, the design of formal invariants and specifications is critical. These serve as foundational elements that maintain their truth across the entirety of the implementation process.

By incorporating these strategies, the Shift Left principle emphasizes the importance of moving testing and quality assurance earlier in the development lifecycle. This not only helps in identifying and addressing defects sooner, when they are less complex and costly to fix but also aligns development efforts more closely with the intended design and specifications, ensuring a higher quality and more secure final codebase.

### 4. Fuzzing

Fuzzing is an automated testing technique that involves executing tests with thousands or millions of computer-generated inputs. Fuzzing is recommended to test parts of the code that are hard to reason for the human mind like integer arithmetic prone to rounding errors, assembly blocks, and complex data compression.

There are three types of fuzzing:

**Stateless**: This approach involves randomly generating inputs and immediately checking the results. After each test, the system is reset before proceeding with the next set of inputs.

**Stateful**: In this method, the fuzzer is given the autonomy to decide which functions to call and with what inputs. The tester defines an invariant that must be maintained. For example, the total sum of balances should not exceed the total supply.

**Differential**: Differential testing involves using fuzzing on two different implementations of the same functionality and comparing the results. If libraries A and B implement the same feature, their outputs should match any given input. This is especially useful for math libraries, where you can compare your math against a Python implementation to check for rounding errors.

When choosing input ranges for fuzzing, think about limiting compute by removing value ranges you already know with certainty will revert or produce a successful result. Also, think about covering enough input ranges that will cover all branches of the control flow.
