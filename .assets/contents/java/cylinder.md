
---

- [Back to java](../java.md)
- [Back to main](../../../README.md)

---

Cylinder.java

```java
public class Cylinder {
    private int height;
	private int radius;

    public Cylinder(int height, int radius) {
		this.height = height;
		this.radius = radius;
	}

    public int getHeight() {
		return height;
	}

	public void setHeight(int height) {
		this.height = height;
	}

	public int getRadius() {
		return radius;
	}

	public void setRadius(int radius) {
		this.radius = radius;
	}

    public double getSurface() {
		return 2*(Math.pow(this.radius, 2)*Math.PI)+this.height*2*this.radius*Math.PI;
	}
	
	public double getVolume() {
		return Math.pow(this.radius, 2)*Math.PI*this.height;
	}
	
	public void terVolumeWritesOut() {
		System.out.println("The volume of the cylinder: " + getVolume());
	}
}
```

SolidCylinder.java

```java
public class SolidCylinder extends Cylinder {
    
    private double density;

	public SolidCylinder(int height, int radius, double density) {
		super(height, radius);
		this.density = density;
	}

	public double getDensity() {
		return density;
	}

	public void setDensity(double density) {
		this.density = density;
	}

    public double getMass() {
		return this.density*this.getVolume();
	}

    public void volumeWriteOut() {
		System.out.println("The volume of the solid cylinder: " + this.getVolume());
	}
}
```

Tube.java

```java
public class Tube extends SolidCylinder {

	private int innerRadius;

	public Tube(int height, int radius, double density, int innerRadius) {
		super(height, radius, density);
		this.innerRadius = innerRadius;
	}

	public int getInnerRadius() {
		return innerRadius;
	}

	public void setInnerRadius(int innerRadius) {
		this.innerRadius = innerRadius;
	}

	public double getVolume() {
		return new Cylinder(this.getHeight(), this.getRadius()).getVolume() - new Cylinder(this.getHeight(), this.getInnerRadius()).getVolume();
	}

	public double getSurface() {
		return super.getSurface()+(new Cylinder(this.getHeight(), this.innerRadius)).getSurface() - 4*Math.pow(this.innerRadius, 2)*Math.PI;
	}
}
```

Main.java

```java
public class Main {

    public static void main(String[] args) {

        Cylinder cylinderObj = new Cylinder(10, 1);
		//cylinderObj.setHeight(20);
		cylinderObj.volumeWriteOut();

		System.out.println("Cylinder surface: " + cylinderObj.getSurface());
		System.out.println("Cylinder volume: " + cylinderObj.getVolume());
		System.out.println("Cylinder height: " + cylinderObj.getHeight());


		SolidCylinder solidCylinderObj = new SolidCylinder(10, 2, 0.5);

		System.out.println("Solid cylinder surface: " + solidCylinderObj.getFelszin());
		System.out.println("Solid cylinder volume: " + solidCylinderObj.getTerfogat());
		System.out.println("Solid cylinder mass: " + solidCylinderObj.getTomeg());

		solidCylinderObj.volumeWriteOut();


		Tube tubeObj = new Tube(10, 2, 0.5, 1);

		System.out.println("Tube volume: " + tubeObj.getVolume());
		System.out.println("Tube surface: " + tubeObj.getSurface());
    }
}
```

---

- [Back to java](../java.md)
- [Back to main](../../../README.md)

---