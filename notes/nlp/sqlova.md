### ![SQLova + EGD, Naver](https://ssl.pstatic.net/static/clova/service/clova_ai/research/publications/SQLova.pdf)

1. BERT word representations instead of GloVe.
2. seq2SQL - builds upon SQLNet Xu, et al.
3. Execution Guided Decoding

### Key Points:
1. Borrows a lot of structure from SQLNet. Uses BERT contextualised word representations instead of GloVe.

2. Representation of Input: The NLQ is concatenated with the table headers. Every token consists of token, position and segment embedding(see BERT for more details). It is not entirely clear if this ordering of the input had any effect on the accuracy metric. (This is because this paper largely borrows from SQLNet, and SQLNet does not impose such restrictions on ordering of input)

3. Where-Value: Xu, et al predict the where-value using pointer-networks (Vinyals). But this paper follows Dong and Lapata, 2018 and predicts the start and the end token for the where-val instead of going for a seq2seq approach. Also, where-val is conditioned on where-col and where-op.

4. " The order of where conditions is ignored in measuring logical form accuracy in our model ". Does this not obviously increase the logical accuracy when compared with other models which do not adhere to this practise of ignoring the order of WHERE conditions? 

5. The final output of where-clause will be that one which has the highest joint probability with respect to all the four where predictors.

#### Doubts:
1. Prediction of where-val: Aren't we assuming that all where-value tokens consist of consecutive words in the NLQ? What about counter examples? What's the rationale for usage in Dong and Lapata?

2. In the last paragraph before section 3.3, the authors say " Unlike SQLNet, our modules do not share parameters. " AFAIK, there are no shared learnable weights in SQLNet. (Possible inaccuracy?)

3. The authors claim that SQLNet conditions the where-val only on the where-col. But this is not true. It conditions the where-val on NLQ, column_name, and the partially generated query. This probability is calculated for every column and softmax is used to choose the one with the highest probability. 

