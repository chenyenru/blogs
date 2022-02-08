<<<<<<< HEAD
version https://git-lfs.github.com/spec/v1
oid sha256:33b0615dc0ec8c5b556841242df22cb72f5cc857fc2f4ef5453bfd77841567bb
size 6558
=======
- [ ] Multivariate Regression
	- [x] Research on Variables
	- [x] Confounding Variables
	- [x] research about monthly vs. yearly data (pros and cons of summarizing monthly data into annual data or repeat the annual data 12 times as monthly data)
	- [ ] pick one of the 題目 you come up with, the one you like the most, and write a background/introduction paragraph. The paragraph should present the relevant background info, the problem statement, and our proposed research. And you should also cite sources whenever possible.

# Data Source
<iframe src="https://govstat.taichung.gov.tw/DgbasWeb/statfile.aspx?mode=1&cateno=03#" height=500px width=100%></frame>

<iframe src="https://statdb.dgbas.gov.tw/pxweb/dialog/statfile9.asp" height=500px width=100%></iframe>

<iframe src="https://data.gov.tw/dataset/29947" height=500px width=100%></iframe>
# AQI
First up, what is AQI?
![基於備選傳感器和預測模型的空氣質量試驗](https://aqicn.org/air/experiments/images/aqiscale.png)

### Calculations ([source](https://tw.piliapp.com/aqi/tw/))
先由下列方法來計算出各種副指標值：

-   O3,8hr： 取最近連續8小時移動平均值
-   O3： 取即時濃度值
-   PM2.5： 0.5 × 前12小時平均 + 0.5 × 前4小時平均
-   PM10： 0.5 × 前12小時平均 + 0.5 × 前4小時平均
-   一氧化碳： 取最近連續8小時移動平均值
-   二氧化硫： 取即時濃度值
-   二氧化硫24小時： 取最近連續24小時濃度平均值
-   二氧化氮： 取即時濃度值

再依 **污染物濃度與即時副指標值對照表** 來找出最大的做為 AQI
![[截圖 2022-02-06 下午12.36.51.png]]
台灣的即時空氣品質指標(AQI)計算方式為： O3 (臭氧)、PM2.5 (細懸浮微粒)、PM10 (懸浮微粒)、CO (一氧化碳)、SO2 (二氧化硫)、 NO2 (二氧化氮) 依不同的時間長度來計算出一個指標值，再取出其中最大值為即時空氣品質指標，該最大值測項即為指標污染物。


# Variables
- 台中市
	- 主要死因
		- 氣管、支氣管、肺癌
 [1] "year"                                               
 [2] "population_density"                                 
 [3] "空氣中總懸浮微粒濃度"                               
 [4] "細懸浮微粒手動監測.PM2.5.濃度值"                    
 [5] "空氣中臭氧濃度"                                     
 [6] "二氧化硫含量"                                       
 [7] "AQI.PSI..100之日數比率"                             
 [8] "死亡人數.主要死因_癌症.人."                         
 [9] **"死亡人數.主要死因_肺炎.人."**                         
[10] **"死亡率.主要癌症_氣管.支氣管和肺癌_死亡率.人.十萬人."**
[11] "標準化死亡率.主要死因_總計.人.十萬人."              
[12] "標準化死亡率.主要死因_癌症.人.十萬人."              
[13] "教育程度_15歲以上人口教育程度_研究所..."            
[14] **"教育程度_15歲以上人口教育程度_大學..."**

**bolded words** are the **dependent variables** i wish to investigate on
and other variables are used as confounding variables
- 
# Monthly vs Yearly Data
![[withers2015.pdf]]

According to Withers, 
>To answer the question in the title, we suggest the following rough rule: use annual means if 5 or more years of data are available; and use monthly means if less than 5 years of data are available

Thus, _I'll use annual means because my data contains more than 5 years of records_
# Topic
I'm interested in whether air quality index 

Residuals:
      1       2       3       4       5       6       7       8 
-0.2436 -0.1715  1.0974 -1.5319 -2.6774  1.7966  0.7313  0.9991 

Coefficients:
                                        Estimate Std. Error t value Pr(>|t|)
(Intercept)                           159.679158  76.663727   2.083    0.129
標準化死亡率.主要死因_癌症.人.十萬人.  -0.419007   0.259843  -1.613    0.205
空氣中總懸浮微粒濃度                    0.068962   0.151162   0.456    0.679
population_density                      0.003346   0.008313   0.402    0.714
AQI.PSI..100之日數比率                 -0.383627   0.234252  -1.638    0.200

Residual standard error: 2.278 on 3 degrees of freedom
Multiple R-squared:  0.578,	Adjusted R-squared:  0.01537 
F-statistic: 1.027 on 4 and 3 DF,  p-value: 0.5118

``` ad-note
relevant background info, the problem statement, and our proposed research. And you should also cite sources whenever possible.
```
## Topic 1:  **空氣中總懸浮微粒濃度** and **死亡率.主要癌症_氣管.支氣管和肺癌_死亡率.人.十萬人.**
### Introduction
The discussion that air quality may contribute to determining one's death rates have long been examined. This includes how This study gathered data from the Taiwan 


## Topic 2:  **死亡人數.主要死因_肺炎.人.**   
## Topic 3: **教育程度_15歲以上人口教育程度_大學...**
## Topic 4: **台灣電力公司_火力發電_溫室氣體排放量** and **死亡率.主要癌症_氣管.支氣管和肺癌_死亡率.人.十萬人.**
This is the topic I'm most interested in because the Taichung Trash Incineration Power Plant is actually very close to me.

### Introduction
The balance between economy and health has long been a controversial issue, where to achieve one often means the loss of another. And this question is specifically focused on in Taichung, Taiwan, containing one of the largest thermal power plants in the world. The study gathered data from Taichung Government, Taiwan's Official Statistical data website, and Taiwan Government's Open Data Platform to perform a multivariate analysis that examines on the relationship between the amount of greenhouse gas emission from Taichung thermal power plant and death rate of lung cancer in Taichung.


#### Resources
Chen, Tase-Lung. “Air Pollution Caused by Coal-Fired Power Plant in Middle Taiwan.” _International Journal of Energy and Power Engineering_, vol. 6, no. 6, 15 Nov. 2017, p. 121., https://doi.org/10.11648/j.ijepe.20170606.15.

# Ending words
I feel like my topic has slowly turned on finding independent variables to predict air quality index to _finding dependent variables that may be affected by air quality index._ Not sure if this is a good thing but I'm satisfied now. 

