# scientific_diary_2019-2020

## Articles
_____________
* [SEMI-SUPERVISED CLASSIFICATION WITH GRAPH CONVOLUTIONAL NETWORKS (ICLR 2017)](https://openreview.net/pdf?id=SJU4ayYgl)

Authors propose new type of convolution layers which also consider information extracted from graph through normalized Laplacian of that graph. Convolutions are calculated as follows:  
<p align="center">
<img src="./pics/GCN_layer.png" width="30%" >
</p>

<p align="center">
<img src="./pics/A_det.png" width="11%" >  
</p>

<p align="center">
<img src="./pics/D_det.png" width="11%" >   
</p>
where A - is adjacency matrix, H_l - is output of layer l and W is a matrix of convolution parameters. The main disadvantage of that method is that every convolution step is is applied to every graph node i.e. it is applied to the whole training dataset. __Thomas suggests__: "A good way to address the memory issue is to use some form of mini-batching, as e.g. in GraphSAGE: https://arxiv.org/abs/1706.02216" 

* [Multi-Label Image Recognition with Graph Convolutional Networks (CVPR 2019)](https://arxiv.org/abs/1904.03582#)  

Authors proposed GCN-like architecture for mapping labels from multilabeling task with per-label-classifiers. There are no memory issues since there are only order of hundreds of labels in tasks. Authors studied effects of different embedding representations for labels (there is almost no effect although more powerful embeddings could lead to better performance.). Authors also studied the effect of different adjacency matrix initializations: 
* Binary -- we count conditional probabilities P(L_i|L_j) for each pair of labels and then start procedure of binarization on this probabilities by comparing each node with some threshold (hyperparameter)
* Re-weighted -- aforementioned initializtion lead to problem reffered as oversmoothing -- that is, the node features may be over-smoothed such that nodes from different
clusters (e.g., kitchen related vs. living room related) may
become indistinguishable. To alleviate this problem, authors
propose the following re-weighted scheme:  
<p align="center">
<img src="./pics/reweightscheme.png" width="28%" >
</p>
The proposed architecture:  
<p align="center">
<img src="./pics/ml-gcn.png" width="70%" >
</p>

### 10.11.19
* [Actional-Structural Graph Convolutional Networks for Skeleton-based Action Recognition (CVPR 2019)](https://arxiv.org/pdf/1904.12659.pdf) 

The authors attempt to capture richer dependencies among joints by constructing generalized skeleton graphs.

The authors infer the actional links (A-links) to capture the latent dependencies between any joints. An A-link inference module (AIM) with an encoder-decoder structure is proposed. They also extend the skeleton graphs to represent higher order relationships as the structural links (S-links). Based on the generalized graphs with the A-links and S-links, they propose an actional-structural graph convolution to capture spatial features. 

Paper propose the actional-structural graph convolution network (AS-GCN), which stacks multiple of actional-structural graph convolutions and temporal convolutions. As a backbone network, AS-GCN adapts various tasks: action recognition as the main task and future pose prediction as the side one. The feature responses present that the authors could capture more global joint information than ST-GCN, which only uses the skeleton graph to model the local relations.

The AS-GCN achieves large improvement compared with the previous methods. Moreover, AS-GCN also shows promising results for future pose prediction.
