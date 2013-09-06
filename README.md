
/**
 * Readin a text file, the name of which is given on the command line, 
 * and output information regarding the relative frequency of the words in some way. 
 * At the upper-end of functionality, that would be an html file in which the words are 
 * larger if they are more frequent and smaller if they are less frequent..
 * 
 * @title Word Count
 * @purpose Counting the relative frequency of the words in the file
 * @author Angie Ashok
 * @version 4 September 2013
 * @userInstructions pass a file which has some content, not an empty file
 * @howToStart java word c:\filename (path of the file location). change the '\' with '\\'
 * e.g. C:\\angie\\docs\\somefile.txt and the file contains values like i am smart smart person
 */
import java.io.File;
import java.util.Scanner;
import java.io.IOException;
import java.util.Map;
import java.util.HashMap;
public class Word
{
    
    /**
     * echo the given file
     * @parm the scanner for the file 
     * Counting the words of how many times it is used
     * 
     * 
     *
     */
    public void readIt(Scanner inFile)
    {
        Map<String, Integer> wordCounts = new HashMap<String, Integer>();
        int counter = 0;
        while (inFile.hasNext())
            {
                String word = inFile.next();
                //System.out.println("WORD: " + word);
                if (wordCounts.containsKey(word)){
                    counter = wordCounts.get(word);
                    wordCounts.put(word, counter + 1);
                    //System.out.println(wordCounts);
                    
                }
                else{
                    wordCounts.put(word, 1);
                }
            }
        System.out.println(wordCounts.size());
        System.out.println(wordCounts);
    }
    public static void main (String[] args)
    {
        if (args.length < 1) {
            //System.out.println("Are you sure you want to read this");
            System.out.println("Please pass in a file to read");
        }
        else {
            Word word = new Word(); // creating an instance/object of Word class
            File fileToRead = new File(args[0]);
            try {
                Scanner in = new Scanner(fileToRead);
                word.readIt(in);
            }catch(IOException e){
                System.out.println("Duh, File Error!"+ e);
            }
        }   
    }
    
}
