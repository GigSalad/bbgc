## Coding Class!

If you haven't completed the Objects tutorial on processing.org start there. [Objects tutorial](https://processing.org/tutorials/objects/)

If you have completed that tutorial use the code below to help you teach your cars how to drive on a two lane road.

### Two Lane Road

```
Car myCar1;
Car myCar2; // Two objects!

void setup() {
  size(400,200);
  // Parameters go inside the parentheses when the object is constructed.
  myCar1 = new Car(color(255,0,0),0,110,2); 
  myCar2 = new Car(color(0,0,255),0,10,1);
}

void draw() {
  background(255);
  
  // creates two yellow center lines for your highway 
  stroke(255, 200, 0);
  line(0, height/2 + 2, width, height/2 + 2);
  line(0, height/2 - 2, width, height/2 - 2);
  
  // add two cars to the road
  myCar1.drive();
  myCar1.display();
  myCar2.drive();
  myCar2.display();
}

// Even though there are multiple objects, we still only need one class. 
// No matter how many cookies we make, only one cookie cutter is needed.
class Car { 
  color c;
  float xpos;
  float ypos;
  float xspeed;

  // The Constructor is defined with arguments.
  Car(color tempC, float tempXpos, float tempYpos, float tempXspeed) { 
    c = tempC;
    xpos = tempXpos;
    ypos = tempYpos;
    xspeed = tempXspeed;
  }

  void display() {
    stroke(0);
    fill(c);
    rectMode(CENTER);
    rect(xpos,ypos,20,10);
  }

  void drive() {
    // if this car is in the bottom lane drive from left to right
    if (ypos > height/2) {
      xpos = xpos + xspeed;
      if (xpos > width) {
        xpos = 0;
      }      
    } else if (ypos < height/2) {
      // else if this car is in the top lane drive from right to left
      
      // ADD YOUR CODE HERE


    }
  }
}
```
