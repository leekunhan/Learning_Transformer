# Explaination of the task

## 導言
在 Transformer 架構中，注意力機制（Attention Mechanism）是核心。透過計算查詢（Query）、鍵（Key）和值（Value）之間的關係，它幫助模型專注於輸入中最相關的部分，從而提升模型的性能和效率。在 Transformer 中，自注意力（Self-Attention）和編碼器-解碼器注意力（Encoder-Decoder Attention）共同作用，使模型能更好地捕捉和利用序列中的信息，取得優異的效果。

查詢（Query）、鍵（Key）和值（Value）的概念：
- 查詢（Query）：用於查找相關信息的輸入。
- 鍵（Key）：與查詢匹配以找到相關信息的參數。
- 值（Value）：與鍵關聯的實際信息，當匹配發生時返回。
我們可以用一個學習新語言的例子來解釋這些概念：

假設你在學習法語，你有一本教材，裡面有很多章節，你希望先專注於最重要的部分來學習。
- 查詢向量（Query Vector）：就像你對自己提出的一個問題，例如「我應該先學哪些最重要的部分？」。
- 鍵向量（Key Vector）：就像教材中的索引或目錄，它幫助你找到相關的信息。你可以使用鍵向量來查找與查詢向量中的問題相關的教材部分。
- 值向量（Value Vector）：是你在教材中找到的實際信息，比如詞彙或語法規則。你利用值向量來幫助自己學習這門語言。  
  
在 Transformer 架構中，查詢、鍵和值向量幫助模型專注於輸入序列中最相關的部分，比如一句話或一段文字，忽略不重要的部分。這使得模型能更好地理解輸入的意圖，並生成更準確的輸出，比如翻譯或摘要。

通過這樣的注意力機制，模型可以更高效地處理大量的數據，並在諸多應用中取得傑出的表現。


## 說明
在檔案[dot_product_qkv.ipynb](./dot_product_qkv.ipynb)中，我們希望實現Scaled Dot-Product Attention的機制來更了解模型比較注重文字中哪一個字，其中
- Query 是當前我們關注的詞語，用來查找相關信息
- Key 是我們用來計算與Query相關性的詞語
- Value 是我們根據注意力權重加權求和後生成最終輸出的詞語

### 為什麼 Key 和 Value 設成一樣的值
在自注意力機制（Self-Attention）中，Query、Key 和 Value 通常都來自同一個sequence（句子）。這樣的設計使得模型能夠在同一個句子內找到詞語之間的相關性。

由於我們這裡沒有進行模型訓練，因此我們將 Key 和 Value 設成一樣的值。這樣做的好處是：

1. 簡化了實驗設置，便於理解和實現注意力機制的基本原理。
2. 可以直接觀察詞語之間的關聯性，而不需要訓練過程來調整權重。

我們會在最後透過可視化的結果查看各個權重結果，並在檔案最後進行說明。

如果你對整個Transform架構有興趣，可以看看[transformer_in_pytorch](./transformer_in_pytorch.ipynb)這個檔案，裡面有由pytorch架構構成的完整Transformer架構Source Code.