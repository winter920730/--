# mediapipe
這段程式碼使用 OpenCV 和 Mediapipe 庫進行全身姿勢檢測，並在攝像頭捕獲的實時視頻上繪製骨架和面部網格。以下是程式碼的大致解釋：

首先，導入必要的設定

cv2：OpenCV : 用於圖像處理和顯示。
mediapipe as mp：Mediapipe : 用於執行全身姿勢檢測和繪製關鍵點。
初始化 Mediapipe 組件：

mp_drawing：用於繪製關鍵點和連接線的 Mediapipe 繪圖工具。
mp_drawing_styles：定義繪圖樣式的對象。
mp_holistic：Mediapipe 的全身姿勢檢測模型。
打開攝像頭（Webcam）：

使用 cv2.VideoCapture(0) 打開默認的攝像頭設備。如果成功打開攝像頭，則變數 cap 將持有攝像頭捕獲的圖像流。
使用 mp_holistic.Holistic 對象開始全身姿勢檢測：

在 with 語句中，創建 Holistic 對象，設置檢測和追蹤的信心閾值。
在 while 循環中，不斷從攝像頭捕獲圖像幀。
對圖像進行預處理：

將捕獲的圖像調整大小，以適應顯示窗口。
使用 Mediapipe 進行全身姿勢檢測：

使用 holistic.process() 方法，將 RGB 圖像傳遞給 Mediapipe，執行全身姿勢檢測。檢測結果將存儲在 results 變數中。
繪製面部和身體關鍵點：

使用 mp_drawing.draw_landmarks 方法，將檢測結果中的面部關鍵點和身體骨架關鍵點繪製到圖像上。
這樣可以在實時視頻中可視化出面部網格和身體骨架。

在圖像上顯示坐標：
對於身體骨架關鍵點，通過迭代 results.pose_landmarks.landmark 列表中的關鍵點，將其坐標以文本形式顯示在圖像上。

顯示圖像：
使用 cv2.imshow() 顯示處理後的圖像。

退出循環：
按下鍵盤上的 "q" 鍵時，退出循環。

清理資源：
在程式結束時，釋放攝像頭資源並關閉所有打開的窗口。

這段程式從攝像頭捕獲實時視頻，並使用 Mediapipe 進行全身姿勢檢測和可視化。它在圖像上繪製了面部網格和身體骨架，並在圖像上顯示了身體骨架關鍵點的坐標。這對於姿勢分析和監測非常有用。
