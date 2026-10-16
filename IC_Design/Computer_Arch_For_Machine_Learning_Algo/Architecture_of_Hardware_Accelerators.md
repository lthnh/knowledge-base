## MAC Array
MAC stands for Multiply-Accumulate. This unit is the fundamental computation structure for many accelerators. Chain of MAC units enables vector/matrix multiplication.

> [!info]
> Increasing the number of MAC units does not automatically produce proportional level of improvement.

There are many styles of MAC topology. For more details, see this paper [Accelerating CNN Inference on ASICs: A Survey](https://www.sciencedirect.com/science/article/abs/pii/S1383762120301612).

A systolic array topology is a topology in which MAC units arranged in an interconnected grid where operands flow from one MAC to neighboring MACs in a pipelined fashion.

