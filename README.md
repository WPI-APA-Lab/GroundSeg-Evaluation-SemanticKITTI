# ISICAS2024_GroundSeg_Evaluation_SemanticKITTI
Evaluation Framework for ground segmentation on SemanticKITTI dataset

# Motivation
The conventional evaluation metrics for semantic segmentation may not adequately address the distinct complexities associated with ground plane segmentation. These challenges include the non-uniform density of points at varying distances from the sensor, the necessity to circumvent biases introduced by projection methods, and the aspect of preserving geometric consistency throughout the segmentation process. This discrepancy is illustrated in the figure. Assuming a vertically mounted LiDAR sensor scanning an open area, the segmentation algorithm categorizes points into ground (green) and non-ground (red) classifications.

The left image in the figure offers a bird's-eye view of the detected ground plane, showcasing the areas identified as ground. Conversely, the right image displays how these classifications are represented in a range image, with a noticeable predominance of correctly detected ground points over non-ground ones. However, this representation masks a critical flaw: despite the apparent abundance of correctly identified ground points in the range image, the actual proportion of accurately detected ground area, as viewed from the bird's-eye perspective, falls below 50 percent. This discrepancy underscores the limitations of conventional evaluation metrics, which might not adequately reflect the true effectiveness of ground segmentation algorithms, especially in terms of spatial accuracy and distribution consistency. 

# Dataset

We utilized the SemanticKITTI as an example to evaluate the performance of ground segmentation (Remove). The dataset and directory setup can be referred to [here](http://www.semantic-kitti.org/dataset.html).

# How to run the code

We will release the code after the paper's publication.

# Metrics

## Range Image

$$
    \text{F1 Score} = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}
$$

Where, $\text{Precision}$ is defined as $\frac{TP}{TP + FP}$, with $\text{TP}$ being the number of true positives and $\text{FP}$ the number of false positives.
$\text{Recall}$ is defined as $\frac{TP}{TP + FN}$, with $\text{FN}$ the number of false negatives.

$$
     \text{IoU} = \frac{\text{Area of Overlap}}{\text{Area of Union}} = \frac{\text{TP}}{\text{TP} + \text{FP} + \text{FN}}
$$

## Bird Eye View
$$   \text{IoU-BEV} = \frac{\text{Poly-gt} \cap \text{Poly-pred} }{\text{Poly-gt} \cup \text{Poly-pred}}$$

# Evaluation Result
We take sequence 00 as an example, here is the evaluation result:
|    Method   | F1-RI | IoU-RI | IoU-BEV |
|:-----------:|:-----:|:------:|:-------:|
|    RANSAC   | 85.94 |  76.77 |  64.05  |
| DepthGround | 87.48 |  78.52 |  70.09  |
|     Ours    | 86.67 |  77.29 |  70.55  |

The video demonstration is shown here.


# HDL Implementation Demo
Our previous work has been published as an Example in Matlab 2023b. You could try it with HDL Coder and Vision HDL Toolbox. [Example](https://www.mathworks.com/help/visionhdl/ug/lidar-ground-segmentation.html)


