# bank_product_prediction

#项目背景
对于各大银行公司、金融公司而言，判断一个客户会不会购买产品是至关重要的，这关乎到公司的收益，在本项目中，我从这一现实痛点出发，综合评估客户的各个特征：年龄、职业、婚姻、之前是否有过购买记录等，以及当前市场的情况：银行利率、消费者信心指数等，找到了一种方法：在尽可能保证满足条件的人数足够多的前提下，提高预测准确率。  

#数据集说明
本项目使用的数据集共有22500行以及22个字段，包括：age（年龄）,education（学历）,housing（是否有房贷）,poutcome（之前营销活动的结果：unknow,other,failure,success）,cons_conf_index（消费者信心指数）,lending_rate3m（银行利率）等字段，目标变量为subscribe（是否购买）。  

#分析流程
在拿到数据之后，我先大概看了数据的行数以及各字段的含义，然后进行数据清洗、EDA、特征工程、建模与评估、结论与建议。  

#核心洞察与结论
经过以上一系列步骤，我得到了以下的关键规律：
1.年龄<30且曾有购买记录的客户购买率高，达到了24.9%，但同时满足这两个条件的人数很少，仅占整个数据集的3%左右。
<img width="1473" height="912" alt="屏幕截图 2026-05-20 173041" src="https://github.com/user-attachments/assets/8c588a97-c3e5-4f77-b13d-c902cff00a9f" />
在得到结论1之后，我一直在思考：那我们能不能找到这样一种方法，在尽可能保证满足条件的人数足够多的前提下，提高预测准确率。
于是我又将目光放在了其他的特征上，却意外发现了一个反常现象。
2.消费者信心指数变高，购买人数却没有增多（每组的人数基本相同）。
<img width="1513" height="587" alt="屏幕截图 2026-05-20 173918" src="https://github.com/user-attachments/assets/12693184-2c7e-434e-a448-dd21531d4d97" />
我怀疑：是不是有其他因素在其中影响，甚至是强影响因素。
3.利率是强影响因素：低利率时期购买率显著更高。
<img width="1075" height="602" alt="屏幕截图 2026-05-20 173822" src="https://github.com/user-attachments/assets/d9e68be4-1df6-48a8-a6f6-4283eb841bf3" />
<img width="392" height="165" alt="屏幕截图 2026-05-20 174411" src="https://github.com/user-attachments/assets/2997217d-94fa-4c48-ba34-9943a631776a" />
4.加入利率后的逻辑回归模型，相比原始规则（选取满足年龄<30且曾有过购买记录的客户），在相同营销预算下，真实购买人数提升了30%以上。
<img width="711" height="144" alt="屏幕截图 2026-05-20 174753" src="https://github.com/user-attachments/assets/cfa1a906-d1b9-41e6-b4fc-8f003be2e47f" />
5.在以后的推销过程中，我们就可以采取这样的方法：先计算出客户的订购概率（prob），选择订购概率较高的人进行推销，尽可能降低我们的推销成本，并获得尽可能多的收益。

#复现步骤
环境要求：Python3.1.2。
所需库：numpy，pandas，matplotlib，seaborn，LogisticRegression
运行方式：jupyter notrbook打开.ipynb即可。

#许可证
本项目采用MIT许可证
