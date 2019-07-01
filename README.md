[trump_twitter_archive]: http://www.trumptwitterarchive.com/archive "Trump Twitter Archive"
[wordcloud_twitter]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_english/figures/word_cloud_twitter.png "WordCloud image"
[tsne_tfidf_twitter]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_english/figures/tsne_tfidf.png "t-SNE of TF-IDF"
[wordcloud_104]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_chinese/figures/word_cloud_104.png "WordCloud image of website 104"
[pyldavis_twitter]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_english/figures/pyLDAvis_bow_trump_tweets.png "Pyldavis of Trump's tweets"
[tsne_tfidf_104]: https://github.com/Brandon-HY-Lin/topic_modeling/blob/master/lda_chinese/figures/tsne_tfidf_104.png "t-SNE of TF-IDF"

# Topic Modeling
- To uderstand what's inside Trump's mind by analyze his tweets (English contents).
- To catch the key words in machine learning jobs by analyzing the employment website 104 (which contents are a mixture of Chinese and English).

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
  - Chinese font for WordCloud
    - [Google Onto Fonts](https://www.google.com/get/noto/)

### Results
- TF-IDF
  - Trump's Tweets
    - Keywords
    
    ![WordCloud of Trump's twitter][wordcloud_twitter]
    
    - t-SNE upon the result of TF-IDF
      ![t-SNE of TF-IDF][tsne_tfidf_twitter]

  - Empolyment website 104
    - Keywords
    
    ![WordCloud of Employment Website 104][wordcloud_104]
    
    - t-SNE upon the result of TF-IDF of website 104
    
    ![t-SNE of TF-IDF based on website 104][tsne_tfidf_104]
    

### Hyper-parameters
  - Trump's twitts
    - The number of topics: 3
      - Chosen by using pyLDAvis
        ![Visualize the LDA by using pyLDAvis][pyldavis_twitter]
      
  - Employment website 104
    - The number of topics: 10
    - The number of passes (similar to #batches): 20
    - no_below (low frequency word count): 6
    - no_above (high frequency word ratio): 0.1
    

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
