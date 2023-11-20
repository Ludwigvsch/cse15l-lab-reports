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


	java -cp ..:lib/hamcrest-core-1.3.jar..:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
	JUnit version 4.13.2
	.E
	Time: 0,001
	There was 1 failure:
	1) initializationError(org.junit.runner.JUnitCommandLineParseResult)
	java.lang.IllegalArgumentException: Could not find class [ArrayTests]
		at org.junit.runner.JUnitCommandLineParseResult.parseParameters(JUnitCommandLineParseResult.java:100)
		at org.junit.runner.JUnitCommandLineParseResult.parseArgs(JUnitCommandLineParseResult.java:50)
		at org.junit.runner.JUnitCommandLineParseResult.parse(JUnitCommandLineParseResult.java:44)
		at org.junit.runner.JUnitCore.runMain(JUnitCore.java:72)
		at org.junit.runner.JUnitCore.main(JUnitCore.java:36)
	Caused by: java.lang.ClassNotFoundException: ArrayTests
		at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:641)
		at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:188)
		at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:526)
		at java.base/java.lang.Class.forName0(Native Method)
		at java.base/java.lang.Class.forName(Class.java:534)
		at java.base/java.lang.Class.forName(Class.java:513)
		at org.junit.internal.Classes.getClass(Classes.java:42)
		at org.junit.internal.Classes.getClass(Classes.java:27)
		at org.junit.runner.JUnitCommandLineParseResult.parseParameters(JUnitCommandLineParseResult.java:98)
		... 4 more
	
	FAILURES!!!
	Tests run: 2,  Failures: 1

 
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

**2. Find Files by Modification Time (-mtime)**
This option allows you to find files based on when they were last modified.

Finds files in ./reports that were modified within the last 10 days.

	find ./technical -type f -mtime -30
	./technical/government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
	./technical/government/About_LSC/Progress_report.txt
	./technical/government/About_LSC/Strategic_report.txt
	./technical/government/About_LSC/Comments_on_semiannual.txt
	./technical/government/About_LSC/Special_report_to_congress.txt
	./technical/government/About_LSC/CONFIG_STANDARDS.txt
	./technical/government/About_LSC/commission_report.txt
	./technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt
	./technical/government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
	./technical/government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt
	./technical/government/About_LSC/diversity_priorities.txt
	./technical/government/About_LSC/reporting_system.txt
	./technical/government/About_LSC/State_Planning_Report.txt
	./technical/government/About_LSC/Protocol_Regarding_Access.txt
	./technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt
	./technical/government/About_LSC/conference_highlights.txt
	./technical/government/About_LSC/State_Planning_Special_Report.txt
	./technical/government/Env_Prot_Agen/multi102902.txt
	./technical/government/Env_Prot_Agen/section-by-section_summary.txt
 	.
  	.
   	.

Searches ./technical for files last modified more than 10 days ago.

  	find ./technical -type f -mtime +10
	./technical/government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
	./technical/government/About_LSC/Progress_report.txt
	./technical/government/About_LSC/Strategic_report.txt
	./technical/government/About_LSC/Comments_on_semiannual.txt
	./technical/government/About_LSC/Special_report_to_congress.txt
	./technical/government/About_LSC/CONFIG_STANDARDS.txt
	./technical/government/About_LSC/commission_report.txt
	./technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt
	./technical/government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
	./technical/government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt
	./technical/government/About_LSC/diversity_priorities.txt
	./technical/government/About_LSC/reporting_system.txt
	./technical/government/About_LSC/State_Planning_Report.txt
	./technical/government/About_LSC/Protocol_Regarding_Access.txt
	./technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt
	./technical/government/About_LSC/conference_highlights.txt
	./technical/government/About_LSC/State_Planning_Special_Report.txt
	./technical/government/Env_Prot_Agen/multi102902.txt
	./technical/government/Env_Prot_Agen/section-by-section_summary.txt
	./technical/government/Env_Prot_Agen/jeffordslieberm.txt
	./technical/government/Env_Prot_Agen/final.txt
	./technical/government/Env_Prot_Agen/ctf7-10.txt
 	.
  	.
   	.

Using `-mtime` is particularly useful for locating files that have been recently updated or to clean up old files that haven't been modified for a long period.

**3. Find Files by Type (-type)**
You can find files of a specific type using this option.

	find ./technical -type d
 
Second command:

	find ./technical -type f -exec chmod 0644 {} \;

Output:

	find ./technical -type d
	./technical
	./technical/government
	./technical/government/About_LSC
	./technical/government/Env_Prot_Agen
	./technical/government/Alcohol_Problems
	./technical/government/Gen_Account_Office
	./technical/government/Post_Rate_Comm
	./technical/government/Media
	./technical/plos
	./technical/biomed
	./technical/911report
 
 Second command Output:
 
	find ./technical -type f -exec chmod 0644 {} \;

  	

The first command finds all directories within ./technical. The second changes the permissions of all files to 644, which might be part of a script to set standard file permissions​.

**4. Find Files by Size (-size)**
This option locates files based on their size.

	find ./technical -type f -size +50k

 Output:

	 find ./technical -type f -size +50k
	./technical/government/About_LSC/Strategic_report.txt
	./technical/government/About_LSC/commission_report.txt
	./technical/government/About_LSC/State_Planning_Report.txt
	./technical/government/Env_Prot_Agen/multi102902.txt
	./technical/government/Env_Prot_Agen/section-by-section_summary.txt
	./technical/government/Env_Prot_Agen/jeffordslieberm.txt
	./technical/government/Env_Prot_Agen/ctf7-10.txt
	./technical/government/Env_Prot_Agen/ctf1-6.txt
	./technical/government/Env_Prot_Agen/ctm4-10.txt
	./technical/government/Env_Prot_Agen/atx1-6.txt
	./technical/government/Env_Prot_Agen/bill.txt
	./technical/government/Env_Prot_Agen/tech_adden.txt
	./technical/government/Alcohol_Problems/Session3-PDF.txt
	./technical/government/Alcohol_Problems/Session4-PDF.txt
	./technical/government/Gen_Account_Office/d0269g.txt
	./technical/government/Gen_Account_Office/Testimony_cg00010t.txt
	./technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
	./technical/government/Gen_Account_Office/Sept27-2002_d02966.txt
	./technical/government/Gen_Account_Office/d01376g.txt
	./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
	./technical/government/Gen_Account_Office/pe1019.txt
	./technical/government/Gen_Account_Office/gg96118.txt
	./technical/government/Gen_Account_Office/July11-2001_gg00172r.txt
	./technical/government/Gen_Account_Office/d03419sp.txt
	./technical/government/Gen_Account_Office/Sept14-2002_d011070.txt
	./technical/government/Gen_Account_Office/d03232sp.txt
	./technical/government/Gen_Account_Office/June30-2000_gg00135r.txt
	./technical/government/Gen_Account_Office/d01591sp.txt
	./technical/government/Gen_Account_Office/Oct15-2001_d0224.txt
	./technical/government/Gen_Account_Office/im814.txt
	./technical/government/Gen_Account_Office/ai00134.txt
	./technical/government/Gen_Account_Office/Testimony_Jul17-2002_d02957t.txt
	./technical/government/Gen_Account_Office/ai9868.txt
	./technical/government/Gen_Account_Office/May1998_ai98068.txt
	./technical/government/Gen_Account_Office/d02701.txt
	./technical/government/Gen_Account_Office/ai2132.txt
	./technical/government/Post_Rate_Comm/Mitchell_6-17-Mit.txt
	./technical/biomed/1476-069X-2-4.txt
	./technical/biomed/gb-2003-4-5-r34.txt
	./technical/biomed/gb-2002-3-9-research0043.txt
	./technical/biomed/gb-2001-2-7-research0025.txt
	./technical/biomed/1471-2253-2-5.txt
	./technical/biomed/gb-2003-4-4-r26.txt
	./technical/biomed/1477-7827-1-13.txt
	./technical/biomed/gb-2003-4-7-r42.txt
	./technical/biomed/1471-2121-3-16.txt
	./technical/biomed/gb-2001-2-11-research0046.txt
	./technical/biomed/gb-2002-3-7-research0036.txt
	./technical/biomed/gb-2003-4-7-r43.txt
	./technical/biomed/1471-2121-3-15.txt
	./technical/biomed/gb-2002-3-9-research0045.txt
	./technical/biomed/1472-6904-2-5.txt
	./technical/biomed/gb-2002-3-11-research0059.txt
	./technical/biomed/gb-2002-3-11-research0065.txt
	./technical/biomed/1472-6807-3-1.txt
	./technical/biomed/1471-213X-3-3.txt
	./technical/biomed/1472-6904-3-1.txt
	./technical/biomed/1476-072X-2-4.txt
	./technical/biomed/gb-2003-4-2-r14.txt
	./technical/biomed/1471-2105-2-8.txt
	./technical/biomed/gb-2002-3-12-research0079.txt
	./technical/biomed/1471-2091-3-31.txt
	./technical/biomed/gb-2002-3-12-research0086.txt
	./technical/biomed/1471-2105-3-14.txt
	./technical/biomed/gb-2002-3-12-research0083.txt
	./technical/biomed/gb-2003-4-3-r17.txt
	./technical/biomed/gb-2002-3-12-research0072.txt
	./technical/biomed/1475-4924-1-10.txt
	./technical/biomed/1476-511X-1-2.txt
	./technical/biomed/gb-2002-3-12-research0071.txt
	./technical/biomed/1471-2105-3-18.txt
	./technical/biomed/1471-2121-2-10.txt
	./technical/biomed/1471-2202-3-1.txt
	./technical/biomed/1471-2091-3-14.txt
	./technical/biomed/gb-2001-3-1-research0001.txt
	./technical/biomed/gb-2002-3-12-research0088.txt
	./technical/biomed/1471-2121-3-25.txt
	./technical/biomed/1472-6882-1-10.txt
	./technical/biomed/1471-2210-1-7.txt
	./technical/biomed/1471-2121-3-30.txt
	./technical/biomed/gb-2002-3-10-research0052.txt
	./technical/biomed/gb-2003-4-2-r9.txt
	./technical/biomed/1471-2091-3-4.txt
	./technical/biomed/1471-2105-3-2.txt
	./technical/biomed/1471-2164-4-4.txt
	./technical/biomed/1477-7827-1-36.txt
	./technical/biomed/1471-2199-2-4.txt
	./technical/biomed/1476-069X-2-9.txt
	./technical/911report/chapter-13.4.txt
	./technical/911report/chapter-13.5.txt
	./technical/911report/chapter-13.1.txt
	./technical/911report/chapter-13.2.txt
	./technical/911report/chapter-13.3.txt
	./technical/911report/chapter-3.txt
	./technical/911report/chapter-2.txt
	./technical/911report/chapter-1.txt
	./technical/911report/chapter-5.txt
	./technical/911report/chapter-6.txt
	./technical/911report/chapter-7.txt
	./technical/911report/chapter-9.txt
	./technical/911report/chapter-8.txt
	./technical/911report/chapter-12.txt
	./technical/911report/chapter-11.txt


Second command:

	find ./technical -type f -size -1k


Output:

	find ./technical -type f -size -1k
	./technical/plos/pmed.0020191.txt
	./technical/plos/pmed.0020226.txt

The first command finds files larger than 50 kilobytes, useful for identifying large files that may need to be cleaned up. The second command finds files smaller than 1 kilobytes, which could be useful for identifying files that are not large enough to be a certain type of data file, like video or database dumps.
