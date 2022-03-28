https://medium.com/this-week-in-machine-learning-ai/building-the-product-knowledge-graph-at-amazon-with-luna-dong-60226caa4e92

https://naixlee.github.io/Product_Knowledge_Graph_Tutorial_KDD2021/




https://nijianmo.github.io/amazon/index.html

这里有2018年的amazon评论数据，元数据如下:

```
Sample metadata:

{
  "asin": "0000031852",
  "title": "Girls Ballet Tutu Zebra Hot Pink",
  "feature": ["Botiquecutie Trademark exclusive Brand",
              "Hot Pink Layered Zebra Print Tutu",
              "Fits girls up to a size 4T",
              "Hand wash / Line Dry",
              "Includes a Botiquecutie TM Exclusive hair flower bow"],
  "description": "This tutu is great for dress up play for your little ballerina. Botiquecute Trade Mark exclusive brand. Hot Pink Zebra print tutu.", 
  "price": 3.17,
  "imageURL": "http://ecx.images-amazon.com/images/I/51fAmVkTbyL._SY300_.jpg",
  "imageURLHighRes": "http://ecx.images-amazon.com/images/I/51fAmVkTbyL.jpg",
  "also_buy": ["B00JHONN1S", "B002BZX8Z6", "B00D2K1M3O", "0000031909", "B00613WDTQ", "B00D0WDS9A", "B00D0GCI8S", "0000031895", "B003AVKOP2", "B003AVEU6G", "B003IEDM9Q", "B002R0FA24", "B00D23MC6W", "B00D2K0PA0", "B00538F5OK", "B00CEV86I6", "B002R0FABA", "B00D10CLVW", "B003AVNY6I", "B002GZGI4E", "B001T9NUFS", "B002R0F7FE", "B00E1YRI4C", "B008UBQZKU", "B00D103F8U", "B007R2RM8W"],
  "also_viewed": ["B002BZX8Z6", "B00JHONN1S", "B008F0SU0Y", "B00D23MC6W", "B00AFDOPDA", "B00E1YRI4C", "B002GZGI4E", "B003AVKOP2", "B00D9C1WBM", "B00CEV8366", "B00CEUX0D8", "B0079ME3KU", "B00CEUWY8K", "B004FOEEHC", "0000031895", "B00BC4GY9Y", "B003XRKA7A", "B00K18LKX2", "B00EM7KAG6", "B00AMQ17JA", "B00D9C32NI", "B002C3Y6WG", "B00JLL4L5Y", "B003AVNY6I", "B008UBQZKU", "B00D0WDS9A", "B00613WDTQ", "B00538F5OK", "B005C4Y4F6", "B004LHZ1NY", "B00CPHX76U", "B00CEUWUZC", "B00IJVASUE", "B00GOR07RE", "B00J2GTM0W", "B00JHNSNSM", "B003IEDM9Q", "B00CYBU84G", "B008VV8NSQ", "B00CYBULSO", "B00I2UHSZA", "B005F50FXC", "B007LCQI3S", "B00DP68AVW", "B009RXWNSI", "B003AVEU6G", "B00HSOJB9M", "B00EHAGZNA", "B0046W9T8C", "B00E79VW6Q", "B00D10CLVW", "B00B0AVO54", "B00E95LC8Q", "B00GOR92SO", "B007ZN5Y56", "B00AL2569W", "B00B608000", "B008F0SMUC", "B00BFXLZ8M"],
  "salesRank": {"Toys & Games": 211836},
  "brand": "Coxlures",
  "categories": [["Sports & Outdoors", "Other Sports", "Dance"]]
}

```
有一二三级类目，有alsobuy alsoview商品间的关联关系 有feture和title 可以提取一些属性 但更多的规格信息需要额外爬取


## 现有工作

https://github.com/google-research-datasets/MAVE/tree/f886c1683367c1e9e8383ff25cd82525580dfb65
 The dataset contains 3 million attribute-value annotations across 1257 unique categories on 2.2 million cleaned Amazon product profiles. It is a large, multi-sourced, diverse dataset for product attribute extraction study. 
 
 ```
 {
   "id":"B0002H0A3S",
   "category":"Guitar Strings",
   "paragraphs":[
      {
         "text":"D'Addario EJ26 Phosphor Bronze Acoustic Guitar Strings, Custom Light, 11-52",
         "source":"title"
      },
      {
         "text":".011-.052 Custom Light Gauge Acoustic Guitar Strings, Phosphor Bronze",
         "source":"description"
      },
      ...
   ],
   "attributes":[
      {
         "key":"Core Material",
         "evidences":[
            {
               "value":"Bronze Acoustic",
               "pid":0,
               "begin":24,
               "end":39
            },
            ...
         ]
      },
      {
         "key":"Winding Material",
         "evidences":[
            {
               "value":"Phosphor Bronze",
               "pid":0,
               "begin":15,
               "end":30
            },
            ...
         ]
      },
      {
         "key":"Gauge",
         "evidences":[
            {
               "value":"Light",
               "pid":0,
               "begin":63,
               "end":68
            },
            {
               "value":"Light Gauge",
               "pid":1,
               "begin":17,
               "end":28
            },
            ...
         ]
      }
   ]
}
 ```


https://arxiv.org/abs/2103.13864

https://arxiv.org/pdf/2112.08663.pdf


https://github.com/xu-song/k-plug

https://github.com/THUDM/KOBE/issues?q=is%3Aissue+is%3Aclosed
