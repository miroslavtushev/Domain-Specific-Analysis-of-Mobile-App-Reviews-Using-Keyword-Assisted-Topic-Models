# Domain-Specific-Analysis-of-Mobile-App-Reviews-Using-Keyword-Assisted-Topic-Models

This repository contains the replication package for my ICSE'22 paper along with a small case study.

![download](https://user-images.githubusercontent.com/14366682/144515270-0c4f8b7f-4220-4110-9896-50f2c3859151.png)

![approach1](https://user-images.githubusercontent.com/14366682/144684413-8d56af42-dc5c-4d4a-8dda-10947c86516b.png)

## Abstract
Mobile application (app) reviews contain valuable information for app developers. A plethora of supervised and unsupervised techniques have been proposed in the literature to synthesize useful user feedback from app reviews. However, traditional supervised classification algorithms require extensive manual effort to label ground truth data, while unsupervised text mining techniques, such as topic models, often produce suboptimal results due to the sparsity of useful information in the reviews. To overcome these limitations, in this paper, we propose a fully automatic and unsupervised approach for extracting useful information from mobile app reviews. The proposed approach is based on keyATM, a keyword-assisted approach for topic modeling. keyATM overcomes the problem of data sparsity by using seeding keywords extracted directly from the review corpus. These keywords are then used to generate meaningful domain-specific topics. Our approach is evaluated over two datasets of mobile app reviews sampled from the domains of Investing
and Food Delivery apps. The results show that our approach significantly outperforms traditional topic modeling techniques by producing more coherent topics.

## Repository Structure
The replication code is split into 5 notebooks:

- **1_data_collection.ipynb** contains the code for collecting app reviews for the two domain of apps.
- **2_data_preprocessing.ipynb** describes the text preprocessing steps.
- **3_wiki_corpus_generation.ipynb** outlines how to generate a wikipedia binary sparse matrix for extrinsic evaluation of my approach.
- **4_topic_modeling.ipynb** contains the actual algorithm for summarization topic modeling.
- **5_results_and_visualization.ipynb** plots the results and applies a statistical test to calculate the difference between my approach and LDA.

Additional files are provided:

`food.csv` and `investing.csv` -> user review datasets.

`scores` folder -> results for each keyATM configuration and LDA for each *number of topics* value in pickle format.

`stop_words.txt` -> additional cohort-specific stop-words.

## Additional Considerations
To fully replicate our study, you will need to install several 3rd party packages:
- [keyATM](https://keyatm.github.io/keyATM/) 
- [rpy2](https://rpy2.github.io/)
- [hybrid tf-idf](https://pypi.org/project/hybridtfidf/)
- [app_store_scraper](https://pypi.org/project/app-store-scraper/) and [google_play_scraper](https://pypi.org/project/google-play-scraper/)
- Additional packages (numpy, pandas, scipy, etc.) which may or may not be already installed on your machine.

Using extrinsic evaluation and training a keyATM model is costly. For that reason, a binary matrix is generated for faster word lookup and the NPMI calculation is optimized to save time and resources. Nevertheless, to comfortably execute all the scripts, you need at least 64GB RAM and several days of time. The training can take hours, especially for a large number of topics and a large dataset (food delivery). To quickly verify that everything works, use smaller number of topics and limit the dataset size by using fin_texts[:5000], as an example.
