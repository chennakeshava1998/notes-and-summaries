### [Coarse2Fine : Dong and Lapata, 2018](https://arxiv.org/pdf/1805.04793.pdf)
Work in progress <br>
This is similar to machine-translation but the authors introduce an additional step in the middle.

#### Key Points:
1. Uses simple decoders (Verify)
2. Text2SQL happens in two stages. A rough sketch *a* is first generated, and this is used to guide the final decoding. The rough sketch *a* is devoid of argument-names, variable-names(replaced with it's datatype), and all other lower level details.
3. All the components input *x*, rough sketch *a* and final output *y* are treated as sequences. Hence, this becomes a seq2seq problem.
4. GloVe vectors are used to encode the input.
5. Attention is used extensively to learn soft alignments [Luong, 2015].
6. The training objective maximises the probability of the final meaning representation and that of the intermediate rough sketch also. 
> Preprocesing: 10-dimensional PoS tag embeddings are appended to the embeddings of the words in the natural language question.
7. The accuracy of sketches produced by OneStage and Coarse2Fine are almost identical. The fine meaning decoder does all the difference in the accuracies.



#### Clarifications:
1. Since the decoding process is split into two stages, the number of errors in the prediction will increase. How can we correct situations where the proposed-sketch is correct but the values in the slots are wrong ? What about the cases where multiple sketches are correct ? (This question is more appropriate wrt Yin and Neubig, 2017)
2. What is the advantage of this approach over that of Yin and Neubig, 2017 ? afaik, the latter has an advantage because the supervised learning can happen in two independent stages, and these can be trained parallely/independently.
3. Continuing on point-2, is it always possible to represent the intermediate representations in a sequential format? Is the model being constrained by the necesarily sequential format of *a* ? 
4. OneStage is identical to seq2SQL Zhong, 2017? 
> OneStage model generates meaning representations without an intermediate sketch generation stage
