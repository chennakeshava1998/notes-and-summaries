### [Execution-Guided Decoding (Wang et al 2018)](https://arxiv.org/abs/1807.03100)


#### Key Points:
1. EGD is performed only during inference, and not during training. Using EGD during training may potentially improve the model performance.

2. EGD is model-agnostic and is useful in a variety of auto-regressive tasks (has this been tried on Program Synthesis ??) 

#### Notes:
1. Execution guidance only tries to reduce the number of execution errors. As a by product, the accuracy increases by a small value (because the number of erroneous programs decreases).
**This increases the number of semantically meaningful programs, but not necesarily the number of semantically correct programs**

2. In IncSQL + EGD (Shi et al 2018), using both IncSQL and Execution-Guided Decoding does not improve the accuracy on WikiSQL by a substantial margin.
TODO: Observe the type of errors that can and cannot be tackled by IncSQL and EGD.
