## Lab 3 Bugs and Commands

## Part 1 - Bugs

The bug from lab 4 that we will explore here stems from the ArrayExample.java file and is within the reverseInPlace() method.

Failing test code in ArrayTests.java:


	  @Test 
		public void testReverseInPlace1() {
	    int[] input1 = { 2, 3, 4 };
	    ArrayExamples.reverseInPlace(input1);
	    assertArrayEquals(new int[]{ 4, 3, 2 }, input1);
		}

However, the following test does not fail:

    @Test
    public void testReversedInPlace2() {
      int[] input1 = { 2 };
      ArrayExamples.reverseInPlace(input1);
      assertArrayEquals(new int[]{ 2 }, input1); 
    }









