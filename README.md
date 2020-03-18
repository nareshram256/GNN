# Graph Neural Neworks!!

## Links

Reading
* https://towardsdatascience.com/a-gentle-introduction-to-graph-neural-network-basics-deepwalk-and-graphsage-db5d540d50b3

Unread
* https://arxiv.org/pdf/1812.08434.pdf Graph neural networks, a review of methods and aplications.
* https://towardsdatascience.com/an-introduction-to-graph-neural-networks-e23dc7bdfba5
* https://arxiv.org/abs/1901.00596
* http://snap.stanford.edu/proj/embeddings-www/files/nrltutorial-part2-gnns.pdf
* https://github.com/thunlp/GNNPapers
* https://medium.com/@BorisAKnyazev/tutorial-on-graph-neural-networks-for-computer-vision-and-beyond-part-1-3d9fada3b80d
* https://theaisummer.com/Graph_Neural_Networks/
* https://www.kdnuggets.com/2019/02/comprehensive-survey-graph-neural-networks.html


* https://www.kaggle.com/c/FacebookRecruiting/data facebook friend recommender competition. sample network

* https://arxiv.org/pdf/1806.01973.pdf PIN SAGE Paper.

-------------------------------------
# Notes

## Gentle introduction to GNN, DeepWalk and GraphSage

https://towardsdatascience.com/a-gentle-introduction-to-graph-neural-network-basics-deepwalk-and-graphsage-db5d540d50b3

Node classification problem? Given a network and partially labelled nodes

nodes have features, ground truth label and state(that describes neighbourhood)

how come feature and state are different?
features of neighbourhood and features of the node are different probably.. maybe thats why.

in simple case, state might be features of all the neighbouring nodes
![Imgur](https://imgur.com/LT7jcDL.jpg)

node state is a function F of below 4 terms
1. features of the node
2. features of the edges connecting the node
3. embedding of the neighbouring ndoes
4. features of the neighbouring nodes

then what is the differrence between embedding and features?


Anyway we are seeking a unique solution for the above function. but then why is state important?

we find out the function in an iterative process similar to how we do it in rl using bellman equations. using fixed point theorem

And then actual output o is defined like below

![Imgur](https://imgur.com/CUCcvLR.jpg)

G is a function of state and feature of a node

And G is the graph neural network?

F and G can be feed forward neural networks.

And loss can be L1 loss between o(output) and t(truth value)


Limitations of this GNN proposal.. currently does not make sense to me.
Why are we doing all this to categorize nodes?????????


Stilll dont get the point of graph neural networks. like i need a practical example how it is used.

Limitations of original GNN:
1. iterative process
2. features of edges
3. fixed point can discourage diversification of node distribution and thus maynot be suitable for learning to represent nodes!! this sentence doesnt make sense..


### DeepWalk:

how do we get node embeddings?
turns out when we do a random walk from a given node, the distribution of nodes visited is similar to that of distribution of words in a corpus..

perform random walk from a given node
run skip-gram to learning the embedding of each node based on the nodes visited.

we use hierarchial softmax instead of softmax to compute the embeddings faster!!

after computing the embeddings we train the GNN.
but one disadvantage of deep walk it doesnt generalize properly. when a new node is introduced we have to retrain the model, introduce this node in the embeddings and random walks.


### Graph Sage:

this algorithm generalizes well when a new node is introduced. its more inductive? and node embeddings are generated from neighbours instead of doing a random walk?

its an iterative algorithm to figure out embeddings based on neighbours. it genearlizes well when new nodes are introduced.

Pinterest uses a version of graph sage called pin sage in their content discovery system.

I think I found an application for graph neural networks.

Given a network of friends in instagram. you can recommend new friends?
given a network of pins in a pinterest account. you can recommend similar pins to a user?

---------------------------------

We are learning the represenations of nodes in a graph using neural networks! if you are familiar with represenational learning, these embeddings we are computing can be called as represenations of nodes.







