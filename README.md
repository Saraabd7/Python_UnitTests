#Python Unit Test

Unit testing is a software testing method by which individual units of source code are put under various tests to determine whether they are fit for use (Source). It determines and ascertains the quality of your code.

Generally, when the development process is complete, the developer codes criteria, or the results that are known to be potentially practical and useful, into the test script to verify a particular unit's correctness. During test case execution, various frameworks log tests that fail any criterion and report them in a summary.

The developers are expected to write automated test scripts, which ensures that each and every section or a unit meets its design and behaves as expected.

Though writing manual tests for your code is definitely a tedious and time-consuming task, Python's built-in unit testing framework has made life a lot easier.

The unit test framework in Python is called unittest, which comes packaged with Python.

Unit testing makes your code future-proof since you anticipate the cases where your code could potentially fail or produce a bug. Though you cannot predict all the cases, you still address most of them.

A unit could be bucketed into various categories:

- An entire module,
- An individual function,
- A complete interface like a class or a method.


The best ways to write unit tests for your code is to first start with the smallest testable unit your code could possibly have, then move on to other units and see how that smallest unit interacts with other units, this way you could build up a comprehensive unit test for your applications.

Python's unit testing framework was inspired by java's JUnit and has similar features as major unit testing frameworks in other languages. Python's unit testing framework offers various features like (Source: TutorialsPoint)

- Test automation
- Sharing of setup and shutdown code for tests
- Aggregating tests into collections
- Independence of the tests from the reporting framework

### Calculate the volume of a cube in Python: 
``` 
def cuboid_volume(l):
    return (l*l*l)
``` 

``` 
length = [2,1.1, -2.5, 2j, 'two']
``` 

``` 
for i in range(len(length)):
    print ("The volume of cuboid:",cuboid_volume(length[i]))
``` 

The above output should give you some intuition about the importance of having a unit test in place for your code. Now there are three things which are certainly incorrect in the above code:

First, the volume of cuboid being negative,
Second, the volume of the cuboid is a complex number,
Finally, the code resulting in a TypeError since you cannot multiply a string, which is a non-int.
The third problem thankfully resulted in an error while the first & second still succeeded even though the volume of the cuboid cannot be negative and a complex number.

Unit tests are usually written as a separate code in a different file, and there could be different naming conventions that you could follow. You could either write the name of the unit test file as the name of the ```  code/unit + test ```  separated by an underscore or ```  test + name of the code/unit ```  separated by an underscore.

For example, let's say the above code file name is ``` cuboid_volume.py``` , then your unit test code name could be ``` cuboid_volume_test.py ``` 

Without any further ado, let's write the unit test for the above code.

First, let's create a python file with the name volume_cuboid.py, which will have the code for calculating the volume and second with the name test_volume_cuboid.py, which will have the unit testing code.

``` 
import unittest
``` 

The TestCuboid class inherits the unittest module, and in this class, you would define various methods that you would want your unit test should check with your function cuboid_volume.

The first function you will define is ```  test_volume``` , which will check whether the output your ``` cuboid_volume```  gives is equal to what you expect. To achieve this, you will make use of the ``` assertAlmostEqual```  method.

``` 
class TestCuboid(unittest.TestCase):
    def test_volume(self):
        self.assertAlmostEqual(cuboid_volume(2),8)
        self.assertAlmostEqual(cuboid_volume(1),1)
        self.assertAlmostEqual(cuboid_volume(0),0)
        self.assertAlmostEqual(cuboid_volume(5.5),166.375)
``` 

Let's run the above script. You would run the unittest module as a script by specifying -m while running it.

``` 
python3 -m unittest test_volume_cuboid.py
``` 
The test ran successfully and returned, OK, which means the cuboid_volume function works as you would expect it too.