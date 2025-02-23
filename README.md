摘要  
&emsp;現代數位金融正在飛速發展，許多東西現在已間使用數位服務,投資也能使用加密貨幣,現在銀行也有推出虛擬幣的ETF。本專題以python撰寫機器學習模型交易加密貨幣投資組合,透過反覆訓練來讓投資組合能在理想的範圍內進行預測,以防止爆倉(指當投資者交易方向與市場走反導致投資人權益數（淨值）低於最低保證金，而被第三方強制結算),利用Google Colab來執行機器學習和深度學習模型,並且利用Colab裡面的Python資料庫,來簡單做出一些金融上的指標。  

研究背景與動機  
&emsp;在資訊快速的發展，銀行漸漸把重心放在網銀，還有行動支付改變人們的消費習慣，逐漸崛起的新星---虛擬貨幣,我們希望透過，訓練模型，並在此之上提升其穩定性和性能，能實踐出APP上架。  

研究目的  
&emsp;用python編寫程式碼在Colab上執行並訓練模型，最後匯出一段時間的成果。比特幣做為加密貨幣的元老，其走勢往往能牽動其他的加密貨幣，例如比特幣大漲時會帶動其他小幣可能一起漲，甚至漲得更多，但比特幣大跌時同樣也會讓其他小幣一起大跌，如同加密貨幣的大盤利用比特幣的大盤特性計算一種動能指標來判斷當前市場是樂觀情緒(利於做多)還是悲觀情緒(不利於做多)在比特幣動能<0時判定為不利於做多的市場，將所有幣種賣出並轉換成穩定幣以度過進一步下跌風險在比特幣動能>0後判定為利於做多。  

研究時間
&emsp;本專題的資料劃分（Data Partitioning）是依據時間進行。  
&emsp;資料切分:  
&emsp;訓練時間段 : 2020/10/17 ~ 2021/10/17   
&emsp;蒐集BTC- ETH- BNB- SOL- BUSD的漲幅數據  
&emsp;測試時間段 : 2021/10/18 ~ 2023/10/25  
&emsp;這邊我們是學習模型測試到2023/10/25當下  
軟體功能實作  
步驟1:連結Colab到使用者的google雲端硬碟  
 ![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E9%80%A3%E7%B5%90%E9%9B%B2%E7%AB%AF.png)
步驟2:安裝套件  
 ![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)
步驟3:設定參數  
 ![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E8%A8%AD%E5%AE%9A%E5%8F%83%E6%95%B8.png)
 ![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E7%B4%B9%E5%AE%9A%E5%8F%83%E6%95%B81.png)  
步驟四:資料、環境建置、模型訓練    
  ![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E8%B3%87%E6%96%99%E3%80%81%E7%92%B0%E5%A2%83%E5%BB%BA%E7%BD%AE%E3%80%81%E6%A8%A1%E5%9E%8B%E8%A8%93%E7%B7%B4.png) 
  ![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E8%A8%93%E7%B7%B4.png) 
步驟五:回測結果
   ![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E5%9B%9E%E6%B8%AC%E7%B5%90%E6%9E%9C.png)

為了讓沒有程式背景的使用者操作介面更為簡單,程式碼放在後端我利用python的模組(Module),把要使用的函式另外寫成3個檔案,分別是:data.py ,predicting.py ,training.py
  
data.py:  
&emsp;簡單敘述data.py:  
	&emsp;1.使用joblib、pandas、numpy、talib、ta 等資料庫來處理和分析金融數據。   
	&emsp;2.準備金融數據:prepare_data 函數負責從指定文件夾讀取金融數據，選擇特定的加密貨幣列表（crypto_list），並提取出訓練和交易期間的相關數據。函數中進行了數據的清洗、重新取樣和結構化，以及對每個加密貨&emsp;幣應用各種技術指標。  
	&emsp;3. 特徵生成：  
		&emsp;函數中對於選定的特徵列表（feature_list），生成相應的特徵數據。
  		&emsp;這些特徵包括但不限於：  
		&emsp;hedging：根據特定的指數（如 BTC/USDT）生成對沖策略相關的特徵。  
		&emsp;dd：計算每個加密貨幣的回撤（drawdown）特徵。  
		&emsp;86ta：使用 talib 和其他計算手段生成技術分析指標。  
		&emsp;st：計算超級趨勢（supertrend）指標。  
		&emsp;qlib：根據收盤價格和成交量等計算量化金融特徵。  
		&emsp;catch22：使用 pycatch22 庫計算加密貨幣價格的相關特徵。  
	&emsp;4.數據合併：  
		最後將生成的各種特徵數據合併為一個完整的數據集，用於訓練和測試模型。  




  
predicting.py:  
	&emsp;get_ready_data 函數：此函數用於從加密貨幣交易所（例如 Binance）獲取指定加密貨幣的 OHLCV（開、高、低、收、成交量）數據。它使用 ccxt 函式庫設置交易所和認證，然後從交易所獲取每個加密貨幣對應的 &emsp;OHLCV 數據。返回整理過的 OHLCV 數據以及按日期和加密貨幣整理的收盤價數據。  
	&emsp;tr 和 atr 函數：tr 函數計算真實範圍（True Range），用於後續的平均真實範圍（ATR）計算。  
	&emsp;atr:函數根據指定的期間計算平均真實範圍。  
	&emsp;supertrend 函數：此函數實現超級趨勢指標的計算。它根據前一期的數據計算超級趨勢的上下限和趨勢狀態（上升或下降）。超級趨勢指標用於確定市場趨勢並生成交易信號。
	&emsp;returns 和 drawdown 函數：returns 函數計算基於給定價格的資產增長率。  
	&emsp;drawdown 函數計算資產的回撤。  
	&emsp;get_features 函數：此函數根據指定的加密貨幣列表和特徵列表從 OHLCV 數據中提取所需的技術指標和特徵。它可以計算不同特徵，如動量、波動性、技術分析指標（例如超級趨勢）、資產的收益率和回撤等。這些特徵&emsp;可以用於構建和訓練交易策略模型。  
	&emsp;softmax_normalization 函數：此函數用於對模型預測的動作進行 softmax 正規化，以確保動作權重之和為 1。  
	&emsp;get_predict_result 函數：此函數基於訓練好的強化學習模型，預測下一步的交易行動（例如買入或賣出）。它使用模型預測的動作來計算每個加密貨幣的交易權重，這些權重可以用於配置投資組合。此外，根據特定的&emsp;條件（例如對衡量指標的預測），它可以對投資組合進行對沖操作。    
	&emsp;總之，predicting.py的這些函數組成了一個完整的加密貨幣交易策略框架，包括數據準備、特徵工程、模型訓練和交易預測等功能。它提供了一個基礎架構，可以用於開發和測試不同的加密貨幣交易策略。   


Train.py:  
	&emsp;OpenAI Gym 的強化學習環境，用於加密貨幣投資組合管理的模擬。  
	&emsp;CryptoPortfolioEnv 類別：  
	&emsp;此類別是自定義的 Gym 環境，用於模擬加密貨幣投資組合的交易。  
	&emsp;__init__ 方法初始化環境，設置環境參數，例如加密貨幣數量、初始金額、交易成本比例、獎勵比例等。  
	&emsp;step 方法模擬每一步的交易行為，包括計算投資組合報酬、更新投資組合價值等。  
	&emsp;reset 方法重置環境狀態，用於開始新的交易仿真。  
	&emsp;render 方法用於渲染環境的當前狀態，這裡可能用不到。  
	&emsp;building_environment 函數：  
	&emsp;此函數用於建立模型的訓練和交易環境。  
	&emsp;包括初始化訓練和交易環境的 CryptoPortfolioEnv 實例。  
	&emsp;DRLAgent 類別：  
	&emsp;此類別用於定義深度強化學習（DRL）的訓練和預測操作。  
	&emsp;get_model 方法用於獲取指定算法的 DRL 模型，例如 A2C、DDPG、TD3 等。  
	&emsp;train_model 方法用於訓練 DRL 模型。  
	&emsp;DRL_prediction 方法用於根據訓練後的模型進行預測，生成交易記錄和帳戶價值記錄。  
	&emsp;train_test_agent 函數：  
	&emsp;此函數用於訓練和測試 DRL 模型。首先創建 DRLAgent 的實例。然後根據模型名稱和參數訓練指定的 DRL 模型。  
	&emsp;最後使用訓練後的模型在測試環境上進行交易預測，並保存相關的交易記錄和模型。  


步驟6得到結果:  
![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E7%B5%90%E6%9E%9C1.png)
![image](https://github.com/boyi0701/My-senior-project/blob/main/picture/%E7%B5%90%E6%9E%9C.png)




