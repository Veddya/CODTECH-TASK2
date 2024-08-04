# CODTECH-TASK2
Develop a test automation framework using TestNG for a Java application. 
Set up and configure TestNG in a Java project. Write and organize test cases
using TestNG annotations.


package DemoTestNG;

import org.testng.Assert;
import org.testng.annotations.AfterClass;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.Test; 

import junit.Calculator;

public class CalculatorTest {
    private Calculator calculator;

    @BeforeClass
    public void setUpClass() {
        System.out.println("BeforeClass: Setup resources before any tests are run");
    }

    @BeforeMethod
    public void setUp() {
        calculator = new Calculator();
        System.out.println("BeforeMethod: Setup before each test method");
    }

    @Test(priority = 1)
    public void testAddition() {
        int result = calculator.add(2, 3);
        Assert.assertEquals(result, 5, "Addition test failed");
    }

    @Test(priority = 2)
    public void testSubtraction() {
        int result = calculator.subtract(5, 3);
        Assert.assertEquals(result, 2, "Subtraction test failed");
    }

    @Test(priority = 3, expectedExceptions = IllegalArgumentException.class)
    public void testDivisionByZero() {
        calculator.divide(10, 0);
    }

    @AfterClass
    public void tearDownClass() {
        System.out.println("AfterClass: Clean up resources after all tests are run");
    }
}

