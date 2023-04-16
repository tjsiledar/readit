# Toward a realistic model of speech processing in the brain with self-supervised learning

Recent research has found that deep neural networks can produce similar results to the brain in response to the same input. However, these algorithms have certain limitations, such as 
1. requiring a large amount of data 
2. supervised labels
3. textual input rather than raw sensory input
4. large memory

This study proposes using self-supervised algorithms trained on raw waveform data as a solution for speech processing. The results show that this method can learn brain-like representations with only 600 hours of unlabelled speech, which is comparable to what infants are exposed to during language acquisition. The functional hierarchy of the algorithm aligns with the cortical hierarchy of speech processing, and different training regimes reveal functional specialization similar to the cortex. The study confirms that this specialization is similar to the behavior of additional participants. This research shows how self-supervised learning can explain the organization of speech processing in the brain, and can identify the laws of language acquisition that shape the human brain.

### Comparison of speech representations in brains and deep neural networks
<p>
    <img src="figure1.png" alt><br>
    <em>Figure 1: Comparing speech representations in brain and deep neural networks</em>
</p>

**Part A**: We recorded brain activity of 412 participants using functional Magnetic Resonance Imaging (fMRI) as they passively listened to audio books in their native language (English, French or Mandarin)

**Part B**: We take the activations X of the self-supervised wav2vec 2.0 model trained on 600 hrs of unlabelled data and the brain activity Y. We then measure the similarity between X and Y using standard encoding model W and evaluated using cross-validated Pearson correlation R.

**Part C**: We observe that the true BOLD (blood oxygen level-dependent) response (black) and the predicted BOLD reponse (red) from our model are quite similar indicating that the representations learned by our model are closer to brain-like representations.

### Self supervised wav2vec 2.0 generates brain-like speech representations
<p>
    <img src="figure2.png" alt><br>
    <em>Figure 2: Self-supervised learning for wav2vec 2.0 is enough to generate brain-like representations</em>
</p>

**Part A**: Brain score R is calculated for each participant and voxel independently. Here we show the average scores across subjects using color coding. 

**Part B**: Shows the R scores for the same wav2vec 2.0 model, averaged across subjects and voxels in four brain areas typically involved in speech processing. The gray bar shows the brain score obtained with randomly initialized wav2vec 2.0 model, while the colored bars represent the scores obtained with the trained model. We observe that there is a significant difference between the random and the trained model indicating that the trained model is actually learning the brain-like representations.

**Part C**: 


### The functional hierarchy of self-supervised wav2vec 2.0 maps to the speech hierarchy of the brain
<p>
    <img src="figure3.png" alt><br>
    <em>Figure 3: The functional hierarchy of self-supervised wav2vec 2.0 maps to the speech hierarchy of the brain</em>
</p>

**Part A**: We compute the R scores for each layer of the wav2vec 2.0 model separately and then estimate for each voxel the layer with the highest brain score (averaged across all subjects). We observe that the lower layers (blue) of the transformer model correspond to the low-level auditory cortices i.e A1 and A2 whereas the higher layers (orange and red) correspond to the higher level processes i.e STS and IFG.

**Part B**: Layerwise R scores averaged across all voxels.

**Part C**: We measure the proportion of voxels predicted by the different layers of the model primarily in the four regions involved in speech processing- A1 and A2, STG, STS, and IFG. We observe that voxels belonging to the lower-level brain areas are best predicted by lower layers of the model whereas the higher-level brain areas are best predicted by higher layers of the model.

###  The specialization of wav2vec 2.0’s representations follows and clarifies the acoustic,speech, and language regions in the brain
<img src="figure4.png">
