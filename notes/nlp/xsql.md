[X-SQL He, 2019](https://www.microsoft.com/en-us/research/uploads/prod/2019/03/X_SQL-5c7db555d760f.pdf)

1. Uses MT-DNN instead of BERT to encode the question and to generate a new structural representation for schema
2. [EMPTY] token is appended to every table schema to account for cases where there are no WHERE conditions.

#### WHERE Col-name prediction:
1. KL-Divergence is used as an objective only for WHERE condition column name.
2. The probability distribution for WHERE-Colname is obtained from Eq (3) and KL(Q||P) is the objective function, where Q is the probability distribution for the ground truth.
3. The ground truth Q is calculated as follows:
- If there is no where clause, Q[EMPTY] receives probability mass 1 for special column [EMPTY]
- For n ≥ 1 where clauses, each where column receives probability mass of 1/n




1. Ablation studies on the effects of these both of these changes individually is required.