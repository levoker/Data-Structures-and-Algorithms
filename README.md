# Data-Structures-and-Algorithms
Let's learn something fun!

//Bubble Sort in Java

public class Main {

    public static void main(String[] args) {

        int[] intArray = {10, 38, 45, 22, -18, 17, 84};

        for (int lastUnsortedIndex = intArray.length - 1; lastUnsortedIndex > 0; lastUnsortedIndex--) {

            for(int i =0; i < lastUnsortedIndex; i++) {
                if(intArray[i] > intArray[i + 1]) {
                    swap(intArray, i, i+1);
                }
            }
        }

        for(int i=0; i<intArray.length; i++) {
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
