[trump_twitter_archive]: http://www.trumptwitterarchive.com/archive "Trump Twitter Archive"
[wordcloud_twitter]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_english/figures/word_cloud_twitter.png "WordCloud image"
[wordcloud_104]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_chinese/figures/word_cloud_104.png "WordCloud image of website 104"

# Topic Modeling
- To uderstand what's inside Trump's mind by analyze his tweets (English contents).
- To catch the buzzwords in machine learning jobs by analyzing the employment website 104 (which contents are a mixture of Chinese and English).

### Methods
- LDA(Latent Dirichlet Allocation) based on 
  - BOW (Bag-Of-Words).
  - TF-IDF(Term-Frequency-Inverse Document Frequency).

### Dataset
- [Trump Twitter Archive][trump_twitter_archive]: Date 2019/05/01 - 2019/05/31
  - Total number of tweets: 677
  
- [104 website](https://www.104.com.tw/jobs/search/?ro=0&kwop=7&keyword=machine%20learning&order=1&asc=0&page=1&mode=s&jobsource=2018indexpoc): Date 2019/06/25
  - Total number of jobs: 996
  - [Crawler program](https://github.com/Brandon-HY-Lin/topic_modeling/tree/master/crawler/employment_website_104) is alow implemented by using BeautifulSoup.
  
### Hyper-parameters
  - Trump's twitts
    - The number of topics: 3
  - Employment website 104
    - The number of topics: 10
    - The number of passes (similar to #batches): 20
    - no_below (low frequency word count): 6
    - no_above (high frequency word ratio): 0.1

### Results
- TF-IDF
  - Trump's Tweets
  
  ![WordCloud of Trump's twitter][wordcloud_twitter]


  - Empolyment website 104
  
  ![WordCloud of Employment Website 104][wordcloud_104]


### Key APIs
- Tokenizer
  - English: gensim.utils.simple_preprocess(doc)
  - Chinese/English: gieba.cut(doc)
  
- Stopwords
  - English: gensim.parsing.preprocessing.STOPWORDS
  - Chinese: (Need to be defined by user)
  
- Dictionary:
  - gensim.corpora.Dictionary(docs)
  
- Strip Common/Rare Words
  - gensim.corpora.Dictionary(docs).filter_extremes(no_below, no_above)
  
- BOW
  - gensim.corpora.Dictionary(docs).doc2bow(doc)
  
- TF-IDF Transform
  - gensim.models.TfidfModel(bows)[bows]
  
- LDA
  - gensim.models.LdaModel(corpus)
  
- WordCloud
  - wordcloud.WordCloud().generate(text)
