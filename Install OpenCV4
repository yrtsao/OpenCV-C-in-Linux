Linux環境下安裝OpenCV 4  
參考https://hackmd.io/@xpg109/H1wZiRUNF  

安裝cmake, pkg-config, lib*  

$sudo apt-get install gcc g++ cmake pkg-config build-essential  
$sudo apt-get install libgtk2.0-dev libavcodec-dev libavformat-dev libtiff5-dev libswscale-dev  
從github下載opencv  

$cd ~  
$git clone https://github.com/opencv/opencv.git  
建立build資料夾  

$cd opencv   
$mkdir build  
Step2 編譯lib  
使用cmake產生makefile  

$cd build  
$cmake -D CMAKE_BUILD_TYPE=Release -D OPENCV_GENERATE_PKGCONFIG=YES -D CMAKE_INSTALL_PREFIX=/usr/local ..  
make  

$make -j4 //cpu的核心數  
$sudo make install  
配置pkg-config  




$sudo vim /etc/ld.so.conf  
加入Path: /usr/local/lib  
_______________________________
如何編輯步驟
開啟檔案

bash
sudo vim /etc/ld.so.conf
進入插入模式（編輯文字）

鍵盤按下 i

游標可以移動到檔案底部，然後輸入一行：

/usr/local/lib
存檔並退出

按下 Esc 鍵回到普通模式。

然後輸入 :wq，再按 Enter 就會儲存並退出 vim。

:w 表示 write（儲存）

:q 表示 quit（退出）

合起來 :wq 表示儲存並退出
__________________________________________

$sudo ldconfig -v  
$export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig  

確認 opencv 安裝版本  


$pkg-config --modversion opencv4  


 

Step3 驗證  
創建一個專案資料夾  

$cd ~  
$mkdir cvtest  
使用vs code 在cvtest資料夾下建立  

cvtest.cpp  
lena.jpg 下載測試用照片lena    
wget https://upload.wikimedia.org/wikipedia/en/7/7d/Lenna_%28test_image%29.png -O lena.jpg    
複製貼上以下code  


#include <opencv2/highgui.hpp>  
#include <iostream>  
int main( int argc, char** argv )  
{  
    cv::Mat image;  
    image = cv::imread("lena.jpg",cv::IMREAD_COLOR);  
    if(! image.data)  
        {  
            std::cout<<"Could not open file" << std::endl;  
            return -1;  
        }  
    cv::namedWindow("lena", cv::WINDOW_AUTOSIZE);  
    cv::imshow("lena", image);  
    cv::waitKey(0);  
    return 0;  
}  
在vs code 按下"ctrl+shift+p" 搜尋 “C/C++: Edit Configurations(JSON)”  

在"c_cpp_properties.json"的include path 加入 "/usr/local/include/opencv4/**"  

在cvtest資料夾下，使用vs code創建一個Makefile(#建議自己打，不然可能會有error)  






CC = g++  
PROJECT = cvtest  
SRC = cvtest.cpp  
LIBS = `pkg-config --cflags --libs opencv4`  
$(PROJECT) : $(SRC)  
    $(CC) $(SRC) -o $(PROJECT) $(LIBS)  
回到terminal  

$make  
$./cvtest  

