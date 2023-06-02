# Multiversal pictures

The repository for project at Deep Natural Language Processing at Skoltech - "Multiversal pictures".

The objective of this research addresses the widespread dissemination of misleading information on the internet, which can have significant and irreparable repercussions. The development of technology capable of detecting fake news is necessary to combat this issue. However, existing approaches have limitations, as they rely only on textual information and lack visual evidence.

To address this problem, we propose a new feature called Multiversal pictures, which is based on multimodal evidence. Our hypothesis proposes that pictures can serve as evidence for fake news detection and improve existing methods. We use a technique called Multiverse, which is introduced by Dementieva D. et al., as our baseline and collect multilingual textual data through Google search and supplement it with images obtained using the same method. We utilize the CLIP model to get embeddings for images which are relevant to text of article. Cosine similarities between picture embeddings for different languages added as features for classification. This similarity might serve as a powerful feature to distinguish fake news.

We expected that our approach increases the accuracy of fake news detection compared to existing methods.

## Dataset

We have experimented with a dataset Celebrity proposed by [Veronica Perez-Rosas et al., 2017](https://arxiv.org/pdf/1708.07104v1.pdf). This dataset contains 250 fake and 250 legit news.

## What were done

**1. News translation**
We translate news from the original language - English, to the 4 other languages - Deutsch, Español, French, Russian. We utilize GoogleTranslator API to automize the process of translation.
**2. Image retrieving**
For all five languages we retrieve images related to the headings of the news. By default, we download 10 images for each case, however for some requests there are exist less then 10 relevant images. Also, we experiment only with a subset of the initial dataset - 35 fake and 35 legit news. To do so, we use GoogleSearch API. The resulting images can be found [here](https://drive.google.com/drive/folders/1gF5rgNA-hEEVk_0VBkO4z9BQ9xZ5JZB0?usp=sharing).
**3. Feature extraction**
We calculate embeddings for the each image through CLIP model with ViT/B32 as a backbone.
**4. Similarity calcucaltion**
Finally, to validate our hypothesis, we measure the cosine similarity between vector representations for the original language and embeddings for the other languages. For each pair of languages we average the similarities.

## Results

fake | en-de | en-es | en-fr | en-ru
|--- | --- | --- | --- | --- |
0 | 0.6363 | 0.6478 | 0.6541 | 0.5484
1 | 0.5799 | 0.6335 | 0.6285 | 0.5767

Table 1. Cosine similarity scores between images for the original headings and headings which were translated to the other languages.

fake | score
| --- | --- |
0 | 0.6217
1 | 0.6046

Table 2. Averaged cosine similarity scores between fake and legit news.

## Conclusions
- Seems like image features actually can help with fake detection task, because similarities for legit news is higher then for fake news
- Results should be validated on other datasets datasets. Images for news about celebrities typically contains themselves without any connection with truth nature of the news. Also our train sample doesn't fully cover the Celebrity dataset, so it should be extended
- CLIP similarities might be added to the feature set

## Team:
- Alexander Kharitonov
- Alina Bogdanova
