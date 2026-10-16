Run several simulations with different seeds. Merge the results into a report. Use this report as guide to create new stimulus to reach untested conditions and logic.
## Feedback from Functional Coverage to Stimulus
A random test evolves using feedback. Without feedback, random testing can hardly reach all the design space even with new seeds. As functional coverage approachs its limits, the test needs to be changed to reach uncovered areas of the design. This is known as *coverage-driven verification*.

A more productive testing strategy uses random transactions and terminators. The longer you run it, the higher the coverage. The test can also be made flexible enough to create valid stimuli even if the design's timing changed. This is accomplised by adding a feedback loop that looks at the stimulus so far and then change the contraint weights.

In realistic design, it is hard to figure the changes to stimuli needed to reach a desired design state. This is why dynamic feedback is rarely used for constrained-random stimulus. Instead, you have to manually analyze the functional coverage reports and alter your random constraints.

Feedback is used in formal analysis tools such as Magellan (Synopsys 2003). It analyzes the design to find all unique, possible states. It then runs a short simulation to see how many states were visited. Lastly, it searches from the state machine to the design inputs to calculate the stimulus needed to reach any remaining states then Magellan applies this to the DUT.
