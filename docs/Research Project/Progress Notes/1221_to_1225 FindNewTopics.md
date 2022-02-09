This week
- [x] Explainable NLP Hate Speech
- [x] Chinese NLP
- [x] Taiwan's Air Quality


# Explainable NLP
## Def Explainable AI (XAI):[](https://blog.taus.net/explainable-ai-xai-nlp-edition)
1.  **Feature importance:** uses the score of the importance of a given feature, which is ultimately used to output the final prediction. Text-based features are more intuitive for humans to interpret, enabling feature importance-based explanations.
2.  **Surrogate model:** a second model, or proxy model, used to explain model predictions. These proxy models can achieve both local or global explanations. One drawback of this method is that the learned surrogate models and the original model could use different methodologies when making predictions. 
3.  **Example-driven:** uses examples, usually from labeled data, that are semantically similar to the input example to explain the given prediction. An example of an example-driven explanation is using the nearest-neighbor approach, which has been used in areas such as text classification and question answering. 
4.  **Provenance-based:** utilizes illustrations of some or all of the prediction derivation process. This is often an effective explainability technique when the prediction is the outcome of a series of decision rules or reasoning steps. 
5.  **Declarative induction:** involves human-readable transformations, such as rules and programs to deliver explainability.

![Explainable-AI-(XAI)-NLP-Edition-Figures](https://blog.taus.net/hs-fs/hubfs/Explainable-AI-(XAI)-NLP-Edition-Figures.jpg?width=624&name=Explainable-AI-(XAI)-NLP-Edition-Figures.jpg)
Attention mechanism is commonly used
### LIME for NLP
https://github.com/marcotcr/lime

**tutorial**
https://towardsdatascience.com/explain-nlp-models-with-lime-shap-5c5a9f84d59b
- **more tutorial**
https://stackoverflow.blog/2019/05/06/predicting-stack-overflow-tags-with-googles-cloud-ai/
- **SHAP** 
https://github.com/slundberg/shap

# 中文NLP
## CNSENTI（中國人研究員做的model）

https://github.com/hidadeng/cnsenti

![[截圖 2021-12-22 下午11.15.49.png]]

however, it doesn't seem to be very useful because it doesn't work when I tested the following:
![[截圖 2021-12-22 下午11.17.01.png]]
Lol. Neutral

## BERT Chinese! 
[Hugging Face Page for bert-base-chinese](https://huggingface.co/bert-base-chinese?text=%E5%B7%B4%E9%BB%8E%E6%98%AF%5BMASK%5D%E5%9B%BD%E7%9A%84%E9%A6%96%E9%83%BD%E3%80%82)
[# Google BERT中文应用之微博情感极性分析](https://zhuanlan.zhihu.com/p/55856680)
- 用微博的情感資料集做的
- **限制**：目前的中文資料集還非常少

# 空氣品質
https://sci-hub.se/https://ieeexplore.ieee.org/document/9418342
![[bhat2021.pdf]]

--> This seems pretty feasible
--> 空氣品質指標資料集
https://data.epa.gov.tw/dataset/aqx_p_488




I feel the best topic that would suit my project would be the investigation in Taichung's air quality.