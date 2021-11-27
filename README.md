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
