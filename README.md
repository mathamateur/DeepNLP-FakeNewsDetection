# Multiversal pictures

The repository for project at Deep Natural Language Processing at Skoltech - "Multiversal pictures".

The objective of this research addresses the widespread dissemination of misleading information on the internet, which can have significant and irreparable repercussions. The development of technology capable of detecting fake news is necessary to combat this issue. However, existing approaches have limitations, as they rely only on textual information and lack visual evidence.

To address this problem, we propose a new feature called Multiversal pictures, which is based on multimodal evidence. Our hypothesis proposes that pictures can serve as evidence for fake news detection and improve existing methods. We use a technique called Multiverse, which is introduced by Dementieva D. et al., as our baseline and collect multilingual textual data through Google search and supplement it with images obtained using the same method. We utilize the CLIP model to get embeddings for images which are relevant to text of article. Cosine similarities between picture embeddings for different languages added as features for classification. This similarity might serve as a powerful feature to distinguish fake news.

We expected that our approach increases the accuracy of fake news detection compared to existing methods.

## What were done

1. Image retrieving
2. Feature extraction
3. Similarity calcucaltion

## Main results

fake | en-de | en-es | en-fr | en-ru
|--- | --- | --- | --- | --- |
0 | 0.6609 | 0.6239 | 0.6390 | 0.5214
1 | 0.5816 | 0.6858 | 0.6461 | 0.5265

## Conclusion
- Image features doesn't show significant correlation with truth nature
- Results should be validated on more datasets
- CLIP similarities may be added to the feature set

## Team:
- Alexander Kharitonov
- Alina Bogdanova
