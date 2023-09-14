Parallel testing is the process of executing two or same testcase at the same time. In this scripts can be set up to run each test in more than one browser, more than one OS, more than and one device. One of the benefits of parallel testing is to reduce execution time.

TestNG attribute has a parallel attribute that can be set to classes, methods and tests.

Setting the parallel attribute at methods all the methods will run simultaneously, same for classes two classes will run together.

`threadPoolSize`: the size of the thread pool for this method. The method will be invoked from multiple threads as specified by `invocationCount.` 
**Note**: this attribute is ignored if `invocationCount` is not specified
`invocationCount`: The number of times a particular method should be invoked.

thread-counts sets the default maximum number of threads to use for running tests in parallel. It will only take effect if the parallel mode has been selected. This can be overridden in the suite definition.

```java
//Java Code
public class ParallelTesting{
	WebDriver driver;
	@BeforeMethod
	public void setUP(){
		WebDriverManager.chromedriver().setup();
		driver = new ChromeDriver();
	}

	@Test(threadPoolSize=3, invocationCount=4)
	public void test1(){
		driver.get(URL1);
	}
	@Test
	public void test2(){
		driver.get(URL2);
	}

	@AfterMethod
	public void tearDown(){
		driver.quit;
	}
}
 
//TestNG
<suites name="Parallel Testing" parallel="methods" thread-counts="2">
	<tests>
		<classes>
			<class name="Demo.ParallelTesting"/>
		</classes>
	</tests>
</suites>
```

### Data Driven Testing

Data Provider allows us to perform data driven testing. With them we are allowed to send data. We need a DP annotation along with this we require a DP attribute or a DP class attribute

The data provider attribute allows us to send data from the same class, the data provider class attribute allows us to send data from a different class.

Data Provider method can return other types as well not only Object. Return type as Object is preferred when we need to return heterogenous data. e.g. Integer, String etc. all from one method. Since Object class is super class of all other classes in Java so Object class can provide reference to subclass objects by following Upcasting concept of Java.

```java
public class DataProviderTest{
//Setup code

@DataProvider
public Object[][] datamethod(){
	Object[][] data = new Object[2][2];
	data[0][0]="name";
	data[0][1]="comment";
	data[1][0]="name1";
	data[1][1]="comment1";
	return data;
}

@Test(dataProvider="datamethod")
public void test(String name, String comment){
	System.out.println(name);
	System.out.println(comment);
	driver.get("URL");
	driver.findElement(By.id()).sendKeys(name);
	driver.findElement(By.id()).sendKeys(comment);
}

//Teardown code
}

//If we create in a new file then it will be

@Test(dataProviderClass=ClasName.class, dataProvider="name")
```