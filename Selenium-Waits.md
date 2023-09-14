Below are the different ways:
- `Thread.sleep()`: 
	- (Not a Selenium Wait Method)
	- Causes execution to sleep for a certain number of milliseconds
- Page Load Timeout
	- Sets the wait time for a page to load before throwing an error
- Script Timeout
	- Sets the wait time for JavaScript to execute before throwing an error
- Implicit Wait
	- Instructs WebDriver to wait for all elements connected to the driver
- Explicit Wait
	- Pauses execution until time has expired or an expected condition is met via WebDriver class
- Fluent Wait
	- Allows us to wait for an element, check for the presence of an element, and ignore exceptions
```java
public void explictWait(){
	WebDriverWait wait = new WebDriverWait(driver,Duration.ofSeconds(10));
	wait.unitl(ExpectedConditions.visibilityofElementLocated());
}

public void implictWait(){
	driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
}

public void fluentWait(){
	Wait<WebDriver> wait = new FluentWait<WebDriver>(driver)
       .withTimeout(Duration.ofSeconds(30L))//tells how long to wait for an element
       .pollingEvery(Duration.ofSeconds(5L))//how often the condition should be checked
       .ignoring(NoSuchElementException.class);//ignore the exception

   WebElement foo = wait.until(new Function<WebDriver, WebElement>() {
     public WebElement apply(WebDriver driver) {
       WebElement fooElement = driver.findElement(By.id("foo"));
			 String output = fooElement.getText();
			 return fooElement;
     }
   });
}
```