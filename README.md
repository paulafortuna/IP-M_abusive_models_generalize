# IP-M_abusive_models_generalize

This repository aims at centralizing the code used to support the paper:



In this work we test the generalization of models trained with abusive and harms related datasets.
As this was a very complex set of experiments with different phases, this here we organize different repositories.
(Next time I will try to do a more organized software engineer tidy approach :).

## Datasets

For these experiments there are some needed datasets. These are not provided on my repository but only listed here instead: [W&H](https://github.com/ZeerakW/hatespeech), [Davidson](https://github.com/t-davidson/hate-speech-and-offensive-language), [Ami](http://ceur-ws.org/Vol-2150/overview-AMI.pdf), [TRAC](https://www.aclweb.org/anthology/W18-4407.pdf), [Hateval](https://www.aclweb.org/anthology/S19-2007.pdf), [Kaggle](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge), [Stormfront](https://github.com/Vicomtech/hate-speech-dataset) and [Founta](https://zenodo.org/record/2657374)
I also provide a repository where I've conducted some data manipulation for dataset preparation.

For dataset division we kept only train tests when such a division existed. We also use a schema for standardized category conversion:

| dataset    | st category       | train total N | test total N | train total pos | train perc positive |
|------------|-------------------|---------------|--------------|-----------------|---------------------|
| w h        | sexism            | 11835         | 5073         | 2407            | 0.203               |
| w h        | racism            | 11835         | 5073         | 1377            | 0.116               |
| w h        | hate speech       | 11835         | 5073         | 3784            | 0.320               |
| davidson   | hate speech       | 17348         | 7435         | 2856            | 0.165               |
| davidson   | offense           | 17348         | 7435         | 13517           | 0.779               |
| davidson   | toxicity          | 17348         | 7435         | 16373           | 0.944               |
| ami        | sexism            | 2800          | 1200         | 1249            | 0.446               |
| trac       | covert aggression | 12000         | 3000         | 4240            | 0.353               |
| trac       | overt aggression  | 12000         | 3000         | 2708            | 0.226               |
| trac       | ov cov aggression | 12000         | 3000         | 6948            | 0.579               |
| hateval    | hate speech       | 9000          | 1000         | 3783            | 0.420               |
| hateval    | aggressive hs     | 9000          | 1000         | 1559            | 0.173               |
| kaggle     | toxicity          | 111699        | 47872        | 10754           | 0.096               |
| kaggle     | hate speech       | 111699        | 47872        | 985             | 0.009               |
| kaggle     | severe toxicity   | 111699        | 47872        | 1129            | 0.010               |
| kaggle     | insult            | 111699        | 47872        | 5579            | 0.050               |
| kaggle     | obscene           | 111699        | 47872        | 6003            | 0.054               |
| kaggle     | threat            | 111699        | 47872        | 330             | 0.003               |
| stormfront | hate speech       | 3501          | 1500         | 705             | 0.201               |
| offenseval | toxicity          | 13240         | 860          | 4400            | 0.332               |
| founta     | hate speech       | 64366         | 27587        | 2899            | 0.045               |
| founta     | abusive           | 64366         | 27587        | 14491           | 0.225               |
| founta     | toxicity          | 64366         | 27587        | 17390           | 0.270               |

## Experiment 1 - Intra dataset classification

In this experiment we use BERT, ALBERT, fastText and SVM for intra dataset binary classification on the classes described previously.
We used for this the following implementations:
- SVM
- fastText
- BERT
- ALBERT

## Experiment 2 - Cross dataset classification

In this experiment we use the same models developed in experiment 1 with BERT, ALBERT, fastText and SVM for testing it with data from the remaining classes from the other datasets.

## Experiment 3 - Model generalization prediction with a Random Forest

The results of experiment 2 are now used to build a dataset, together with descriptives on the datasets and models.
This dataset and applied Random Forest Model can be found in the following repository:
- Predicting model generalization with a random forest.

## Experiment 4 - Intra and cross dataset Multilingual Classification.

Finally, we conducted some multilingual experiment with the following datasets:

|             | Considered class | Instances used for training | Instances used for testing |
|-------------|------------------|-----------------------------|----------------------------|
| Ami_sex_En  | Misogynous       | 2800                        | 1200                       |
| Ami_sex_It  | Misogynous       | 2800                        | 1200                       |
| Ami_sex_Sp  | Misogynous       | 2314                        | 993                        |
| Fort_sex_Pt | Sexism           | 3968                        | 1702                       |
| W&H_sex_En  | Sexism           | 11835                       | 5073                       |

For models we applied Multilingual BERT.
