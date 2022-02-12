**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report \#2 – Requirements-Based Test Generation**

| Group \#:      |   6  |
| -------------- | --- |
| Student Names: | Ibrahim Asad    |
|                | Aninda Shome    |
|                | Sanchit Kumar    |
|                | Isaiah Asaolu    |

# 1 Introduction

For this lab, we first set up the Eclipse IDE. Then for the lab we had to test two classes, the Range and DataUtilities classes. From these classes, we had to pick five methods from each to unit test. Once we had picked those five methods from each class, we began testing using the boundaries and equivalence classes we had brainstormed together. The testing required us to look into documentation (Javadoc) for the classes and their methods to be able to understand what they do, what they return, and the arguments they take in. Overall, the process of finding errors and thinking of all possible cases was a long process, but we think we were able to cover a huge area of potential errors and bugs.


# 2 Detailed description of unit test strategy

As a team, we first created a document to hold all of the information about Black Box testing that we were going to gather. It was first important to brainstorm and think out possible requirements that each method we picked in the Range and DataUtilities classes should meet. We also thought of areas in which developers might have overlooked certain inputs to the methods to identify areas where we might want to develop tests. Then, we created Equivalence classes for the inputs to each method. It was important to focus on creating Equivalence classes that clearly defined inputs we needed to analyze, and that also matched the ideas we thought of during our brainstorming. Once this step was done, we used the Equivalence classes to clearly define our partitions, so we knew what exactly we would be coding for the tests. We also performed a boundary value analysis for each method based on these partitions we had made as well as the natural boundaries of the variables. Mocking was used on the Values2d and the KeyedValues classes that DataUtilities used. This made it easier to write shorter code and to emulate other classes without having to directly use them. It also helps to focus only on the class under test and not the classes that are being used by the class under test. However, it also requires in depth knowledge of the methods that are being tested and the ways in which these methods are executed. This is needed in order to be able to create a proper mock that is able to replicate the mocked classes properly. 

Partitions for Doubles: Double.NaN and a valid double (ex. 2.3).
The Boundaries of a Double were: Lower Bound: 2-1022  and Upper Bound: (2-2-52)·21023

Partitions for Range Object: Null, Valid Range (ex. (2,4)), a range containing a Double.NaN

Partitions for KeyedValues Object: Null or a Valid KeyedValues object

Partitions for Values2D Object: Null or a valid Values2D object

Partitions for Integers: Valid integer, or an int casted Double.NaN
The Boundaries of a Integer were: Lower Bound: -2147483648 and Upper Bound: 2147483647

Partitions for Int Array: Null array, a valid int array with integers, an array that contains an int casted Double.NaN

Partitions for a 2D double array: A 2d array with valid doubles, a 2d array with a Double.NaN, and a null 2d array

Partition for a double array: An array with valid doubles, an array with a Double.NaN, and a null array


# 3 Test cases developed

Range Class Tests:

Method: contains(double value) 

testValuePresentInRangeForMethodContains()
Partitions Covered: Valid double

testValueNotInRangeForMethodContains()
Partitions Covered: Valid double

testValueIsUpperBoundaryForMethodContains()
Partitions Covered: Valid double

testValueIsLowerBoundaryForMethodContains()
Partitions Covered: Valid double

testValueIsNaNForMethodContains()
Partitions Covered: Double.NaN

testLowestDoubleForMethodContains()
Partitions Covered: Valid double

testNegativeInfinityValueForMethodContains()
Partitions Covered: Valid double

testPositiveInfinityValueForMethodContains()
Partitions Covered: Valid double

Method: constrain(double value) 
testValueInTheRangeForMethodConstrain()
Partitions Covered: Valid double
testValueThatIsNaNForMethodConstrain()
Partitions Covered: Double.NaN
testUpperBoundNumberForMethodConstrain()
Partitions Covered: Valid double
testInfinityValueForMethodConstrain()
Partitions Covered: Valid double

Method: Shift(Range base, double delta) 
testUpperBoundaryShiftWithDecimalForMethodShift() 
Partitions Covered: Valid Double
testLowerBoundaryShiftWithDecimalForMethodShift()
Partitions Covered: Valid Double
testUpperBoundaryShiftNoDecimalForMethodShift()
Partitions Covered: Valid Double
testLowerBoundaryShiftNoDecimalForMethodShift()
Partitions Covered: Valid Double
testNaNShiftForMethodShift()
Partitions Covered: Double.NaN and Valid Range
testPositiveInfinityForMethodShift()
Partitions Covered: Double.NaN and Valid Range
testRangeObjectWithNaNBoundaryForMethodShift() 
Partition Covered: Range contains Double.NaN-Double.NaN range and Valid Double
testNullRangeObjectForMethodShift()
Partition Covered: Range contains Null to 10 and Valid Double

Method: expandToInclude(Range range, double value)
testValidDoubleValueForMethodExpandToInclude()
Partition Covered: Valid Range and valid double 
testDoubleNaNValueForMethodExpandToInclude()
Partition Covered: Valid Range and Double.NaN double
testNullRangeForMethodExpandToInclude()
Partition Covered: Null Range and valid double
testNaNRangeForMethodExpandToInclude()
Partition Covered: Range containing a range of Double.NaN-Double.NaN and valid double.

Method: combine(Range range1, Range range2) 
testValidRangeInputForMethodCombine()
Partitions Covered: Valid Range
testSingleNullRangeInputForMethodCombine()
Partitions Covered: Null range and Valid Range
testTwoNullRangesInputForMethodCombine()
Partitions Covered: Null range
testSingleNaNInputForMethodCombine()
Partitions Covered: Range containing Double.NaN

Data Utilities Tests:

Method: getCumulativePercentages(KeyedValues data)
testAValidInputForMethodGetCumulativePercentages()
Partitions Covered: Valid KeyedValues object
testANullInputForMethodGetCumulativePercentages()
Partitions Covered: Null KeyedValues object
testADoubleNaNForMethodGetCumulativePercentages()
Partitions Covered: KeyedValues object with Double.NaN 

Method: calculateColumnTotal(Values2d data, int column, int[] validRows)
testAValidInputForMethodCalculateColumnTotal()
Partitions Covered: Valid Values2d object, valid integer, and valid integer array
testNullValues2DObjectForMethodCalculateColumnTotal()
Partitions Covered: Null Values2d object, valid integer, and valid integer array
testForNaNInputForColumnForMethodCalculateColumnTotal()
Partitions Covered: Valid Values2d object, integer typecasted Double.NaN, and valid integer array
testForNullIntArrayForMethodCalculateColumnTotal()
Partitions Covered: Valid Values2d object, valid integer, and null integer array
testForNaNIntArrayForMethodCalculateColumnTotal()
Partitions Covered: Valid Values2d object, valid integer, and integer array with typecasted Double.NaN

Method: calculateRowTotal(Values2d data, int row)
testAValidInputForMethodCalculateRowTotal()
Partitions Covered: Valid Values2d object and valid integer
testNullValues2DObjectForMethodCalculateRowTotal()
Partitions Covered: Null values2d object and valid integer
testForNaNInputForRowForMethodCalculateRowTotal()
Partitions Covered: Valid Values2d object and integer typecasted Double.NaN

Method: equal(double[][] a, double[][] b)
testForTwoEqualArrayInputForMethodEqual()
Valid 2d array a and valid 2d array b
testForTwoDifferentArrayInputForMethodEqual()
Valid 2d array a and valid 2d array b
testForOneNullArrayInputForMethodEqual()
Null 2d array a and valid 2d array b
testForTwoNullArrayInputForMethodEqual()
Null 2d array a and null 2d array b
testForOneNaNArrayInputForMethodEqual()
2d array a with Double.NaN as one value and valid 2d array b
testForTwoNaNArrayInputForMethodEqual()
2d array a with Double.NaN as one value and 2d array b with Double.NaN as one value

Method: createNumberArray(double[] array)
testForAValidArrayInputForMethodCreateNumberArray()
Valid array
testForANullArrayInputForMethodCreateNumberArray()
Null array
testForANaNArrayInputForMethodCreateNumberArray()
Array with Double.NaN as a value


// write down the name of the test methods and classes. Organize the based on
the source code method // they test. identify which tests cover which partitions
you have explained in the test strategy section //above

# 4 How the team work/effort was divided and managed

The team decided that the best way to go about this lab was to work at the same time in a voice call. To start off, we chose to test the Range class. We first picked 5 methods and wrote them down in a google docs together. Then we wrote out the boundary value analysis and equivalence classes together, thinking about all the possible things we could add in them. Once that was done, as a group we began writing the unit tests up by using our equivalence classes and boundary analysis exploration we had done earlier. We also made sure that we covered as much ground as we could when we made these tests to make sure we tested each method thoroughly. Once the Range class was finished, we then repeated what we did for it for the DataUtilities class. After we finished the testing, we then discussed the lab report as a group and wrote down the answers while still working together in a call.

# 5 Difficulties encountered, challenges overcome, and lessons learned

We encountered some difficulties mainly when trying to set up Eclipse for the unit tests. The instructions given in the lab document were unclear on the ways in which Eclipse should be properly set up to ensure that unit tests can be run properly. Another great difficulty was creating unit tests for the methods in the Range and DataUtilities classes. This was because it was hard to find all the requirements for the methods, and explore them thoroughly. Black Box testing, and techniques such as Equivalence Classes and Boundary-Value Analysis, helped us to analyze each method and come up with the appropriate tests for them. However, it was still difficult to create proper Equivalence Classes and Boundaries from those classes. A lesson we learned is that when doing these unit tests, it's best to brainstorm ideas first with your group members about areas with potential bugs or things we need to check out for a method. We also learned that it is hard to know the correct expected outcome in most situations. Therefore, the expected outcome needs to be assumed by the tester and brought up to the developers at a later time.

# 6 Comments/feedback on the lab itself

The lab document was confusing to read. It first mentioned setting up Eclipse on a singular computer to conduct all tests, however all computers need to have the unit tests on them for the demos. At the same time, not all libraries needed were given in the artifacts.zip file. A major library, the hamcrest-all library, was missing from the artifacts.zip file and we had to decipher the error message and find that outside of the lab. Setting up Eclipse with the correct libraries was also difficult as the instructions given did not match what needed to be done. For example, for the libraries to work correctly, all of the libraries needed to be added to the classpath of the project. However, this is not mentioned anywhere in the lab document when setting up Eclipse. 

