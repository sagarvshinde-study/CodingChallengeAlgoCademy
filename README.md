
//This is the repository for solving coding challenge of AlgoCademy

import java.io.BufferedReader;

import java.io.InputStreamReader;

import java.util.Arrays;

public class MyClass {
    
    // This method is to get an array which tells how many stars will be present in each row. Every index of an array 
    // will tell then of starts in particular row 
    public static int[] reverseArray(int a[],int n){
        
        int[] b = a;
        int j = n-1;
        System.out.println("\n n/2 is:" + n/2);
        
        for (int i = 0; i <n/2; i++) {
            System.out.println("j" +j);
            b[j] = a[i];
            j = j - 1;
        }
        System.out.println("\n Before return b array is:" + Arrays.toString(b));     
        return b;
    }
    
    
    public static void main(String args[]) {
      int totalRows=0;    
      String s="";
      
      System.out.println("Enter odd positive integer");
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      try{
         s = br.readLine();  
      }catch(Exception e) {
        System.out.println("Exception");  
      }
      System.out.println("Total Number of rows entered by user: "+s);
      totalRows = Integer.parseInt(s);
      System.out.println("Total Number of rows entered by user int: "+ totalRows);
   
    // Declare array for total positive odd integer entered by user
     int arr[] = new int[totalRows];
    
     // Create an array of odd integers
     int cnt = 0;
     for(cnt = 0; cnt !=totalRows; cnt++){
         if ((2*cnt+1)>totalRows)  // Any number * 2 + 1 is always an odd number. 
                  break;
         else{
             arr[cnt] = 2 * cnt + 1;
         }
        System.out.print("\t"+ arr[cnt]);
    }
    
    // Reverese original array with length -1. This is required to get full array which gives number of starts to be printed in each row 
        int b[] = reverseArray(arr, arr.length);
        
        arr = b; // reinitialising arr with full array for * printing 
     
     // This is actual for loop and logic to print the rhobus of * 
     
      for(int j=0; j<arr.length;j++){  
          int k=0;
          // This gives the starts count to be printed in each row - based on index j 
          int getStarsCount = arr[j];
      
        //    System.out.println("Total star count:"+ getStarsCount);
          int spacesInRows = totalRows-getStarsCount;
        //  System.out.println("Total spaces in row:"+ spacesInRows +"\n");
          
        //  System.out.println("Starting row:"+ j);
        
        // This is the counter for preceding and trailing spaces 
          int spl=0;
          //This loop is for preceeding spaces
          for(spl=0; spl<spacesInRows /2 ;spl++){
            System.out.print(">");
          }
          // print all the * in the row
          while(k<getStarsCount){  
            System.out.print("*");
            k++;
          }
          //This loop is for following spaces
          for(;spl>0;spl--){
            System.out.print(">");
          }
        System.out.println("");
      }   
    
    }
}
