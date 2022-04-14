# ML_Class3
## CNN(專門被用在影像上的架構)
### 為什麼設計network架構可以讓結果變得更好？
1. for fully connected network
   
   雖然參數的增加可以增加模型的彈性與能力，但也可能增加了overfitting的風險！
   
   考慮到影像的特性，其實並不一定需要fully connected，不需要每一個neuron跟每一個input的每一個dimension都有一個weight!

2. 對影像本身特性的觀察
   
   (1)去觀察圖片裡面是否出現一些特別重要的patterns，而這些patterns是代表某個物件！
   
      就不需要每個neuron都去看一整張完整的圖片，就不需要把整張圖片當作輸入！
      
      每一個neuron都只需要關心自己的receptive field發生了什麼事情！
      
      receptive field由自己來定義，可以根據對問題的理解來決定receptive field的形狀！
    
   (2)同樣的patterns可能會出現在不同的區域裡面
   
      多個neuron共用同一組參數：filter
      
   (3)Receptive Field + Parameter Sharing = Convolutional Layer
   
      share weight這件事其實就是把filter掃過一張圖片：為convolutoin
      
      不同的receptive field可以共用參數，而這組共用的參數就叫做filter！
      
3. Pooling來自subsampling，能夠減少運算量，但如果運算能力夠的話，pooling為可有可無！

   Pooling是沒有要根據data去學任何東西
   
4. CNN並不能處理影像放大、縮小、旋轉的問題！
   但Spatial Transformer layer這個架構可以處理此問題！

## Self-Attention(另一個常見的network架構)
### Input is a set of vectors，且vector set的大小可能不一樣
1. 例如文字處理中的句子、聲音訊號、graph(如social network)
2. I saw a saw. 兩個saw對model來說是一樣的，必須去考慮上下文的資訊！

   開一個window去考慮上下文再去判斷詞性！

   若是開了太大的window，意味著fully connected的network會需要非常多的參數，運算量會很大，也容易發生overfitting!
3. 可用self-attention解決上述問題

   若不希望把整個sequence包在一個window裡面，所以要find the relevant vectors in a sequence
4. Multi-head Self-attention
   
   要用多少head是一個hyper parameter，需要自己調整
   
   為什麼會需要比較多的head?
   
       相關這件事情有很多種形式、定義，所以不能只有一個q，多個q去負責不同種類的相關性
5. Self-attention v.s. CNN

   CNN: 考慮整張圖片
   
   Self-attention: 只考慮receptive field
   
   <img width="247" alt="image" src="https://user-images.githubusercontent.com/62006029/163110574-b902454b-81a6-42f7-9942-4207d15a7e79.png">
   
6. CNN(因其彈性較小，所以需要較多的訓練資料)在資料量少的時候表現較佳

   Self-attention(因其彈性較大，所以需要較多的訓練資料)在資料量多的時候表現較佳
7. Self-attention v.s. RNN

   RNN無法平行處理所有的input
   


