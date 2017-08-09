title: Lucene
tags:
---


查看文档得分的具体构成：Searcher.explain(Query query, int doc)

得分算法：  tf * idf * boost * lengthNorm

	tf：是查询的词在文档中出现的次数的平方根  （term frequent）
	idf：表示反转文档频率，观察了一下所有的文档都一样，所以那就没什么用处，不会起什么决定作用。 
	boost：激励因子，可以通过setBoost方法设置，需要说明的通过field和doc都可以设置，所设置的值会同时起作用 
	lengthNorm：是由搜索的field的长度决定了，越长文档的分值越低。 

所以我们编程能够控制score的就是设置boost值

还有个问题，为什么一次查询后最大的分值总是1.0呢？ 
因为Lucene会把计算后，最大分值超过1.0的分值作为分母，其他的文档的分值都除以这个最大值，计算出最终的得分。






lucene first demo: 开始建立索引 ... 
lucene first demo: 索引建立完成
lucene first demo: 开始查询....
总记录数：1
得分：0.11506981
field: stored,indexed,tokenized<content:this is my first lucene demo>
得分算法：0.11506981 = (MATCH) weight(content:lucene in 0) [DefaultSimilarity], result of:
  0.11506981 = fieldWeight in 0, product of:
    1.0 = tf(freq=1.0), with freq of:
      1.0 = termFreq=1.0
    0.30685282 = idf(docFreq=1, maxDocs=1)
    0.375 = fieldNorm(doc=0)




lucene first demo: 开始建立索引 ... 
lucene first demo: 索引建立完成
lucene first demo: 开始查询....
总记录数：2
得分：0.22295055
field: stored,indexed,tokenized<content:this is my first lucene demo>
得分算法：0.22295056 = (MATCH) weight(content:lucene^2.0 in 0) [DefaultSimilarity], result of:
  0.22295056 = score(doc=0,freq=1.0 = termFreq=1.0
), product of:
    0.99999994 = queryWeight, product of:
      2.0 = boost
      0.5945349 = idf(docFreq=2, maxDocs=2)
      0.8409935 = queryNorm
    0.22295058 = fieldWeight in 0, product of:
      1.0 = tf(freq=1.0), with freq of:
        1.0 = termFreq=1.0
      0.5945349 = idf(docFreq=2, maxDocs=2)
      0.375 = fieldNorm(doc=0)





得分：0.22295055
field: stored,indexed,tokenized<content:this is my first lucene demo>
得分算法：0.22295056 = (MATCH) weight(content:lucene^2.0 in 0) [DefaultSimilarity], result of:
  0.22295056 = score(doc=0,freq=1.0 = termFreq=1.0
), product of:
    0.99999994 = queryWeight, product of:
      2.0 = boost
      0.5945349 = idf(docFreq=2, maxDocs=2)
      0.8409935 = queryNorm
    0.22295058 = fieldWeight in 0, product of:
      1.0 = tf(freq=1.0), with freq of:
        1.0 = termFreq=1.0
      0.5945349 = idf(docFreq=2, maxDocs=2)
      0.375 = fieldNorm(doc=0)