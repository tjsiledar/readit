# Toward a realistic model of speech processing in the brain with self-supervised learning

Recent research has found that deep neural networks can produce similar results to the brain in response to the same input. However, neural networks have certain limitations, such as -
1. Requiring a large amount of data
2. Supervised labels
3. Textual input rather than raw sensory input
4. Large memory

To address these challenges in speech processing, we propose utilizing _self-supervised algorithms_ that are trained on raw waveform data. Our research demonstrates that this approach can create brain-like representations with just **600 hours of unlabeled speech**, a _similar_ exposure rate to that of _infants_ during language acquisition. The functional hierarchy of such algorithms align with the cortical hierarchy of speech processing, and various training methods reveal functional specialization that is comparable to the cortex. Our research confirms that this specialization is analogous to the behavior of additional participants.

Furthermore, we showcase how self-supervised learning can explicate the organization of speech processing in the brain and identify the language acquisition laws that shape the human brain.
<hr>

### Comparison of speech representations in brains and deep neural networks.
We test out hypothesis on a recent self-supervised model - <a href="https://www.google.com/search?client=safari&rls=en&q=wav2vec+2.0&ie=UTF-8&oe=UTF-8">wav2vec 2.0</a>. We observe that wav2vec 2.0, trained on raw sensory data, can produce activations similar to brain activity (Figure 1).
<p align="center">
    <img src="figure1.png" alt><br>
    <b>Figure 1</b>: <em>Comparing speech representations in brain and deep neural networks</em>
</p>

**Part A**: We recorded brain activity of **412** participants using functional Magnetic Resonance Imaging (fMRI) as they passively listened to audiobooks in their native language (English, French, or Mandarin).

**Part B**: We take the activations X of the self-supervised wav2vec 2.0 model trained on 600 hours of the same unlabelled speech data and the brain activity Y. We then measure the similarity between X and Y, by first transforming X using standard linear encoding model W and then evaluated using cross-validated Pearson correlation _R_ (also referred to as the brain score).

**Part C**: We observe that **_the true BOLD (blood oxygen level-dependent) response (black) and the predicted BOLD response (red) from our model are quite similar_** indicating that the representations learned by our model are closer to brain-like representations.

**Key Takeaway**: We map the activations obtained from the trained wav2vec 2.0 model to the brain activity and measure the similarity using Pearson correlation R (higher is better). Representations learned by our model map to those obtained from brain.
<hr>

### Can brain-like representations be generated using self supervised modeling?
We compare **three** different models. An _untrained wav2vec 2.0 model_, a model trained with a _self-supervised objective_, and a _supervised model_ trained for phonetic prediction from the same 600 hours of speech.
<p align="center">
    <img src="figure2.png" alt><br>
    <b>Figure 2</b>: <em>Self-supervised learning for wav2vec 2.0 is enough to generate brain-like representations</em>
</p>

**Part A**: Brain score R is calculated for each participant and voxel (a small volume of brain tissue) independently. Here we show the average scores across subjects using color coding. 

**Part B**: Shows the R scores for the same wav2vec 2.0 model, averaged across subjects and voxels in four brain areas typically involved in speech processing. The gray bar shows the brain score obtained with randomly initialized wav2vec 2.0 model, while the colored bars represent the scores obtained with the trained model. We observe that there is a significant difference between the random and the trained model indicating that the trained model is actually learning brain-like representations.

**Part C**: We compare unsupervised, supervised, and self supervised trained models on 600 hours of effective speech using R scores. We observe that self supervised model better corresponds to generating brain-like representations.

**Key Takeaway**: **_Brain activity in nearly all cortical areas can be predicted with significant accuracy based on the activations of the models. Self-supervision performs better than supervised._**
<hr>

### Is there a mapping between the functional hierarchy of the self-supervised models and the speech hierarchy of the brain?
Next, we try _mapping the functional hierarchy (model layers) of our self-supervised model with that of the speech hierarchy_ i.e speech related regions of brain such as A1 and A2 (Heschl gyrus), STG (superior temporal gyrus), STS (superior temporal sulcus), and IFG (inferior frontal gyrus).
<p align="center">
    <img src="figure3.png" alt><br>
    <b>Figure 3</b>: <em>The functional hierarchy of self-supervised wav2vec 2.0 maps to the speech hierarchy of the brain</em>
</p>

**Part A**: We compute the R scores for each layer of the wav2vec 2.0 model separately and then estimate for each voxel the layer with the highest brain score (averaged across all subjects). We observe that the lower layers (blue) of the transformer model correspond to the low-level auditory cortices i.e A1 and A2 whereas the higher layers (orange and red) correspond to the higher level processes i.e STS and IFG.

**Part B**: Layerwise R scores averaged across all voxels. Lower layers better correspond to lower cortical regions whereas higher layers better correspond to higher regions.

**Part C**: We measure the proportion of voxels predicted by the different layers of the model primarily in the four regions involved in speech processing- A1 and A2, STG, STS, and IFG. We observe that voxels belonging to the lower-level brain areas are best predicted by lower layers of the model whereas the higher-level brain areas are best predicted by higher layers of the model.

**Key Takeaway**: **_The hierarchy of representations from model layers aligns with the expected cortical hierarchy._** Lower regions (A1, A2) are best predicted by lower layers and higher regions (IFG, STS) are best predicted by higher layers.
<hr>

###  Can we use such self-supervised models to identify regions in brain that correspond to acoustic, speech, and language?
We compare the phonetic representations of our models to those of humans using ABX matching-to-sample task. For humans this meant for each sound triplet "ABX" identify whether stimulus X is more similar to A or B. For our models this just meant computing the euclidean distance between these using the most discriminative layer (transformer layer 5).
<p align="center">
    <img src="figure4.png" alt><br>
    <b>Figure 4</b>: <em>The specialization of wav2vec 2.0’s representations follows and clarifies the acoustic, speech, and language regions in the brain</em>
</p>

**Part A**: We use ABX matching-to-sample task to evaluate humans' ability to perceive phonemes of their native and non-native languages. As expected the accuracy for native is better than non-native.

**Part B**: We evaluate four models- random, non-speech, English, and French. The random model is the wav2vec 2.0 without any training whereas the other models are trained using self-supervision. These models are evaluated on the same evaluation set as that of human participants. English and French models are evaluated on the same (native) or different (non-native) whereas the random and non-speech are evaluated on both.

**Part C**: Here we report the R scores of these different models (averaged across voxels) in four regions of the brain.

**Part D**: Here we identify for each voxel in the brain which of the four models give a higher R score. This helps in identifying areas in brain that corresponds to acoustic, speech, and language.

**Key Takeaway**: Humans are better at discriminating native sounds than non-native sounds as expected. Applying the same discriminating test, **_our models also show similar discrimination for native and non-native, even better than humans_**. Results confirm that 600 hours of self supervised learning suffices for wav2vec 2.0 to learn language representations. 
<hr>

### Conclusion
Human infants can acquire language with little supervision in a few hundred hours of speech. Our study tests whether self-supervised learning on limited speech can explain the organization of speech processing in the human brain as measured by fMRI. Wav2vec 2.0 models trained on French, English, and Mandarin datasets are compared to fMRI recordings of French, English, and Mandarin speakers listening to audio stories. Our results show that this self-supervised model learns 
1. Representations that linearly map onto a remarkably distributed set of cortical regions (Figure 2)
2. A computational hierarchy that aligns with the cortical hierarchy (Figure 3)
3. Features specific to the language of the participants (Figure 4)

The human brain is complex and difficult to understand, and some believe that there is no simple theory to describe it. **_However, this work shows that self-supervised learning can lead to brain-like processes_**, challenging the belief that a simple theory cannot exist.

[Link to the original paper](https://openreview.net/pdf?id=Y6A4-R_Hgsw)
