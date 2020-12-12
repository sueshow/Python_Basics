# Python_Basics

## 運算子(Operator)
* 基本運算：`+`、`-`、`*`
* 常見的運算： `/` 為直接相除、 `//` 為取商、 `%` 為取餘數
* 邏輯運算：`==`、`>=`、`<=`、`!=`
<br>

## 可變與不可變物件
* 不可變：int、float、bool、string、tuple、unicode
* 可變：list、set、dict
* 語法
  * `id()`：一個變數的地址
  * `type()`：每個變數的型別，不同的型別存放的資料也不同，如：int存放整數、float存放浮點數、list存放陣列等等...
  * `pop()`：把陣列的最後一個物件丟掉
<br>

## 字串(String)
* 單字符在 Python 作爲一個字符串使用
* 訪問子字符串，可使用方括號來截取字符串
```
var01 = 'Hello World!'
var02 = 'Python Basic'
 
print('var01[0]: ', var01[0])
print('var02[1:5]: ', var02[1:5])
print('更新字符串: ', var1[:6]+'Basic!')
print('L' in var01)
print('l' in var01)
```
<br>

* 在 Python 中，字符串格式化使用與 C 中 sprintf 函數一樣的語法
  * %c：格式化字符及其 ASCII 碼
  * %s：格式化字符串
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
<br>

## 列表(List)
* \(在行尾時)	續行符
* \\	反斜槓符號
* \'	單引號
* \"	雙引號
* \a	響鈴
* \b	退格(Backspace)
* \e	轉義
* \000	空
* \n	換行
* \v	縱向製表符
* \t	橫向製表符
* \r	回車
* \f	換頁
* \oyy	八進制數，yy代表的字符，例如：\o12代表換行
* \xyy	十六進制數，yy代表的字符，例如：\x0a代表換行
* \other	其它的字符以普通格式輸出
<br>

## 參考資料：
* https://github.com/AI-FREE-Team/Python-Basics
