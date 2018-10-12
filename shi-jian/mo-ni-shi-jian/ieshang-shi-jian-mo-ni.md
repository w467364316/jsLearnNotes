调用document.createEventObject\(\)方法创建一个event对象，然后手工为对象添加所有必要的信息（挨个属性的添加），最后一步是在目标元素上调用fireEvent\(\)方法时传入两个参数，=事件处理程序名称和event对象

