### [Execution-Guided Decoding (Wang et al 2018)](https://arxiv.org/abs/1807.03100)


#### Key Points:
1. EGD is performed only during inference, and not during training. Using EGD during training may potentially improve the model performance.

2. EGD is model-agnostic and is useful in a variety of auto-regressive tasks (has this been tried on Program Synthesis ??) 

3. EGD uses the partially generated queries and weeds out the incorrect SQL statements(those that produce a runtime error) and *queries that do not match any records*. Some of the questions may not have any suitable records in the table. The authors hypothesize that this could be because the decoder generated an overly-restrictive *where* condition. 

4. The ATIS and GeoQuery queries are much more complex and rich in (structure + information), in contrast to WikiSQL.

5. 

#### Notes:
1. Execution guidance only tries to reduce the number of execution errors. As a by product, the accuracy increases by a small value (because the number of erroneous programs decreases).
**This increases the number of semantically meaningful programs, but not necesarily the number of semantically correct programs**

2. In IncSQL + EGD (Shi et al 2018), using both IncSQL and Execution-Guided Decoding does not improve the accuracy on WikiSQL by a substantial margin.
TODO: Observe the type of errors that can and cannot be tackled by IncSQL and EGD.
