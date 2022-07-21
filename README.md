本次項目分析使用UCI Machine Learning dataset的零售業公開銷售數據。
首先以python 進行資料預處理與轉換後，選擇訂單日期、訂單編號，以及總消費金額做為計算RFM指標的依據，以四分位距來進行分組，可分別得到RFM三項指標的顧客價值評分。
另外也進行Cohort Analysis，計算顧客留存率並繪製矩陣。

補充說明資料前處理時遇到的問題:

進行資料清洗時，發現產品數量及單價皆有負值，然而若使用一般方法直接刪除負值，由於原先的資料並非所有列皆為數值列，因此將會擦除非常大量的有價值數據。
此筆資料數據量龐大，若直接進行補值除了耗費時間，也可能影響分析結果。

之後我找到一個不必刪除整列的方法，使用Pandas dataframe的select_dtypes:

dataframe.select_dtypes(include, exclude)

Parameter	Value	Description
include	string|list	Which column(s) to include in the result. Required if the exclude parameter is not present.
exclude	string|list	Which column(s) to exclude from the result. Required if the include parameter is not present.
另外由於之後會使用power bi做自動化報表，其不支援巢狀列表。因此須注意將二維陣列轉換為一維陣列
