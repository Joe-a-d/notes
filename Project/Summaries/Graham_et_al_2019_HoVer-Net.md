source : [[Graham_et_al_2019_HoVer-Net.pdf]]
tags : 
related : 

# Short Summary
 
### Outline
 
- "Current manual assessment of Haematoxylin and Eosin (H&E) stained histology slides suffers from low throughput and is naturally prone to intraand inter-observer variability" [[Graham_et_al_2019_HoVer-Net.pdf#page=1|manual disadvantages]]

- "efficient processing, analysis and management of the tissue specimens" [[Graham_et_al_2019_HoVer-Net.pdf#page=1|automation advantages]]

- "nuclear segmentation must be carried out as an initial step. However, this remains a challenge because nuclei display a high level of heterogeneity and there is significant interand intra-instance variability in the shape, size and chromatin pattern between and within different cell types, disease types or even from one region to another within a single tissue sample. Tumour nuclei, in particular, tend to be present in clusters, which gives rise to many overlapping instances, providing a further challenge for automated segmentation, due to the difficulty of separating neighbouring instances." [[Graham_et_al_2019_HoVer-Net.pdf#page=1|challenges of nuclear seg]]

- "similar to nuclear segmentation, classifying the type of each nucleus is difficult, due to the high variance of nuclear appearance within each WSI." [[Graham_et_al_2019_HoVer-Net.pdf#page=1|nuclear classification similar problem]]

- "nuclei are classified using two disjoint models: one for detecting each nucleus and then another for performing nuclear classification [8], [9]. However, it would be preferable to utilise a single unified model for nuclear instance segmentation and classification" [[Graham_et_al_2019_HoVer-Net.pdf#page=1|states that a single model for both tasks is better. It doesn't say why]]

- "approach1 present a deep learning for simultaneous segmentation and classification of nuclear instances in histology images. The network is based on the prediction of horizontal and vertical distances (and hence the name HoVer-Net) of nuclear pixels to their centres of mass, which are subsequently leveraged to separate clustered nuclei" [[Graham_et_al_2019_HoVer-Net.pdf#page=1|main contribution intro]]

- "each segmented instance, the nuclear type is subsequently determined via a dedicated up-sampling branch. To the best of our knowledge, this is the first approach that achieves instance segmentation and classification within the same network" [[Graham_et_al_2019_HoVer-Net.pdf#page=2|new approach]]

- "The main contributions of this work are listed as follows: A novel network, targeted at simultaneous segmentation and classification of nuclei, where horizontal and vertical distance map predictions separate clustered nuclei. We show that the proposed HoVer-Net achieves state-of- the-art performance on multiple H&E histology image datasets, as compared to over a dozen recently published methods. An interpretable and reliable evaluation framework that effectively quantifies nuclear segmentation performance and overcomes the limitations of existing performance measures. dataset2 A new of 24,319 exhaustively annotated nuclei within 41 colorectal adenocarcinoma image tiles" [[Graham_et_al_2019_HoVer-Net.pdf#page=2|main contributions]]

- "energy-based methods, in particular the watershed algorithm, have been widely utilised to segment nuclear instances." [[Graham_et_al_2019_HoVer-Net.pdf#page=2|watershed algorithm as most common till now]]

- "thresholding relies on a consistent difference in intensity between the nuclei and background, which does not hold for more complex images" [[Graham_et_al_2019_HoVer-Net.pdf#page=2|why thresholding, hence watershed is no bueno]]

- "automatically extracting a representative set of features, that strongly correlate with the task at hand. As a result, they are preferable to hand-crafted approaches, that rely on a selection of pre-defined features." [[Graham_et_al_2019_HoVer-Net.pdf#page=2]]

- "U-Net [22] has been successfully applied to numerous segmentation tasks in medical image analysis. The network has an encoder-decoder design with skip connections to incorporate low-level information and uses a weighted loss function to assist separation of instances. However, it often struggles to split neighbouring instances and is highly sensitive to pre-defined parameters in the weighted loss function." [[Graham_et_al_2019_HoVer-Net.pdf#page=2|U-Net : overview and downsides]]

- "multiple resolutions and as a result, gains robustness against nuclei with varying size. In [24], the authors developed a network that is robust to stain variations in H&E images by introducing a weighted loss function that is sensitive to the Haematoxylin intensity within the image." [[Graham_et_al_2019_HoVer-Net.pdf#page=2|Others improved on U-net]]

- "DCAN [25] that utilised a dual architecture that outputs the nuclear cluster and the nuclear contour as two separate prediction maps. Instance segmentation is then achieved by subtracting the contour from the nuclear cluster prediction." [[Graham_et_al_2019_HoVer-Net.pdf#page=2|DCAN : nuclear contour strategy overview]]

- "[31] proposed a deep learning approach to detect superior markers for watershed by regressing the nuclear distance map. Therefore, the network avoids making a prediction for areas with indistinct contours." [[Graham_et_al_2019_HoVer-Net.pdf#page=2|Other : DL approach]]

- "the field of instance segmentation within natural images is also rapidly progressing and have had a significant influence on nuclear instance segmentation methods. A notable example is Mask-RCNN [32], where instance segmentation approach is achieved by first predicting candidate regions likely to contain an object and then deep learning based segmentation within those proposed regions." [[Graham_et_al_2019_HoVer-Net.pdf#page=2|MASK-RCNN : influence of field of natural image instance segmentation]]

- "Typically, classifying each nucleus is done via a two-stage approach, where the first step involves either nuclear segmentation or nuclear detection. When segmentation is used as the initial step, a series of morphological and textural features are extracted from each instance, which are then used within a classifier to determine the nuclei classes." [[Graham_et_al_2019_HoVer-Net.pdf#page=3|Nuclear classification : 1 step of 2-step approach. Segment ⇒ get features ⇒ use features in some classifier (e.g. AdaBoost) to determine the classes]]

- "Otherwise, detection is performed as an initial step and a patch centred at the point of detection is fed into a classifier, to predict the type of nucleus" [[Graham_et_al_2019_HoVer-Net.pdf#page=3]]

- "simultaneously segment nuclear instances and obtain the corresponding nuclear types. The framework is based upon the horizontal and vertical distance maps, which can be seen in Fig. 3. In the figure, each nuclear pixel denotes either the horizontal or vertical distance of pixels to their centres of mass." [[Graham_et_al_2019_HoVer-Net.pdf#page=3|introduction new method]]

- "feature extraction component of the network is inspired by the pre-activated residual network with 50 layers [36] (Preact-ResNet50), due to its excellent performance in recent computer vision tasks [37] and robustness against input perturbation" [[Graham_et_al_2019_HoVer-Net.pdf#page=3|feature extraction component of the network inspiration]]

- "Following Preact-ResNet50, we perform nearest neighbour up-sampling via three distinct branches to simultaneously obtain accurate nuclear instance segmentation and classification. We name the corresponding branches: (i) nuclear pixel (NP) branch; (ii) HoVer branch and (iii) nuclear classification (NC)" [[Graham_et_al_2019_HoVer-Net.pdf#page=3|3-branching nearest neighbour up-sampling]]

- "The NP branch predicts whether or not a pixel belongs to the nuclei or background, whereas the HoVer branch predicts the horizontal and vertical distances of nuclear pixels to their centres of mass. Then, the NC branch predicts the type of nucleus for each pixel. In particular, the NP and HoVer branches jointly achieve nuclear instance segmentation by first separating nuclear pixels from the background (NP branch) and then separating touching nuclei (HoVer branch). The NC branch determines the type of each nucleus by aggregating the pixel-level nuclear type predictions within each instance" [[Graham_et_al_2019_HoVer-Net.pdf#page=4|what each branch of NN up-sampling algo does]]

- "1) Loss Function: The proposed network design has 4 different sets of weights: , , and which refer to w0 w1 w2 w3 the weights of the Preact-ResNet50 encoder, the HoVer branch decoder, the NP branch decoder and the NC branch decoder." [[Graham_et_al_2019_HoVer-Net.pdf#page=4|Loss function]]

- "It must be noted that the NC branch loss and are only Le Lf calculated when the classification labels are available. In other words, as mentioned in Section III-A, the network performs only instance segmentation if there are no classification labels given." [[Graham_et_al_2019_HoVer-Net.pdf#page=6|loss function, not all elements computed if labels don't exist]]

- "Within each horizontal and vertical map, pixels between separate instances have a significant difference. This can be seen in Fig. 3 and is highlighted by the arrows. Therefore, calculating the gradient can inform where the nuclei should be separated because the output will give high values between neighbouring nuclei, where there is a significant difference in the pixel values." [[Graham_et_al_2019_HoVer-Net.pdf#page=6|post-processing: calculating the gradient to identify significant differences between the neighboring cells, i.e. the segmentation region between two nuclei]]

- "preferable to break the problem into sub-tasks and measure the performance of the method on each sub-task." [[Graham_et_al_2019_HoVer-Net.pdf#page=6|they use different metrics for each sub-task]]

- "For nuclear instance segmentation, the problem can be divided into the following three sub-tasks: Separate the nuclei from the background Detect individual nuclear instances Segment each detected instance " [[Graham_et_al_2019_HoVer-Net.pdf#page=7|nuclear segmentation subtasks]]

- "Ensemble Dice (DICE2) [30], and 2) Aggregated Jaccard Index (AJI)" [[Graham_et_al_2019_HoVer-Net.pdf#page=7|current popular metrics]]

- "only provide an overall score for the instance segmentation quality and therefore provides no further insight into the sub-tasks at hand. In addition, these two metrics have a limitation, which we illustrate in Fig. 4. From the figure, although prediction A only differs from prediction B by a few pixels, the DICE2 and AJI scores for B are inferior. These scores are shown in Table I. This problem arises due to over-penalisation of the overlapping regions" [[Graham_et_al_2019_HoVer-Net.pdf#page=7]]
- [[Graham_et_al_2019_HoVer-Net.pdf#page=7]]_

- "Panoptic Quality: We propose to use another metric for accurate quantification and interpretability to assess the performance of nuclear instance segmentation. Originally proposed by [40], panoptic quality (PQ) for nuclear instance segmentation is defined as:" [[Graham_et_al_2019_HoVer-Net.pdf#page=7|PQ, the new metric]]

- "Overall, to fully characterise and understand the performance of each method, we use the following three metrics: 1) DICE to measure the separation of all nuclei from the background; 2) Panoptic Quality as a unified score for comparison publications3 and 3) AJI for direct comparison with previous" [[Graham_et_al_2019_HoVer-Net.pdf#page=7|summary of seg metrics]]

- "We chose to focus on a single cancer type, so that we are able to display the true variation of tissue within colorectal adenocarcinoma WSIs, as opposed to other datasets that instead focus on using a small number of visual fields from various cancer types." [[Graham_et_al_2019_HoVer-Net.pdf#page=8|dataset only single cancer type]]

- "different nuclei types were present," [[Graham_et_al_2019_HoVer-Net.pdf#page=8|dataset has different nuclei types]]

- "every nucleus was annotated by one of two expert pathologists (A.A, Y-W.T). After full annotation, each annotated sample was reviewed by both of the pathologists; therefore refining their own and each others' annotations. By the end of the annotation process, each pathologist had fully checked every sample and consensus had been reached." [[Graham_et_al_2019_HoVer-Net.pdf#page=8|dataset, methodology involved 2 experts manually anotating]]

- "TensorFlow version 1.8.0 [41] on a workstation equipped with two NVIDIA GeForce 1080 Ti GPUs." [[Graham_et_al_2019_HoVer-Net.pdf#page=8|implementation : hardware, software]]

- "we initialised the model with pre-trained weights on the ImageNet dataset [37], trained only the decoders for the first 50 epochs, and then fine-tuned all layers for another 50 epochs. We train stage one for around 120 minutes and stage two for around 260 minutes. Therefore, the overall training time is around 380 minutes." [[Graham_et_al_2019_HoVer-Net.pdf#page=8|implementation, transfer learning from ImageNet ; training times]]

- "For this experiment, because we do not have the classification labels for all datasets, we perform instance segmentation without classification." [[Graham_et_al_2019_HoVer-Net.pdf#page=8|methodology for evaluation; seg only for the above datasets]]

- "We compared our proposed model to recent segmentation approaches used in computer vision [21], [44], [32], medical imaging [22] and also to methods specifically tuned for the task of nuclear segmentation [25], [23], [31], [29], [30]. We also compared the performance of our model to two open source software applications" [[Graham_et_al_2019_HoVer-Net.pdf#page=9|methodology for evaluation; comparison against various methods]]

- "tion is particularly evident in the Kumar and CoNSeP datasets, where there exists a large number of overlapping nuclei varia-" [[Graham_et_al_2019_HoVer-Net.pdf#page=10|seg comparison results; large variation due to a lot of overlapping nuclei]]

- "Due to the reasoning given in Section IV, we place a larger emphasis on PQ to determine the success of different models. In particular, we consistently obtain an improved performance over DIST, which justifies the use of our proposed horizontal and vertical maps as a regression target. We also report a better performance than the winners of the Computational Precision Medicine and MoNuSeg challenges [30], [29], that utlised the CPM-17 and Kumar datasets respectively. Therefore, HoVerNet achieves state-of-the art performance for nuclear instance segmentation compared to all competing methods on multiple datasets that consist of a variety of different tissue types. Our approach also outperforms methods that were fine-tuned for the task of nuclear segmentation." [[Graham_et_al_2019_HoVer-Net.pdf#page=11|seg results summary]]

- "large scale study to assess how all methods generalise to new H&E stained images. To analyse the generalisation capability, we assessed the ability to segment nuclei from: i) new organs (variation in nuclei shapes) and ii) different centres (variation in staining)." [[Graham_et_al_2019_HoVer-Net.pdf#page=11|methadology; generalisation study]]

- "We used Kumar as the training and validation set, due to its size and diversity, whilst the combined CPM (CPM-15 and CPM-17), TNBC and CoNSeP datsets were used as three independent test sets. We split the test sets in this way in accordance with their origin." [[Graham_et_al_2019_HoVer-Net.pdf#page=11|test ; val set justification]]

- "Therefore, testing with CPM reflects the ability for the model to generalise to new organs, as mentioned above by the first generalisation criterion." [[Graham_et_al_2019_HoVer-Net.pdf#page=11|why testing with this dataset is good to prove generalistation w.r.t new organs, i.e. different nuclei shapes]]

- "Therefore, this reflects the second generalisation criterion" [[Graham_et_al_2019_HoVer-Net.pdf#page=11|TNBC for different centres criteria]]

- "We observe that our proposed model is able to successfully generalise to unseen data in all three cases." [[Graham_et_al_2019_HoVer-Net.pdf#page=11|results of generalisation Positive]]

- "SegNet proves to successfully detect nuclear pixels, reporting a greater DICE score than HoVerNet on both the TNBC and CoNSeP datasets. However, the overall segmentation result for HoVer-Net is superior because it is better able to separate nuclear instances by incorporating" [[Graham_et_al_2019_HoVer-Net.pdf#page=11|SegNet superior in a narrow way; but Hover does best overall due to the horiz/vertical map approach]]

- "We converted the top four performing nuclear instance segmentation algorithms, based on their panoptic quality on the CoNSeP dataset, such that they were able to perform simultaneous instance segmentation and classification" [[Graham_et_al_2019_HoVer-Net.pdf#page=13|classification eval method]]

- "because SC-CNN does not produce a segmentation mask, we do not report the PQ for this method." [[Graham_et_al_2019_HoVer-Net.pdf#page=14|why PQ is missing on one of the models being compared]]

- "that we should expect a lower F1 score for the miscellaneous class because there are significantly less nuclei represented" [[Graham_et_al_2019_HoVer-Net.pdf#page=14|why F1 scores are overall lower]]

- "HoVer-Net is able to achieve a satisfactory performance on this class, where other methods fail." [[Graham_et_al_2019_HoVer-Net.pdf#page=14|++Hover]]

- "we suggest that our model may be used for sophisticated subsequent cell-level downstream analysis in computational pathology" [[Graham_et_al_2019_HoVer-Net.pdf#page=14|possible application of Hover]]

- "In this paper, we have proposed HoVer-Net for simultaneous segmentation and classification of nuclei within multitissue histology images that not only detects nuclei with high accuracy, but also effectively separates clustered nuclei. Our approach has three up-sampling branches: 1) the nuclear pixel branch that separates nuclear pixels from the background; 2) the HoVer branch that regresses the horizontal and vertical distances of nuclear pixels to their centres of mass and 3) the nuclear classification branch that determines the type of each nucleus. We have shown that the proposed approach achieves the state-of-the-art instance segmentation performance compared to a large number of recently published deep learning models across multiple datasets, including tissues that have been prepared and stained under different conditions." [[Graham_et_al_2019_HoVer-Net.pdf#page=14|summary of main contributions and performance]]

- "therefore be effectively used as a prerequisite step before nuclear-based feature extraction. We have shown that utilising the horizontal and vertical distances of nuclear pixels to their centres of mass provides powerful instance-rich information, leading to state-of-the-art performance in histological nuclear segmentation." [[Graham_et_al_2019_HoVer-Net.pdf#page=14|summary of other results]]

- "segment and" [[Graham_et_al_2019_HoVer-Net.pdf#page=14]]

- "show that our model is able to successfully segment and classify nuclei with high accuracy." [[Graham_et_al_2019_HoVer-Net.pdf#page=14|classification summary when labels available]]

- "Region proposal (RP) methods, such as Mask-RCNN, show great potential in dealing with overlapping instances because there is no notion of separating instances; instead nuclei are segmented independently. However, a major limitation of the RP methods is the difficulty in merging instance predictions between neigbouring tiles during processing." [[Graham_et_al_2019_HoVer-Net.pdf#page=14|How RP methods suchas as Mask-RCNN do well in the case of overlapping nuclei, but have a major limitation]]

- "approximately 9.7 faster. On the other hand, the average processing time for DIST and Micro-Net was 0.600 and 0.832 seconds respectively. Mask-RCNN" [[Graham_et_al_2019_HoVer-Net.pdf#page=15|runtime comparison]]

- "Future work will explore the trade-off between the efficiency of HoVer-Net and its potential to accurately perform instance segmentation and classification." [[Graham_et_al_2019_HoVer-Net.pdf#page=15|future work]]

- "major bottleneck for the development of successful nuclear segmentation algorithms is the limitation of data; particularly with additional associated class labels. In this work, we introduce the colorectal adenocarcinoma nuclear segmentation and phenotypes (CoNSeP) dataset, containing over 24K labelled nuclei from challenging samples to reflect the true difficulty of segmenting nuclei in whole-slide images. Due to the abundance of nuclei with an associated nuclear category, CoNSeP aims to help accelerate the development of further simultaneous nuclear instance segmentation and classification models to further increase the sophistication of cell-level analysis within computational pathology" [[Graham_et_al_2019_HoVer-Net.pdf#page=15|how the contribution of the dataset will help the field. Since a major bottleneck is the lack of labeled data]]

- "We encourage researchers to utilise the proposed measures to not only maximise the interpretability of their results, but also to perform a fair comparison with other methods." [[Graham_et_al_2019_HoVer-Net.pdf#page=15|metric contribution]]

- "Utilising our model for nuclear segmentation and classification enables the exploration of the spatial relationship between various nuclear types combined with nuclear morphological features and therefore may provide additional diagnostic and prognostic value. Currently, our model is trained on a single tissue type, yet due to the strong performance of our instance segmentation model across multiple tissues, we are confident that our model will" [[Graham_et_al_2019_HoVer-Net.pdf#page=15|confidence on generalisation]]

- "Future work will involve obtaining more samples within this category, including necrotic and mitotic nuclei, to improve the class balance of the data" [[Graham_et_al_2019_HoVer-Net.pdf#page=15|future work; expanding to new types of nuclei to improve class balance of the data]]

# Main Contributions

# Problem addressed

# Results

# Conclusion

# Methodology

# Learned

# Why read?