# Week 5: Lab Report 3
### Colin Wang
## Part 1 - Bugs:
- For the `reversed` method in `ArrayExamples.java` this is a failure-inducing input:
```
@Test
public void testReversedBug() {
    int[] input = {1, 2, 3};
    assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input));
}
```
- For the `reversed` method in `ArrayExamples.java` this is an input that does not cause a failure:
```
@Test
public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
}
```
- Here is the output of the JUnit tests for these two: ![failure](Failure_output.png)
- Here is the original code with bug:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
}
```
- Here is the code with the bug fixed:
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
}
```
  This fixes the code because it actually uses the new array that is created to store the values in reverse. The original code only instantiates a new array, but then modifies and returns the original, which causes the incorrect behavior.

## Part 2 - Researching Commands:
# grep command options from [linuxcommand.org](https://linuxcommand.org/lc3_man_pages/grep1.html)
1. -r is an option for grep that recursively searches for the phrase under each directory.
- Example 1:
`grep -r "base pair" technical/biomed`
```
a lot of lines
biomed/grep-biomed.txt:gb-2002-3-12-research0079.txt:          98.7% of the base pairs are contained within 100-kb
biomed/grep-biomed.txt:gb-2002-3-12-research0079.txt:          and the total number of base pairs involved in those        
biomed/grep-biomed.txt:gb-2002-3-12-research0083.txt:            hundred base pairs, and the separation can be as much     
biomed/grep-biomed.txt:gb-2002-3-6-research0029.txt:          micro-exons, ranging from 3 to 25 base pairs (bp) in
biomed/grep-biomed.txt:gb-2003-4-4-r24.txt:        important considering that within a few hundred base pairs,
biomed/grep-biomed.txt:rr196.txt:          approximately 500 base pairs upstream of the stop codon,
biomed/rr196.txt:          approximately 500 base pairs upstream of the stop codon,
```
This command goes to recursively find the instances of the phrase "base pair" within the technical/biomed sub directory. This can be useful if you want to use * in the filepath to search any directories that meet a certain requirement.
- Example 2:
`grep -r "base pair" technical/plos > grep-plos.txt`
`no output`
This command gives no output because it instead redirects the outputs into a file called `grep-plos.txt`. This is very useful because we can then use other linux commands on the file like `wc`, instead of looking at a mass text output.