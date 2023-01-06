# slip10


Q.1 Write a Java Program to implement Strategy Pattern for Duck Behavior. Create
instance variable that holds current state of Duck from there, we just need to handle all
Flying Behaviors and Quack Behavior 
Q. 2 Write a Python program to prepare Scatter Plot for Iris Dataset. 
Q. 3 Create a node.js file that Insert Multiple Records in "student" table, and display the
result object on console. 


Q.1 Write a Java Program to implement Strategy Pattern for Duck Behavior. Create
instance variable that holds current state of Duck from there, we just need to handle all
Flying Behaviors and Quack Behavior.

:
public abstract class Duck {
  private FlyingBehavior flyingBehavior;
  private QuackBehavior quackBehavior;

  public Duck() {
    // Set default behaviors
    flyingBehavior = new FlyWithWings();
    quackBehavior = new Quack();
  }

  // Set the flying behavior at runtime
  public void setFlyingBehavior(FlyingBehavior flyingBehavior) {
    this.flyingBehavior = flyingBehavior;
  }

  // Set the quacking behavior at runtime
  public void setQuackBehavior(QuackBehavior quackBehavior) {
    this.quackBehavior = quackBehavior;
  }

  // Perform the flying behavior
  public void performFly() {
    flyingBehavior.fly();
  }

  // Perform the quacking behavior
  public void performQuack() {
    quackBehavior.quack();
  }

  // Other duck methods...
}

// Concrete implementation of the FlyingBehavior interface
public class FlyWithWings implements FlyingBehavior {
  public void fly() {
    System.out.println("I'm flying with wings!");
  }
}

// Concrete implementation of the QuackBehavior interface
public class Quack implements QuackBehavior {
  public void quack() {
    System.out.println("Quack!");
  }
}

// Example usage
public static void main(String[] args) {
  Duck duck = new MallardDuck();
  duck.performFly();  // Output: "I'm flying with wings!"
  duck.performQuack();  // Output: "Quack!"

  // Change the flying behavior at runtime
  duck.setFlyingBehavior(new FlyNoWay());
  duck.performFly();  // Output: "I can't fly."

  // Change the quacking behavior at runtime
  duck.setQuackBehavior(new MuteQuack());
  duck.performQuack();  // Output: "<< Silence >>"
}


Q. 2 Write a Python program to prepare Scatter Plot for Iris Dataset. 

:import seaborn as sns
import matplotlib.pyplot as plt
from pandas.plotting import parallel_coordinates
import pandas as pd
# Parallel Coordinates
# Load the data set
iris = sns.load_dataset("iris")
parallel_coordinates(iris, 'species', color=('#556270', '#4ECDC4', '#C7F464'))
plt.show()


from pandas.plotting import andrews_curves
# Andrew Curves
a_c = andrews_curves(iris, 'species')
a_c.plot()
plt.show()



from seaborn import pairplot
# Pair Plot
pairplot(iris, hue='species')
plt.show()


from plotly.express import scatter_3d
# Plotting in 3D by plotly.express that would show the plot with capability of zooming,
# changing the orientation, and rotating
scatter_3d(iris, x='sepal_length', y='sepal_width', z='petal_length', size="petal_width",
                   color="species", color_discrete_map={"Joly": "blue", "Bergeron": "violet", "Coderre": "pink"})\
            .show()


Q. 3 Create a node.js file that Insert Multiple Records in "student" table, and display the
result object on console. 
:

const mysql = require('mysql');

// Create a connection to the database
const connection = mysql.createConnection({
  host: 'localhost',
  user: 'your_username',
  password: 'your_password',
  database: 'your_database'
});

// Connect to the database
connection.connect(error => {
  if (error) throw error;

  console.log('Successfully connected to the database.');
});

// Define the records to be inserted
const records = [
  ['John', 'Doe', 'john@example.com'],
  ['Jane', 'Doe', 'jane@example.com'],
  ['Bob', 'Builder', 'bob@example.com']
];

// Insert the records into the table
connection.query(
  'INSERT INTO student (first_name, last_name, email) VALUES ?',
  [records],
  (error, result) => {
    if (error) throw error;

    console.log(result);
  }
);

// Close the connection to the database
connection.end();


