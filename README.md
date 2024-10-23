摘要  
	現代數位金融正在飛速發展，許多東西現在已間使用數位服務,投資也能使用加密貨幣,現在銀行也有推出虛擬幣的ETF。本專題以python撰寫機器學習模型交易加密貨幣投資組合,透過反覆訓練來讓投資組合能在理想的範圍內進行預測,以防止爆倉(指當投資者交易方向與市場走反導致投資人權益數（淨值）低於最低保證金，而被第三方強制結算),利用Google Colab來執行機器學習和深度學習模型,並且利用Colab裡面的Python資料庫,來簡單做出一些金融上的指標。  

研究背景與動機  
	在資訊快速的發展，銀行漸漸把重心放在網銀，還有行動支付改變人們的消費習慣，逐漸崛起的新星---虛擬貨幣,我們希望透過，訓練模型，並在此之上提升其穩定性和性能，能實踐出APP上架。  

研究目的  
	用python編寫程式碼在Colab上執行並訓練模型，最後匯出一段時間的成果。比特幣做為加密貨幣的元老，其走勢往往能牽動其他的加密貨幣，例如比特幣大漲時會帶動其他小幣可能一起漲，甚至漲得更多，但比特幣大跌時同樣也會讓其他小幣一起大跌，如同加密貨幣的大盤利用比特幣的大盤特性計算一種動能指標來判斷當前市場是樂觀情緒(利於做多)還是悲觀情緒(不利於做多)在比特幣動能<0時判定為不利於做多的市場，將所有幣種賣出並轉換成穩定幣以度過進一步下跌風險在比特幣動能>0後判定為利於做多。  

研究時間
	本專題的資料劃分（Data Partitioning）是依據時間進行。  
	資料切分:  
	訓練時間段 : 2020/10/17 ~ 2021/10/17   
	蒐集BTC- ETH- BNB- SOL- BUSD的漲幅數據  
	測試時間段 : 2021/10/18 ~ 2023/10/25  
	這邊我們是學習模型測試到2023/10/25當下  
軟體功能實作
	步驟1:連結Colab到使用者的google雲端硬碟  
 ![image](https://github.com/boyi0701/My-senior-project/blob/main/%E9%80%A3%E7%B5%90%E9%9B%B2%E7%AB%AF.png)
	步驟2:安裝套件  
 ![image](https://github.com/boyi0701/My-senior-project/blob/main/%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)    
	步驟3:設定參數  
 ![image](https://github.com/boyi0701/My-senior-project/blob/main/%E8%A8%AD%E5%AE%9A%E5%8F%83%E6%95%B8.png)    
 ![image](https://github.com/boyi0701/My-senior-project/blob/main/%E7%B4%B9%E5%AE%9A%E5%8F%83%E6%95%B81.png)    
 	步驟四:資料、環境建置、模型訓練  
  ![image](https://github.com/boyi0701/My-senior-project/blob/main/%E8%B3%87%E6%96%99%E3%80%81%E7%92%B0%E5%A2%83%E5%BB%BA%E7%BD%AE%E3%80%81%E6%A8%A1%E5%9E%8B%E8%A8%93%E7%B7%B4.png)  
  ![image](https://github.com/boyi0701/My-senior-project/blob/main/%E8%A8%93%E7%B7%B4.png)  
  	步驟五:回測結果
   ![image](https://github.com/boyi0701/My-senior-project/blob/main/%E5%9B%9E%E6%B8%AC%E7%B5%90%E6%9E%9C.png)
  
