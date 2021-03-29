

# CVID
Dataset and Code of CVID (Human Identification and Interaction Detection in Cross-View Multi-Person Videos with Wearable Cameras), published in ACM MM 2020.

```
@inproceedings{han2020cvid,
  title={Complementary-View Multiple Human Tracking}, 
  author={Zhao, Jiewen and Han, Ruize and Gan, Yiyang and Feng, Wei and Wan, Liang and Wang, Song},  
  year={2020},  
  booktitle={ACM International Conference on Multimedia}
}
```

## Introduction

<div align=center><img src="https://github.com/RuizeHan/CVID/blob/master/figs/example1.jpg" width="500" height="300" alt="example"/><br/>
<div align= justify>

Compared to a single fixed camera, multiple moving cameras, e.g., those worn by people, can better capture the human interactive and group activities in a scene, by providing multiple, flexible and possibly complementary views of the involved people. In this setting the actual promotion of the activity detection is highly dependent on the effective correlation and collaborative analysis of multiple videos taken by different wearable cameras, which is highly challenging given the time-varying view differences across different cameras and mutual occlusion of people in each video. By focusing on two wearable cameras and the interactive activities that involve only two people, in this paper we develop a new approach that can simultaneously: (i) identify the same persons across the two videos, (ii) detect the interactive activities of interest, including their occurrence intervals and involved people, and (iii) recognize the category of each interactive activity. Specifically, we represent each video by a graph, with detected persons as nodes, and propose a unified Graph Neural Network (GNN) based framework to jointly solve the above three problems. A graph matching network is developed for identifying the same persons across the two videos and a graph inference network is then used for detecting the human interactions. We also build a new video dataset, which provides a benchmark for this study, and conduct extensive experiments to validate the effectiveness and superiority of the proposed method.

## Method

![framework](https://github.com/RuizeHan/CVID/blob/master/figs/framework.jpg)
<div align= justify>
  
We provide an example to intuitively illustrate the proposed method as shown in above. Given a pair of synchronized video frames, we represent all the subjects in each frame as a complete graph by taking each subject as node and the relation between two subjects as edge. Then the initial graphs are first imported
into the GMN (b). The network iteratively updates the graph node representation by intra-graph and inter-graph embeddings, as shown in the left of subfigure (b).
After that, the similarity of every two nodes from different graphs is calculated to compose the affinity matrix. Through the Sinkhornoperation, the predicted permutation matrix is to compute the cross-entropy loss together with ground-truth permutation matrix. The matching results is used for the following
GIN (c), which also takes the initial graphs as input. As shown in the left of the subfigure (c), the networks iteratively update the adjacency
matrix (note the change of edge thickness) and node representation (note the change of node color).
Next, we combine the updated node representations of the same subject from different videos (using the matching results) for the interaction category recognition in the right of (c). For this purpose, we use an LSTM function layer to capture the temporal information followed by a fully connected layer to predict the
final interaction labels. 

Dataset: Link: https://pan.baidu.com/s/1ma3ll4EUIUlFKqibqb_KZA @ CVID

To get the annotation, please contact the authors. The dataset is only used for academic research.

Ruize Han (han_ruize@tju.edu.cn); Jiewen Zhao (zhaojw@tju.edu.cn); Yiyang Gan (realgump@tju.edu.cn).

