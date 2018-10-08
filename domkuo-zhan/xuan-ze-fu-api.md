根据CSS选择符选择与某个模式匹配的DOM元素。



# querySelector\(\)

接受一个CSS选择符，返回与该模式匹配的第一个元素，如果没有找到则返回null

# querySeletorAll\(\)

参数也是CSS选择符，只不过会返回一个NodeList实例，包含的是全部匹配的元素。document调用表示从文档内全部元素中寻找，如果Element类型元素调用，则只会在其后代中查找。



# matchesSelector\(\)

接受一个CSS选择符，如果调用元素与CSS选择符匹配，则返回true，否则返回false。



