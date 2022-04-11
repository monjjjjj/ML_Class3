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

