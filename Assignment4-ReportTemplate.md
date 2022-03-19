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

![](./media/NEW_DATAUTILITIES.png)

[Details Here](./media/NEW_REPORT_DATAUTILITIES.pdf)

# Analysis drawn on the effectiveness of each of the test classes

# A discussion on the effect of equivalent mutants on mutation score accuracy

# A discussion of what could have been done to improve the mutation score of the test suites

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

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


# Difficulties encountered, challenges overcome, and lessons learned

# Comments/feedback on the lab itself
