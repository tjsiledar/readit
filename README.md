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
<img src="figure2.png">

### The functional hierarchy of self-supervised wav2vec 2.0 maps to the speech hierarchy of the brain
<img src="figure3.png">

###  The specialization of wav2vec 2.0’s representations follows and clarifies the acoustic,speech, and language regions in the brain
<img src="figure4.png">
