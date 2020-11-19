# Neural style transfer
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/1010code/Neural-style-transfer/blob/main/Neural_style_transfer_(keras).ipynb)

此程式參考於 [Keras](https://keras.io/examples/generative/neural_style_transfer/)，重現 [A Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576) 論文方法.

> Transfering the style of a reference image to target image using gradient descent.

## 簡介
style transfer 可以根據輸入照片產生一張與輸入風格相似的圖片。此模型有3個輸入，分別有`輸入圖片`、`內容圖片`和`風格圖片`。並透過梯度下降法逐漸修正輸入的圖像，使定義的 Loss 越來越小，從而使得最新的輸入圖像在內容和風格上都更像輸入的內容圖片和風格圖片。

通常我們拍攝的照片只有內容，例如：人物、汽車、建築物...等。而藝術家的畫作添加了個人風格，例如：抽象派、印象派...等。其中人類是可以很容易地辨識一幅畫的內容以及風格，也就是說我們可以把一幅畫的內容和風格分割開來。

如下圖所示，在內容重建(Content Reconstruction)的部分。我們透過卷積神經網路，每一層建立在前一層的基礎上，因此逐層學習到越來越高層，越來越抽象的特徵。我們可以發現第一層網路可以重建出原始圖像的細節，隨著層數越高會學習到更抽象的特徵。

風格重建(Style Reconstruction)部分，通常一張畫的風格是一致的，不管 Filter 的內容是什麼，都會有風格特徵包含在其中。因此提取風格就是要找出不同 Filter 的共同點。實作中是透過計算同一層 Filter 的相關性來提取風格的特徵。

![](https://i.imgur.com/D0kWZvr.png)

## Result
| Content Image                        | Style Image                          | Style Transfer                       |
|--------------------------------------|--------------------------------------|--------------------------------------|
| ![](https://i.imgur.com/SGcqzia.jpg) | ![](https://i.imgur.com/PkRvbHg.jpg) | ![](https://i.imgur.com/oIGnPPH.png) |

## Reference
[風格轉換(Style Transfer) -- 人人都可以是畢卡索](https://ithelp.ithome.com.tw/articles/10192738)

[Neural Style Transfer](http://fancyerii.github.io/books/neural-style-transfer/#neural-style-1)