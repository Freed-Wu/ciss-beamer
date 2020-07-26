Good afternoon, my dear professors. It is a great honor to have an opportunity for this speech. The topic of my speech is CiSS, an abbreviation of context-reinforced semantic segmentation. So, what is CiSS? Before answer this question, we should have some necessary knowledge about sementic segmentation.

As these pictures presented, some tasks of neural network are listed. from left to right, they are semantic segmentation, classification, object detection, instance segmentation. Different from other tasks, semantic segmentation only accents pixels not objects. For example, if the 4th picture is semantically segmented, the dogs and cats will not be divided separately.

Now, let us return back to the topic. The p-map is short for prediction segmented map. We know the neural network usually consist of many layers. In the primary layers, we can get some low-level information, such as texture, colors, boundaries. However, if we want to get more high-level information, such as contextual information, we need to depend on the help of high layer. It is because p-map has encoded a large number of contextual information not only local but also global, the function of p-map can not be emphasized too much. Hence, the paper named context-reinforced semantic segmentation proposes a new model which the researchers named CiSS to explore the p-map to generate another source of scene context which can be effectively combined with traditional features.

Firstly, let us see the comparison of CiSS and the traditional model -- we take fully convolutional network as baseline -- to know the variety. Take a look at these pictures. The input is a picture about the surface of water. The ground truth is the actual label, which we want our result looks like as possible. The CFN gives us a result of semantic segmentation. Nevertheless, the reflection of trees on the water deceives it into recognizing as true trees. As a comparison, CiSS canabout  distinguish its deception.

the truth whether reflection can be recognized is only a subject index. Here we introduce some objective evaluation index. An evaluation index should statisfy the following conditions. The range restriction and monotonicity. IFF means 'if and only if'. Some indexes are listed here. Although the definitions are different, set theorem can tell us they are similar. We choose mean of intersection over union as our index. the mIoU of CiSS is larger 3.9% than CFN's. In additon, I list the formula of quantization of the cap and cup. the M menas matrix of image.

Second, take a look at the framework of CiSS. we can see the three subnetwork in this graph. Segment net, context net, encoder. xxx means XXX. Something we should notice are: ... This is an end-to-end design. the output of S-Net is one of inputs of C-Net. for C-Net, it is same as the output of C-Net is one of inputs of S-Net. this design is better than step by step. the paramters can be updated together not step by step.

This is the construction of encoder. The one-hot coding is a special encoding. for example, 001, 010, 100 is the one-hot coding of1, 2, 3. the number of channel, stride, kernel size can be get from the graph. we concatenate the result before output. Notice: 

S-net is composed of 2 subnetwork: base net and bias net. A means add.

C-net is a 5-layer CNN. the parameter of neural network can be seen in the graph.

Now, let us introduce reinforce learning. the MDP is the basis of RL. in probability theorem, we has know what is Markov chain. it is related to Markob attribution. in fact, MDP is the extension of Markov chain. it is a tuple. when A is a one-element set, the MDP will degrade to Markov chain.

The task of us is to solve this model. some function are proposed. such as value function V, action value function Q, the advantage function is the diff of Q and V. because the infty can not be calculated, we use Ak to approximate it. 2 truth should be noticed. first, A > 0 means the the action is better than the average of all actions. in the contrast, it is worse. second, the eta is value function of s0.

the content of algorithm is exact. in brief, we call it A3C algorithm. the proof about this algorithm why can solve this problem can be found in that paper of google.

A good definition of loss function can help us solve this model. some definition are displayed. A truth can not be ignored.

the loss function of CiSS is this expression.

third, we should experiment to check our thought. we choose 3 dataset. they are XXX. contain.

the specific steps of the expriment are as following:

in the part of sensitivity analysis, we adjust parameters to analysize variety. keep lambda1 is equal to one. the relation of IoU and gamma or beta2 is monotone.

Ablation study usually study the robustness of a model. we change some structure of the model to observe the variety. we can find

iteration steps can also be changed. as same as parameter gamma and beta2, it also display a monotonicity. however.

we can compare CiSS and other state-of-the-art models. When we use ResNet-50 to initial the model, CiSS can achieve a good result. When we use ResNet-100 to initial the model, CiSS can outperform the most of others.

In the part of discussion, there are three points should be paid close attention to.

Last but not least, let us conclude it. the model has some innovation. such as ... and none. For a paper, ...

I dare to think the expression of reward functin is too trival.  ... last,  ... yes, 16 Nvidia M40 GPUs count 50 kilo yuan. The poorness restricts my imagination.
