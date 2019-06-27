[trump_twitter_archive]: http://www.trumptwitterarchive.com/archive "Trump Twitter Archive"
[wordcloud_twitter]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_english/figures/word_cloud_twitter.png "WordCloud image"
[wordcloud_104]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_chinese/figures/word_cloud_104.png "WordCloud image of website 104"

# Topic Modeling
- Analyze Trump's Tweet (English content).
- Analyze employment website 104 which content is a mixture of Chinese and English.

### Methods
- LDA(Latent Dirichlet Allocation) based on 
  - BOW (Bag-Of-Words).
  - TF-IDF(Term-Frequency-Inverse Document Frequency).
- The number of topics: 3


### Dataset
- [Trump Twitter Archive][trump_twitter_archive]: Date 2019/05/01 - 2019/05/31
  - Total number of tweets: 677
  
- [104 website](https://www.104.com.tw/jobs/search/?ro=0&kwop=7&keyword=machine%20learning&order=1&asc=0&page=1&mode=s&jobsource=2018indexpoc): Date 2019/06/25
  - Total number of jobs: 996
  - [Crawler program](https://github.com/Brandon-HY-Lin/topic_modeling/tree/master/crawler/employment_website_104)
  
### Results
- TF-IDF
  - Trump's Tweets
  
![WordCloud of Trump's twitter][wordcloud_twitter]


  - Empolyment website 104
  
  ![WordCloud of Employment Website 104][wordcloud_104]


