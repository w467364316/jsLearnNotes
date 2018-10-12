## 键盘事件

* keydown
  * 当用户按下键盘上的任意键时触发，如果按住不放，会重复触发
* keyup
  * 当用户释放键盘上的键是触发，如果按住不放，会重复触发
* keypress

## 1 键码

event对象的keyCode属性

## 2 字符编码

event对象的charCode属性，只有在发生keypress事件时才会包含值。

## 3 DOM3级变化

DOM3级变化不在包含charCode属性，增加了key和char属性。

key: 在按下字符按键时，key的值为相应的文本字符。非字符按键时，key的值是相应键的名。

char: 再按下字符按键时，和key的值一样，非字符键值为null

## 4 textInput事件

当用户在可编辑区域中输入字符时，就会触发这个事件。只有在编辑区域才能触发textInput事件。

对应的event事件中有的属性

* data属性，为用户输入的字符（不是字符编码）
* inputMethod属性，表示把文本输入到文本框中的方式。



