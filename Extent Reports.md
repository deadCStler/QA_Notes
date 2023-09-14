Test Result reports are reports used to communicate important information necessary to make critical decisions.

Extent Reports is an open-source reporting library useful for test automation. It can be easily integrated with major testing frameworks like JUnit, NUnit, TestNG, etc. These reports are HTML documents that depict results as pie charts. They also allow the generation of custom logs, snapshots, and other customized details.

********Note:******** Remember to add the dependency in the build.gradle file

Extent Report Class: is used to generate an HTML report on the user-specified path. The Boolean flag indicates if the existing report needs to be overwritten or a new report needs to be created. Value ‘true’ is the default value, which means all the existing data will be overwritten.

Extent Test Class: is used to log the steps onto the generated HTML reports.

Extent Spark Reporter: It is the newest report that is building the HTML reports because there are others listener as well but this is the latest.

************Note:************ If using Extent Spark Reporter then the path will be given for that object else the path will be given in the Extent Report object.

The method config() has been deprecated in the recent versions of Extent Reports. The Recommended way is to use a config XML file.

```java
//Without Extent Spark Reporter(deafult)
ExtentReports reports = new ExtentReports("Path of directory to store the resultant HTML file", true/false);
ExtentTest test = reports.startTest("TestName");
report.loadConfig(new File("<XML_FILE_PATH>"));

//With Extent Spark Reporter(latest)*EXTRA*
ExtentReport extent = new ExtentReports();
ExtentSparkReporter spark = new ExtentSparkReporter(System.getProperty("user.dir") + "/test-output/ExtentReport.html");
extent.attachReporter(spark);
spark.loadXMLConfig(new File("<XML_FILE_PATH>"));
ExtentTest test = extent.startTest("TestName");
//////////////////////////////////////////////////////////////  
/*Build in methods for above both classes
	-startTest: executes preconditions of testcase
	-endTest: executes postconditions of testcase
	-Log: logs the status of each step onto the HTML report being generated
	-Flush: Erases any previous data on a relevant report and creates a whole new report
*/
/*
 The Log method takes in two parameters, the first being the test status and 
 the second being the message to be printed onto the resultant report.
*/
test.log(LogStatus.PASS,"Test Passed");
test.log(LogStatus.FAIL,"Test Failed");
test.log(LogStatus.SKIP,"Test Skipped");
test.log(LogStatus.INFO,"Test Info");
reports.endTest();

//config.xml
<?xml version="1.0" encoding="UTF-8"?> 
<extentreports>
<configuration>
//title ofthe document
<documentTitle>Report</documentTitle>
//protocol for script and stylesheets
//defaults to https
<protocol>http</protocol>
//document encoding –>
//defaults to UTF-8 –>
<encoding>UTF-8</encoding>
//report theme
//standard,dark
<theme>standard</theme>
//report name = displayed at top-nav with logo
<reportName align="center">
//<img src=”../logo.png” style=”position:absolute;left:75px;”/>
<message>Automation Report</message>
</reportName>
//locationofchartsinthetestview
//top,bottom
<testViewChartLocation>bottom</testViewChartLocation>
</configuration>
</extentreports>
```

### Capturing Screenshots

```java
test.log(LogStatus.FAIL,test.addScreenCapture(capture(driver))+ "Test Failed");
//Above will be added in the place for capturing screenshot

public static String capture(WebDriver driver) throws IOException {
File scrFile = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);
File Dest = new File("src/QKARTImages/" + System.currentTimeMillis()
+ ".png");
String errflpath = Dest.getAbsolutePath();
FileUtils.copyFile(scrFile, Dest);
return errflpath;
}
```
