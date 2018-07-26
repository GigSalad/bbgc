## Coding Class!

Today we're going to work with arrays and user input. 

### Arrays
First let's review the [arrays tutorial](https://processing.org/tutorials/arrays/). 
- An array is a list of values like `[1, 4, 2, 34, 0]`.
- Arrays are indexed starting at 0. The first value in an array is indexed at 0. The second value is indexed at 1.
- To use an array in Processing you have to
  - Declare it: `int[] names;`
  - Initialize/create it: `names = int[5];` (we use the number 5 here to say our `names` array should have 5 elements)
  - Assign it: `names[0] = 'Kory';`
- Once you have declared, initialized, and assigned all the elements of your array you will want to access them using a *for loop*
```
for (int i = 0; i < names.length; i++) {
    print(names[i]);
}
```


### User input
From the [interactivity tutorial](https://processing.org/tutorials/interactivity/) were going to use the [`mouseReleased()`](https://processing.org/reference/mouseReleased_.html) function.

`mouseReleased()` is a function that is triggered anytime a mouse button is clicked and then unclicked (or released). You use `mouseReleased()` like this...
```
void setup() {
  size(400,200);
}

void draw() {
}

void mouseReleased() {
 // Do stuff below here!
 ellipse(mouseX, mouseY, 22, 22); 
}
```


### Add cars to our road using the an array and the mouseReleased() function

Last week we got our cars driving in two lanes. Now lets add a car to the road every time you click the mouse.

I've already converted the old two lane road program to use an array of `Car` objects. Your job is to look at the `mouseReleased()` function and add two lines. You need to declare a new array that will be home to all your existing cars but still have room for on more new car. Then you need to add your new car to its home in your new array of `Car` objects.

### Two Lane Road

```
Car[] cars = new Car[2];

void setup() {
  size(400,200);
  // Parameters go inside the parentheses when the object is constructed.
  cars[0] = new Car(color(255,0,0),0,110,2); 
  cars[1] = new Car(color(0,0,255),0,10,1);
}

void draw() {
  background(255);
  
  // creates two yellow center lines for your highway 
  stroke(255, 200, 0);
  line(0, height/2 + 2, width, height/2 + 2);
  line(0, height/2 - 2, width, height/2 - 2);
  
  // add cars to the road
  for (int i = 0; i < cars.length; i++) {
    cars[i].drive();
    cars[i].display();
  }
}

void mouseReleased() {
  // create our new car with random colors and random speed
  Car newCar = new Car(color(random(255),random(255),random(255)),mouseX,mouseY,random(10));
  
  // Look at the array review to remember how to DECLARE and CREATE an array
  // Then make a newArray that is one element bigger than our old cars array
  // Hint: to set your new arrays size to 1 larger than the cars array use cars.length + 1

  // YOUR CODE HERE
  
  
  // Shift our array values up one index
  for (int i = newArray.length-1; i > 0; i--) {
    newArray[i] = cars[i-1];
  }
  
  // Add your new car as the first element of your newArray
  // Hint: Array indexes start a 0
  // YOUR CODE HERE
  
  cars = newArray;
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
      xpos = xpos - xspeed;
      if (xpos < 0) {
        xpos = width;
      }      


    }
  }
}
```
