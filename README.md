# CS_NOTE
## Linux (Git Bash) ##
### 檔案名 ###
長度至多256個字元，可包刮字母、數字、"."、"_"、"-"
### 路徑 ###
#### 絕對路徑 ####
例如： /usr/share/doc
#### 相對路徑 ####
例如由 /usr/share/doc 要到 /usr/share/man 底下時，寫成： 『cd ../man』
#### 一些語法 ####
 cd 變換目錄 
 
 pwd顯示目前的目錄 
 
 mkdir 建立一個新目錄 
 
 rmdir 刪除一個裡面是空的空目錄 
 
 cp 複製 
 
 mv 移動 
 
 ls 顯示目錄下的所有內容 
 
 cat 查看檔案內容
### 編輯檔案 ###
#### nano ####
Ctrl W：查詢命令，按下後會跳轉到末行的反白位置，輸入要查詢的內容
#### vi/vim ####
* 一般:  可使用上下左右進行游標 宜動、刪除字元及複製貼上檔案 資料 
* 進階: 編輯文字
* 命令

  :w 將編輯的資料寫入硬碟檔案中
  
  :w! 若檔案屬性為『只讀』時，強制寫入該檔案(!為強制)

  :q 離開
  
  :wq 儲存後離開
  
  :w[filename] 將編輯的資料儲存成另一個檔案（類似另存新檔）
  
  :r[filename] 在編輯的資料中，讀入另一個檔案的資料
  
  set nu  顯示行號，設定後會在每一列的自首顯示該列的行號
### 使用者 ###
user(owner)
  
group
  
others
系統管理員:root
#### 一些語法 ####
/. :（根目錄）：所有的檔案皆從根目錄開始，只有root使用者具該目錄的許可權

/root：此目錄為系統管理員，也稱作超級許可權者的使用者主目錄

/bin：存著經常使用的指令

/boot：系統啟動時必須讀取的檔案，包括系統核心、連線檔案以及映象檔案

/dev：存放周邊設備代號的檔案

/etc：放置與系統設定、管理相關的檔案

/home：存放普通使用者的主目錄，在Linux中每個使用者都有一個自己的目錄，一般該目錄名是以使用者的帳號命名的

/media：可用來做為光碟、軟碟片、隨身碟與其他分割區的自動掛載點

/tmp：供全部使用者暫時放罝檔案的目錄

/usr：為非常重要的目錄，使用者的很多應用程式和檔案都放在此目錄下，類似windows 下的program files目錄

/var：系統執行時，內容經常變動的資料或暫存檔 (1og file)，都會放罝在這倜目錄裡
#### 更改使用者權限 ####
ls-l 可查看各檔案與目錄的擁有者和群組

chown 可修改檔案或目錄有者及群組

chmod 可控制檔案如何被他人調用

>chmod[-cfvR][--help][--version]mode file...

mode 許可控制檔案如何被他人調用
>[ugoa...][[+-=][rwxX]...][,...]
>>u：檔案擁有者

>>g：與該檔案的擁有者同一個群體者

>>o：其他以外的人

>>a:三者皆是

>>＋：增加許可權

>>-：取消許可權

>>=：唯一設定許可權

>>r：可讀取(4)

>>w：可寫入(2)

>>x：可執行(1)

檔案 filel. txt 設為所有人皆可讀取：
chmod ugotr filel. txt

將檔案 filel. txt 與file2.txt 設為該檔案擁有者，與其所屬同一個群體者可寫入但其他以外的人則不可寫入：
chmod ug+w,o-w filel. txt file2.txt

將ex1. py 設定為只有該檔案擁有者可以執行:
chmod u+x exl.py

將目前目錄下的所有檔案與子目錄皆設為任何人可讀取：
chmod -R a+r*

chmod a=rwx file == chmod 777 file

chmod ug=rwx, o=x file ==chmod 771 file
### 壓縮檔案 ###
#### gzip ####
壓縮：gzip FileName

解壓縮：

gunzip FileName.gz

gzip -d FileName.gz
#### xz ####
壓縮：xz -z FileName

解壓縮：xz -d FileName.xz
#### tar.gz ####
壓縮：tar -zcvf FileName.tar.gz DirName

解壓縮：tar -zxvf FileName.tar.gz
### 檔案搜尋 ###
#### find [path] [option] [action] filename ####
>option

>>-size EX：找出大於500M的檔案→-size +500M

>>-name EX：找出為照片的檔案→-name "*.jpg"

>>-type EX：-type f→一般檔案;-type d→一般目錄

>>→-user user1 -o -user user2

>action -exec
>>ls

>>print

>which filename
>>-n<文件名长度>指定文件名長度，指定的長度必須大於或等於所有文件中最長的文件名。

>>-p<文件名長度>與-n参數相同，但此處的<文件名長度>包括了文件的路徑。

>>-w指定輸出欄位的寬度。

>>-V顯示版本訊息。

### 檔案內容查閱 ###
cat  從第一行顯示檔案內容、形成新檔案
>cat -n file1 > file2→把file1的檔案內容加上行號後輸入file2檔案

>>-n→由1開始對所有輸出的行數編號

>>→將多個文件覆蓋到目標文件中

>>→將多個文件追加到目標文件中

tac  從最後一行開始顯示
>tac -r -s 'x\|[^x]' test.log→一個接著一個字符的反轉一個文件

>>-r→將分隔符作為基礎正規表達是處理

>>-s→使用String作為分隔符代替默認的換行符

more 一頁一頁的顯示檔案內容
>more +20 testfile→從第20行開始顯示testfile的文檔內容

>>ENTER：向下n行(default為1行)

>>Ctrl+F/SPACE：向下滾動一屏

>>Ctrl+B：返回上一屏

less 與 more 類似，顯示檔案室允許用戶既可以向前又可以向後翻頁閱讀檔案

>ps -ef |less→ps查看進程信息並通過less分頁顯示	

>>j→下一行

>>k→上一行

>>G→移動到最後一行

>>g→移動到第一行

head/tail 只看頭/尾巴幾行
>head -n 20 state.txt | tail -10→顯示11~20行的內容
### 網路相關 ###
#### route ####
  
add ：新增一條路由規則
  
del：刪除一條路由規則
  
-net：目的地址是一個網路
  
-host：目的地址是一個主機
  
target：目的網路或主機
  
netmask：目的地址的網路掩碼
  
gw：路由資料包通過的閘道器
  
dev ：為路由指定的網路介面

#### ping ####
常用網路檢測工具，可籍由發送 ICMP ECHO REQUEST 封包，檢查自己與特定設備之間的阔路是否暢通，並同時測量網路連線的來回通訊延選時間 (round-trip delay time)

-n：参数指定封包数 EX: ping -n 10 blog.gtwang.org

-t：持續監看網路是否正常 EX: ping -t blog.gtwang.org

-4/-6: IPv4/ IPv6

-c:指定ping次数 EX: ping -c 4 blos. gtwang.org

-s:指定發送的数據字結數 EX： ping -s 1024 facebook.com

-i:指定收發資訊間隔時間 EX:ping -i 0.4 facebook.com

#### netstat ####
LISTEN ：偵聽來自遠方的TCP端口的連接請求

SVN-SENT ：再發送連接請求後等待匹配的連接請求（如果有大量這檬的狀態包，檢查是否中招了)

SYN-RECEIVED：再收到和發送一個連接請求後等待對方封連接請求的確認(如有大量此狀態估計被food攻聖了）

ESTABLISHED：代表一個打開的連接

FIN-WAIT-1：等待遠程TCP連接中斷請求，或先前的連接中断請求的確認

FIN-WAIT-2：從遠程TCP等待連接中斷請求

CLOSE-WAIT：等待從本地用戶發來的連接中断請求

CLOSTNG：等待遠程TCP對連接中斷的確認

LAST-ACK：等待原來的發向遠程TCP的連接中断請求的確認（不是什麼好東西，此項出現，檢查是否被攻擊）

TIME-WAIT ：等待足夠的時間以確保通程TCP接收到連接中斷請求的確認

CLOSED：沒有任何連接狀態

*查看端口是否被占用：netstat -a|grep 3306

*查看數據包統計信息：netstat -s

*查看路由信息：netstat -r


