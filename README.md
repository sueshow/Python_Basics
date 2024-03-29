# Basics

## 物件導向
* 特性：繼承意指當一個物件被賦予其屬性後，其值不可延續，且必須尊崇 class 所給的屬性；封裝則是把方法鎖在 class 裡無法被更改。
  * _(只有一個底線)：變數名稱不重要，之後用不到，通常在不得已的時候使用
  * _命名：具有私有性(private)，隱藏此物件，不輕易被使用
  * __命名：具有唯一性，無法被修改，在 class 中有作用，前面有雙底線就會被改名
  * 命名_：避免與 Python 的 built-in keywords (如：from等) 或 built-in functions (如：list等) 使用過相同的變數名
  * __命名__：這是留給Python builtin 的 methods 或是 variables，稱為 dunder methods
* 變數的命名
  * 規則
    * 名稱只能由大小寫字母、數字、下底線、中文來命名變數
    * 第一個字母不能是數字，必須是大小寫字母、下底線、中文
    * 有分大小寫，不同大小寫字母視為不同的變數
    * 名稱不能與Python內建的保留字相同
    * 建議以英文為變數名稱比較好，可以減少未知的錯誤
  * 保留字
    <table border="1" width="12%">
      <tr>
        <th width="2%"> 	</a>
        <th width="2%">  </a>
        <th width="2%">  </a>
        <th width="2%"> 	</a>
        <th width="2%">  </a>
        <th width="2%">  </a>
      </tr>
      <tr>
        <td> acos </td>
        <td> and </td>
        <td> array </td>
        <td> asin </td>
        <td> assert </td>
        <td> atan </td>
      </tr>  
      <tr>
        <td> break </td>
        <td> class </td>
        <td> close </td>
        <td> continue </td>
        <td> cos </td>
        <td> Data </td>
      </tr>  
      <tr>
        <td> def </td>
        <td> del </td>
        <td> e </td>
        <td> elif </td>
        <td> else </td>
        <td> except </td>
      </tr> 
      <tr>
        <td> exec </td>
        <td> exp </td>
        <td> fabs </td>
        <td> flost </td>
        <td> finally </td>
        <td> floor </td>
      </tr>
      <tr>
        <td> for </td>
        <td> from </td>
        <td> global </td>
        <td> if </td>
        <td> import </td>
        <td> in </td>
      </tr> 
      <tr>
        <td> input </td>
        <td> int </td>
        <td> is </td>
        <td> lambda </td>
        <td> log </td>
        <td> log10 </td>
      </tr> 
      <tr>
        <td> not </td>
        <td> open </td>
        <td> or </td>
        <td> pass </td>
        <td> pi </td>
        <td> print </td>
      </tr>
      <tr>
        <td> raise </td>
        <td> range </td>
        <td> return </td>
        <td> sin </td>
        <td> sqrt </td>
        <td> tan </td>
      </tr>
      <tr>
        <td> try </td>
        <td> type </td>
        <td> while </td>
        <td> write </td>
        <td> zeros </td>
        <td>  </td>
      </tr>
    </table>
<br>


## 文字檔案的讀取和儲存
* 開啟檔案：`檔案物件=open(檔案路徑, mode=開啟模式)`
  * 開啟模式：r(讀取模式)、w(寫入模式)、r+(讀寫模式)
* 讀取檔案：
  * 讀取全部文字：`檔案物件.read()`
  * 一次讀取一行：`for 變數 in 檔案物件:`，意旨從檔案依序讀取美行文字到變數中
  * 讀取 JSON 格式：
    ```
    import json 
    讀取到的資料 = json.load(檔案物件)
    ```
* 寫入檔案：
  * 寫入文字：`檔案物件.write(字串)`
  * 寫入換行符號：`檔案物件.write('這是範例文字\n')`
  * 寫入 JSON 格式：
    ```
    import json
    json.dump(要寫入的資料, 檔案物件)
    ```
* 關閉檔案：`檔案物件.close()`
* 最佳實務
  ```
  with open(檔案路徑, mode=開啟模式) as 檔案物件:
      讀取或寫入檔案的程式
  # 以上區塊會自動、安全的關閉檔案
  ```
* 範例
  * 儲存檔案
    ```
    ## 方法一
    file = open('data.txt', mode='w', encoding='utf-8')   # 開啟
    file.write('測試中文\n好棒棒')                         # 操作
    file.close()                                          # 關閉
    ## 方法二
    with open('data.txt', mode='w', encoding='utf-8') as file:
        file.write('測試中文\n好棒棒')
    ```
  * 讀取檔案(已存在的檔案)
    ```
    with open('data.txt', mode='w', encoding='utf-8') as file:
        file.write('5\n3')
  
   
    ## 讀取全部文字
    with open('data.txt', mode='r', encoding='utf-8') as file:
        data = file.resd()
    print(data)
    ## 一次讀取一行：把檔案中的數字資料，一行一行讀取出來，並計算總合
    sum = 0
    with open('data.txt', mode='r', encoding='utf-8') as file:  
        for line in file:   # 一行一行的讀取
            sum += int(line)
    print(sum)
    ```
  * 使用 JSON 格式讀取、複寫檔案
    * JSON 格式
      ```
      {
          "name":"My Name",
          "version":"1.2.5"
      }
      ```
    * 讀取資料：從檔案中讀取 JSON 資料，放入變數 data 裡面
      ```
      import json
      with open('config.json', mode='r') as file:
          data = json.load(file)   # data是字典資料
      print('name: ', data['name'])
      print('version: ', data['version'])
      ```
    * 修改資料
      ```
      data['name'] = 'New Name'  # 修改變數中的資料
      # 把最新的資料複寫回檔案中
      with open('config.json', mode='w') as file:
          json.dump(data, file)  
      ```
<br>


## 運算子(Operator)
* 基本運算：`+`、`-`、`*`
* 常見的運算： `/` 為直接相除、 `//` 為取商、 `%` 為取餘數
* 邏輯運算：`==`、`>=`、`<=`、`!=`   
<br>


## 可變(mutable)與不可變(immutable)
* 不可變：int(整數)、float、bool、numbers、string(字串)、tuple(元組)、unicode
  * 變量 `a=5` 後，再給定 `a=10`，這裏實際上是新生成一個 int 值對象 10，再讓 a 指向它，而 5 被丟棄，而不是改變 a 的值，相當於新生成 a
  * 類似 c++ 的值傳遞
* 可變：list、set、dict
  * 變量 `la=[1,2,3,4]` 後，再給定 `la[2]=5` ，是將 list la 的第三個元素值更改，本身 la 沒有動，只是其內部的一部分值被修改
  * 類似 c++ 的引用傳遞
* 語法
  * `id()`：一個變數的地址
  * `type()`：每個變數的型別，不同的型別存放的資料也不同，如：int存放整數、float存放浮點數、list存放陣列等等...
  * `pop()`：把陣列的最後一個物件丟掉 
<br>


## 字串(String)
* 單字串在 Python 作爲一個字串使用
* 訪問子字串，可使用方括號來截取字串
* `+` 用於組合，`*` 用於重複
  ```
  var01 = 'Hello World!'
  var02 = 'Python Basic'
 
  print('var01[0]: ', var01[0])
  print('var02[1:5]: ', var02[1:5])
  print('更新字串: ', var01[:6]+'Basic!')
  print('L' in var01)
  print('l' in var01)
  print(var01[::-1])
  ```
  > var01[0]: H <br>
  > var02[1:5]: ytho <br>
  > 更新字串: Hello Basic! <br>
  > False <br>
  > True <br>
  > !dlroW olleH <br>
<br>

* 常用：
  1. 字符串對象的 `rjust()` 可將字符串靠右，並在左邊填充空格，類似的方法如 `ljust()`、`center()`、`zfill()`：在數字的左邊填充 0
     ```
     for x in range(1, 11):
        print(repr(x).rjust(2), repr(x*x).rjust(3), end=' ')
         # 注意前一行 'end' 的使用
        print(repr(x*x*x).rjust(4)) 
     ``` 
     > 1   1    1 <br>
     > 2   4    8 <br>
     > 3   9   27 <br>
     > 4  16   64 <br>
     > 5  25  125 <br>
     > 6  36  216 <br>
     > 7  49  343 <br>
     > 8  64  512 <br>
     > 9  81  729 <br>
     >10 100 1000 <br>
  2. 括號及其裏面的字串將會被 `format()` 中的參數替換
     ```
     print('{0} 和 {1}'.format('Google', 'Intel'))
     print('{1} 和 {0}'.format('Google', 'Intel'))

     print('{name}位置： {address}'.format(name='Jamie', address='Taiwan/Taipei'))
     ```
     > Google 和 Intel <br> 
     > Intel 和 Google <br>
     > Jamie位置： Taiwan/Taipei <br>
  3. !a (使用 `ascii()`), !s (使用 `str()`) 和 !r (使用 `repr()`) 可以用於在格式化某個值之前對其進行轉化
  4. {0:.3f}：小數點後三位
  5. 使用方括號 [] 來訪問鍵值
     ```
     import math
     print('數學pi的值近似爲： {!r}。'.format(math.pi))
     print('pi近似值爲 {0:.3f}。'.format(math.pi))
     ```
     > 數學pi的值近似爲： 3.141592653589793 <br>
     > pi近似值爲 3.142 <br>
     ```
     table = {'August': 8, 'March': 3, 'July': 7}
     print('March: {0[March]:d}; August: {0[August]:d}; July: {0[July]:d}'.format(table))
     print('March: {March:d}; August: {August:d}; July: {July:d}'.format(**table))
     ```
     > March: 3; August: 8; July: 7 <br>
     > March: 3; August: 8; July: 7 <br>
  6. 輸入 
     ```
     str1 = input("請輸入：");
     print ("你輸入的內容是: ", str1)
     ```
  7. 重要
     * 在 Python 中，字串格式化使用與 C 中 sprintf 函數一樣的語法
       * %c：格式化字串及其 ASCII 碼
       * %s：格式化字串
       * %d：格式化整數
       * %u：格式化無符號整型
       * %o：格式化無符號八進位數
       * %x：格式化無符號十六進位數
       * %X：格式化無符號十六進位數(大寫)
       * %f：格式化浮點數，可指定小數點後的位數
       * %e：用科學計數法格式化浮點數
       * %E：同 %e，科學計數法格式化浮點數
       * %g：%f 和 %e 的簡寫
       * %G：%F 和 %E 的簡寫
       * %p：用十六進位數格式化變量的地址
         ```
         print('My name is %s and weight is %d kg!' % ('Zara', 21)) 
         ```
         > My name is Zara and weight is 21 kg! <br>
         ```
         import string
         string.ascii_lowercase
         string.ascii_uppercase
         ```
         > 'abcdefghijklmnopqrstuvwxyz' <br>
         > 'ABCDEFGHIJKLMNOPQRSTUVWXYZ' <br>
<br>


## 列表(List)
* `append()`：新增 list 元素
* `del()` or `remove()` or `pop()`=`list[:-1]`：刪除 list 元素
* `+`：用於組合，`*`：用於重複
* `reverse()` or `reversed()`：反序
* `index()`
* `insert()`：Add an element at the specified index (position) of a list 
  ```
  test=[]                 ## 空列表
  test.append('1991')     ## 使用 append() 新增元素
  test.append('Python')
  print(test)

  del(test[0])
  print(test)
  ```
  > ['1991', 'Python'] <br>
  > ['Python'] <br>

* Convert list to string
  ```
  list_ = ['A','B','C']
  string = '/'.join( list_ )
  string

  list_ = [1,2,3,4,5,6,7,8,9]
  str2 = ''.join( str(i) for i in list_ if i%2==0 ) 
  str2
  ```
  > 'A/B/C'  <br>
  > '2468'   <br>

* Pick up elements in a list
  ```
  list_ = [1,2,3,4,5,6,7,8,9]
  print(list_[:3])  # or list_[:3:]
  print(list_[:-3])
  print(list_[::3])
  print(list_[::-3])
  print(list_[3::-1])
  print(list_[:3:-1])
  #list_[::-1]  # or list( reversed(list_) ) 
  ```
  > [1, 2, 3]             <br>
  > [1, 2, 3, 4, 5, 6]    <br>
  > [1, 4, 7]             <br> 
  > [9, 6, 3]             <br>
  > [4, 3, 2, 1]          <br> 
  > [9, 8, 7, 6, 5]       <br>
<br>


## 元組(Tuple)
* tuple 的元素值不可以修改、刪除
* 結構簡單，資料型態的大小比 list 小
  ```
  test = ()               ## 空元組

  listA = list(range(1000))
  tupleA = tuple(range(1000))

  print ('list 資料大小：', listA.__sizeof__())
  print ('tuple 資料大小：', tupleA.__sizeof__())
  ```
  > list 資料大小： 9088 <br>
  > tuple 資料大小： 8024 <br>
<br>


## 範圍(Range)：
* Range 內的元素是不可變的，且可使用索引，通常用於迴圈(Loop)
* 語法：range(start, stop, step)
  * start：計數從 start 為起點。如果沒有數字就是從 0 開始
  * stop：計數到 stop 為終點，但不包括 stop 的數字。
  * step：移動步長，沒有數字就視為 1
    ```
    r = range(0,10,2)
    print(r)
    print(list(r))
    print(r.index(2))
    print(r[:3])
    print(r[-1])

    state = ['New Jersey', 'Nevada', 'Montana']
    range(len(state))
    ```
    > range(0, 10, 2) <br>
    > [0, 2, 4, 6, 8] <br>
    > 1 <br>
    > range(0, 6, 2) <br>
    > 8 <br>
    > range(0, 3) <br>
<br>


## 集合(Set)：
* 運算
  * 判斷資料是否存在：使用 in 和 not in 運算符號
  * 交集、聯集：使用 & 和 | 運算符號
  * 差集、反交集：使用 - 和 ^ 運算符號 
  * 字串拆解為集合：set(字串)
    ```
    x = set('runoob')
    y = set('google')
    print(x & y)  # 交集
    print(x | y)  # 並集
    print(x - y)  # 差集
    ```
    > {'o'} <br>
    > {'r', 'l', 'e', 'n', 'b', 'o', 'g', 'u'} <br>
    > {'r', 'u', 'n', 'b'} <br>
* 集合運算
  ```
  s1 = {3,4,5}
  print(10 not in s1)
    
  s2 = {4,5,6,7}
  s3 = s1 & s2      # 交集：取兩個集合中、相同的資料
  s3 = s1 | s2      # 聯集：取兩個集合中的所有資料，但不重複取
  s3 = s1 - s2      # 差集：從s1中減去和s2重疊的部分
  s3 = s1 ^ s2      # 反交集：取兩個集合中，不重疊的部分
  ```
<br>


## 字典(Dictionary)：
* 基本觀念：字典的每個鍵值 key、value 對用冒號 `:` 分割，每個鍵值對之間用逗號 `,` 分割，整個字典包括在括號 `{}` 中，如 dict1 = {key1:value1, key2:value2}
* 語法：`字典[Key] = Value`
* 能刪單一的元素，也能清空字典
* key 
  * 唯一的：不允許同一個 key 出現兩次。如果同一個 key 給兩次 value，後一個 value 會被記住
  * 不可變，型態可為字串、數字、元組
* value 
  * 不需唯一
  * 型態可取任何數值類型
    ```
    keys = [1,2,3]
    values = ['A','B','C']
    dict_ = dict( zip(keys,values) )
    dict_
    dict_ = { k:v for k, v in zip(keys,values) }
    dict_
    ```
    > {1: 'A', 2: 'B', 3: 'C'}  <br>

    ```
    dict = {"Name": "Soren", "Age": 1000, "Class": "apple"}
 
    print('dict['Name']:', dict['Name'])
    print('dict['Age']:', dict['Age'])

    del dict['Name']  
    print(dict)

    dict.clear() 
    print(dict) 
    ```
    > dict["Name"]: Soren <br>
    > dict["Age"]: 1000 <br>
    > {'Age': 1000, 'Class': 'apple'} <br>
    > {} <br>
* 運算
  * 判斷資料是否存在：使用 in 和 not in 運算符號
  * 刪除鍵值對：使用 del 運算關鍵字
  * 以列表的資料為基礎來建立字典
  * Add an item into the 1st location in a dictionary
    ```
    dict_ = {1:'A',2:'B',3:'C'}
    dict_ = {4:'D', **dict_}
    dict_
    ```
    > {4: 'D', 1: 'A', 2: 'B', 3: 'C'}  
* 字典運算：key-value 配對
  ```
  dic = {"apple":"蘋果", "bug":"蟲蟲"}
  print(dic['apple'])
  dic['apple'] = '小蘋果'
  print(dic['apple'])
  
  # 判斷 key 是否存在
  print('apple' in dic)
  print('test' in dic)
  
  # 刪除字典中的鍵值對
  print(dic)
  del dic['apple']
  print(dic)
  
  # 以列表的資料為基礎來建立字典
  dic = {x:x*2 for x in [3,4,5]}
  print(dic)
  ```
<br>


## 條件語法(If-else)
* 任何非 0 和非空 (null) 值爲true，0 或者 null爲false
* 形式爲：
  ```
  if 判斷條件1:
      執行語句1……
  elif 判斷條件2:
      執行語句2……
  elif 判斷條件3:
      執行語句3……
  else:
      執行語句4……
  ``` 
<br>


## 迴圈(While)
* 用於循環執行程序，即在某條件下，循環執行某段程序，以處理需要重複處理的相同任務
* 重要的命令：`continue`用於跳過該次循環，`break`則是用於退出循環
* "判斷條件"可以是常值，表示循環必定成立
* 形式：
  ```
  while(繼續條件):
     當條件成立時，會執行的程式
  ```
  ```
  i = 1
  while i < 10:   
      i += 1
      if(i%2)> 0:     # 非雙數時跳過輸出
          continue
      print('pass!!')
      print(i)         # 輸出雙數2、4、6、8、10
 
  j = 1
  while 1:            # 循環條件爲1必定成立
      print(j)         # 輸出1~10
      j += 1
      if j > 5:     # 當i大於10時跳出循環
          break
  print('end')
  ```
  > pass!! <br>
  > 2 <br>
  > pass!! <br>
  > 4 <br>
  > pass!! <br>
  > 6 <br>
  > pass!! <br>
  > 8 <br>
  > pass!! <br>
  > 10 <br>
  > 1 <br>
  > 2 <br>
  > 3 <br>
  > 4 <br>
  > 5 <br>
  > end 
<br>


## 迴圈(for)
* 形式：
  ```
  for iterating_var in sequence:
     statements(s)
  ```
  ```
  for num in range(0,20):   # 疊代 0 到 20 之間的數字
     for i in range(2,num): # 根據因子疊代
        if num%i == 0:      # 確定第一個因子  
           j=num/i          # 計算第二個因子
           print('%d 等於 %d * %d' % (num,i,j))
           break            # 跳出當前循環
        else:                  # 循環的 else 部分
           print(num, '是一個質數')
  ```
  > 0 是一個質數 <br>
  > 1 是一個質數 <br>
  > 2 是一個質數 <br>
  > 3 是一個質數 <br>
  > 4 等於 2 * 2 <br>
  > 5 是一個質數 <br>
  > 6 等於 2 * 3 <br>
  > 7 是一個質數 <br>
  > 8 等於 2 * 4 <br>
  > 9 等於 3 * 3 <br>
  > 10 等於 2 * 5 <br> 
  > 11 是一個質數 <br>
  > 12 等於 2 * 6 <br>
  > 13 是一個質數 <br>
  > 14 等於 2 * 7 <br>
  > 15 等於 3 * 5 <br>
  > 16 等於 2 * 8 <br>
  > 17 是一個質數 <br>
  > 18 等於 2 * 9 <br>
  > 19 是一個質數 
<br>


## 函式(function)
* 提高應用的模塊性
* 代碼的重複利用率
* 形式：
  ```
  def functionname( parameters ):
     function_suite
     return [expression]
  ```
* 參數類型：
  * 必備參數：以正確的順序傳入函數
  * 關鍵字參數：使用關鍵字參數允許函數時，參數的順序與聲明時不一致
  * 默認參數：默認參數的值如果沒有傳入，則被認爲是默認值
  * 不定長參數：形式如下
    ```
    def functionname([formal_args,] *var_args_tuple ):
       function_suite
       return [expression]
    ```
    ```
    def printinfo( prm1, *vartuple ):
       print(prm1)
       for var in vartuple:
          print(var)
       return
 
    printinfo(10)
    printinfo(70,60,50)
    ```
    > 10 <br>
    > 70 <br>
    > 60 <br>
    > 50 <br>
* 匿名函數
  * 使用 lambda 來創建匿名函數
  * 形式：
    ```
    lambda [arg1 [,arg2,.....argn]]:expression
    ```
    ```
    sum = lambda arg1, arg2: arg1 + arg2;

    print('相加後的值爲 : ', sum( 10, 20 ))
    print('相加後的值爲 : ', sum( 20, 20 ))
    ```
    > 相加後的值爲 :  30 <br>
    > 相加後的值爲 :  40 <br>
* 全域變數和區域變數
  * 定義在函數內部的變量擁有一個區域作用域，定義在函數外的擁有全域作用域
    ```
    total = 0                                 # 這是一個全域變數

    def sum( prm1, prm2 ):
       total = prm1 + prm2                    # total在這裏是區域變數.
       print('函數內是區域變數: ',total)
       return total
 
    sum(10,20);
    print('函數外是全域變數 : ',total)
    ```
    > 函數內是區域變數 :  30 <br>
    > 函數外是全域變數 :  0 
<br>


## 類別(class)
* Python 是物件導向的程式語言 (Object-oriented programming)
* 具有屬性與方法
  1. 基本屬性
     ```
     # 建構一個 family 類別
     class family():
       # 函式 __init__ 會自動執行
       def __init__(self,name,age):
       # self是class本身,所以第一個不用更動,而這邊新增兩個屬性,一個是名字,另一個是年齡
         self.name = name
         self.age = age
     
       Amy = family('Amy',17)
       print(Amy.name)
       print(Amy.age) 

       # 可以透過這樣修改實體的屬性
       Amy.age = 18
       print(Amy.age)
     ```
     > Amy <br>
     > 17 <br>
     > 18 <br>
  2. 取用自己的方法
     ```
     class Human:
       def __init__(self,h=0,w=0):
         # 可在參數後面帶值
         self.height=h
         self.weight=w
       def BMI(self):
         return self.weight / ((self.height/100)**2)

       steve = Human() 
       # 這樣即使在宣告的時候沒有帶參數也可以建立一個實體 
       print(steve.height)
       print(steve.height)
      
     luffy = Human(180,80)
     print(luffy.BMI())
     ```
     > 0 <br>
     > 0 <br>
     > 24.691358024691358 <br>
  3. 繼承：建構類別的時候透過 super().__ init__() 帶入父類別
     ```
     class Woman(Human):
       def __init__(self,h,w,bust=0,waist=0,hip=0):
         super().__init__(h,w)
     ```
     ```
     # 'Human' 有的屬性及方法會被 'Woman' 繼承
     class Woman(Human):
         def __init__(self,h,w,bust=0,waist=0,hip=0):
             super().__init__(h,w)
             self.bust=bust
             self.waist=waist
             self.hip=hip
         def printBWH(self):
             print('bust= {},waist= {},hip= {}'.format(self.bust,self.waist,self.hip))
         
     nana = Woman(165,54,83,64,84) 
     # 父類別 的方法 BMI()
     print(nana.BMI())
     # 子類別 的方法 printBWH()
     nana.printBWH()
     ```
     > 19.834710743801654 <br>
     > bust= 83,waist= 64,hip= 84 <br>
<br>


## 其他(others)
* `zip()` method takes iterables (can be zero or more), aggregates them in a tuple, and return it
  ```
  A_list = ['A1','A2','A3','A4']
  B_list = ['B1','B2']
  for a, b in zip( A_list, B_list ):
      print( a, b )
  ```
  > A1 B1               <br>
  > A2 B2               <br>

* `Enumerate()` method adds a counter to an iterable and returns it in a form of enumerate object
  ```
  list_ = ['A','B','C']
  for i, a in enumerate( list_ ):
      print( i, a )
  ```
  > 0 A                 <br>
  > 1 B                 <br>
  > 2 C                 <br>
<br>


## 程式錯誤
* 類型
  * 語法錯誤：Syntax Error
  * 型態錯誤：ValueError
  * 陣列(List)長度錯誤：IndexError
  * 任何意外錯誤：Exception
* 例外 Exception：在某些狀況下會出現錯誤
  * 事先預想、處理可能發生的例外
    ```
    try:
       可能會發生例外的程式區塊
    except Exception:
       若上述 try 區塊的程式發生例外
       跳進此區塊中的程式，繼續執行
    ```
  * 使用者如果輸入的資料格式不能轉換成數字，請他重新輸入，直到輸入成功為止
    ```
    while True:
        data = input('請輸入一個數字:')
        try:
            number = int(data)
            break
        except Exception:
            print('輸入格式錯誤，請重新再輸入')
    number = number*2
    print(number)
    ```
<br>


## 備註
* \(在行尾時)：續行符
* \\：反斜槓符號
* \'：單引號
* \"：雙引號
* \a：響鈴
* \b：退格(Backspace)
* \e：轉義
* \000：空
* \n：換行
* \v：縱向製表符
* \t：橫向製表符
* \r：回車
* \f：換頁
* \oyy：八進制數，yy代表的字符，例如：\o12代表換行
* \xyy：十六進制數，yy代表的字符，例如：\x0a代表換行
* \other：其它的字符以普通格式輸出
<br>


## 參考資料：
* [python-__底線__-的意義](https://note.artchiu.org/2019/02/22/python-__%E5%BA%95%E7%B7%9A__-%E7%9A%84%E6%84%8F%E7%BE%A9/)
* [AI-FREE-Team / Python-Basics](https://github.com/AI-FREE-Team/Python-Basics)
* [YenLinWu / Coding_Notes](https://github.com/YenLinWu/Coding_Notes/tree/main/Python%20Syntax)
* [Python 文字檔案的讀取和儲存 By 彭彭](https://www.youtube.com/watch?v=C4OkV6DrVRs)
* [Python 集合、字典的基本運算 - Set、Dictionary By 彭彭](https://www.youtube.com/watch?v=L3-KuGYhw78&list=PL-g0fdC5RMboYEyt6QS2iLb_1m7QcgfHk&index=5)
