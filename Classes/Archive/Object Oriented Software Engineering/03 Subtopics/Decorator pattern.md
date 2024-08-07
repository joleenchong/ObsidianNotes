![[Pasted image 20240324131733.png]]
Creates a linked list of objects to provide more functionality -> avoids huge amt of subclasses. Wrapper / decorator classes decorate objects with more function. 

Example:
```java
//Main interface
public interface GameCharacter
{
	int attack();
	void defend(int damage);
	void setHealth(int health);
	int getHealth();
}

//base implementation
public class ElfCharacter implements GameCharacter
{
	private int health = 100;

	@Override
	public int attack() { return 10; }

	@Override
	public void defend(int damage)
	{
		health -= damage;
		if (health == 0) {...}
	}
	...
}
```