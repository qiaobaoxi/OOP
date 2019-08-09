# OOP
    类与实例：怎么生成一个类，类的声明，
    怎么生成一个实例类于继承：如何实现继承，
    继承的几种方式类的声明：function Animal () {this.name = ‘name'}
                      ES6中的class声明：class Animal2{constructor(){this.name = ’name'}}
                      实例化类的对象：new Animal(new Animal2()实现继承的基本原理就是原型链。
    Js的继承有几种方式：要逐步写。
    第1种，借助构造函数实现继承：
      function Parent1(){this.name = ‘parent1’;}function child1(){Parent1.call(this); //这句话是执行父级的构造函数，也可以用apply，改变函数运行的上下文this.type = ‘child1’;}new Child1()
      缺点（问题）：Parent1的prototype上面的属性或者方法是不能被Chlid1继承的，只实现了部分继承。
    第2种，借助原型链实现继承：
      function Parent2() {this.name = ‘parent2’;}function Child2() {this.type = ‘child2’;}Child2.prototype = new Parent2();new Chlid2()
      缺点（问题）：父类中增加新的属性，那么所有的实例都会同时改变。如果某个实例的属性值（来自父类的）发生了变化，那么其他实例也都跟着发生了变化。因为所有实例的__proto__是同一个，所以相互之间会有影响。
    第3种，组合方式：
      function Parent3() {this.name = ‘parent3’;This.play = [1,2,3,4];}function Child3(){Parent3.call(this);this.type = ‘child3’;}Child3.prototype = new Parent3();var s3 = new Child3();var s4 = new Child3();
      缺点（问题）：父级的构造函数执行了两次，而并没有必要
    第4中，组合继承的优化方式
      1：function Parent4() {this.name = ‘parent4’;This.play = [1,2,3,4];}function Child4(){Parent4.call(this);this.type = ‘child4’;}Child4.prototype = Parent4.prototype;var s5 = new Child4();var s6 = new Child4();s5 instanceof Child4 ======>>>trues5 instanceof Parent4 ======>>>true
      问题：怎么区分一个对象是由子类实例化的，还是父类实例化的（直接实例化）constructor方法在这里会出问题，因为s5.constructor 指向的是 Parent4。（其实前面的方法也有这个问题）
    第5中，组合继承的优化方式
      2：function Parent5() {this.name = ‘parent5’;This.play = [1,2,3,4];}function Child5(){Parent5.call(this);this.type = ‘child5’;}Child5.prototype = Object.create(Parent5.prototype);Child5.prototype.constructor = Child5;var s7 = new Child5();var s8 = new Child5();
      面试的时候不建议直接写出最后一种，时间长点儿，就能少问几道，在会的地方多展示一点儿，能提升面试印
