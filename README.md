# Optimal-Brain-Damage

## Abstract:
Optimally removing the weights from a neural network without affecting it accuracy, or by trading off the evaluation speed and cost by having a minimum impact on the accuracy. Because an optimized model is the one which is efficient, fast and inexpensive.

![image](https://user-images.githubusercontent.com/41909437/162667656-b6da25f0-eb94-460b-b948-9bbba776be70.png)

## Methods:
Given a layer of a neural network ReLU(xW) are two well-known ways to prune it:
1. Weight pruning: set individual weights in the weight matrix to zero. This corresponds to deleting connections as in the figure above.
Here, to achieve sparsity of k% we rank the individual weights in weight matrix W according to their magnitude (absolute value) |wi,j|, and then set to zero the smallest k%.
2. Unit/Neuron pruning: set entire columns to zero in the weight matrix to zero, in effect deleting the corresponding output neuron.
Here to achieve sparsity of k% we rank the columns of a weight matrix according to their L2-norm |w| = i=1N(xi)2 and delete the smallest k%.


## Analyze your results:

#### What interesting insights did you find
It was my first time, when I was working with pruning. So learning about the concept in itself was very intriguing for me. 

#### Do the curves differ

![image](https://user-images.githubusercontent.com/41909437/162666578-5fc79381-dce8-4f78-8557-89ab9ee834af.png)

Form the above image we can observe that unit pruning perform better than weight prunning. I have a theory that unit pruning has a more structured way of deleting the weights, which is the reason.

#### Do you have any hypotheses as to why we are able to delete so much of the network without hurting performance
While deleting the network weight, we were deleting weights of a pre trained model, and we made sure that we took the weights which had the least impact on the output vis-à-vis the eficieny. This is the reason why we deleted so much from the network, still there was a slight impact on the performance.
But from the above map, we can also see that if we had pruned away too much of significance data, the accuract dropped significantly. So in order to get a good performing neural network we have to see keep this tradeoff between accuracy and performance in mind.

#### See if you can find a way to use your new-found sparsity to speed up the execution of your neural net! This can be tricky but is a worthwhile engineering lesson in the optimization of your models.
Pruning the neural net had speed up the overall execution, which is a great thing. As we can easily visualize the tradeoff between accuracy and efficiency, we can choose the best sparsity index for the model, which can cut down a alot on computing power. 
We can use these pruned models for transfer learning, as recently there are very few pruned pre-trainied models in the machine leanring community.

## How To Replicate:
1. In order to replicate the result, you can either reuse the Pruning Class, that have three function.
2. The code uses MNIST, and the keras model is built for MNIST dataset. If you want to utilize this for other dataset, change the number of input and output nodes in the model.

Note:
1. optimal brain damage function need a trained model, and the sparsity percentage.
2. Setting the unit flag as True will result in unit pruning. Default nature of this function is to perform weight pruning.

## Reference
[1] Optimal Brain Damage, Yann Lecun, 1990

[2]https://jacobgil.github.io/deeplearning/pruning-deep-learning
