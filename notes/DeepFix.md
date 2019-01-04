### [DeepFix : Fixing Common C Language Errors by Deep Learning](http://www.iisc-seal.net/deepfix)

TLDR; The paper trains a neural network for fixing the syntactic (non-semantic) programming errors in the C language. The authors train 
a GRU with attention to achieve ~60% accuracy. The literals are given a fixed vector representation (as they donot affect the syntax) and all the identifiers
are given a similar fixed representation.

#### Key Points:
1. Initial weights of the GRU is drawn from a uniform distribution within (-0.07, 0.07)

2. Both encoder and decoder have 4 layers, 300 cells each.

3. The model performs the error localization upto ~80% accuracy.

4. The tokens are fed as (<line number>, <token representation>). This helps the model make small changes at a time.



#### Notes:
1. LSTM+attention is not expressive enough for this problem, the error on the seeded dataset is also very large. We need to find a more expressive model for this problem.

2. Check the results using the granularity of tokens instead of lines. The paper considers corrections in a line-by-line fashion. But this
adds unnecesary data (line numbers) into the model, which may be acting as noise.

3. Neural network-1 corrects the mistakes in identifiers, whereas the second neural network is left to handle all the other types of errors.
This maybe causing an overload on the second neural network. Can we train different neural networks for different classes of errors?

4. The mutations in the dataset (seeded) were performed manually by the authors. This might have introduced bias and might be the reason for 
the poor performance.

5. Certain types of errors might never be suitable for LSTMs. For instance, assignment of an array into another is not allowed in the C 
language (unlike Python). The solution to this is to use a for loop and index through all the elements of the array. It might be 
impossible to enable an LSTM to generate such solutions.

6. Can the error messages from the compiler be used in the model? Caveat: The line numbers in the error messages might not always be 
indicative of the location of errors.

7. The authors select only one erroroneous program per student for every programming task citing the concern of bias. But since syntactic 
errors are independent of the semantic nature of the program, this leads to wastage of training data. It is true that there may be some 
correlation between the programming task and the syntax errors and a specific student, but it will be useful if a comparison had been provided.

8. Is it necessary to counter the bias? Real-world data might also have a similar distribution of the types of errors. By forcing equal
representation, are we not losing the information on the priority of errors? TODO: Are such biases handled in grammatical error correction
for natural languages?

9. The model is stopped from continuing if one of it's proposed corrections is rejected by the oracle(during iterative repair). I think this bound must be reduced to 3/4, because
a single line might contain multiple fixes(at different positions) to eliminate a single error message.

10. TODO: Do we get similar results for functional programming languages and scripting languages ?

11. It is not entirely clear if the vanilla attention mechanism is adding value to the process. We can experiment with using reinforcement
learning to predict the approximate location to focus the attention, as explained in https://arxiv.org/abs/1406.6247
