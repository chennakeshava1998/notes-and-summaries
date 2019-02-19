### [SQLNet Xu, 2017](https://arxiv.org/abs/1711.04436)
SQL generation using sketch-based model is proposed. The contents of the sketch is filled with the help of neural networks. Column attention is used extensively (in three different steps). 

#### Key Points:
1. Sketch based approach is an idea borrowed from program synthesis. Neural networks are used to fill up the content for the slots.

2. Previous work by Zhong et al, 2017 already used column attention to predict SELECT and AGG values.

3. Order matters: The order of the conditions do not matter in SQL. But during evaluation, the order indeed matters. Authors propose a seq2set model for this purpose.

4. In hindsight, this is very similar to the approach of generate AST + fill in the slots.

5. To decide whether or not to include a column name in the WHERE condition, the authors are just performing binary classification.

6. Although attention is expensive and in-efficient, it improves the accuracy by 3 percentage points.

7. The mechanism of predicting the column names for SELECT and WHERE clauses are identical. But we cannot share the weights of the trainable matrices because, the column in either of SELECT or WHERE, need not be present in the other also. (infact it might not be present in most of the cases)

#### Doubts:
1. In the sketch, $VALUE depends only on the $COL. Also, in the implementation $VALUE is conditioned on $COL, h(partially produced SQL query) and the NLQ. ANy ablation studies for conditioning on lesser parameters? 

2. In predicting columns for WHERE condition, the authors do not share weights between the bi-LSTMs used for encoding the column names and the question. They propose that this ensures independence of the decisions made. But isn't this counter-intuitive? The decision of selecting a column is supposed to be made on the basis of the given NLQ.

3. WikiSQL does not contain examples of self-join where a single table is involved?
