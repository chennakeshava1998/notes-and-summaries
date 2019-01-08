### [seq2SQL+RL, Zhong, Salesforce](https://arxiv.org/abs/1709.00103)

The paper attempts to translate natural language questions into SQL. Augmented pointer network is used to reduce the output space. Attention mechanism is extensively used. Reinforcement Learning(policy gradients) is used to reward the generation of WHERE condition because *order of the conditions do not matter*.

#### Key Points:
1. In the WHERE section, the order of the conditions do not matter. Cross-entropy incorrectly penalises some of the answers, hence RL is used to learn a policy.

2. Consequently, teacher-forcing cannot be used to handle this problem. Teacher-Forcing: While training RNNs, feeding the output at timestep t as the input at time step (t+1). Even if the RNN generates an incorrect output at time t, it is not penalised subsequently because the expected ground truth will be fed as input for the next timestep.

3. To predict AGG, attention mechanism is used, followed by a softmax layer. For predicting column-name, attention mechanism ois followed by a augmented-pointer-decoder network.

4. AGG and SEL is trained using cross entropy loss. Negative of the expected reward is used for calculating the loss with respect to WHERE. But the authors propose a mixed objective function, and calculate the gradient with respect to all the three losses. 

5. *The model needs to generalise to new questions and new table schemas.*

6. No table is repeated across the train-dev-test splits. This makes sure that the model is tested on new table schemas and questions.

7. Dong and Lapata, 2016 is more likely to use common words in the WHERE condition, but seq2SQL is not affected by the rarity of words because it uses an augmented pointer network.

8. Using a classifier for AGG calculation improves it's accuracy. (Have ensembles been used for generative tasks?)


#### Notes:
1. The paper attempts to encode the question for predicting the AGG and column-name. The authors propose disparate sets of learnable parameters to do the same. Instead, if the same embedding can be used for both tasks of predicting AGG and column-name, it would save a lot of learnable parameters. [AGG needs (1 + 3) matrices and column-name needs 3 matrices]

2. It's not clear if teacher-forcing was used for training the first half of the query (excluding the WHERE condition). 

3. Instead of using the execution results as a reward signal, I think it is more appropriate to use a symbolic execution software to determine if the generated SQL query is logically identical to the ground-truth. 

4. The authors do not justify the need for a mixed objective function. Since this is a template/slot filling technique, individual neural network's could have ben trained on the respective losses only. It would have been nice to do ablation studies pertaining to the same.

5. Using policy gradients has only provided gains of ~2% accuracy. Does more sophisticated RL models(can we use A3C?) help in improving the accuracy ?

6. Furthermore, leveraging the structure of SQL queries has only resulted in ~3.5% gains, when compared against Dong and Lapata, 2016. It needs to be seen if alternative slot-filling algorithms have acheived better accuracy by better exploiting the SQL structure. The poor result might probably be because there is no sharing of information between neural networks, ie none of the networks use the partially generated SQL query as an input. 


