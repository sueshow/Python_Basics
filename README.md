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
