# Lab Report 3: Feb 13, 2024

* [Part 1: Bugs](#part-1)
* [Part 2: Researching Commands](#part-2)

## Part 1: Bugs <a name="part-1"></a>

* A failure-inducing input for the buggy program  
  ```java
  @Test
    public void testReverseInPlaceFail() {
      int[] input1 = { 3, 4, 5 };
      ArrayExamples.reverseInPlace(input1);
      assertArrayEquals(new int[] { 5, 4, 3 }, input1);
    }
  ```

* An input that doesn't induce a failure, as a JUnit test and any associated code  
  ```java
  @Test
    public void testReverseInPlacePass() {
      int[] input1 = { 5, 6, 6, 5 };
      ArrayExamples.reverseInPlace(input1);
      assertArrayEquals(new int[] { 5, 6, 6, 5 }, input1);
    }
  ```

* The symptom, as the output of running the tests  
  <img src="./img/lab3-junit.png" alt="screenshot of running tests" width="700"/>

* The bug, as the before-and-after code change required to fix it

  * Before:

    ```java
    static void reverseInPlace(int[] arr) {
      for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
      }
    }
    ```

  * After: 

    ```java
    static void reverseInPlace(int[] arr) {
      for (int i = 0; i < arr.length / 2; i += 1) {
        int temp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = temp;
      }
    }
    ```
    
  Using a temporary variable prevents the previous value of `arr[i]` from being lost after `arr[i]` is reassigned to `arr[arr.length - i - 1]`.
  Additionally, `i < arr.length` is changed to `i < arr.length / 2` so that the pairs of elements being swapped are only swapped once instead of twice.


  ## Part 1: Researching Commands <a name="part-2"></a>

  
