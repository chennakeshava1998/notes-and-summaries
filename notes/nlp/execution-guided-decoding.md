### [Execution-Guided Decoding (Wang et al 2018)](https://arxiv.org/abs/1807.03100)


#### Key Points:
1. EGD is performed only during inference, and not during training. Using EGD during training may potentially improve the model performance.

2. EGD is model-agnostic and is useful in a variety of auto-regressive tasks (has this been tried on Program Synthesis ??) 

3. EGD uses the partially generated queries and weeds out the incorrect SQL statements(those that produce a runtime error) and *queries that do not match any records*. Some of the questions may not have any suitable records in the table. The authors hypothesize that this could be because the decoder generated an overly-restrictive *where* condition. 

4. The ATIS and GeoQuery queries are much more complex and rich in (structure + information), in contrast to WikiSQL. The ATIS dataset on average references 6 tables per query, while the GeoQuery dataset on average references 3 tables per query

5. It is hard to use EGD in pure seq2seq models, because it's hard to know ar what stage the partial programs are executable.

6. EGD requires changes in generation only during test-time(inference), EGD is not used during training.(Using it in training might improve the accuracy, by letting the underlying model to focus on the more important things). The authors use the pre-trained models to test the effectiveness of EGD.

7. In ablation studies, the authors note that EGD has the highest effect on generating WHERE conditions, and the least effect in generating AGG function.

#### Notes:
1. Execution guidance only tries to reduce the number of execution errors. As a by product, the accuracy increases by a small value (because the number of erroneous programs decreases).
**This increases the number of semantically meaningful programs, but not necesarily the number of semantically correct programs**

2. In IncSQL + EGD (Shi et al 2018), using both IncSQL and Execution-Guided Decoding does not improve the accuracy on WikiSQL by a substantial margin.
TODO: Observe the type of errors that can and cannot be tackled by IncSQL and EGD.

3. Is it possible to implement EGD for all auto-regressive tasks? For tasks like music generation, there are no standard set of rules to determine if an audio piece is syntactically and semantically correct (except for systems like Carnatic/Hindustani music ??)

4. Has the teacher-student model been tried against NLQ2SQL ? Like a generator versus a discriminator model?

5. Pointer-SQL(Wang et al, 2017) assumes a single column is selected - Not extendible beyond WikiSQL, ie Ptr-SQL assumes the template of the SQL query as : Select agg col_name From table_name where (col op value)*

6. The authors make an imp observation that many queries in WikiSQL are grammatically wrong. This might hinder possible approaches like that of GANs.   

7. It is not clear whether the beam-size plays an important role in determining the accuracy.


