访问器在用于manager类时就会出现一些逻辑上的问题.因为manager类的工资中应该包含基本的工资以及奖金,所以需要在manager类中修改对应的访问器来确保得到的工资是正确的工资.

这里首先需要为manager类添加一个属性的修改器


	public void setBonus(double bonus) {
		this.bonus = bonus;
	}
然后需要覆盖对应的超类中的方法


public double getSalary(){
	...
			
	}
manager类中的工资是基本工资加上奖金,因此只需要将奖金添加进去即可.

	public double getSalary(){
		double salary = super.getSalary();
		salary += bonus ;
		return salary;
			
	}
需要注意的是,虽然没有显示的定义salary属性以及对应的访问器,但是依旧可以使用它们,因为子类自动的继承了超类的这些属性和方法.

还有需要注意的是,因为在子类中也存在getSalary方法,当我们需要调用超类的访问器时,如果不使用super关键字指定调用父类的方法,那么子类会一直循环的调用自身的getSarary方法致使程序报错.
