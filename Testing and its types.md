Testing is the process of executing a program with the aim of finding the errors.

### Types of Testing

*Black box testing* involves testing a system with no prior knowledge of its internal working.

*White box testing* is an approach that allows software test engineers to inspect and verify the inner workings of a software system.

*Grey Box Testing* is a software testing technique to test a software product or application with partial knowledge of the internal structure of the application.

*Static Testing* is a type of software testing method which is performed to check the defects in software without actually executing the code of the software application. and when done while executing the code is Dynamic Testing.

##### AUT (Application Under Test)

*Functional testing* is a type of software testing that validates the software system against the functional requirements/specifications. Purpose is to test each function of the application.

*Non-Functional testing* is defined as a type of Software testing to check non-functional aspects (performance, usability, reliability, etc.) of a software application.

### Sanity, Smoke and Regression Testing

*Smoke Testing* is a software testing process that determines whether the deployed software build is *stable or not.*

*Sanity testing* is a kind of software testing performed after receiving a software build, *with minor changes in code, or functionality*, to ascertain that the bugs have been fixed and no further issues are introduced due to these changes.

*Regression Testing* is defined as a type of software testing to confirm that a recent program or code change has not adversely affected existing features, it is nothing but a full or partial selection of already executed test cases which are re-executed to ensure existing functionalities work fine.

##### Smoke → Regression → Sanity

*Accessibility testing* is the practice of making your web and mobile apps usable to as many people as possible. It makes apps accessible to those with disabilities, such as vision impairment, hearing disabilities, and other physical or cognitive conditions.

*Graphical user interface testing (GUI)* is the process for ensuring proper functionality of the GUI for a specific application.

*Performance testing* is a type of software testing that ensures software applications perform properly under their expected workload.

*Stress testing* is a software testing technique that determines the robustness of software by testing *beyond the limits of normal operation.*

*Recovery testing* aims at testing whether a *system can recover from failures or not.*

### Test Case Design

*Test case scenarios* contain a high level documentation describing an end to end functionality to be tested.
A *test case* is a set of actions performed on an application under test (AUT) to verify if it’s functionalities are working as expected or not. A well documented test case has information including:

- Test case ID
- Objective
- Category
- Prerequisite
- Test steps
- Expected result
- Execution status, etc.

*Specification-Based test case* design techniques involve deriving test cases directly from a requirement specification. It uses specification of the application as the point of reference for test data selection.
- Boundary value analysis is the process of deriving test cases based on extreme ends or boundaries of the input values defined in the specification.
- Equivalence class partitioning can be used for a given specification when input values can be classified into different sets or groups which the system should handle in the same manner.
- A decision table is used when software test engineers want to, Execute the combinations of inputs and/or stimuli (causes) or Provide better test coverage for complex business logic

*Experience-based test case* design techniques involves a software test engineer deriving the test cases using his/her past experience of testing the same application, domain and knowledge about the development team.

### Test Case Techniques

When someone writes the **test cases**, chances are there that they can skip or miss some test cases to avoid this one round of **review** and approval is done.

A **test case repository** is a centralized location where all the baseline test cases (written, review, and approved) are stored.

**Test data enumeration** is a process where we define what are the possible values / test data given as input to verify an application’s behavior. They are divided into valid data and invalid data.

### Pareto Principle

To overcome the challenge that the application changes constantly, we suggest being inspired by the 80:20 rule, the Pareto Principle, and start testing small and early.

The 80-20 rule define that 80% of outcomes (output) come from 20% of cause (inputs) Applying the 80-20 rule in software testing helps in achieving more in less time/effort 80% coverage/confidence would come from 20% of test cases

Pareto analysis is simply a technique that helps you optimize your efforts. Instead of distributing your focus, time and efforts on all 100% test case execution, you should look at 20% of the test cases which when executed will cover 80% of the application functionality.

### Test Reporting and Metrics

**Test reports** are documents that summarize the results obtained from a testing process. They provide information about the objectives, methodology, results, and conclusions of the test, and are used to communicate the test results to stakeholders and provide a record of the testing process.

Software **test metrics** are the quantitative measures used to evaluate progress, quality, productivity and health of the software testing process to take the decision about software application release.