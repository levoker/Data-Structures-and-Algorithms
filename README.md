# Data-Structures-and-Algorithms

Algorithms and notes from Data Structures and Algorithms: Deep Dive Using Java by Sarah Ettritch  

//Bubble Sort in Java

public class Main {

    public static void main(String[] args) {

        int[] intArray = {10, 38, 45, 22, -18, 17, 84};

        for (int lastUnsortedIndex = intArray.length - 1; lastUnsortedIndex > 0; lastUnsortedIndex--) {

            for (int i = 0; i < lastUnsortedIndex; i++) {
                if (intArray[i] > intArray[i + 1]) {
                    swap(intArray, i, i+1);
                }
            }
        }

        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }
    }

    //we use static because we are going be calling it from the Main method.
    public static void swap(int[] array, int i, int j) {

        if (i == j) {
            return;
        }

        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;

    }
}

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

// Selection Sort in Java

// Sort in ascending order
// quadratic algorithm O(n^2)


public class Main {

    public static void main(String[] args) {

        int[] intArray = {10, 30, 45, -16, 12, 7 };

        for (int lastUnsortedIndex = intArray.length - 1; lastUnsortedIndex > 0; lastUnsortedIndex--) {

            int largest = 0;

            for (int i = 1; i <= lastUnsortedIndex; i++) {
                if (intArray[i] > intArray[largest]) {
                    largest = i;
                }
            }

            swap(intArray, largest, lastUnsortedIndex);

        }

        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }

    }

    public static void swap(int[] array, int i, int j) {

        if (i == j) {
            return;
        }

        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;

    }

}

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

//Insertion Sort

//quadratic algorithm O(n^2)

//Sort in ascending order

//Stable algorithm




public class Main {

    public static void main(String[] args) {

        int[] intArray = {18, 35, 10, -15, 60, 3, 66};
        // outer loop is to grow the sort of partition by one
        for (int firstUnsortedIndex = 1; firstUnsortedIndex < intArray.length; firstUnsortedIndex++) {
            // save the value we are going to insert into a new element
            int newElement = intArray[firstUnsortedIndex];
            // i declared outside of loop - index used to traverse the sorted partition from right to left.
            int i;
            // inner loop used to traverse the sorted partition and look for the correct position to insert the element and to do the shifting
            for (i = firstUnsortedIndex; i > 0 && intArray[i - 1] > newElement; i--) {
                // shift element from left to right
                intArray[i] = intArray[i - 1];
            }
            // assign intArray[i] with newElement
            intArray[i] = newElement;

        }
        // print intArray
        for (int i = 0; i < intArray.length; i++) {
            System.out.println(intArray[i]);
        }
    }
}

/*Notes:

inner loop - if we haven't hit the front of the array, and if the element[i-1] is greater than the element we are inserting. If that's the case we want to shift the element at i-1 to the right because we need to make room for new element

*/

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

//Shell Sort

//In-place algorithm

// time complexity depends on gap; does not require as much shifting as insertion sort

//unstable algorithm

public class Main {

    public static void main(String[] args) {

        int[] intArray = {20, 35, -15, 7 , 55, 1 , -22};

            //loop to initialize the gap value, and then reduce it on each iteration
            for (int gap = intArray.length / 2; gap > 0; gap /= 2) {

                //loop to compare and shift elements
                for (int i = gap; i < intArray.length; i++) {
                    int newElement = intArray[i];

                    //use j to do traversing
                    int j = i;

                    //inner loop to find correct position to insert
                    while (j >= gap && intArray[j -gap] > newElement) {
                        //shift element
                        intArray[j] = intArray[j - gap];

                        //used to compare new element with whatever comes x positions over
                        j -= gap;
                    }
                    //assign intArray[i] with newElement
                    intArray[j] = newElement;

                }
            }

            for (int i = 0; i < intArray.length; i++) {
                System.out.println(intArray[i]);
            }

    }
}



