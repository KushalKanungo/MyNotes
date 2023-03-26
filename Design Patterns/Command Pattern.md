> **Command** is a behavioral design pattern that turns a request into a stand-alone object that contains all information about the request. This transformation lets you pass requests as a method arguments, delay or queue a request’s execution, and support undoable operations.

- We cannot hardcode the code in the _Invoker Class_ (For eg. **Button**)
- Because we want to do different thing through the _Invoker Object_
- So where should we keep the code ?
- It is very similar to [[Strategy Design Pattern]]

IMP: IN JS we have functions which are _first class citizen_ which we can pass around like commands but to achieve this type of functionality we use **Command Pattern**.

DESIGN 
![[Command Pattern Diagram]]

```java
interface ICommand(){
	void execute();
	void unExecute();
}
```

```java
class LightOnCommand implements ICommand{
	public Command(Receiver Light){
		this.light = Light
	}

	public void execute(){
		this.light.on()
	}
}
```

```java
class Invoker{
	ICommand on;
	ICommand off;
	ICommand up;
	ICommand down;

	public Invoker(ICommand onCommand, ICommand offCommand, ...){
		this.on = onCommand;
		this.off = offCommand;
		this.up = upCommand;
		this.down = downCommand;
	}
}

Invoker remote =  new Invoker(new LightOnCommand)

```