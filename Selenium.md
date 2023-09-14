Selenium automates browser.

It a free(open-source) automated testing framework/suite used to validate web applications across different browsers and platforms.

### Selenium Tool Suite

It consists of different components:

- Selenium 2
    - Selenium Integrated Development Environment (IDE)
    - Selenium Remote Control (RC) / Selenium 1
- WebDriver
- Selenium Grid

### Selenium Web Driver

WebDriver drives a browser natively, Selenium WebDriver refers to both the language bindings and the implementations of the individual browser controlling code.

### Locators:

Locators are the way to identify an HTML element on a web page
Below are orders are in preference:

- ID: `driver.findElement(By.id(”ID value”);`
- Name: `driver.findElement(By.name(”Name value”);`
- ClassName: `driver.findElement(By.classname(”classnamevalue”);`
- LinkText: `driver.findElement(By.linkText(”textofLink”);`
- PartialLinkText: `driver.findElement(By.partialLinkText(”PartialTextofLink”);`
- Tagname: `driver.findElement(By.tagname(”HTMLTag”);`
- CSS: `driver.findElement(By.cssSelector(”value”);`
- Xpath: `driver.findElement(By.xpath(”value”);`

Remote Code to run in cloud machine for crio:

```java
@BeforeTest(alwaysRun = true)
public void createDriver() throws MalformedURLException {

    final DesiredCapabilities capabilities = new DesiredCapabilities();
    capabilities.setBrowserName(BrowserType.CHROME);
    driver = new RemoteWebDriver(new URL("<http://localhost:8082/wd/hub>"), capabilities);
        //In above URL we are telling the HUB address
        //capabilities, we are telling the code about the capabilities we've set before
        // This line creates a new instance of RemoteWebDriver in each test class
    driver.manage().window().maximize();
}
```

Basic operations:

- `get()`: use to open a URL
- `sendKey()`: use to send values
- `click()`: used to click on a button
- `getText()`: return text body of that element
- `getAttribute(”need to pass that attribute”)`: to retrieve value from input box

### Dropdown

To find if its a dropdown or not; the HTML tag will be `<select>`. There are majorly two dropdowns:
- Single Dropdown
- Multiple Dropdown

To select any dropdown we get the select class:

```java
//For Single Dropdown
Select single_sel= new Select(WebElement);
single_sel.selectByIndex(int index);
single_sel.selectByValue(String attribute);
single_sel.selectByVisibleText("body text");
//The below statment will return the selected option
WebElement output= sel.getFirstSelectedOption.getText();
//For Multiple Dropdown
Select multiple_sel= new Select(WebElement);
multiple_sel.selectByIndex(int index);
multiple_sel.selectByValue(String attribute);
multiple_sel.selectByVisibleText("body text");
//The below statment will return the selected option
List<WebElement> multiple_output= sel.getAllSelectedOptions;
for(WebElement out:multiple_output){
	System.out.println(out.getText());
}
```

### Alerts

It is used to change the focus of the user. If there is an alert you can’t interact with the webpage.

```java
Alert alert=driver.switchTo().alert();
//functions for alert
System.out.println(alert.getText());//Will give the text in alert
alert.accept();
alert.dismiss();
alert.sendKeys("Value to fill in field");
alert.accept();

//Exception we get
UnhandledAlertException //When alert is open and you interact with page
NoSuchAlertException//When no alert is there and you try to switch
```

For Sweet/ Modern alert we can treat it as Web Element.

### Window Handling

Parent/Main window is the one which is open first and from there which other windows/tab opens are known as child window.

For each and every tab there is a new unique identifier which changes each time we run.

```java
//Open the parent window
driver.get("Parent Window");
String parentWindow=driver.getWindowHandle();
//Click on child window link
driver.findElement(By.id("value")).click();
//This returns the multiple windows open in List
//which is internally implemented as Linked Hash Set
Set<String> windowHandles=driver.getWindowHandles();
List<String> windows=new ArrayList<String>(windowHandles);
//Will move to child window
driver.switchTo().window(windows.get(1));
driver.switchTo().window(parentWindow);
driver.quit();//closes all the windows
//driver.close();closes the window of focus
```

### Frames

HTML embedded within an HTML is known as frame.

```java
WebElement mainframe=driver.findElement(By.xpath(//iframe1));
driver.switchTo().frame(mainframe);
/*frame can receive three values
	1. int index; least preferred
	2.String name
	3.WebElement element 
*/
/*Some operations on mainFrame*/
//Nested Iframes
WebElement innerframe=driver.findElement(By.xpath(//iframe2));
driver.switchTo().frame(innerframe);
/*Some opertaions on innerframe*/
//switches to one step above
driver.switchTo().parentFrame();
//If we want to switch to Main page or frame; deafult content
driver.switchTo().defaultContent();
```

### Window Authentication

It has multiple fields to enter, also known as Web Authentication popup used to add just a secure layer.

```java
String username="admin";
String password="admin";
/* Normal URL
	driver.get("<https://the-internet.herokuapp.com/basic_auth>");
*/
driver.get("https://"+username+":"+password+"@"+"the-internet.herokuapp.com/basic_auth");
```

### Taking Screenshot

``` Java
//Since we'll use WebDriver we need to typecast the Screenshot (TakeScreenshot) 
WebDriver driver = new ChromDriver();
driver.get(URL);
File screenshotAs = ((TakeScreenshot) driver).getScreenshotAs(OutputType.File);
/*getScreenshotAs has 3 options
	1. BASE64:Used in ExtentReport
	2. BYTES: Used in Cumcumber
	3. FILE: Output as file
*/
/*
FileHandler filehandler = new FileHandler();
filehandler.copy("source","destination");
It is a static function hence we can call it like below
*/
FileHandler.copy(screenshotAs,new File("./screenshots"));

//Taking Screenshot of particular region
WebElement ele = driver.findElement(By.id());
File scr = ele .getScreenshotAs(OutputType.File);
FileHandler.copy(scr ,new File("./screenshots"));
```
