TestNG (Test Next Generation) is a testing framework inspired from JUnit and NUnit but introducing some new functionalities that make it more powerful and easier to use.

TestNG is designed to cover all categories of tests: unit, functional, end-to-end, integration, etc.

It is a testing framework for writing and running test scripts, the purpose is to inspect the testing process of an application.

Test Frameworks are important because it simplifies the process of testing and providing the ability to run the tests as collections.

Functions of test frameworks:

- Create & Execute Test Scripts
- Generate Test Reports
- Generate Logs
- Read & Write Test Data

### TestNG annotations

It is the data which has special meaning for Java methods, our execution flow will depend on this.

Two types of annotations are the one we use mainly:

- Test annotation(@Test): identifies our test method, we can add them at class or method level.
    - Above is also known as ****************************************Condition annotation****************************************
    - priority: helps in setting the running priority
    - groups: helps in grouping test cases
    - description: used to give a brief about the test
- Configuration annotation: It starts with before/after, and each annotations performs an event before and after our test.
    - Pre-Conditions - @Before
    - Post-Conditions - @After
    - @AfterClass & @BeforeClass
    - @AfterGroups & @BeforeGroups
    - @AfterMethod & @BeforeMethod
    - @AfterSuite & @BeforeSuite
    - @AfterTest & @BeforeTest

### TestNG.xml Structure

```java
//Standard TestNG
<?xml version="1.0" encoding="UTF-8">
<!DOCTYPE suite SYSTEM "<http://testng.org/testng-1.0.dtd>">
<suite name="">
	<test name="">
		<groups>
			<run>
				<include ="">
			</run>
		</groups>
		<classes>
			<class name=""/>
				<methods>
					<include name="">
				</methods>
			</class>
			<class name=""/>
				<methods>
					<include name="">
				</methods>
			</class>
		</classes>
	</test>
</suite>
```

- A suite contains one or more test
- A test contains one or more classes
- Class name starts with package name then the class name
- A class contains one or more methods
- Methods
    - include: we can include tests
    - exclude: we can exclude tests
- Groups
    - @Test(groups={”regression”})
    - There can be more than one groups
    - In the groups annotation @BeforeGroups and @AfterGroups we need to pass the groups similar to above annotation

For ********************WebDriverManager******************** setup we can use **@BeforeClass** annotation because it execute **before** the 1st test method in the class

For tear down (driver.quit) we will use **********************@AfterClass**********************

****TestNG executes the testcase in the ascending order if priority is not given.****

### TestNG Assertions

It verifies if the test passes or fails.

- Hard Assert: stops execution after a failure and moves to the next annotation.
- Soft Assert: continues after a failure and move to the next statement line.

```java
/*
	Assertion Methods:
	-assertTrue: condition is true
	-assertFalse: condition is false 
	-assertSame: 2 objects refer to same object
	-assertNotSame: 2 objects don't refer to same
	-assertNotNull: object is not null
	-assertEquals: actual and expected results are =
*/
import org.testng.Assert
Assert.anyMethodAbove();//Hard Assert

SoftAssert softassert = new SoftAssert();
/*After adding softassert to methods always use assertAll*/
softAssert.assertAll();
```

### Parameterized Testing

Parameterized start with parameter tag and @Parameter Annotation, the purpose of parameter tag is to define the name and value of the parameter and the purpose of @Parameter annotation is to specify how to pass the parameters and which parameters to pass the annotation.

For parameterization we need a testng.xml file(parameter tag) and java class(@Parameter annotation)

**Note**: You can give same name to a parameter in suite and test but test value will **override** the suite value as the closer to the class will be considered.

```java
//Java Code
package JavaCodeTestNG
public class ClassTest {
	@BeforeClass
	@Parameters({"URL"})
	public void setUp(String url){
		WebDriverManager.chromedriver().setup();
		driver = new ChromeDriver();
		driver.manage().window().maximize();
		driver.get(URL);
	}
	
	@Test
	@Parameters({"Task","TestResult"})
	public void test(String task,String testresult){
		driver.findElement(By.linkText()).click;
		driver.findElement(By.id()).sendKeys(task + "Execution: "+ testResult);
	}

	@AfterClass
	public void tearDown(){
		driver.quit();
	}
}

//Testng.xml
<?xml version="1.0" encoding="UTF-8">
<!DOCTYPE suite SYSTEM "<http://testng.org/testng-1.0.dtd>">
<suite name ="Parameter Suite">
	<parameter name="URL" value="<https://www.google.com>"/>
	<parameter name="Task" value='Download file'/>
	<test name="Pass PT">
		<parameter name="TestResult" value="Pass"/>
		<classes>
			<class name="JavaCodeTestNG.ClassTest"/>
		</classes>
	</test>
	<test name="Fail PT">
		<parameter name="TestResult" value="Fail"/>
		<classes>
			<class name="JavaCodeTestNG.ClassTest"/>
		</classes>
	</test>
	<test name="Skip PT">
		<parameter name="TestResult" value="Skip"/>
		<classes>
			<class name="JavaCodeTestNG.ClassTest"/>
		</classes>
	</test>
</suite>
```

We can take failed screenshots in TestNG by using the ITestResult class we can use that in the parameter of a take screenshot method and then use the methods provided by ITestResult.