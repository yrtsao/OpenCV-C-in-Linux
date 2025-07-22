# OpenCV-C-in-Linux
紀錄筆記  
學習如何用C++在linux環境下使用OpenCV  
會嘗試項目:  
1. OpenCV基本功能引用  
2. 結合GUI製作小工具
3. 使用Cuda加速
4. (持續更新中...


________
依照Copilot 提供的入門學習
🚀 入門目標  
建立一個 C# GUI（WinForms 或 WPF），並整合 OpenCV（C++）來執行影像處理邏輯，例如顯示圖片、擷取攝影機、邊緣偵測等。  

🔧 開發環境準備  
工具	說明  
Visual Studio	建議使用 2022 以上版本  
OpenCV for C++	建議使用 v4.x（可從 OpenCV 官方網站下載）  
CMake	編譯 OpenCV / C++ 專案使用  
C++/CLI	建立中介 DLL（C++ ↔ .NET）  
.NET Framework / .NET 6+	C# GUI 應用程式開發使用  
📦 建立中介 DLL（C++/CLI）  
在 Visual Studio 建立「CLR Class Library」專案  

在此專案中引入 OpenCV 標頭與 lib 檔（可以參考 這篇教學）  

將 OpenCV 的功能寫成 class method，例如：Mat ConvertToGray(string path)  
 
使用 cv::Mat 處理圖片，再轉換結果為 byte[] 傳給 C#  

🧬 建立 C# GUI 應用程式  
建立 WinForms 或 WPF 專案  

加入中介 DLL 的參考  

使用 PictureBox 或 Image 控制元件顯示影像  

呼叫 DLL 中的方法，例如：var imgBytes = CvBridge.ConvertToGray(filePath);  
 
🎯 實作小功能（由淺入深） 
功能	難度	建議順序  
顯示圖片	⭐	第一個 target  
攝影機串流	⭐⭐	VideoCapture → bitmap  
灰階處理	⭐⭐	cv::cvtColor()  
邊緣偵測	⭐⭐⭐	cv::Canny()  
臉部偵測	⭐⭐⭐⭐	cv::CascadeClassifier  
📝 延伸技巧  
若想避免用 C++/CLI，可使用 P/Invoke，但要小心 cv::Mat 與 byte[] 的資料轉換問題  

也可以使用 Emgu CV 這類封裝好的 .NET library，雖然效能稍低但設定簡單  
