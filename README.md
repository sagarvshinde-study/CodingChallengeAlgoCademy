import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;

public class MyClass {
    
   
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
   
     
     // This is actual for loop and logic to print the rhobus of * 
     //int starCountInRow = 0;
     int cursorStarCount = 0;
     int minSize= totalRows/2;
     int starArray[] = new int[100];  // array to maintain count of *'s in each row, will be updated run time and then will be traversed reverse as well 
     int getStarsCount = 0;
     boolean maxLimitReached = false;
     
      for(int j=0; j<totalRows;j++){  
          // k is for printing * on each row and is set to 0 initially and will be calculated subsequently at run time like 1, 3, 5, 3
          int k=0;
          // This gives the stars count to be printed in each row - based on index j 
           
           if(!maxLimitReached){
                int starCountInRow = j *2+1;
                starArray[cursorStarCount] = starCountInRow; 
                cursorStarCount++;
                if(cursorStarCount>totalRows/2) 
                    maxLimitReached = true;
               
           }
            else { // since max limit of * is printed, so start reducing counter to get next actual stars in next each row 
               
               //Only once reduce the cursor by 2 and then subsequently by 1     1 3 5 3 1     1 3 5 7 9 7 5 3 1 
               if (cursorStarCount> totalRows/2)
                  cursorStarCount = cursorStarCount -2;
                else{
                    maxLimitReached = true;
                    cursorStarCount = cursorStarCount -1;
                
                    
                }
            }    
           /* keep on storing the count of * values in array using index j
              until j <= totalRows/2. As soon as j becomes greater remember that 
              maximum * row is printed. And we have to traverse array back 
              to display lower part of Rhombus
            */
            if(j<=totalRows/2)
              getStarsCount = starArray[j];  
            else{
                maxLimitReached = true;
                getStarsCount = starArray[cursorStarCount];   
            }
              
       
        //    System.out.println("Total star count:"+ getStarsCount);
          int spacesInRows = totalRows-getStarsCount;
        //  System.out.println("Total spaces in row:"+ spacesInRows +"\n");
          
        //  System.out.println("Starting row:"+ j);
        
        // This loop is for preceding spaces
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
          /* This loop is for following spaces. You can either use same variable spl and decrement it 
             OR you can start again with fresh variable and display remaining trailing spaces with same for loop as above of preceding spaces 
          */
          
        /*
          for(;spl>0;spl--){
            System.out.print(">");
          }
        */ 
          /* Use above for loop OR you can use below for loop with fresh variable for trailing spaces */
          
          for(spl=0;spl<spacesInRows/2;spl++){
            System.out.print("<");     // changing this symbol to < from >, just for a different look 
          }
          
        System.out.println("");
      }   
    
    }
}
