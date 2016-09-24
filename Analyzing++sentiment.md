

```python
import graphlab
```

# read some data


```python
products=graphlab.SFrame('amazon_baby.gl/')
```

    /opt/conda/lib/python2.7/site-packages/requests/packages/urllib3/connection.py:266: SubjectAltNameWarning: Certificate for beta.graphlab.com has no `subjectAltName`, falling back to check for a `commonName` for now. This feature is being removed by major browsers and deprecated by RFC 2818. (See https://github.com/shazow/urllib3/issues/497 for details.)
      SubjectAltNameWarning
    [INFO] graphlab.cython.cy_server: GraphLab Create v2.0.1 started. Logging: /tmp/graphlab_server_1473077012.log


    This non-commercial license of GraphLab Create for academic use is assigned to dharun199531@gmail.com and will expire on August 17, 2017.



```python
products.head()
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">review</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rating</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Planetwise Flannel Wipes</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">These flannel wipes are<br>OK, but in my opinion ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Planetwise Wipe Pouch</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">it came early and was not<br>disappointed. i love ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Annas Dream Full Quilt<br>with 2 Shams ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Very soft and comfortable<br>and warmer than it ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This is a product well<br>worth the purchase.  I ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">All of my kids have cried<br>non-stop when I tried to ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">When the Binky Fairy came<br>to our house, we didn't ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">A Tale of Baby's Days<br>with Peter Rabbit ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Lovely book, it's bound<br>tightly so you may no ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Perfect for new parents.<br>We were able to keep ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">A friend of mine pinned<br>this product on Pinte ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This has been an easy way<br>for my nanny to record ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
    </tr>
</table>
[10 rows x 3 columns]<br/>
</div>



# word count


```python
products['word_count']=graphlab.text_analytics.count_words(products['review'])
```


```python
products.head()
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">review</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rating</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">word_count</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Planetwise Flannel Wipes</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">These flannel wipes are<br>OK, but in my opinion ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 5, 'stink': 1,<br>'because': 1, 'ordered': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Planetwise Wipe Pouch</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">it came early and was not<br>disappointed. i love ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 3, 'love': 1,<br>'it': 2, 'highly': 1, ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Annas Dream Full Quilt<br>with 2 Shams ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Very soft and comfortable<br>and warmer than it ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'quilt': 1,<br>'it': 1, 'comfortable': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This is a product well<br>worth the purchase.  I ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'ingenious': 1, 'and':<br>3, 'love': 2, ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">All of my kids have cried<br>non-stop when I tried to ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'parents!!':<br>1, 'all': 2, 'puppet.': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">When the Binky Fairy came<br>to our house, we didn't ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'cute': 1,<br>'help': 2, 'doll': 1, ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">A Tale of Baby's Days<br>with Peter Rabbit ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Lovely book, it's bound<br>tightly so you may no ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'shop': 1, 'be': 1,<br>'is': 1, 'it': 1, 'as': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Perfect for new parents.<br>We were able to keep ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'feeding,': 1, 'and': 2,<br>'all': 1, 'right': 1, ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">A friend of mine pinned<br>this product on Pinte ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 1, 'help': 1,<br>'give': 1, 'is': 1, ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This has been an easy way<br>for my nanny to record ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'journal.': 1, 'all': 1,<br>'standarad': 1, ...</td>
    </tr>
</table>
[10 rows x 4 columns]<br/>
</div>




```python
graphlab.canvas.set_target('ipynb')
```


```python
products['name'].show()
```



# explore vulie sophie


```python
giraffe_reviews=products[products['name'] == 'Vulli Sophie the Giraffe Teether']
```


```python
len(giraffe_reviews)
```




    785




```python
giraffe_reviews['rating'].show(view='Categorical')
```



# building a sentiment classifier


```python
products['rating'].show(view='Categorical')
```



# define whats positive and negative sentiment


```python
products=products[products['rating']!=3]
```

## positive sentiment-4 and 5 stars negative-1 and 2 stars


```python
products['sentiment']=products['rating']>=4
```


```python
products.head()
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">review</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rating</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">word_count</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sentiment</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Planetwise Wipe Pouch</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">it came early and was not<br>disappointed. i love ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 3, 'love': 1,<br>'it': 2, 'highly': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Annas Dream Full Quilt<br>with 2 Shams ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Very soft and comfortable<br>and warmer than it ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'quilt': 1,<br>'it': 1, 'comfortable': ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This is a product well<br>worth the purchase.  I ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'ingenious': 1, 'and':<br>3, 'love': 2, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">All of my kids have cried<br>non-stop when I tried to ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'parents!!':<br>1, 'all': 2, 'puppet.': ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">When the Binky Fairy came<br>to our house, we didn't ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'cute': 1,<br>'help': 2, 'doll': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">A Tale of Baby's Days<br>with Peter Rabbit ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Lovely book, it's bound<br>tightly so you may no ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'shop': 1, 'be': 1,<br>'is': 1, 'it': 1, 'as': ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Perfect for new parents.<br>We were able to keep ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'feeding,': 1, 'and': 2,<br>'all': 1, 'right': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">A friend of mine pinned<br>this product on Pinte ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 1, 'help': 1,<br>'give': 1, 'is': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This has been an easy way<br>for my nanny to record ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'journal.': 1, 'all': 1,<br>'standarad': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I love this journal and<br>our nanny uses it ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 1, 'forget': 1,<br>'just': 1, "daughter's": ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
</table>
[10 rows x 5 columns]<br/>
</div>



## training the sentiment classifier


```python
train_data,test_data=products.random_split(.8,seed=0)
```

sentiment_model=graphlab.logistic_classifier.create(train_data,target='sentiment',features=['word_count'],validation_set=test_data)

## evaluate the sentiment model


```python
sentiment_model.evaluate(test_data,metric='roc_curve')
```




    {'roc_curve': Columns:
     	threshold	float
     	fpr	float
     	tpr	float
     	p	int
     	n	int
     
     Rows: 100001
     
     Data:
     +-----------+----------------+----------------+-------+------+
     | threshold |      fpr       |      tpr       |   p   |  n   |
     +-----------+----------------+----------------+-------+------+
     |    0.0    |      1.0       |      1.0       | 27976 | 5328 |
     |   1e-05   | 0.909346846847 | 0.998856162425 | 27976 | 5328 |
     |   2e-05   | 0.896021021021 | 0.998748927652 | 27976 | 5328 |
     |   3e-05   | 0.886448948949 | 0.998462968259 | 27976 | 5328 |
     |   4e-05   | 0.879692192192 | 0.998284243637 | 27976 | 5328 |
     |   5e-05   | 0.875187687688 | 0.998212753789 | 27976 | 5328 |
     |   6e-05   | 0.872184684685 | 0.998177008865 | 27976 | 5328 |
     |   7e-05   | 0.868618618619 | 0.998034029168 | 27976 | 5328 |
     |   8e-05   | 0.864677177177 | 0.997998284244 | 27976 | 5328 |
     |   9e-05   | 0.860735735736 | 0.997962539319 | 27976 | 5328 |
     +-----------+----------------+----------------+-------+------+
     [100001 rows x 5 columns]
     Note: Only the head of the SFrame is printed.
     You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.}




```python
sentiment_model.show(view='Evaluation')
```



## applying the learned model for a product


```python
giraffe_reviews['predicted_sentiment']=sentiment_model.predict(giraffe_reviews,output_type='probability')
```


```python
giraffe_reviews.head()
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">review</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rating</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">word_count</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">predicted_sentiment</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">He likes chewing on all<br>the parts especially the ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 1, 'all': 1,<br>'because': 1, 'it': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999513023521</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">My son loves this toy and<br>fits great in the diaper ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 1, 'right': 1,<br>'help': 1, 'just': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999320678306</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">There really should be a<br>large warning on the  ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'all': 1,<br>'latex.': 1, 'being': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.013558811687</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">All the moms in my moms'<br>group got Sophie for ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'one!': 1,<br>'all': 1, 'love': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.995769474148</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I was a little skeptical<br>on whether Sophie was ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 3, 'all': 1,<br>'old': 1, 'her.': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.662374415673</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I have been reading about<br>Sophie and was going  ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 6, 'seven': 1,<br>'already': 1, 'love': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999997148186</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">My neice loves her sophie<br>and has spent hours ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 4, 'drooling,':<br>1, 'love': 1, 'her.': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.989190989536</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">What a friendly face!<br>And those mesmerizing ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 3, 'chew': 1,<br>"don't": 1, 'is': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999563518413</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">We got this just for my<br>son to chew on instea ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'chew': 2, 'because': 1,<br>'just': 2, 'what': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.970160542725</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">My baby seems to like<br>this toy, but I could ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'already': 1,<br>'in': 1, 'some': 1, ' ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.195367644588</td>
    </tr>
</table>
[10 rows x 5 columns]<br/>
</div>



## sort the reviews on the predicted sentiment


```python
giraffe_reviews=giraffe_reviews.sort('predicted_sentiment',ascending=False)
```


```python
giraffe_reviews.head()
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">review</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rating</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">word_count</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">predicted_sentiment</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Sophie, oh Sophie, your<br>time has come. My ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'giggles': 1, 'all': 1,<br>"violet's": 2, 'food' ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I'm not sure why Sophie<br>is such a hit with the ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'peace': 1, 'month': 1,<br>'bright': 1, 'softer' ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999999703</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I'll be honest...I bought<br>this toy because all the ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 2, 'pops': 1,<br>'existence.': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999999392</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">We got this little<br>giraffe as a gift from a ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 2, "don't": 1,<br>'(literally).so': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.99999999919</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">As a mother of 16month<br>old twins; I bought ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cute': 1, 'all': 1,<br>'reviews.': 2, 'just' ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999998657</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Sophie the Giraffe is the<br>perfect teething toy. ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'just': 2, 'both': 1,<br>'month': 1, 'ears,': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999997108</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Sophie la giraffe is<br>absolutely the best toy ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 5, 'the': 1,<br>'all': 1, 'that': 2, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999995589</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">My 5-mos old son took to<br>this immediately. The ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'just': 1, 'shape': 2,<br>'mutt': 1, '"dog': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999995573</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">My nephews and my four<br>kids all had Sophie in ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 4, 'chew': 1,<br>'all': 1, 'perfect;': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999989527</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Vulli Sophie the Giraffe<br>Teether ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Never thought I'd see my<br>son French kissing a ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'giggles': 1, 'all': 1,<br>'out,': 1, 'over': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999985069</td>
    </tr>
</table>
[10 rows x 5 columns]<br/>
</div>




```python
giraffe_reviews[0]['review']
```




    "Sophie, oh Sophie, your time has come. My granddaughter, Violet is 5 months old and starting to teeth. What joy little Sophie brings to Violet. Sophie is made of a very pliable rubber that is sturdy but not tough. It is quite easy for Violet to twist Sophie into unheard of positions to get Sophie into her mouth. The little nose and hooves fit perfectly into small mouths, and the drooling has purpose. The paint on Sophie is food quality.Sophie was born in 1961 in France. The maker had wondered why there was nothing available for babies and made Sophie from the finest rubber, phthalate-free on St Sophie's Day, thus the name was born. Since that time millions of Sophie's populate the world. She is soft and for babies little hands easy to grasp. Violet especially loves the bumpy head and horns of Sophie. Sophie has a long neck that easy to grasp and twist. She has lovely, sizable spots that attract Violet's attention. Sophie has happy little squeaks that bring squeals of delight from Violet. She is able to make Sophie squeak and that brings much joy. Sophie's smooth skin is soothing to Violet's little gums. Sophie is 7 inches tall and is the exact correct size for babies to hold and love.As you well know the first thing babies grasp, goes into their mouths- how wonderful to have a toy that stimulates all of the senses and helps with the issue of teething. Sophie is small enough to fit into any size pocket or bag. Sophie is the perfect find for babies from a few months to a year old. How wonderful to hear the giggles and laughs that emanate from babies who find Sophie irresistible. Viva La Sophie!Highly Recommended.  prisrob 12-11-09"




```python
giraffe_reviews[1]['review']
```




    "I'm not sure why Sophie is such a hit with the little ones, but my 7 month old baby girl is one of her adoring fans.  The rubber is softer and more pleasant to handle, and my daughter has enjoyed chewing on her legs and the nubs on her head even before she started teething.  She also loves the squeak that Sophie makes when you squeeze her.  Not sure what it is but if Sophie is amongst a pile of her other toys, my daughter will more often than not reach for Sophie.  And I have the peace of mind of knowing that only edible and safe paints and materials have been used to make Sophie, as opposed to Bright Starts and other baby toys made in China.  Now that the research is out on phthalates and other toxic substances in baby toys, I think it's more important than ever to find good quality toys that are also safe for our babies to handle and put in their mouths.  Sophie is a must-have for every new mom in my opinion.  Even if your kid is one of the few that can take or leave her, it's worth a try.  Vulli, the makers of Sophie, also make natural rubber teething rings that my daughter loves as well."




```python
giraffe_reviews[-1]['review']
```




    "My son (now 2.5) LOVED his Sophie, and I bought one for every baby shower I've gone to. Now, my daughter (6 months) just today nearly choked on it and I will never give it to her again. Had I not been within hearing range it could have been fatal. The strange sound she was making caught my attention and when I went to her and found the front curved leg shoved well down her throat and her face a purply/blue I panicked. I pulled it out and she vomited all over the carpet before screaming her head off. I can't believe how my opinion of this toy has changed from a must-have to a must-not-use. Please don't disregard any of the choking hazard comments, they are not over exaggerated!"




```python
selected_words = ['awesome', 'great', 'fantastic', 'amazing', 'love', 'horrible', 'bad', 'terrible', 'awful', 'wow', 'hate']
```


```python
def awesome_count(x):
    if 'awesome' in x:
        return x.get('awesome')
    else:
        return 0
    
def great_count(x):
    if 'great' in x:
        return x.get('great')
    else:
        return 0    

def fantastic_count(x):
    if 'fantastic' in x:
        return x.get('fantastic')
    else:
        return 0    

def amazing_count(x):
    if 'amazing' in x:
        return x.get('amazing')
    else:
        return 0
    
def love_count(x):
    if 'love' in x:
        return x.get('love')
    else:
        return 0
    
def horrible_count(x):
    if 'horrible' in x:
        return x.get('horrible')
    else:
        return 0
    
def bad_count(x):
    if 'bad' in x:
        return x.get('bad')
    else:
        return 0
    
def terrible_count(x):
    if 'terrible' in x:
        return x.get('terrible')
    else:
        return 0
    
def awful_count(x):
    if 'awful' in x:
        return x.get('awful')
    else:
        return 0
    
def wow_count(x):
    if 'wow' in x:
        return x.get('wow')
    else:
        return 0
    
def hate_count(x):
    if 'hate' in x:
        return x.get('hate')
    else:
        return 0    
    
```


```python
awesome_count()

```


```python
awesome_c
```




    0




```python
  products['awesome'] = products['word_count'].apply(awesome_count)
  products['great'] = products['word_count'].apply(great_count)
  products['fantastic'] = products['word_count'].apply(fantastic_count)
  products['amazing'] = products['word_count'].apply(amazing_count)
  products['love'] = products['word_count'].apply(love_count)
  products['horrible'] = products['word_count'].apply(horrible_count)
  products['bad'] = products['word_count'].apply(bad_count)
  products['terrible'] = products['word_count'].apply(terrible_count)
  products['awful'] = products['word_count'].apply(awful_count)
  products['wow'] = products['word_count'].apply(wow_count)
  products['hate'] = products['word_count'].apply(hate_count)

```


```python
products.head()
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">review</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rating</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">word_count</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sentiment</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">awesome</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Planetwise Wipe Pouch</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">it came early and was not<br>disappointed. i love ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 3, 'love': 1,<br>'it': 2, 'highly': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Annas Dream Full Quilt<br>with 2 Shams ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Very soft and comfortable<br>and warmer than it ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'quilt': 1,<br>'it': 1, 'comfortable': ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This is a product well<br>worth the purchase.  I ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'ingenious': 1, 'and':<br>3, 'love': 2, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">All of my kids have cried<br>non-stop when I tried to ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'parents!!':<br>1, 'all': 2, 'puppet.': ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Stop Pacifier Sucking<br>without tears with ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">When the Binky Fairy came<br>to our house, we didn't ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 2, 'cute': 1,<br>'help': 2, 'doll': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">A Tale of Baby's Days<br>with Peter Rabbit ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Lovely book, it's bound<br>tightly so you may no ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'shop': 1, 'be': 1,<br>'is': 1, 'it': 1, 'as': ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Perfect for new parents.<br>We were able to keep ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'feeding,': 1, 'and': 2,<br>'all': 1, 'right': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">A friend of mine pinned<br>this product on Pinte ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 1, 'help': 1,<br>'give': 1, 'is': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This has been an easy way<br>for my nanny to record ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'journal.': 1, 'all': 1,<br>'standarad': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Tracker&amp;reg; - Daily<br>Childcare Journal, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I love this journal and<br>our nanny uses it ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 1, 'forget': 1,<br>'just': 1, "daughter's": ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">great</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">fantastic</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">amazing</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">love</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">horrible</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bad</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">terrible</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">awful</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">wow</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">hate</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
</table>
[10 rows x 16 columns]<br/>
</div>




```python
products['word_count']
```




    dtype: dict
    Rows: 166752
    [{'and': 3, 'love': 1, 'it': 2, 'highly': 1, 'osocozy': 1, 'bags': 1, 'holder.': 1, 'moist': 1, 'does': 1, 'recommend': 1, 'was': 1, 'wipes': 1, 'it.': 1, 'early': 1, 'disappointed.': 1, 'not': 2, 'now': 1, 'wipe': 1, 'keps': 1, 'wise': 1, 'i': 1, 'leak.': 1, 'planet': 1, 'my': 2, 'came': 1}, {'and': 2, 'quilt': 1, 'it': 1, 'comfortable': 1, 'warmer': 1, 'size': 1, 'anyone': 1, 'for': 1, 'looking': 1, 'to': 1, 'recommend': 1, 'type': 1, 'full': 1, 'very': 1, 'looks...fit': 1, 'than': 1, 'perfectly...would': 1, 'this': 1, 'of': 1, 'bed': 1, 'the': 1, 'soft': 1}, {'ingenious': 1, 'and': 3, 'love': 2, 'positive,': 1, 'is': 4, 'it': 1, 'losing': 1, 'fairy.': 1, 'have': 1, 'in': 2, 'rid': 1, 'what': 1, 'her': 1, 'how': 1, 'to': 1, 'much': 1, 'has': 1, 'approach': 2, 'worth': 1, 'she': 1, 'tool.': 1, 'product': 2, 'clever': 1, 'chart': 1, 'else': 1, 'most': 1, 'artwork,': 1, 'ownership': 1, 'not': 1, 'little': 1, 'purchase.': 1, 'herself,': 1, 'a': 2, 'about': 1, 'daughter': 1, 'like': 1, 'anything': 1, 'getting': 1, 'this': 3, 'of': 3, 'proud': 1, 'well': 1, 'this,': 1, 'i': 3, 'back,': 1, 'so': 1, 'binky.': 2, 'loves': 1, 'found': 1, 'the': 7, 'my': 1}, {'and': 2, 'parents!!': 1, 'all': 2, 'puppet.': 1, 'help': 1, 'cried': 1, 'is': 3, 'it': 1, 'soo': 1, 'rock!!': 1, 'way': 1, 'have': 1, 'pacifier': 1, 'my': 1, 'your': 1, 'tried': 1, 'from': 1, 'for': 2, 'their': 2, 'when': 1, 'to': 5, 'going': 1, 'easy': 1, 'pacifier,': 1, 'you': 2, 'save': 1, 'until': 1, "love's": 1, 'book!': 1, 'them': 4, 'buy': 1, 'ween': 1, 'book,': 1, 'part': 1, 'understand': 1, 'it.this': 1, 'binky': 1, 'an': 1, 'with': 1, 'must': 1, 'a': 2, 'great': 1, 'kids': 2, 'off': 1, 'gift': 1, 'this': 1, 'many': 1, 'work': 1, 'non-stop': 1, 'thumbuddy': 1, 'will': 1, 'i': 2, 'expecting': 1, 'allow': 1, 'of': 1, 'found': 1, 'fairy': 1, 'where': 1, 'headaches.thanks': 1}, {'and': 2, 'cute': 1, 'help': 2, 'doll': 1, 'is': 2, "didn't": 1, 'it': 1, 'house,': 1, 'highly': 1, 'product': 1, 'have': 1, 'pacifier': 1, 'comes.': 1, 'your': 1, 'special': 1, 'happens': 1, 'what': 1, 'thumb': 1, 'would': 1, 'to': 6, 'lots': 1, 'explain': 1, 'when': 2, 'habit.': 1, 'any': 2, 'how': 1, 'book': 2, 'item.': 1, 'recommend': 1, 'pacifier.': 1, 'adorable': 1, 'we': 2, 'sucking': 1, 'parent': 1, 'our': 2, 'stop': 1, 'great': 1, 'movies': 1, 'break': 1, 'job': 1, 'important': 1, 'child': 1, 'telling': 1, 'using': 1, 'binky': 3, 'trying': 1, 'with': 1, 'the': 6, 'a': 2, 'loss': 1, 'about': 2, 'made': 1, 'daughter': 1, 'her': 1, 'gift': 1, 'i': 1, 'of': 2, 'favorite': 1, 'their': 1, 'this': 2, 'prepare': 1, 'does': 1, 'fairy': 3, 'or': 1, 'came': 1, 'for': 2}, {'shop': 1, 'be': 1, 'is': 1, 'it': 1, 'as': 1, 'spaces': 1, 'at': 1, 'in': 1, 'before': 1, 'from': 1, 'for': 1, '&': 1, '29.95!': 1, 'barnes': 1, 'currently': 1, 'able': 1, 'aside': 1, 'tightly': 1, 'to': 1, 'add': 1, 'listed': 1, 'you': 2, 'lovely': 1, 'noble': 1, 'photos/cards': 1, 'around': 1, 'may': 1, 'designated': 1, 'book,': 1, 'book.': 1, 'bound': 1, 'not': 1, 'purchase,': 1, 'of': 1, 'so': 1, 'alot': 1, "it's": 1, 'the': 2}, {'feeding,': 1, 'and': 2, 'all': 1, 'right': 1, 'able': 1, 'we': 2, 'two': 1, 'because': 1, 'sleep': 1, 'questions': 1, 'perfect': 1, 'her': 1, 'doctor': 1, 'when': 1, 'there!': 1, 'for': 2, 'to': 1, 'new': 1, 'easier': 1, 'life': 1, 'schedule': 1, 'track': 1, 'it': 1, 'diaper': 1, 'half': 1, 'ask': 1, 'change': 1, 'had': 1, 'a': 1, 'about': 1, 'made': 1, 'would': 1, 'of': 2, 'months': 1, 'keep': 1, 'habits': 1, 'were': 1, 'life.': 1, 'the': 2, 'parents.': 1, "baby's": 1, 'first': 1}, {'and': 1, 'help': 1, 'give': 1, 'is': 1, 'mine': 1, 'decided': 1, 'are': 1, 'if': 1, 'pinterest': 1, 'pinned': 1, 'to': 1, 'feedings,': 1, 'new': 1, 'you': 2, 'friend': 1, 'product': 1, 'like!': 1, 'track': 1, 'fantastic!': 1, 'whirl!': 1, 'it': 2, 'diaper': 1, 'a': 3, 'on': 1, 'i': 1, 'of': 2, 'parent,': 1, 'keep': 1, 'will': 1, 'this': 2, 'so': 1, 'the': 1, 'changes': 1}, {'journal.': 1, 'all': 1, 'standarad': 1, 'another': 1, 'informed': 1, 'is': 2, 'some': 1, 'it': 1, 'one': 1, 'not': 2, 'because': 1, 'at': 1, 'have': 1, 'in': 1, 'happen': 1, 'your': 1, 'out': 1, 'options.i': 1, "you're": 1, 'what': 1, 'for': 1, 'record': 1, 'ordering': 1, 'there': 1, 'when': 2, 'while': 1, 'been': 2, 'the': 1, 'to': 4, 'only': 1, '5': 1, 'easy': 1, 'recommend': 1, 'has': 1, 'home.': 1, 'events': 1, 'more': 1, 'wants': 1, 'we': 1, 'someone': 1, 'run': 1, 'way': 1, 'that': 1, 'who': 1, 'stay': 1, 'reason': 1, 'pre-printed': 1, 'key': 1, 'baby': 2, 'highly': 1, 'with': 1, 'pages': 1, 'a': 1, 'on': 1, 'would': 1, 'this': 3, 'plan': 1, 'could': 1, 'up': 1, 'i': 1, 'home.the': 1, 'of': 2, 'an': 1, "i'm": 1, 'my': 2, 'think': 1, "isn't": 1, 'nanny': 1}, {'all': 1, 'forget': 1, 'just': 1, "daughter's": 1, 'sleep': 1, 'milk': 1, 'weekly': 1, 'layout': 1, 'had': 1, 'hot': 1, 'to': 11, 'add': 1, 'easy': 1, 'has': 2, 'real': 1, 'complaint': 1, 'etc.)': 1, 'food': 1, 'overall': 1, 'sleep,': 1, 'nanny,': 1, 'now': 1, 'older).my': 1, 'today)': 1, 'instructions': 1, 'notes': 1, 'all,': 1, 'leave': 1, 'she': 3, 'night': 1, 'often': 1, 'back': 1, 'design': 1, 'our': 2, 'out': 1, 'what': 1, 'and/or': 1, 'for': 2, 'space': 1, 'sun': 1, 'comments': 2, 'time,': 1, "nanny's": 1, 'day,': 1, 'reply': 1, 'previous': 1, 'screen': 1, 'knowing': 1, 'we': 1, 'eating': 1, 'schedule': 1, 'journal': 1, 'communicate': 1, 'nanny': 2, 'rash,': 1, 'ask': 1, 'on': 3, 'about': 1, '(please': 1, 'column': 1, 'of': 4, 'amount': 1, 'changes': 1, 'or': 2, 'love': 2, "baby's": 2, 'time--tummy': 1, 'highly': 1, 'specifics': 1, 'morning.': 1, 'use': 2, 'notes.': 1, 'her': 2, "it's": 1, 'there': 1, 'took,': 1, 'quickly': 1, 'recommend': 1, 'tracker.': 1, '(i.e.': 3, 'naturally': 1, 'only': 1, 'that': 2, "didn't": 1, 'stick': 1, 'baby': 4, 'with': 1, 'specify': 1, 'rush': 1, 'this': 2, 'tell': 1, 'etc)': 1, 'my': 2, 'and': 5, 'activities.': 1, 'is': 2, 'post-its': 1, 'moved': 1, 'it': 3, 'as': 2, 'want': 1, 'in': 5, 'everyday': 1, 'fill': 1, 'patterns': 1, 'make': 1, '-': 1, 'walk': 1, 'also': 1, 'nap': 1, 'other': 2, 'details': 2, 'gets': 1, 'play': 1, 'track': 2, 'uses': 1, 'lunch,': 1, 'a': 1, 'no': 1, 'i': 7, 'sometimes': 1, 'well': 1, 'park,': 1, 'time': 1, 'very': 1, 'the': 9}, {'and': 1, 'this': 3, 'is': 1, 'mom,': 1, 'back': 1, 'changes,': 1, 'in': 1, 'perfect!': 1, 'would': 1, 'doctor': 1, "it's": 1, 'to': 1, 'enough': 1, 'book': 2, 'easy': 1, 'recommend': 1, 'feedings,': 1, 'new': 2, 'that': 1, 'track': 1, 'it': 1, 'moms.': 1, 'diaper': 2, "i'm": 1, 'sleep.': 1, 'throw': 1, 'a': 1, 'made': 1, 'for': 2, 'i': 1, 'of': 1, 'so': 1, 'keep': 1, 'visits.': 1, 'definitely': 1, 'plus': 1, 'time': 1, 'small': 1, 'the': 1, 'first': 1}, {'all': 1, 'just': 1, 'when': 2, 'one.': 1, 'front': 1, 'paper': 1, '6pm': 1, 'provided.': 1, 'before': 1, 'perfect': 2, 'fit': 1, 'how': 2, 'information.': 1, 'day,': 1, 'him': 1, 'better': 1, 'to': 9, 'only': 1, 'pretty': 2, 'has': 1, 'gave': 1, 'real': 1, 'shorthand,': 1, '7': 2, 'emergency': 1, 'get': 1, 'very': 1, 'big': 1, 'me': 1, 'they': 1, 'not': 1, 'now': 1, 'complain': 1, 'entire': 1, 'helpful': 1, 'try': 1, 'situation.': 1, 'she': 4, 'also,': 1, 'each': 1, 'small': 1, 'works': 1, 'page': 1, "isn't": 1, 'incomplete/inaccurate': 1, 'because': 1, 'me,': 1, 'wohld': 1, 'some': 2, 'home': 1, 'leave': 1, 'for': 7, 'space': 2, 'section': 1, 'behind': 1, 'goes': 1, 'ends': 1, 'use': 2, 'reported': 1, 'phone.': 1, 'nanny': 2, 'wanted': 2, 'on': 1, 'about': 1, 'her': 1, 'getting': 2, 'of': 6, 'could': 1, "it's": 1, "i'm": 2, 'out.': 1, 'control': 1, 'useful': 1, 'info.': 1, 'app': 1, 'daycare/nanny/caregiver': 1, '6.': 1, 'deal.': 1, 'down': 1, 'little': 2, 'from': 2, 'additional': 1, 'would': 2, 'transfer': 1, 'format.': 1, 'there': 1, 'two': 1, 'much': 1, 'too': 1, 'way': 1, '6': 1, '6pm.': 1, 'was': 2, 'baby.': 1, 'park': 1, 'but': 2, 'phone': 1, 'with': 2, 'info': 2, 'this': 5, 'originally': 1, 'up': 1, 'reviews': 1, 'suppose': 1, 'starts': 1, 'problem': 1, 'my': 4, 'example': 1, 'at': 2, 'and': 5, 'is': 3, 'changes.': 1, 'it': 2, 'an': 2, 'complaint:': 1, 'something': 1, 'have': 1, 'in': 1, 'if': 1, 'information': 3, 'documents': 1, 'end': 1, 'provide': 1, 'solution!': 1, '-': 6, 'write': 1, 'also': 2, 'other': 1, 'pad': 2, 'take': 2, 'you': 2, 'fill': 1, 'day': 1, 'difficult': 1, 'track': 1, 'notebook': 1, 'pouch': 1, 'pages': 1, 'a': 8, '7am': 2, 'tracking': 1, 'remember': 1, 'i': 7, 'naps/feedings/diaper': 1, 'contact': 1, 'time': 1, 'the': 15, 'wanted.': 1}, {'it.': 1, 'info': 1, 'what': 1, 'exactly': 1, 'useful': 1, 'and': 1, 'for': 1, 'space': 1, 'i': 1, 'come': 1, 'is': 1, 'wanted!!': 1, 'with': 1, 'it': 1, 'photos,': 1, 'monthly': 1, 'a': 1, 'lot': 1, 'of': 1, 'stickers': 1}, {'and': 3, 'there': 1, 'useful': 1, 'calender': 2, 'just': 1, 'photo': 1, 'is': 3, 'placed.': 1, 'it': 3, 'whatever': 1, 'one': 1, 'date': 1, 'as': 4, 'well.': 1, 'likes': 1, 'have': 2, 'fine': 1, 'event': 1, 'special': 1, 'before': 1, 'baby': 1, 'write': 1, 'what': 1, 'do.': 1, 'would': 1, 'also': 1, 'not': 1, 'stickers': 1, 'weight,': 1, 'for': 5, 'day.': 1, 'to': 3, 'only': 1, 'does': 1, 'asterisks': 1, 'has': 1, 'sticker': 1, 'friend': 1, 'happened': 1, 'be': 1, 'complaint': 1, 'colorful': 1, 'that': 2, 'very': 2, 'some': 1, 'like,': 1, 'but': 1, 'boxes': 1, 'son.': 1, 'put': 1, 'writing.': 1, 'a': 3, 'on': 2, 'myself': 1, 'room': 3, 'i': 4, 'many': 1, 'second': 1, 'height,': 1, 'this': 1, 'she': 1, 'each': 2, 'found': 1, 'the': 1, 'bought': 2, 'my': 2, 'page': 2}, {'and': 1, 'the': 2, 'all': 1, 'love': 1, 'like': 1, 'i': 2, 'of': 2, "baby's": 1, 'little': 1, 'too.': 1, 'keep': 1, 'this': 1, 'track': 1, 'can': 1, 'you': 1, 'stickers': 1, 'illustrations,': 1, 'firsts.': 1, 'calender,': 1}, {'and': 1, 'this': 2, 'there': 1, 'one': 3, 'second': 1, 'are': 1, 'calender': 1, 'year': 1, 'still': 1, 'find': 1, 'note': 1, 'for': 2, 'things': 1, 'him.': 1, 'better': 1, 'to': 2, 'only': 1, 'got': 1, 'cause': 1, 'was': 2, 'after': 1, 'year.': 1, 'they': 1, 'wanted': 1, 'than': 1, 'i': 3, 'many': 1, 'could': 1, 'turn': 1, 'continue': 1, 'so': 1, 'did': 1, 'the': 4, 'first': 2, '1.': 1}, {'and': 5, 'all': 3, 'have': 1, 'moments': 1, 'in': 1, 'it': 1, 'second': 1, 'something': 1, 'questions': 1, 'year': 2, 'calendar': 2, 'still': 1, 'stickers': 1, 'enjoyed': 1, 'special': 2, 'really': 2, 'layout': 1, 'want': 1, 'to': 2, "it's": 1, 'since': 1, '-': 2, 'least': 1, 'day.': 1, 'doing': 1, 'amazing': 1, 'much': 1, 'you': 1, 'might': 1, "son's": 1, 'his': 1, 'moments!': 1, 'that': 1, 'completed': 1, 'tracking': 1, 'every': 1, 'milestone': 1, 'not': 1, 'wanted': 1, 'those': 1, 'like': 1, 'a': 1, 'milestones': 1, 'for': 1, 'i': 3, 'of': 2, "he's": 1, 'simple': 1, 'keep': 1, 'recording': 1, 'while': 1, 'continue': 1, 'so': 2, 'things': 1, 'fun': 1, 'the': 4, 'first': 1, 'my': 1, 'at': 1}, {'and': 2, 'cute': 1, 'there': 2, 'is': 1, 'something': 1, 'our': 1, 'keep': 1, 'out': 1, 'option.': 1, 'what': 1, 'wanted': 1, 'get': 1, 'to': 2, 'does': 1, 'we': 2, "child's": 1, 'track': 1, 'exactly': 1, "aren't": 1, 'a': 1, 'milestones': 1, 'this': 2, 'of': 1, 'choices': 1, 'many': 1, 'other': 1, 'wanted.': 1}, {'and': 3, 'all': 1, 'memories.': 1, 'reference': 1, 'do': 2, 'is': 3, 'hard': 1, 'some': 1, 'it': 2, 'one': 1, 'milestones...and': 1, 'put': 1, 'as': 2, 'vs': 1, 'have': 1, 'year': 1, 'calendar': 1, 'find': 1, 'down': 1, 'out': 1, 'little': 1, 'to': 5, 'much': 1, 'that': 1, 'had': 1, 'two': 1, 'write': 1, 'everything': 1, 'enough': 1, 'book': 1, 'way': 1, 'finding': 1, 'you': 1, 'fill': 1, 'across': 1, 'so!': 1, 'picture': 1, 'only': 1, 'jot': 1, 'squares': 1, 'on': 1, 'track': 1, 'big': 1, "month's": 1, 'spot': 1, 'book.': 1, 'great!': 1, 'they': 1, 'baby': 2, 'years': 1, 'change': 1, 'a': 6, 'ones!': 1, 'great': 1, 'has': 1, 'in': 2, 'like': 1, 'this': 3, 'of': 1, 'later': 1, 'well': 1, 'second': 1, 'keep': 1, 'large': 1, 'i': 5, 'easier': 1, 'calendar,': 1, 'so': 2, 'can': 2, 'time': 1, 'the': 5, 'came': 1, 'first': 1}, {'and': 1, 'cute': 1, 'because': 2, 'just': 1, 'second-year': 2, 'is': 1, 'lack': 1, 'some': 1, 'it': 2, 'one': 3, 'certain': 1, 'calendar.': 1, 'finish': 1, 'are': 1, 'purchased': 1, 'in': 1, 'general,': 1, 'calendar': 1, 'stickers': 1, 'really': 1, 'for': 4, 'come': 1, 'old-fashioned': 1, 'had': 1, 'pages': 2, 'write': 1, 'to': 1, 'only': 2, 'other': 1, 'pretty': 1, 'hopefully': 1, 'selection': 1, 'got': 1, 'out': 1, 'was': 2, 'an': 1, 'available': 1, 'son': 1, 'looking.': 1, 'okay': 1, 'which': 1, 'with': 3, 'pens.': 1, 'calendars': 2, 'makes': 1, 'they': 1, "aren't": 1, 'disappointed': 1, 'purchasers.': 1, 'a': 1, 'on': 2, 'daughter.': 1, 'hard': 1, 'i': 4, 'of': 2, 'ones.': 1, 'will': 1, 'this': 1, 'future': 1, 'so': 1, 'glossy': 1, "it's": 1, 'very': 1, 'the': 6, 'my': 2}, {'and': 4, 'cute': 1, 'stop': 1, 'on': 2, 'love': 1, 'reocording': 1, 'just': 1, 'is': 2, "nature's": 1, 'year': 4, 'one.': 1, 'highly': 1, 'helped': 1, 'not': 1, 'second': 2, 'are': 2, 'want': 1, '1st': 1, 'calendar': 2, 'stickers': 1, 'calendar!': 1, 'out': 1, 'perfect': 1, 'recording': 1, 'gender.': 1, 'for': 3, "it's": 1, 'own.': 1, 'there': 2, 'to': 2, 'wonderful': 1, 'lullabies': 1, 'recommend': 1, 'might': 1, 'events': 2, "son's": 1, 'continuing': 1, 'his': 1, 'that': 2, 'with': 1, "didn't": 1, 'calendars': 1, 'keeping.': 1, 'plenty': 1, 'baby': 1, 'now': 1, 'super': 1, 'he': 1, 'me': 1, 'loved': 1, 'milestones': 1, 'brat': 1, 'i': 4, 'of': 6, 'this': 2, 'daily': 1, 'thought': 1, 'record': 2, 'plus': 1, 'either': 1, 'have': 1, 'life.': 1, 'the': 1, 'my': 2, 'think': 1, 'first': 1}, {'and': 2, 'dont': 1, 'just': 1, 'sticker': 1, 'it': 1, 'as': 1, 'spaces': 1, 'down,': 1, 'have': 1, 'actually': 1, 'stickers': 1, 'out': 1, 'option.': 1, 'comes': 1, 'use': 1, 'for': 3, 'sit': 1, 'scrap': 1, 'mark': 1, 'to': 3, 'enough': 1, 'ton': 1, 'easy': 1, 'scrapbook': 1, 'borders': 1, 'is': 1, 'booking': 1, 'well.': 1, 'lot': 1, 'very': 1, 'who': 1, 'new': 1, 'includes': 1, 'photos': 1, 'haul': 1, 'milestone': 1, 'with': 1, 'a': 3, 'moms': 1, 'especially': 1, 'wife': 1, 'this': 1, 'of': 2, 'photos,': 1, 'calender.': 1, 'supplies': 1, 'firsts.': 1, 'loves': 1, 'time': 1, 'the': 1, 'options': 1, 'etc,': 1}, {'and': 2, 'one-year': 1, 'work': 1, 'art': 1, '-': 2, 'keepsake.': 1, '1st': 1, 'nearing': 1, 'son': 1, 'calendar.': 1, 'second': 1, 'ago.': 1, 'thanks': 1, 'year': 3, 'tender': 1, 'calendar': 1, 'stickers': 1, 'fill': 1, 'i': 1, 'her': 3, 'record': 1, 'had': 1, 'looking': 1, 'to': 4, 'wonderful': 1, 'sweet': 1, 'fill.': 1, 'was': 3, 'over': 1, 'nice': 1, 'it.': 1, 'his': 2, 'get': 1, 'amazon': 1, 'birthday': 1, 'baby': 1, 'unique': 1, 'pages': 1, 'milestones.': 1, 'helpful': 1, 'a': 6, 'daughter': 1, 'for': 3, 'gift': 1, 'this': 1, 'when': 1, 'up': 1, 'able': 1, 'old!': 1, 'did': 1, 'she': 3, 'loves': 1, 'my': 1, 'receive': 1, 'first': 2}, {'and': 1, 'remembering': 1, 'tired': 1, 'ate,': 1, 'helped': 1, 'baby': 1, 'as': 1, 'through': 1, 'long': 1, 'mom,': 1, 'useful!': 1, 'inexpedient,': 1, 'two': 1, 'months.': 1, 'how': 1, 'new': 1, 'a': 1, 'me': 1, 'not': 1, 'extremely': 1, 'ago': 1, 'this': 1, 'definitely': 1, 'the': 1, 'first': 1}, {'and': 2, 'because': 1, 'family': 1, 'people': 1, "baby's": 1, 'is': 1, 'some': 1, 'it': 1, 'one': 1, 'see': 1, 'washable!': 1, 'in': 1, 'star': 1, 'your': 1, 'perfect': 1, 'just': 1, 'less': 1, '-': 1, '1': 1, 'to': 1, 'white': 1, 'gave': 1, 'diversity': 1, 'not': 1, ';)': 1, 'than': 1, 'like': 1, 'books,': 1, 'of': 1, 'favorite': 1, 'i': 1, "i'd": 1, 'the': 1, 'typical': 1, 'first': 1}, {'family': 1, 'over': 1, 'it': 2, 'seat': 1, 'hook': 1, 'members.': 1, 'go': 1, 'your': 1, 'attach': 1, '-': 1, 'to': 3, 'book': 1, 'way': 1, 'has': 1, 'wont': 1, 'get': 1, 'lost.': 1, 'how': 1, 'a': 1, 'great': 1, 'like': 1, 'i': 1, 'car': 1, 'stroller': 1, 'the': 1, 'or': 1}, {'beautiful': 1, 'saying': 1, 'love': 1, 'it': 1, 'are': 1, 'little': 2, 'interacting': 1, 'when': 1, 'actually': 1, 'to': 1, 'you': 1, 'it.': 1, 'then': 1, 'attention': 1, 'story': 1, 'book.': 1, 'and': 2, 'finished': 1, 'baby': 2, 'hold': 1, 'with': 1, 'pages': 1, 'a': 1, 'on': 1, 'great': 1, 'short': 1, 'you....keeps': 1, 'i': 1, 'of': 1, 'turn': 1, 'can': 1, 'the': 4}, {'and': 1, 'page.': 1, 'says': 1, 'cute': 1, 'is': 1, 'money.': 1, 'it': 2, 'born': 1, 'are': 1, 'open': 1, 'before.': 1, 'for': 1, "it's": 1, 'there': 1, 'to': 4, 'book': 1, 'worth': 1, 'be': 1, '9+': 1, 'very': 1, 'use': 1, 'but': 1, 'every': 1, 'baby': 1, 'wait': 1, 'box': 1, 'on': 2, 'i': 1, 'months': 1, 'this': 1, 'try': 1, 'interactive!': 1, 'so': 2, 'flaps': 1, 'the': 2, 'my': 1, "can't": 1}, {'and': 3, 'chew': 1, 'one-year-old': 1, 'house!': 1, 'love': 1, 'just': 1, 'simple': 1, 'over': 1, 'it': 3, 'rip': 1, 'carry': 1, 'paper': 1, 'learning': 1, 'chunks': 1, 'our': 1, '"puppy,"': 1, 'open': 1, 'out': 1, '"daddy,"': 1, 'for': 1, 'all': 1, "it's": 1, 'bite': 1, 'book': 2, 'board': 1, 'got': 1, 'is': 1, 'nice': 1, 'it.': 2, 'we': 2, 'that': 2, 'she': 5, 'little': 1, 'it,': 2, 'one.': 1, 'words': 1, 'pull': 1, 'a': 2, 'on': 2, 'like': 3, 'this': 1, 'of': 1, 'flaps': 1, 'so': 1, 'can': 2, 'loves': 2, '"mommy,"': 1, 'the': 2, 'etc.': 1, 'or': 1, "can't": 1}, {'and': 2, 'overnight.': 1, 'is': 2, 'detergent.': 1, 'older.': 1, '6months': 1, 'in': 1, 'perfect': 1, 'and/or': 1, 'for': 1, 'material.': 1, 'only': 1, 'book': 2, 'was': 1, 'then': 1, 'colorful': 1, "didn't": 1, 'let': 1, 'dunked': 1, 'strong': 1, 'pages': 1, 'dry': 1, 'like': 1, 'i': 2, 'smell': 1, 'thing': 1, 'of': 1, 'dyes': 1, 'the': 6}, {'page.': 1, "couldn't": 1, 'be': 1, 'is': 1, 'moving': 1, 'books': 2, 'drool...so': 1, 'another': 1, 'your': 1, 'flap': 1, 'perfect': 1, 'looking': 1, 'what': 1, 'adds': 1, 'for': 3, 'been': 1, 'plastic': 1, 'baby!': 1, 'to': 1, 'book': 3, 'babies!': 1, "old's": 1, 'which': 1, 'options.': 1, 'damaged': 1, 'cloth': 2, 'part': 1, 'every': 1, 'by': 1, '10-month': 1, 'a': 1, 'on': 1, 'great': 1, 'level': 1, 'this': 2, "i'd": 1, 'were': 1, 'fun': 1, 'book--a': 1, 'interactive': 1, 'my': 3, 'or': 2, 'usual': 1}, {'all': 1, 'being': 1, 'course': 1, 'still': 1, 'perfect': 1, 'now': 2, "he's": 1, 'to': 1, 'only': 2, 'board': 1, 'teaching': 1, 'his': 2, 'lamaze': 2, 'nearly': 1, 'they': 1, 'not': 2, 'one': 2, 'like': 1, 'this': 4, 'them,': 1, 'enjoy': 1, 'chew': 1, 'because': 1, 'books': 1, 'are': 2, 'out': 1, 'for': 4, 'parent.i': 1, 'does': 1, 'reading': 1, 'discovery': 1, 'peek': 1, 'we': 2, 'of': 3, 'book,': 1, 'members': 1, 'infant.': 1, 'on': 1, 'about': 1, 'etc.': 1, "i'd": 1, 'liked': 1, 'love': 1, 'family': 1, 'son': 3, 'names': 1, "doesn't": 1, 'additional': 1, 'would': 1, 'two': 1, 'lot': 1, 'was': 3, 'flap': 1, 'series,': 1, 'that': 3, 'much,': 1, 'but': 4, 'lift': 1, 'child': 1, 'with': 2, 'he': 3, 'loved': 1, 'look': 1, 'books,': 1, 'cat,': 1, 'as': 3, 'well.': 1, 'learn': 1, 'fun': 2, 'favorites.': 1, 'my': 3, 'and': 6, 'sister,': 1, "didn't": 1, 'it': 6, 'an': 1, 'say': 1, 'issue.': 1, 'at': 1, 'have': 1, 'grandparents,': 1, 'book': 2, 'destroy': 1, 'used': 1, 'again.': 1, 'farm': 1, 'a': 3, 'i': 1, 'dog': 1, 'boo,': 1, 'the': 5, 'playing': 1}, {'and': 1, 'it': 3, 'our': 1, 'for': 1, '&': 1, 'own.': 1, 'when': 1, 'to': 1, 'him,': 1, 'book': 1, 'enjoys': 2, 'has': 1, '...': 1, 'his': 1, 'loved': 1, 'read': 1, 'baby': 1, 'now': 1, 'with': 1, 'he': 1, 'a': 1, 'on': 1, 'this': 1, 'i': 1, 'while': 1, 'loves': 1, 'playing': 1}, {}, {'a': 1, 'brushing': 1, 'play': 1, 'kids': 1, ':)': 1, 'almost': 1, 'with': 1, 'haha': 1, 'too': 1, 'son': 1, 'to': 1, 'book': 1, 'let': 1, 'likes': 1, 'of': 1, 'the': 1, "elmo's": 1, 'my': 1, 'teeth.': 1, 'nice': 1}, {'and': 3, 'imaginative': 1, 'old': 1, 'grandchildren.': 1, 'it': 2, 'through': 1, 'are': 1, 'year': 1, 'go': 1, 'love': 1, 'would': 1, 'sit': 1, 'pictures': 1, 'young': 1, '.': 1, 'to': 1, 'book': 1, 'themselves': 1, 'appeal': 1, 'was': 1, 'buy': 1, 'again!': 1, 'birthday': 1, 'they': 1, 'children.': 1, '2': 1, 'by': 1, 'present': 1, 'a': 1, 'for': 1, 'this': 2, 'will': 1, 'the': 1, 'my': 1, 'page': 2}, {'and': 3, 'cute': 1, 'rating': 1, 'have': 1, 'just': 1, 'give': 1, 'battery': 1, 'is': 1, "disappointment....it's": 1, 'it': 6, 'other': 1, 'down': 1, 'batteries': 1, 'growled': 1, 'something': 1, 'giggled': 1, 'in': 1, 'handle': 1, 'saw': 1, 'find': 1, 'simple': 1, 'if': 2, 'even': 1, 'but': 1, 'would': 2, 'no': 1, "it's": 1, 'absolutely': 1, 'when': 1, 'now!': 1, 'actually': 1, 'to': 2, 'going': 1, '5': 1, 'take': 1, 'mail': 1, 'adorable': 1, 'kenzie,': 1, 'star': 1, 'was': 2, 'bear': 1, 'back': 1, 'how': 1, 'dead': 1, 'got': 1, 'was!': 1, 'such': 1, 'new': 1, 'day': 1, 'a': 4, 'super': 1, 'like': 1, 'gift': 1, 'this': 1, 'my': 1, 'could': 1, 'as': 2, 'excited': 1, 'granddaughter,': 1, 'i': 6, 'suppose': 1, 'place': 1, 'the': 3, 'to!': 2, 'where': 1, 'or': 1, "can't": 1}, {'and': 4, 'soft': 1, 'all': 1, 'would': 1, 'hides': 1, 'elmo': 3, 'too.': 1, 'is': 5, 'it': 2, 'one': 1, 'illustrated': 1, 'baby': 1, 'featured': 1, 'street': 1, 'are': 1, 'another': 1, 'beautifully': 1, 'fun,': 1, '(which': 1, 'page,': 1, 'seemed': 1, 'perfect': 1, 'little': 1, 'lovers': 1, 'because': 1, 'price).': 1, 'for': 3, 'twinkle': 1, 'absolutely': 1, 'character': 1, 'right:': 1, 'also': 2, 'time.': 1, 'book': 3, 'which': 1, 'recommend': 1, 'he': 1, 'was': 1, 'happy': 1, 'available': 1, 'centric': 1, '"reads"': 1, 'to': 1, 'that': 1, 'each': 1, 'amazon': 1, '"twinkle,': 1, 'everywhere': 1, 'characters': 1, 'street/elmo': 1, 'the': 3, 'great,': 1, 'a': 1, 'on': 2, 'great': 1, 'main': 1, 'takes': 1, 'her.': 1, 'i': 2, 'my': 2, 'say': 1, 'elmo"': 1, 'sesame': 2, 'this': 2, 'while': 1, 'so': 2, 'loves': 1, 'of': 2, "i'm": 1, 'nice': 1, 'interactive,': 1, 'other': 1}, {'and': 2, 'bright': 1, 'love': 1, 'is': 1, 'colors': 1, 'are': 1, 'any': 1, "doesn't": 1, 'for': 2, 'two': 1, 'book': 1, 'lastly,': 1, 'baby,': 1, 'bought': 1, 'who': 1, 'baby': 1, 'showers!': 1, 'recent': 1, 'great': 1, 'i': 1, 'soft': 1, 'elmo!': 1, 'the': 2, 'interactive,': 1, 'beautiful.': 1}, {'and': 2, 'another': 1, 'elmo': 1, 'is': 2, 'one': 1, 'creative.': 1, 'softplay': 1, 'fun,': 1, 'birds': 1, 'variety': 1, 'two': 1, 'to': 1, 'only': 1, 'book': 2, 'has': 1, 'bird': 1, 'more': 2, 'we': 2, 'get': 1, 'big': 2, 'book,': 1, 'but': 1, 'wanted': 1, 'friends': 1, 'like': 1, 'this': 1, 'books.': 1, 'found': 1, 'the': 3}, {'and': 1, 'a': 1, 'little': 1, 'soft.': 1, 'safe.': 1, 'for': 1, 'cute': 1, 'this': 1, "it's": 2, 'is': 2, 'easy': 1, 'story': 1, 'book.': 1, 'handle.': 1, 'to': 1, 'it': 1, 'peek-a-boo': 1, 'baby': 1}, {'and': 7, 'old': 1, 'elmo': 1, 'is': 1, 'laughs': 1, 'we': 3, 'month': 1, 'say': 1, 'books': 1, 'have': 1, 'find': 1, 'different': 1, '&#34;peekaboo': 1, 'for': 1, 'few': 1, 'to': 1, '3': 1, '5': 1, 'stars': 1, 'it': 1, 'over': 2, 'sure.': 1, 'smiles': 1, 'it,': 1, 'elmo!&#34;': 1, 'colorful': 1, 'read': 1, 'book.': 1, 'read.': 1, 'most': 1, 'every': 1, 'baby': 1, 'son': 1, 'he': 1, 'a': 1, 'adores': 1, 'this': 2, 'my': 1, 'so': 1, 'loves': 1, 'time': 1, 'fun': 1, 'the': 1, 'soft': 1}, {'book!': 2, 'great': 1, 'colorful': 1, 'for': 1, '&': 1, 'very': 1, 'make': 1, 'bright': 1, 'son': 1, 'this': 2, 'toddlers.': 1, 'cute': 1, 'loves': 1, 'babies': 1, 'illustrations': 1, 'the': 1, 'my': 1, 'interactive': 1}, {'and': 2, 'over.': 1, 'all': 1, 'love': 2, 'they': 8, 'safe.': 1, 'elmo': 1, 'mos,': 1, 'play': 1, 'high': 1, 'as': 1, 'are': 3, 'still': 1, 'if': 1, 'use': 1, 'now': 1, 'for': 1, 'how': 1, 'before': 1, 'when': 2, 'two': 1, 'to': 2, 'time.': 1, '9': 1, 'got': 1, 'reading': 1, 'bought': 1, 'soft,': 1, 'we': 1, 'buy': 1, 'blocks': 1, 'see': 1, 'book,': 1, 'it': 1, 'them': 1, 'granddauchildren': 1, 'kiss': 1, 'fall': 1, 'baby': 1, 'falls': 1, 'with': 2, 'stack': 1, 'a': 1, 'on': 1, 'elmo.': 1, 'i': 1, 'present.': 1, 'so': 1, 'can': 1, 'were': 1, 'fun': 1, 'them.': 2, 'the': 4, 'them,': 1, 'having': 1}, {'and': 5, 'chew': 1, 'all': 1, 'the,': 2, 'have': 1, 'over': 2, "didn't": 1, 'baby': 1, 'teething': 1, 'crawling.': 1, 'letting': 1, 'bank.': 1, 'for': 3, 'to': 2, 'their': 1, 'encourage': 1, 'setting': 1, 'ruining': 1, 'babies': 1, 'christmas': 1, 'them': 2, 'great': 3, 'about': 1, 'break': 1, 'they': 1, 'rolling': 1, 'entertaining': 1, 'younger': 1, 'off': 1, 'gift': 1, 'these': 1, 'worrying': 1, 'droll': 1, 'i': 1, 'without': 1, 'were': 2, 'them.': 1, 'the': 2, 'side': 1}, {'a': 1, 'boring.': 1, 'would': 1, 'to': 1, 'i': 1, 'of': 1, 'is': 2, 'money.': 1, 'it': 2, 'this': 1, 'granddaughter.': 1, 'book': 1, 'nothing': 1, 'recommend': 1, 'not': 1, 'waste': 1, 'my': 1, 'stimulate': 1}, {'old': 1, 'want': 1, 'show': 1, 'is': 2, 'hard': 1, 'it': 1, 'one': 1, 'not': 1, 'books': 1, 'looks': 1, 'have': 1, 'year': 1, 'images': 1, 'our': 1, 'find': 1, 'looking': 1, 'what': 3, 'animals/objects': 1, 'unrealistic': 1, '1': 1, 'to': 2, 'for!!when': 1, 'is,': 1, '"lion"': 1, 'many': 1, 'real': 2, 'we': 3, 'fantastic.': 1, 'that': 1, 'portrayals': 1, 'like,': 1, 'exactly': 1, 'lion...': 1, 'but': 1, 'cloth': 1, 'were': 1, 'nothing': 1, 'teach': 1, 'with': 1, 'him': 1, 'like': 1, 'a': 4, 'on': 1, 'actual': 1, 'look': 1, 'this': 1, 'lion.': 1, 'so': 2, 'them!': 1, 'of': 1, 'drawing': 1}, {'is': 1, 'something': 1, 'cute...so': 1, '&#34;': 1, 'for': 1, 'no': 1, 'memories': 1, 'there': 1, 'young': 1, 'destroying..many': 1, 'reading': 1, 'happy': 2, 'them': 1, 'very': 1, 'little': 1, 'chance': 1, 'they': 1, 'child,': 1, 'of': 1, 'read&#34;': 1, 'can': 1, 'the': 1, 'or': 1}, {'and': 1, 'be': 1, 'great': 1, 'love': 1, 'daughter': 1, 'this': 1, "it's": 1, 'when': 1, 'it!': 1, 'will': 1, 'me': 1, 'so': 1, 'a': 2, 'our': 1, 'fun': 1, 'born.': 1, 'calendar': 1, 'bought': 1, 'was': 1, 'friend': 1, 'momento.': 1}, {'a': 2, 'and': 1, 'little': 1, 'milestones': 1, 'especially': 1, 'for': 1, 'all': 1, 'with': 1, 'of': 1, 'first-time': 1, 'one,': 1, 'up': 1, 'keep': 1, 'to': 1, 'mom.': 1, 'easy': 1, 'quick': 1, 'the': 1, 'busy,': 1, 'first': 1}, {'remembering': 1, 'and': 4, 'reviews.': 1, 'pictures.': 1, 'personalization': 1, 'am': 1, 'back': 1, 'month': 1, 'down': 1, 'year': 1, 'calendar': 1, 'throughout': 1, 'perfect': 1, 'based': 1, 'for': 3, 'to': 1, 'memories': 1, 'did.': 1, "baby's": 1, 'spots': 1, 'jotting': 1, 'also': 1, 'high': 1, 'low': 1, 'has': 1, 'happy': 1, 'be': 1, 'on.': 1, 'that': 1, '&#34;firsts&#34;.': 1, 'quick': 1, 'one': 1, 'a': 1, 'on': 2, 'dates': 1, 'look': 1, 'i': 3, 'of': 1, 'will': 1, 'this': 1, 'so': 1, 'searched': 1, 'fun': 1, 'the': 2, 'settled': 1, 'first': 1}, {'enjoy': 1, 'would': 1, 'give': 1, 'children.': 1, 'is': 2, 'it': 1, 'one': 1, 'born': 1, 'as': 3, 'are': 1, 'want': 1, 'from': 1, 'i': 1, 'for': 2, 'their': 1, 'had': 1, 'looking': 1, 'to': 3, 'parents': 2, 'themselves.': 1, 'new': 1, 'you': 1, 'start': 1, '&#34;firsts&#34;': 1, 'good': 1, 'that': 1, 'very': 2, 'calendars': 1, 'chart': 1, 'soon': 1, '&#34;firsts&#34;.': 1, 'five': 1, 'they': 3, 'baby': 1, 'now': 1, 'beginning': 1, 'mother.': 1, 'a': 2, 'especially': 1, 'gift': 1, 'this': 1, 'of': 2, 'up': 1, 'these': 1, 'so': 1, 'can': 1, 'each': 1, 'the': 3, 'my': 1}, {}, {'and': 2, 'it.': 1, 'all': 1, 'love': 1, 'version': 1, 'absolutely': 1, 'it': 1, 'born': 1, 'purchased': 1, 'in': 1, 'for': 1, 'when': 1, 'same': 1, 'to': 1, 'book': 1, 'scripture': 1, 'daughter-in-law': 1, 'again.': 1, 'was': 2, 'thrilled': 1, 'baby': 1, 'he': 1, 'boy': 1, 'grandson': 1, 'i': 1, 'of': 1, 'receive': 1, 'the': 3, 'my': 2}, {'simple': 1, 'down.': 1, 'verses': 1, 'as': 1, 'at': 1, 'in': 1, 'pages.': 1, 'law.': 1, 'for': 1, 'bottom': 1, 'memories': 1, 'to': 1, 'bought': 1, 'it.': 1, 'but': 1, 'important': 1, 'put': 1, 'a': 2, 'loved': 2, 'daughter': 1, 'gift': 1, 'i': 1, 'of': 1, 'place': 1, 'she': 1, 'the': 1, 'my': 1}, {'and': 4, 'cute': 1, 'liked': 1, 'when': 2, 'is': 3, 'gift!': 1, 'one.': 1, 'one': 1, 'locks': 1, 'want': 1, 'your': 2, 'perfect': 1, 'little': 2, 'for': 4, 'also': 1, 'memories': 1, 'had': 1, 'hair....etc!': 1, 'to': 2, 'asking': 1, 'foot': 1, 'which': 1, 'main': 1, 'questions.': 1, 'you': 1, 'has': 1, 'book!': 1, 'we': 1, 'prints': 1, 'even': 1, 'it': 2, 'reason': 1, 'keepsakes': 1, 'baby': 3, 'hand': 1, 'why': 1, 'bigger': 1, 'a': 2, 'loved': 1, 'great': 1, 'gets': 1, 'remember': 1, 'places': 1, 'born': 1, 'this': 2, 'of': 1, 'put': 1, 'omg.....we': 1, 'shower': 1, 'so': 1, 'place': 1, 'pockets': 1, 'starts': 1, 'the': 2, 'first': 1}, {'pink': 1, 'pastel': 1, 'life': 1, 'love': 1, 'to': 1, 'i': 1, 'with': 1, 'cherished': 1, 'book,': 1, 'great': 1, 'granddaughters': 1, 'record': 1, 'beautiful': 2, 'in': 1, 'it': 1, 'the': 1, 'color.': 1, 'my': 1, 'times': 1}, {'and': 2, 'mini': 1, 'happy!': 1, 'is': 2, 'one.': 1, 'an': 1, 'firsts...and': 1, 'really': 1, 'maternity': 1, 'hair,': 1, 'in': 1, 'fill': 1, 'perfect': 1, 'bracelet...really': 1, 'for': 1, 'with': 1, 'family,': 1, 'looking': 1, 'to': 2, 'book': 1, 'lot': 1, ':': 1, 'was': 1, 'happy': 1, 'preserve': 1, 'flammish)': 1, 'french': 1, 'baby': 1, 'purchase.': 1, 'info': 1, 'i': 1, 'of': 1, 'this': 2, 'pockets': 1, 'english': 1, 'the': 2, 'daddy': 1, "(i'm": 1}, {'and': 2, 'photographs': 1, 'detailed': 1, 'everyone': 1, 'is': 1, 'child': 1, 'it': 1, 'serving': 1, 'through': 1, 'are': 1, 'questions': 1, 'in': 1, '"my': 1, 'its': 1, 'perfect': 1, 'kindergartener.': 1, 'for': 2, 'record': 2, 'your': 2, 'kindergarten': 2, 'to': 3, 'book': 2, 'way': 1, 'recommend': 1, 'answer': 1, 'receiving': 1, 'was': 1, 'surprised': 1, "one's": 1, 'entitled,': 1, "parent.i'd": 1, "child's": 1, 'very': 1, 'memory': 1, 'upon': 1, 'important': 1, 'purpose': 1, 'life.': 1, 'with': 1, 'pleasantly': 1, 'a': 1, 'i': 1, 'of': 1, 'experience': 1, 'this': 2, 'while': 1, 'time': 1, 'fun': 1, 'year".': 1, 'the': 4, 'descriptions': 1}, {'and': 1, 'already': 1, 'it': 1, 'years': 1, 'see': 1, 'questions': 1, 'stumbled': 1, 'how': 1, 'answering': 1, 'answered': 1, 'memory': 1, 'questions.': 1, 'has': 1, 'be': 1, 'to': 2, 'started': 1, 'upon': 1, 'back': 1, 'son': 1, 'the': 1, 'glad': 1, 'he': 1, 'a': 1, 'great': 1, 'look': 1, 'i': 2, 'later': 1, 'think': 1, 'will': 1, 'these': 1, 'so': 1, "i'm": 1, 'my': 1, 'gem.': 1}, {'and': 1, 'page.': 1, 'old': 1, 'just': 2, 'character': 1, 'is': 1, 'it': 1, 'son.': 1, 'month': 1, 'as': 1, 'have': 1, 'toy': 1, "he's": 1, 'when': 1, 'long': 1, 'pages': 1, 'few': 2, 'enough': 1, 'book': 2, 'stuffed': 1, 'elephant': 1, 'neat': 1, 'be': 1, 'we': 1, 'attention': 1, 'to': 3, '6': 1, 'realization': 1, 'words': 1, 'with': 1, 'between': 1, 'association': 1, 'a': 2, 'short': 1, 'older': 1, 'of': 2, 'well': 1, 'see': 1, 'keep': 1, 'will': 1, 'so': 1, 'each': 1, 'the': 7, 'my': 1}, {'and': 1, 'is': 1, 'gift.': 1, 'pretty,.': 1, 'for': 1, 'also': 1, 'recommend': 1, 'gives': 1, 'be': 1, 'used': 1, 'very': 1, 'it': 3, 'years...i': 1, 'a': 3, 'great': 1, 'made': 1, 'this': 1, 'light': 1, 'well': 1, 'will': 1, 'highly.': 1, 'nice': 1, 'makes': 1}, {'affordable': 1, 'try': 1, '!easy': 1, 'and': 2, 'for': 1, 'wall': 1, 'spring': 1, 'a': 1, '...fine': 1, 'up': 1, '**********': 1, 'room..': 1, 'decals': 1, 'this': 1, ',fun': 1, 'brightens': 1, '5+': 1, 'quality': 1, 'project': 1, 'any': 1, 'out': 1}, {'all': 1, 'because': 1, 'reason:small': 1, 'wall': 1, 'money': 1, 'is': 1, 'it': 1, 'one': 1, 'second': 1, 'in': 2, 'apply': 1, 'flowers': 1, 'flower': 1, 'floor': 1, 'when': 1, 'to': 1, 'only': 1, 'you': 1, 'waste': 1, 'roll.': 1, 'most': 1, 'fell': 1, 'know': 1, 'pieceyou': 1, 'day': 1, 'a': 1, 'on': 2, 'sizehard': 1, 'of': 1, 'see': 1, 'morning': 1, 'will': 1, 'part': 1, 'how': 1, 'the': 4}, {'and': 1, 'wall': 1, 'coming': 1, 'decals': 1, 'as': 1, 'thick': 1, 'recommend.': 1, 'again': 1, 'would': 2, 'literally': 1, 'stayed': 1, 'plastic': 1, 'stuck': 1, '5': 1, 'was': 1, 'then': 1, 'almost': 1, 'started': 1, 'peeling': 1, 'like': 1, 'stick!': 1, 'not': 2, 'off': 1, 'off.': 1, 'purchase': 1, 'about': 1, 'applying': 1, 'for': 1, 'i': 1, 'them!': 1, 'were': 2, 'the': 3, 'minutes': 1, 'or': 1}, {'and': 3, 'fantastic': 1, 'themed': 1, 'winnie': 1, 'paintwork.': 1, 'cost': 1, 'at': 1, 'in': 1, '&#34;look&#34;': 1, 'stickers': 2, 'impressed': 1, 'decor': 1, 'with.': 1, "don't": 1, '-': 1, 'seamless': 1, 'to': 1, 'that': 1, 'easy': 1, 'new': 1, 'was': 1, 'a': 1, 'option': 1, 'get': 1, 'very': 4, 'stick': 1, 'they': 2, 'not': 1, 'pooh': 1, 'wall': 2, 'like': 1, 'zealand': 1, 'on': 3, 'look': 1, 'effective': 1, 'i': 2, 'all.': 1, 'could': 1, 'these': 2, 'were': 2, 'professional': 1, 'the': 3}, {'page.': 1, 'on': 1, 'about': 1, 'said': 1, 'and': 1, 'i': 2, 'came': 1, 'ir': 1, 'grat': 1, 'satisfied': 1, 'reccomend': 1, 'very': 1, 'as': 1, 'product,': 2, 'it': 1, 'follow': 1, 'more.': 1, 'highly': 1, 'design,': 1, 'the': 2, 'buying': 1}, {'love': 1, 'chain': 1, 'jesus': 1, 'lives!': 1, 'in': 1, 'need': 1, 'our': 1, 'divine': 3, 'your': 1, 'jesuswho': 1, 'for': 1, 'pray': 1, 'god': 1, 'to': 1, 'offers': 1, 'neck.': 1, 'you': 1, 'nice': 1, 'an': 1, 'around': 1, 'mercy': 2, 'very': 1, 'it!': 1, 'pendant': 1, 'mercy.': 1, 'now': 1, 'him': 1, 'on': 1, 'of': 2, 'country.': 1, 'us': 1, 'ocean': 1, 'represents': 1, 'my': 1}, {"i'll": 1, 'soft': 1, 'right': 1, 'love': 1, 'simple': 1, 'wipes.': 2, 'are': 3, 'changes.': 1, 'our': 1, 'done.': 1, 'find': 1, 'and': 4, 'for': 2, 'ordering': 1, 'get': 1, 'now!': 1, 'actually': 1, 'other': 1, 'more': 1, 'a': 2, 'them': 2, 'million': 1, 'that': 1, 'price': 1, 'after': 1, 'uses': 1, 'know': 1, 'they': 3, 'baby': 1, 'during': 1, 'reusable': 1, 'dry': 1, 'great': 1, 'these': 1, 'of': 1, 'days': 1, 'i': 2, 'so': 1, 'clean': 1, "i'm": 1, 'my': 1, 'diaper': 2}, {'and': 2, 'thought,': 1, 'smaller': 1, 'just': 1, 'is': 1, 'it': 2, 'wall.': 1, 'looks': 1, 'measurements.': 1, 'what': 1, 'was': 2, 'nice': 1, 'that': 1, 'but': 1, 'not': 1, 'bit': 1, 'than': 1, 'a': 1, 'on': 1, 'great': 1, 'i': 1, 'fault': 1, 'taking': 1, 'the': 1, 'my': 2}, {'and': 2, 'old': 1, 'significantly': 1, 'them': 1, 'one': 1, 'high': 1, 'as': 1, 'are': 1, 'broken': 1, 'year': 1, 'seem': 1, 'open': 3, 'size': 1, 'given': 1, 'for': 1, 'needed': 1, 'package...': 1, 'that': 1, 'able': 1, 'their': 1, 'only': 1, 'of': 2, 'safety': 1, 'normal': 1, '6': 1, 'pins': 3, 'new': 1, 'learned': 1, 'has': 1, 'was': 2, 'bought': 1, 'we': 2, 'his': 1, 'to': 4, 'though': 1, 'price': 1, 'night': 1, 'use': 1, 'clothes.': 1, 'break': 1, 'how': 1, 'bit': 1, 'son': 1, 'than': 1, 'he': 2, 'a': 1, 'on': 1, 'open.': 1, 'autistic': 1, 'sturdy': 1, 'these': 1, 'recall': 1, "hasn't": 1, 'shipping': 1, 'side': 1, 'i': 1, 'reasonable': 1, 'time': 1, 'the': 4, 'more': 2, 'my': 1, 'or': 1, 'once': 1}, {'and': 1, 'duty--able': 1, 'quality--worked': 1, 'good': 1, 'fine--heavy': 1, 'to': 1, 'in': 1, 'no': 1, 'these': 1, 'others': 1, 'needed': 1, 'as': 1, 'used': 1, 'way': 1, 'were': 1, 'need': 1, 'be': 1, 'my': 1, 'any': 1, 'filled': 1}, {'and': 1, 'a': 3, 'great': 2, 'has': 1, 'colors': 1, 'for': 1, 'dozen.': 1, 'that': 1, 'lots': 1, 'of': 1, 'easy': 1, 'bargain': 1, 'to': 1, 'bright': 1, 'safety': 1, 'pin': 1, 'uses.': 1, 'with': 1, 'find': 1}, {'and': 1, 'not': 1, 'are': 2, 'in': 1, 'thick': 1, 'little': 1, 'fabric': 1, 'no': 2, 'fortunately': 1, 'there': 1, 'to': 1, 'flimsy': 1, 'stuck.': 1, 'pins': 2, 'was': 2, 'them': 1, 'used': 1, 'on.': 1, 'involved,': 1, 'received': 1, 'diaper': 1, 'baby': 1, 'attractive,': 1, 'hold': 1, 'on': 1, 'i': 2, 'metal': 1, 'up': 1, 'did': 1, 'while': 1, 'so': 1, 'the': 4}, {'honduras,': 1, 'honduras': 1, 'sent.': 1, 'is': 1, 'it': 1, 'kits': 1, 'have': 1, 'in': 2, 'our': 1, 'find': 1, 'also': 1, 'with': 1, 'appreciated': 1, 'to': 3, 'pins': 2, 'sent': 1, 'difficult': 1, 'do': 1, 'we': 2, 'diapers': 1, 'cloth': 1, 'diaper': 2, 'they': 2, 'not': 1, '&#34;pampers&#34;.': 1, 'hold': 1, '&#34;disposable&#34;': 1, 'went': 1, 'age.': 1, 'these': 1, 'the': 3, 'missionaries.': 1}, {'and': 3, 'dressmaker': 1, 'since': 1, 'have': 1, 'pin': 1, 'up': 1, 'it': 1, 'socks': 2, 'years': 1, 'course': 1, 'through': 2, 'a': 1, 'using': 1, 'open': 1, 'your': 1, 'cycle.': 1, 'yet.': 1, 'little': 1, 'working': 1, 'to': 4, 'that': 1, 'been': 1, 'pins,': 1, 'needed': 1, 'recommended': 1, 'tended': 1, 'pins': 2, 'perfectly': 1, 'was': 2, 'do': 1, 'staying': 1, 'tried': 1, 'get': 1, 'never': 1, "thery're": 1, 'washing.': 1, '&#34;friended': 1, 'we': 2, 'but': 3, 'they': 2, 'during': 1, 'brass': 1, 'one': 1, 'matter': 1, 'tricky': 1, 'open,': 1, 'has': 1, 'like': 1, 'lost': 1, 'wash': 2, 'up&#34;.': 1, 'of': 2, 'wife': 1, 'suggested': 1, 'together': 2, 'keep': 1, 'idea.': 1, 'i': 2, 'can': 1, 'many': 1, 'them.': 1, 'the': 4, 'my': 2, 'fact': 1, 'diaper': 2}, {'and': 4, 'the': 11, 'reviews.': 1, 'have': 1, 'pin': 2, "don't": 1, 'clothespins,': 1, 'sock': 1, 'into': 1, 'each': 1, 'am': 1, 'idea': 1, 'socks': 6, 'one': 1, 'as': 2, 'done': 1, 'are': 2, 'another': 1, 'reviewer': 1, 'my': 2, 'dried,': 1, 'still': 1, 'saved': 1, 'hamper': 1, 'out': 1, 'washer,': 1, 'these': 1, 'use': 1, 'now': 1, 'just': 2, 'open': 1, 'line.': 1, 'with': 2, 'noted,': 1, 'had': 1, 'matching': 1, 'to': 2, 'feet.': 1, 'lot': 1, 'before': 1, 'hamper,': 1, 'has': 1, 'it.': 1, 'dry': 2, 'them': 1, 'after': 1, 'on.': 1, 'stay': 1, 'read': 1, 'hang': 2, 'of': 4, 'shelf.': 1, 'great': 2, 'here': 1, 'it': 1, 'by': 1, 'pins': 1, 'mismatched': 1, 'they': 2, 'put': 1, 'line': 1, 'washing.': 1, 'come': 1, 'grab': 1, 'glad': 1, 'a': 3, 'on': 5, 'about': 1, 'for': 1, 'lost': 1, 'this': 2, 'wish': 1, 'side': 1, 'leave': 1, 'i': 7, 'without': 1, 'dirty': 1, 'time': 1, 'life.': 1, 'problem': 1, 'whole': 1, 'or': 1, 'once': 1}, {'fabric.': 1, 'work': 1, 'old': 1, 'is': 1, 'hard': 1, 'it': 1, 'through': 1, 'at': 1, 'still': 1, 'pins,': 1, 'recommend.': 1, 'would': 1, 'thicker': 1, 'to': 1, 'which': 1, 'steel': 1, 'have.': 1, 'very': 1, 'part': 1, 'diaper': 1, 'not': 2, 'strong': 1, 'a': 1, 'unlike': 1, 'i': 1, 'all,': 1, 'the': 2}, {'there': 1, 'am': 1, 'back': 1, 'really': 1, 'are': 2, 'have': 1, 'in': 1, '10.': 1, 'should': 1, 'out': 1, 'thought': 1, 'use': 1, 'that': 1, 'when': 1, 'mark': 1, 'to': 2, 'only': 2, 'going': 1, 'safety': 1, 'pins': 1, 'pins.': 1, 'was': 1, 'be': 1, 'them': 1, 'dozen': 1, 'pins..turns': 1, 'overpriced.': 1, 'regular': 1, 'they': 1, 'crochet': 1, 'sad..and': 1, 'a': 1, 'getting': 1, 'i': 8, 'yarn': 1, 'counted': 1, 'will': 1, 'so': 1, 'picture..as': 1, 'the': 2, 'think': 1}, {'because': 1, 'anymore.': 1, 'tabs': 1, 'is': 1, 'am': 1, 'them': 1, 'through': 2, 'bend': 1, 'sharp': 1, 'said,': 1, "doesn't": 1, 'pain.': 1, 'which': 1, 'dislike': 1, '=': 2, 'ends': 1, 'that': 2, 'pushing': 1, 'diapers': 2, 'velcro': 2, 'easier.': 1, 'sides': 1, 'a': 1, 'on': 1, 'pierce': 1, 'like': 1, 'older': 1, 'i': 1, 'work': 1, 'the': 2, 'my': 2}, {'a': 1, 'useful': 1, 'to': 2, 'no': 1, 'this': 1, 'item': 1, 'is': 1, 'hard': 1, '-': 1, 'locally!': 1, 'matter': 1, 'have': 1, 'diaper': 1, 'purpose...': 1, 'pins': 1, 'the': 1, 'find': 1, 'are': 1}, {'do': 1, 'them': 1, 'peel': 1, 'start': 1, 'these': 1, 'soon': 1, 'wall.': 2, 'to': 3, 'as': 2, 'stick': 2, 'they': 1, 'not': 1, 'you': 1, 'the': 2}, {'money': 1, 'frustrating!': 1, 'when': 1, 'is': 1, "wouldn't": 1, 'it': 2, 'sticky': 1, 'ended': 1, 'at': 1, 'bedroom': 1, 'bedroom!': 1, 'glue': 1, 'wall...very': 1, 'for': 1, 'not': 1, 'girls': 1, 'to': 3, 'disappointing.': 1, 'got': 1, 'waste': 1, 'was': 2, 'excited': 1, 'it.': 1, 'floor!': 1, 'product': 1, 'get': 1, 'very': 2, 'back': 1, 'every': 1, 'baby': 1, 'picking': 1, 'pieces': 1, 'super': 1, 'on': 1, 'off': 1, 'all!': 1, 'i': 4, 'of': 1, 'into': 1, 'up': 2, 'walked': 1, 'having': 1, 'this': 1, 'so': 1, 'time': 2, 'the': 5, 'my': 1, 'or': 1}, {'and': 3, 'heart': 1, 'because': 1, 'blessed': 1, 'pope': 2, 'photo': 1, 'is': 2, 'am': 1, 'it': 4, 'as': 1, 'in': 3, 'ordered': 1, 'between': 1, 'to': 1, 'again': 1, 'strong': 1, 'just': 1, 'would': 1, 'untier': 1, 'giving': 1, 'disappointed': 1, 'whom': 1, 'francis.': 1, 'recommend': 1, 'has': 1, 'was': 1, 'knotted': 1, 'friend': 2, 'lady': 1, 'fathers.': 1, 'buy': 1, 'devotion.': 1, 'crystal,': 1, 'our': 2, 'novena': 1, 'beat.': 1, 'made': 1, 'not': 1, 'along': 1, 'francis': 1, 'with': 2, 'by': 1, 'copy': 1, 'a': 4, 'lovely': 1, 'rosary': 2, 'for': 2, 'undoer)': 1, 'i': 4, 'of': 3, 'looked': 1, 'this': 3, 'definitely': 1, '(or': 1, 'the': 3, 'my': 1, 'beautiful,': 1, 'knots,': 1}, {'and': 2, 'all': 1, 'right': 1, 'price.': 1, 'just': 1, 'scapular': 1, 'some': 1, 'an': 1, 'quality': 1, 'for': 2, 'to': 1, 'more': 1, 'wearing': 1, 'brown': 1, 'around': 1, 'blessing': 1, 'precious.': 1, 'excellent': 1, 'a': 1, 'neck': 1, 'makes': 1, 'value': 1, 'item': 1, 'the': 5, 'such.': 1, 'or': 1, 'orattaching': 1}, {'and': 2, 'slid': 1, 'tough': 2, 'fit.': 1, 'over': 1, 'am': 1, 'product': 1, 'hair': 1, 'snug': 1, 'are': 2, 'have': 2, 'love': 1, 'shipping!': 1, 'satisfied': 1, 'pleased': 1, 'size': 1, 'fit': 1, 'bangle': 1, 'had': 1, 'fitting': 1, 'fast': 1, '.': 1, 'to': 3, 'lotion.': 1, 'whew': 1, 'bangles': 1, 'small.': 1, 'was': 1, 'hand.': 1, 'them': 1, 'get': 1, 'got': 1, 'were': 1, 'overall': 1, 'however': 1, 'but': 2, 'like': 1, 'if': 1, 'adult': 1, 'they': 4, 'hands': 1, 'bit': 1, 'hand': 1, 'with': 3, 'bigger': 1, 'kid': 1, 'a': 3, 'on': 2, 'for': 1, 'i': 5, "wouldn't": 1, 'large': 1, 'these': 1, 'stay.': 1, 'also.': 1, 'product.': 1, 'small': 2, 'wrist': 1, 'the': 3, 'my': 1, 'on!!': 1}, {'and': 2, 'set': 1, 'old': 1, 'cooking.': 1, 'for': 1, '2': 1, 'lot': 1, 'has': 1, 'was': 1, 'granddaughter': 1, 'with': 1, 'a': 1, 'great': 1, 'yr.': 1, 'this': 1, 'of': 1, 'pretend': 1, 'she': 1, 'fun': 1, 'the': 1, 'my': 1, 'playing': 1}, {'and': 1, 'is': 1, 'wash': 1, 'are': 1, 'also': 1, 'useful.': 1, 'to': 1, 'easy': 1, 'awesome.': 1, 'them': 1, 'dry.': 1, 'very': 2, 'price': 1, 'much.': 1, 'bibs.': 1, 'they': 1, 'friends': 1, 'those': 1, 'like': 2, 'i': 1, 'the': 1, 'my': 1}, {'beautiful': 1, 'old': 1, 'too.': 1, 'curls': 1, 'is': 1, 'wash': 1, 'good': 1, 'in': 1, 'messy': 1, 'mouth.': 1, 'provided': 1, '20': 1, 'for': 1, 'to': 2, 'front': 1, 'boy': 1, 'when': 1, 'eaters,': 1, 'bibs,': 1, 'easy': 1, 'elbows': 1, 'his': 2, 'missing': 1, 'very': 1, 'who': 1, 'pasta': 2, 'pocket': 1, 'marinara': 1, 'protections': 1, 'fall': 1, 'fingers.': 1, 'bibs': 1, 'with': 1, 'eat': 1, 'a': 1, 'loved': 1, 'daughter': 1, 'grandson': 1, 'this': 2, 'months': 1, 'loves': 1, 'the': 2, 'my': 2, 'or': 1}, {'perfect': 1, 'and': 1, 'i': 1, 'collection!': 1, 'collect': 1, 'this': 2, 'tree!': 1, 'is': 2, 'it': 1, 'for': 1, 'nativity': 2, 'to': 2, 'add': 1, 'cute': 1, 'a': 1, 'ornaments': 1, 'ornament,': 1, 'such': 1, 'my': 2, "can't": 1, 'wait': 1}, {'and': 2, 'help': 1, 'is': 2, 'it': 1, 'used': 1, 'pees': 1, 'really': 1, 'feeding': 1, 'poops': 1, 'make': 1, 'to': 3, 'enough.': 1, 'month.': 1, 'wet': 1, 'you': 1, 'if': 1, 'book!': 1, 'we': 1, 'sure': 1, 'eating': 1, 'that': 1, 'track': 2, 'breastfeed': 1, 'diapers': 1, 'baby': 1, 'during': 1, 'great': 1, 'helpful': 1, 'this': 1, 'of': 2, 'us': 1, 'keep': 2, 'patterns': 1, 'first': 1}, {'and': 3, 'love': 1, 'just': 1, 'info.': 1, 'use.': 1, 'is': 2, 'life': 1, 'adoption,': 1, 'are': 1, 'have': 1, 'perfect': 2, 'home': 1, 'to': 2, 'fill': 1, 'up.': 1, 'for': 4, 'also': 1, 'travel': 1, 'there': 1, 'when': 1, 'needed': 1, 'book': 3, 'memory': 1, 'schedule.': 2, 'more': 1, 'be': 3, 'we': 2, 'complete': 1, 'emergency': 1, 'track': 2, 'saver!': 1, 'after': 1, 'spot': 1, "baby's": 2, 'how': 1, 'important': 1, 'beginning': 1, 'adopting': 1, 'buying': 1, 'a': 4, 'going': 1, 'keeping': 1, 'i': 5, 'of': 2, 'terrible': 1, 'keep': 1, 'will': 2, 'this': 3, 'traveling,': 1, 'definitely': 1, 'babysitter': 1, 'at': 2, 'the': 3, 'or': 1, 'numbers': 1}, {'love': 3, 'activities': 1, 'when': 1, 'too,': 1, 'soon': 1, 'one': 1, 'as': 3, 'sleep': 1, 'another': 1, 'need': 1, 'your': 2, 'really': 1, 'up.': 1, 'for': 4, '"remember"': 1, 'daycare,': 1, "baby's": 1, 'day.': 1, 'how': 1, 'much': 1, 'tracker': 1, 'provider': 1, 'new': 1, 'you': 2, 'was': 1, 'bought': 1, 'it!!': 1, 'used': 1, 'to': 1, 'get': 1, 'got!!': 1, 'moms-': 1, 'about': 1, 'it': 4, 'no': 1, 'got': 1, 'baby': 2, 'last': 1, 'gift,': 1, 'with': 1, 'be!!': 1, 'a': 1, 'also': 1, 'great': 2, 'ate': 1, 'communicate': 1, 'clock': 1, 'round': 1, 'so': 1, 'can': 1, 'to-': 1, 'care-': 1, 'the': 2, 'my': 1, 'or': 1, 'first': 1}, {'and': 2, 'over.': 1, 'major': 1, 'because': 1, 'love': 1, 'all': 3, 'simple': 1, 'had': 1, 'is': 1, "didn't": 1, 'life': 1, 'really': 1, '(and': 1, 'down': 1, 'course': 1, 'as': 1, 'sure': 1, 'happened.': 1, 'been': 2, 'have': 2, 'in': 1, 'caregiver': 1, 'to': 5, 'out': 1, 'even': 1, 'funny': 1, 'little': 1, 'routines': 1, 'i': 6, 'would': 1, 'how': 1, 'though,': 1, 'things': 1, 'that': 2, 'able': 1, 'finally': 1, 'months),': 1, 'everything': 1, 'enough': 1, 'book': 2, 'easy': 1, 'time': 1, 'probably': 1, 'has': 1, 'was': 2, 'until': 1, 'a': 2, 'saver!!': 1, 'his': 3, 'jot': 1, 'way': 2, 'get': 1, 'knew': 1, 'great/easy': 1, 'after': 1, 'what': 1, 'it': 2, 'forgotten!': 1, 'it,': 1, 'know': 1, 'they': 1, 'baby': 1, '2': 1, 'beginning': 1, 'day': 1, 'me': 3, 'on': 1, 'about': 1, 'milestones': 1, 'for': 3, 'went.': 1, 'this': 2, 'of': 4, "wouldn't": 1, 'work': 1, 'record': 1, 'so': 1, 'transfer': 1, 'let': 1, 'the': 3, 'my': 1, "baby's": 1}, {'and': 2, 'useful': 1, 'being': 1, 'am': 2, 'it': 4, 'one': 2, 'newborn': 1, 'not': 1, 'as': 1, 'at': 1, 'have': 1, 'looks.': 1, 'remember,': 1, 'looked': 1, 'needs': 1, 'from': 2, 'for': 1, 'everything': 1, 'had': 1, 'looking': 1, 'very': 1, '4': 1, 'saw.': 1, 'tracker.': 1, 'was': 1, 'hope': 1, 'happy': 1, 'it.': 1, 'ends': 1, 'used': 1, 'to': 1, 'that': 1, 'read': 1, 'what': 1, 'but': 1, 'delivery': 1, 'baby': 1, 'with': 1, 'weeks': 1, 'a': 1, 'down': 1, 'like': 1, 'this': 1, 'of': 1, 'up': 1, 'reviews': 1, 'i': 6, 'write': 1, 'so': 1, 'the': 1, 'bought': 1, 'my': 1, 'first': 1}, {'and': 4, 'development,': 1, 'have': 1, 'people': 1, 'too.': 1, "baby's": 1, 'some': 1, 'it': 3, 'one': 3, 'see': 1, 'are': 1, 'another': 2, 'our': 1, 'story,': 1, 'bought': 1, 'what': 1, 'rummage': 1, 'visiting': 1, 'things': 1, 'section': 1, 'family,': 1, 'when': 1, 'useful,': 1, 'write': 2, 'also': 1, 'that': 3, 'much': 1, 'helps': 1, '"notes"': 1, 'so': 2, 'sale': 1, 'has': 1, 'filled': 1, 'more': 1, 'be': 2, 'we': 2, 'etc.)': 1, 'to': 3, "i've": 1, 'use': 1, 'like': 1, 'helping': 1, 'feels': 1, '"dad"': 1, 'baby': 1, 'almost': 1, 'with': 1, 'day': 2, 'buying': 1, 'room': 1, 'a': 1, 'loved': 1, 'about': 1, 'several': 1, 'especially': 1, 'this': 1, '(ex:': 1, 'having': 1, 'will': 1, 'i': 2, 'connected.': 1, 'plus': 1, 'at': 1, 'found': 2, 'the': 3, 'happened': 1, 'etc.': 1, 'book': 1, 'soon!': 1}, {'and': 1, 'all': 1, 'winner': 1, '...': 1, 'absolutely': 1, 'is': 2, 'am': 1, 'iparenting': 1, 'an': 1, 'as': 1, 'from': 1, 'work.': 1, 'media': 1, 'starts!': 1, 'better': 1, 'tracker': 1, '5': 1, 'it': 2, 'got': 1, 'seen.': 1, 'worth': 1, 'then': 1, 'good': 1, "i've": 1, 'organized': 1, 'much': 1, 'part': 1, 'reason.': 1, 'others': 1, 'baby': 1, 'extremely': 1, 'a': 1, 'for': 2, 'getting': 1, 'i': 2, 'of': 1, 'package': 1, 'well': 1, "'new": 1, 'this': 2, 'expecting': 1, '$$.': 1, "parents'": 1, 'friends!': 1, 'the': 2, 'my': 2}, {'and': 6, 'the': 1, 'activities': 1, "baby's": 2, 'is': 2, 'in': 1, 'am': 1, 'it': 4, 'one': 1, 'down': 2, 'something': 1, 'another': 1, 'feedings': 1, 'beyond': 1, 'perfect!': 1, 'your': 1, 'out': 1, 'looking': 1, 'i': 4, 'for': 3, 'area': 1, 'ordering': 1, 'with': 1, 'extra': 1, 'when': 1, 'months.': 1, 'write': 2, 'to': 4, '3': 1, 'patterns': 1, 'lot': 1, 'dr': 1, 'new': 1, 'reminder': 1, 'has': 2, 'was': 1, 'happy': 1, 'be': 1, 'run': 1, 'that': 1, 'track': 1, 'patterns.': 1, 'appointments': 1, 'diaper': 1, 'mom': 1, 'medications.': 1, 'an': 1, 'extremely': 1, 'pages': 1, 'a': 3, 'great': 1, 'like': 1, 'anything': 1, 'this': 1, 'of': 2, 'space': 1, 'daily': 1, 'will': 1, 'record': 1, 'sleeping.': 1, "i'm": 1, 'my': 1, 'book': 1, 'changes,': 1}, {'and': 1, 'love': 1, 'helpful': 1, 'for': 2, 'this': 2, 'easy': 1, 'first': 1, 'keep': 1, 'to': 1, 'book': 1, 'track': 1, 'pediatrician': 1, 'mom': 1, 'time': 1, '....super': 1, 'sooooooooo': 1, 'appts': 1, '..especially': 1}, {'and': 1, 'set': 1, 'often': 1, 'share': 1, 'it': 2, 'for': 1, 'doctor': 1, 'to': 3, 'book': 1, 'was': 2, 'baby.': 1, 'used': 1, 'eating': 1, 'track': 1, 'took': 1, 'how': 2, 'appointments': 1, 'important': 1, 'everything.': 1, 'loved': 1, 'about': 1, 'i': 3, 'always': 1, 'up': 1, 'keep': 1, 'this': 1, 'year.': 1, 'she': 1, 'of': 1, 'everything': 1, 'the': 1, 'first': 1}, ... ]




```python
products['word_count']['awesome']
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-46-1529b00764f3> in <module>()
    ----> 1 products['word_count']['awesome']
    

    /opt/conda/lib/python2.7/site-packages/graphlab/data_structures/sarray.pyc in __getitem__(self, other)
       1264             return SArray(_proxy = self.__proxy__.copy_range(start, step, stop))
       1265         else:
    -> 1266             raise IndexError("Invalid type to use for indexing")
       1267 
       1268     def materialize(self):


    IndexError: Invalid type to use for indexing



```python
products['awesome']
```




    dtype: int
    Rows: 166752
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, ... ]




```python
products[products['awesome'] ==3]
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">review</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rating</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">word_count</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sentiment</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">awesome</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Munchkin 2 Pack Fresh<br>Food Feeder, Colors May ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">AWESOME MUST HAVE!!!!! ok<br>i got these at first b/c ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 1, 'being': 1,<br>'able': 1, 'using': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Fisher-Price Rainforest<br>Open-Top Cradle Swing ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">We bought this swing for<br>our 3 week old when we ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'infant': 1, 'just': 3,<br>'when': 2, 'feature.' ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Child Airplane Travel<br>Harness - Cares Safety ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This contraption is<br>awesome. We recently  ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'move': 1, 'go': 1,<br>'row': 1, 'had': 1, ' ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Lascal BuggyBoard Maxi+ -<br>Black ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">bought it, attached it<br>and traveled with it ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 4, 'all': 2,<br>'set': 1, 'old': 2, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Chicco NextFit<br>Convertible Car Seat, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I purchased this car seat<br>online through BRUS a ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 7, 'concept': 1,<br>'consider': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
</table>
[? rows x 6 columns]<br/>Note: Only the head of the SFrame is printed. This SFrame is lazily evaluated.<br/>You can use sf.materialize() to force materialization.
</div>




```python
sum_terms
for i in selected_words:
 print(i,products[i].sum())
```

    ('awesome', 2002)
    ('great', 42420)
    ('fantastic', 873)
    ('amazing', 1305)
    ('love', 40277)
    ('horrible', 659)
    ('bad', 3197)
    ('terrible', 673)
    ('awful', 345)
    ('wow', 131)
    ('hate', 1057)



```python
sum_terms
```




    1057




```python
tr_data,te_data=products.random_split(.8, seed=0)
selected_words_model=graphlab.logistic_classifier.create(tr_data,target='sentiment',features=selected_words,validation_set=te_data)
```


<pre>Logistic regression:</pre>



<pre>--------------------------------------------------------</pre>



<pre>Number of examples          : 133448</pre>



<pre>Number of classes           : 2</pre>



<pre>Number of feature columns   : 11</pre>



<pre>Number of unpacked features : 11</pre>



<pre>Number of coefficients    : 12</pre>



<pre>Starting Newton Method</pre>



<pre>--------------------------------------------------------</pre>



<pre>+-----------+----------+--------------+-------------------+---------------------+</pre>



<pre>| Iteration | Passes   | Elapsed Time | Training-accuracy | Validation-accuracy |</pre>



<pre>+-----------+----------+--------------+-------------------+---------------------+</pre>



<pre>| 1         | 2        | 0.165510     | 0.844299          | 0.842842            |</pre>



<pre>| 2         | 3        | 0.274127     | 0.844186          | 0.842842            |</pre>



<pre>| 3         | 4        | 0.369975     | 0.844276          | 0.843142            |</pre>



<pre>| 4         | 5        | 0.469403     | 0.844269          | 0.843142            |</pre>



<pre>| 5         | 6        | 0.568830     | 0.844269          | 0.843142            |</pre>



<pre>| 6         | 7        | 0.672232     | 0.844269          | 0.843142            |</pre>



<pre>+-----------+----------+--------------+-------------------+---------------------+</pre>



<pre>SUCCESS: Optimal solution found.</pre>



<pre></pre>



```python
selected_words_model['coefficients']
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">index</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">class</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">value</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">stderr</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">(intercept)</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.36728315229</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.00861805467824</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">awesome</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.05800888878</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.110865296265</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">great</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.883937894898</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0217379527921</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">fantastic</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.891303090304</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.154532343591</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">amazing</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.892802422508</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.127989503231</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">love</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.39989834302</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0287147460124</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">horrible</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-1.99651800559</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0973584169028</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">bad</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-0.985827369929</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0433603009142</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">terrible</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-2.09049998487</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0967241912229</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">awful</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-1.76469955631</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.134679803365</td>
    </tr>
</table>
[12 rows x 5 columns]<br/>Note: Only the head of the SFrame is printed.<br/>You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.
</div>




```python
selected_words_model['coefficients'].sort('value',ascending=False)
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">index</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">class</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">value</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">stderr</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">love</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.39989834302</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0287147460124</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">(intercept)</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.36728315229</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.00861805467824</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">awesome</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1.05800888878</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.110865296265</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">amazing</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.892802422508</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.127989503231</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">fantastic</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.891303090304</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.154532343591</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">great</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.883937894898</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0217379527921</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">wow</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-0.0541450123333</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.275616449416</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">bad</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-0.985827369929</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0433603009142</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">hate</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-1.40916406276</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0771983993506</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">awful</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">None</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">-1.76469955631</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.134679803365</td>
    </tr>
</table>
[12 rows x 5 columns]<br/>Note: Only the head of the SFrame is printed.<br/>You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.
</div>




```python
selected_words_model.evaluate(te_data,metric='roc_curve')
```




    {'roc_curve': Columns:
     	threshold	float
     	fpr	float
     	tpr	float
     	p	int
     	n	int
     
     Rows: 100001
     
     Data:
     +-----------+-----+-----+-------+------+
     | threshold | fpr | tpr |   p   |  n   |
     +-----------+-----+-----+-------+------+
     |    0.0    | 1.0 | 1.0 | 27976 | 5328 |
     |   1e-05   | 1.0 | 1.0 | 27976 | 5328 |
     |   2e-05   | 1.0 | 1.0 | 27976 | 5328 |
     |   3e-05   | 1.0 | 1.0 | 27976 | 5328 |
     |   4e-05   | 1.0 | 1.0 | 27976 | 5328 |
     |   5e-05   | 1.0 | 1.0 | 27976 | 5328 |
     |   6e-05   | 1.0 | 1.0 | 27976 | 5328 |
     |   7e-05   | 1.0 | 1.0 | 27976 | 5328 |
     |   8e-05   | 1.0 | 1.0 | 27976 | 5328 |
     |   9e-05   | 1.0 | 1.0 | 27976 | 5328 |
     +-----------+-----+-----+-------+------+
     [100001 rows x 5 columns]
     Note: Only the head of the SFrame is printed.
     You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.}




```python
selected_words_model.show(view='Evaluation')
```




```python
diaper_champ_reviews=products[products['name'] == 'Baby Trend Diaper Champ']
```


```python
diaper_champ_reviews['predicted_sentiment']=sentiment_model.predict(diaper_champ_reviews,output_type='probability')
```


```python
diaper_champ_reviews=diaper_champ_reviews.sort('predicted_sentiment',ascending=False)
```


```python
diaper_champ_reviews.head()
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">review</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rating</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">word_count</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">sentiment</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">awesome</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Luke can turn a<br>clean diaper to a dirty ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 1, 'less': 1,<br>"friend's": 1, '(which': ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I LOOOVE this diaper<br>pail!  Its the easies ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'just': 1, 'over': 1,<br>'rweek': 1, 'sooo': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">We researched all of the<br>different types of di ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 2, 'just': 4,<br>"don't": 2, 'one,': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">My baby is now 8 months<br>and the can has been ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{"don't": 1, 'when': 1,<br>'over': 1, 'soon': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">This is absolutely, by<br>far, the best diaper  ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'just': 3, 'money': 1,<br>'not': 2, 'mechanism' ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Diaper Champ or Diaper<br>Genie? That was my ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'all': 1, 'bags.': 1,<br>'son,': 1, '(i': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Wow!  This is fabulous.<br>It was a toss-up between ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'and': 4, '"genie".': 1,<br>'since': 1, 'garbage' ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I originally put this<br>item on my baby registry ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'lysol': 1, 'all': 2,<br>'bags.': 1, 'feedback': ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Two girlfriends and two<br>family members put me ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'just': 1, 'when': 1,<br>'both': 1, 'results': 1, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Baby Trend Diaper Champ</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">I am one of those super-<br>critical shoppers who ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'taller': 1, 'bags.': 1,<br>'just': 1, "don't": 4, ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">great</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">fantastic</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">amazing</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">love</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">horrible</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">bad</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">terrible</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">awful</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">wow</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">hate</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">predicted_sentiment</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999937267</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999917406</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999899509</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999836182</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999824745</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999759315</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999692111</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999642488</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999604504</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.999999486804</td>
    </tr>
</table>
[10 rows x 17 columns]<br/>
</div>




```python
selected_words_model.predict(diaper_champ_reviews[0:1], output_type='probability')
```




    dtype: float
    Rows: 1
    [0.7969408512906713]




```python
sentiment_model=graphlab.logistic_classifier.create(train_data,target='sentiment',features=['word_count'],validation_set=test_data)
```


<pre>WARNING: The number of feature dimensions in this problem is very large in comparison with the number of examples. Unless an appropriate regularization value is set, this model may not provide accurate predictions for a validation/test set.</pre>



<pre>Logistic regression:</pre>



<pre>--------------------------------------------------------</pre>



<pre>Number of examples          : 133448</pre>



<pre>Number of classes           : 2</pre>



<pre>Number of feature columns   : 1</pre>



<pre>Number of unpacked features : 219217</pre>



<pre>Number of coefficients    : 219218</pre>



<pre>Starting L-BFGS</pre>



<pre>--------------------------------------------------------</pre>



<pre>+-----------+----------+-----------+--------------+-------------------+---------------------+</pre>



<pre>| Iteration | Passes   | Step size | Elapsed Time | Training-accuracy | Validation-accuracy |</pre>



<pre>+-----------+----------+-----------+--------------+-------------------+---------------------+</pre>



<pre>| 1         | 5        | 0.000002  | 1.283331     | 0.841481          | 0.839989            |</pre>



<pre>| 2         | 9        | 3.000000  | 2.582358     | 0.947425          | 0.894877            |</pre>



<pre>| 3         | 10       | 3.000000  | 3.013683     | 0.923768          | 0.866232            |</pre>



<pre>| 4         | 11       | 3.000000  | 3.496982     | 0.971779          | 0.912743            |</pre>



<pre>| 5         | 12       | 3.000000  | 3.997275     | 0.975511          | 0.908900            |</pre>



<pre>| 6         | 13       | 3.000000  | 4.480168     | 0.899991          | 0.825967            |</pre>



<pre>| 10        | 18       | 1.000000  | 6.676904     | 0.988715          | 0.916256            |</pre>



<pre>+-----------+----------+-----------+--------------+-------------------+---------------------+</pre>



<pre>TERMINATED: Iteration limit reached.</pre>



<pre>This model may not be optimal. To improve it, consider increasing `max_iterations`.</pre>



```python

```
