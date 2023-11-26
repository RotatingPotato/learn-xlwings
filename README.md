# xlwings 

```python
#建立Excel檔案
workbook = xw.Book() # 建立新的工作簿
sheet = workbook.sheets['工作表1'] # 選取工作表
sheet.cells(1, "A").value = "Hello!"
sheet.range('A2').value = "Woo!"
#插入matplotlib圖表
sheet.pictures.add(fig, name="MyPlot", update=True, left=sheet.range('H5').left, top=sheet.range('A1').top)
for i in range(10):
    sheet.range("B"+str(i+1)).value =np.random.random_integers(1,100+1)
#合併儲存格
merged_range = sheet.range('C1:D3') # 合併範圍
merged_range.merge() # 合併儲存格

# 取得合併範圍的左上角儲存格
top_left_cell = merged_range[0, 0] 

# 設定文字格式
top_left_cell.api.Font.Bold = True # 粗體
top_left_cell.api.Font.ColorIndex = 3 # 紅色
top_left_cell.api.Font.Size = 20 # 字體大小 
top_left_cell.api.HorizontalAlignment = -4108 # 水平置中
top_left_cell.api.VerticalAlignment = -4108 # 垂直置中
top_left_cell.value = '合併' # 設定儲存格文字

# 設定儲存格框線
sheet.range('C4:D5').api.Borders(5).LineStyle = 1 
sheet.range('C4:D5').api.Borders(9).LineStyle = 2
sheet.range('C4:D5').api.Borders(7).LineStyle = 3 
sheet.range('C4:D5').api.Borders(10).LineStyle = 4 
sheet.range('C4:D5').api.Borders(5).Weight =4
sheet.range('C4:D5').api.Borders(9).Weight =3
sheet.range('C4:D5').api.Borders(7).Weight =2 
sheet.range('C4:D5').api.Borders(10).Weight =1

#折線圖
chart = sheet.charts.add()
chart.set_source_data(sheet.range('B1:B10'))
chart.chart_type = 'line'
chart.top = sheet.range('A11').top
chart.left = sheet.range('A11').left


workbook.save("LinearRegression/test8.xlsx") # 儲存檔案
time.sleep(60)
workbook.close() # 關閉檔案
```


|   Borders    |  名稱  | 對應編號 |
|:------------:|:------:|:--------:|
|  xlEdgeLeft  | 左邊框 |    7     |
|  xlEdgeTop   | 上邊框 |    8     |
| xlEdgeBottom | 下邊框 |    9     |
| xlEdgeRight  | 右邊框 |    10    |



|    LineStyle    |    名稱    | 對應編號 |
|:---------------:|:----------:|:--------:|
|  xlContinuous   |    實線    |    1     |
|     xlThick     |    粗線    |    4     |
|  xlDashDotDot   |  雙點劃線  |    5     |
| xlSlantDashDot  | 斜線點劃線 |    13    |
|     xlDash      |    虛線    |  -4115   |
|    xlDouble     |    雙線    |  -4119   |
|      xlDot      |    點線    |  -4118   |
|    xlMedium     |  中等粗細  |  -4138   |
| xlLineStyleNone |   無線條   |  -4142   |
