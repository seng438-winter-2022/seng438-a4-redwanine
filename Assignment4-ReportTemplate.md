**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#4 – Mutation Testing and Web app testing**

| Group \#:       |   |
|-----------------|---|
| Student Names:  |  Rahat Islam |
|                 |  Redwanul Islam |
|                 |  Zeeshan Chougle |
|                 |  Mahtab Khan |

# Introduction
The aim of this lab is to explore various concepts and tools related to Mutation Testing and GUI Testing. In the first part, we used PIT, a mutation testing tool to inject mutants into our code and analyse the effectiveness of our original test suite. We then created more tests in order to improve our mutation coverage for specific classes. In part two, we used a tool called Selenium to create GUI tests, by recording and playing tests. We then compared Slenium to Sikulix, which is another tool used for GUI testing.

# Analysis of 10 Mutants of the Range class 

1) Line 123, Mutant 9<br />
Replaced double subtraction with multiplication → KILLED<br />
This mutant deals with the getLength() method in the Range class.<br />
The mutant replaces the subtraction operator with the multiplication operator. <br />
return this.upper - this.lower; -> return this.upper * this.lower;<br />
The mutant is killed potentially by test case (testGetLengthPositivePositive()) which expects a value of 4. However, once getLength() is mutated, it returns a value of 5, therefore the unit test fails and the mutation is killed. 

2) Line 144, Mutant 2<br />
replaced boolean return with true for org/jfree/data/Range::contains → KILLED<br />
This mutant deals with the contains(double value) method in Range class.<br />
The mutant replaces the returned value with true. Therefore, the mutant is killed is killed potentially by test case (rangeDoesntContainAboveUpperBound()) which expects a value of false returned by contain(). Therefore, the unit test fails for this case, hence the mutant has been killed.

3) Line 123, Mutant 1<br />
Replaced double subtraction with addition → KILLED<br />
This mutant deals with the getLength() method in the Range class.<br />
The mutant replaces the subtraction operator with the addition operator. <br />
return this.upper - this.lower; -> return this.upper + this.lower;<br />
This mutant was killed by test case (testGetLengthPositivePositive()) with range(1,5), with an expected output of 4.<br />
Once the mutant is created by replacing – with +, the test failed, as the new output would be 6. Therefore, the mutant was killed.<br />

4) Line 144, Mutant 1<br />
replaced boolean return with false for org/jfree/data/Range::contains → KILLED<br />
This mutant deals with the contains(double value) method in Range class.<br />
The mutant replaces the returned value with false. Therefore, the mutant is killed potentially by test case (rangeContainsAboveLowerBound()) which expects a value of true returned by contains(). Therefore, the unit test fails for this case, hence the mutant has been killed.<br />

5) Line 132, Mutant 1<br />
Substituted 2.0 with 1.0 → KILLED<br />
This mutant deals with the getLength() method in the Range class.<br />
The mutant replaces the 2.0 with 1.0.  PIT does not specify which 2.0 is replaced by 1.0<br />
return this.lower / 2.0 + this.upper / 2.0; -> return this.lower / 1.0 + this.upper / 2.0; OR
return this.lower / 2.0 + this.upper / 1.0;<br />
This mutant is not killed as we do not have any test cases which deal with getCentralValue(), therefore there is no coverage.<br />
The mutant is killed potentially by test case (centralValueShouldBeThree()) which expects a return value of 3 by getCentralValue(). However, the mutant returned either 4 or 5. Therefore, the unit test fails for this case, hence the mutant has been killed.<br />

6) Line 132, Mutant 5<br />
Replaced double addition with subtraction → KILLED<br />
This mutant deals with the getCentralValue() method in the Range class.<br />
The mutant replaces the + operator with the - operator.  <br />
return this.lower / 2.0 + this.upper / 2.0; -> return this.lower / 1.0 - this.upper / 2.0;<br />
The mutant is killed potentially by test case (centralValueShouldBeThree()) which expects a return value of 3 by getCentralValue(). However, the mutant returned -1. Therefore, the unit test fails for this case, hence the mutant has been killed.<br />

7) Line 123, Mutant 11<br />
Replaced double subtraction with modulus → KILLED
This mutant deals with the getLength() method in the Range class.
The mutant replaces the subtraction operator with the modulus operator. 
return this.upper - this.lower; -> return this.upper % this.lower;
The mutant is killed as potentially by test case (testGetLengthPositivePositive()) which expects a value of 4. However, once getLength() is mutated, it returns a value of 0, therefore the unit test fails and the mutation is killed. 


8) Line 312, Mutant 1<br />
replaced return value with null for org/jfree/data/Range::expandToInclude → KILLED<br />
This mutant deals with the expandToInclude(Range range, double value) method in the Range class.<br />
The mutant replaces the return value in line 312 with a null value.<br />
return range: -> return null;<br />
The mutant is killed as potentially by test case (testExpandToIncludeValueInRange()) which does not expect a null value. However, once expandToInclude(Range range, double value) is mutated, it returns a value of null, therefore the unit test fails and the mutation is killed. <br />

9) Line 123, Mutant 10<br />
Replaced double subtraction with division → KILLED<br />
This mutant deals with the getLength() method in the Range class.<br />
The mutant replaces the subtraction operator with the division operator. <br />
return this.upper - this.lower; -> return this.upper / this.lower;<br />
The mutant is killed as potentially by test case (testGetLengthPositivePositive()) which expects a value of 4. However, once getLength() is mutated, it returns a value of 5, therefore the unit test fails and the mutation is killed. <br />

10) Line 176, Mutant 1<br />
replaced boolean return with false for org/jfree/data/Range::intersects → NO_COVERAGE<br />
This mutant deals with the intersects(Range range) method in the Range class.<br />
This mutant replaces the original return boolean value with false.<br />
return intersects(range.getLowerBound(), range.getUpperBound()); -> return false;<br />
This mutant is not killed as we do not have any test cases which deal with intersects(Range range), therefore there is no coverage.<br />

# Report all the statistics and the mutation score for each test class

Original Test Suite (Range class)

![](./media/OLD_RANGE.PNG)

[Details Here](./media/OLD_REPORT_RANGE.pdf)

Updated Test Suite (Range class)

![](./media/NEW_RANGE.PNG)

[Details Here](./media/NEW_REPORT_RANGE.pdf)

Original Test Suite (DataUtilities class)

![](./media/OLD_DATAUTILITIES.png)

[Details Here](./media/OLD_REPORT_DATAUTILITIES.pdf)

Updated Test Suite (DataUtilities class)

![](./media/NEW_DATAUTILITIES.PNG)

[Details Here](./media/NEW_REPORT_DATAUTILITIES.pdf)<br />

[Final Test Suite Here](./JFreeChart_Lab4.zip)

# Analysis drawn on the effectiveness of each of the test classes

The effectiveness of the updated test suite for the DataUtilities class is high, as we managed to reach a mutation coverage of 88%. This signifies that majority of the mutations have been killed. For Range class we managed to reach a mutation coverage of 72%, which is also very high, signifying that our test cases are effective. We did not manage to reach 100% mutation coverage for various reasons, one of which is the presence of stillborn and equivalent mutants.

# A discussion on the effect of equivalent mutants on mutation score accuracy including a discussion on how equivalent mutants could be detected

**Effect of equivalent mutants on mutation score accuracy:**

The problem of equivalent mutants--- mutations that leave the program's overall semantics unchanged, and therefore cannot be caught by any test suite. Equivalent mutants thus act as false positives: They appear to indicate a weakness in the test suite, but in fact do not, as no test can detect them. The mutation score is the percentage of killed mutants divided by the total number of mutants multiplied by 100.

Because of equivalent mutations, the stated mutation coverage will never approach 100%. This is because similar mutants increase the number of mutants in the test suite but do not change the number of mutants killed. Because a lower score often indicates that a test suite requires improvement, these similar alterations degrade the accuracy of the assessment.

**Detecting equivalent mutants:**

Equivalent mutant detection is one of the biggest obstacles for practical usage of mutation testing. A review of the source code is required to find equivalent mutants. Test inputs should be checked for accuracy, which includes comparing the source code to the mutant code and flagging any discrepancies. Testers should examine their suites' behaviour from a black-box to a white-box perspective, looking for logic changes and logic outputs. Unfortunately, these methods can be difficult and time-consuming, and as a result, they are not favoured by all.

**Equivalent mutations we found manually:**

line 127 of DataUtilities:
for(int r = 0; r < rowCount; i++) -> for(int r = 0; r != rowCount; i++)

line 153 of DataUtilities:
for(int v = 0; v < validRows.length; i++) -> for(int v = 0; v != validRows.length; i++)

line 245 of DataUtilities:
for (int i = 0; i < l1; i++) -> for (int i = 0; i != l1; i++)

line 265 of DataUtilities:
for (int i = 0; i < data.getItemCount(); i++) -> for (int i = 0; i != data.getItemCount(); i++)

line 272 of DataUtilities:
for (int i = 0; i < data.getItemCount(); i++) -> for (int i = 0; i != data.getItemCount(); i++)


# A discussion of how we improved the mutation score of the test suites. Our design strategy.

We created test cases that deal with methods that had no coverage. For example, the following method

-   intersect() , had 6 mutants and they all survived. So we wrote 2 new tests that ensured all the surviving mutants were killed.

We manually checked for mutants that survived and specifically created test cases to kill those mutants.

We created tests for methods that had coverage but survived. For example, for the following methods

-   getUpperBound() we wrote 1 new test

-   getCentralValue() we wrote 2 new tests

Lastly, we ran into a significant execution time problem when running Pitclipse. Each mutation test run took over 20 minutes, so it was impractical to run Pitclipse after every new test case we developed. Oftentimes, instead of running Pitclipse, we went and modified the source code with a specific mutation to see if our new test case would fail with it. If our new test case did fail, this would mean that the associated mutation would be killed in a new run of Pitclipse. After completing all of our new test cases, we did a final run of Pitclipse to confirm the results, which turned out as expected.

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

Why do we need it?

Other testing methodologies, such as white or black-box testing, enable testers to create high-quality test suites. Even if the tests have a high percentage of coverage metrics, they may not be considered effective. By injecting flaws into the source code, mutation testing can be used to assess the robustness of test suites. These alterations in the source code are evaluated to see if the existing suite is capable of detecting these errors.

Advantages:

-   After this testing, customers receive the most stable and reliable system

-   Mutation testing has the ability to detect all faults in the source code

-   High coverage of the source program is attained

-   Quality of software programs is improved.

-   Using tools, such as Pitest, provide testers with metrics to determine whether the system is adequately tested.

Disadvantages:

-   Complex mutations are difficult to implement.

-   Requires familiarity with the code base, as testers must determine how to catch each mutation. Thus, it can be tedious and time consuming. 

-   Depending on the system, computation time required to run automation may be lengthy 

-   Injecting changes to source code can result in equivalent mutants


# Explain your SELENUIM test case design process

The test case design process was to atleast have some coverage over the main functionality of the website. We wanted end to end coverage of the different functionalitieis to ensure that the process was able to completely fullfil its requirements. The main areas we wanted to test was through searching the catalog, signing up on the mailing list, signing in, choosing a store, and being able to access the trueFit webpage. Each person split up to design their own test cases for different functionalities

# Explain the use of assertions and checkpoints

Assertions and verification checkpoints where required to make sure that the webpage was actually showing the desired output. For instance, when we expected a certain object to render, we asserted that it would be present, such that if it wasnt, the test would fail.


# how did you test each functionaity with different test data

<p>For most of our test cases, tests were designed such that the actual input data could be changed. That way, we could check to make sure the tests weren’t responding to only that specific input. For instance, when entering a wrong promo code, we entered multiple different wrong codes to make sure that the program still behaved accordingly.</p>

<p>For certain functionalities, we also used different data to test certain scenarios. This was for instance done when entering valid and invalid mailing information. Different data was also used in find a store given a postal code. For instance, we put in a calgary postal code and a toronto postal code, and compared is stores showed up specific to the region.</p>


# Discuss advantages and disadvantages of Selenium vs. Sikulix

Sikulix

Pros:

-   Image based recognition: very accurate to evaluate the regions on the screen properly

-   Can be used on web, desktop and mobile apps

-   Setup is easy

-   Supports multiple languages

Cons:

-   Very slow

-   Documentation is poor

-   Play-back isn't available

Selenium

Pros:

-   Very easy to use, especially with IDE

-   Playback functionality is helpful

-   Supports multiple browsers

Cons:

-   No support for images

-   The recordings often crash. Tests have to be recreated

-   Less features that can be tested.


# How the team work/effort was divided and managed

We split the work evenly across each person. We each spent time doing the mutation tests, and created ways to handle the survived mutants. Afterwards, each person created their own tests for selenium and we compiled them all after everyone was complete.

# Difficulties encountered, challenges overcome, and lessons learned

The mutation testing was very annoying for our group. That is because it took a long time to setup, due to many different errors that we were encountering. Furthermore, running the PIT tool took on average 20 minutes to load. Selenium on the other hand wasn’t as difficult to use, although it is also buggy at times. Running the same tests on a different computer or different internet network would sometimes mess with the test’s success for no reason. Hopefully the next assignment will involve tools that are more user friendly for students to actually use. 

# Comments/feedback on the lab itself

Overall the assignment taught us some skills on testing more features of a program. It would be really appreciated if for the next lab, we will not be given tools are very difficult to use by students. Something that is easier to setup, less buggy and doesn’t take 20 minutes to run would be appreciated :).
