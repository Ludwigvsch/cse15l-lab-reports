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

Here is the symptom as the test output:

![Screenshot 2023-11-05 at 8 22 49 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/d715e68a-9c5e-49d3-a03a-6a10f372955b)


The code with the bug in it:

	static void reverseInPlace(int[] arr) {
	    for(int i = 0; i < arr.length; i += 1) {
	      arr[i] = arr[arr.length - i - 1];
	    }
	  }

The code without the bug:

	static void reverseInPlace(int[] arr) {
	    for(int i = 0; i < arr.length / 2; i += 1) {
	      int temp = arr[i];
	      arr[i] = arr[arr.length - i - 1];
	      arr[arr.length - i - 1] = temp;
	    }
	  }

The issue in the earlier code stemmed from modifying the array during iteration, which led to the duplication of elements. In contrast, the revised approach processes only half of the array, temporarily holding an element due for removal. This technique avoids both the duplication of elements and the loss of data.

## Part 2 Researching Commands

Here are four interesting command-line options I found on https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/ for the find command along with examples for each, using files and directories.

**1. Find Files by Name (-name)**
This option locates files by their name.

	find ./technical -type f -name ar422.txt
 	> ./technical/biomed/ar422.txt

 	find ./technical -type f -iname ar615.txt
	> ./technical/biomed/ar615.txt
The first example searches for files named exactly "ar422.txt". The second uses -iname for a case-insensitive search, which is useful when the exact case of the filename is unknown​​.

**2. Find Files by Extension (-name with wildcard)**
This allows for searching files by their extension.

	find ./ -type f -name "*.java"
 	> .//DocSearchServer.java
	> .//Server.java
	> .//TestDocSearch.java


  	find ./ -type f -not -name "*.txt"
   	> .//FileHelpers.class
	> .//URLHandler.class
	> .//DocSearchServer.java
	> .//count-txts.sh
	> .//ServerHttpHandler.class
	.
 	.

The first command looks for all ".java" files. The second command finds files that do not have the ".txt" extension, which can be handy when you want to exclude a certain file type from your search results​.

**3. Find Files by Type (-type)**
You can find files of a specific type using this option.

	find ./technical -type d

	find ./technical -type f -exec chmod 0644 {} \;

![Screenshot 2023-11-05 at 9 26 24 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/20f6bb8d-cee4-41f2-b18c-bd35f2282066)

The first command finds all directories within ./technical. The second changes the permissions of all files to 644, which might be part of a script to set standard file permissions​.

**4. Find Files by Size (-size)**
This option locates files based on their size.

	find ./technical -type f -size +50k

![Screenshot 2023-11-05 at 10 04 07 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/2612f669-0792-43de-9780-5a9cbcf532b0)


	find ./technical -type f -size -1k

![Screenshot 2023-11-05 at 10 05 34 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/514c44df-0e4d-445b-9f23-845041aa8239)


The first command finds files larger than 50 kilobytes, useful for identifying large files that may need to be cleaned up. The second command finds files smaller than 1 kilobytes, which could be useful for identifying files that are not large enough to be a certain type of data file, like video or database dumps.
