# AgriChain

Problem 1 : Program for following:
Given a string, find the length of the longest substring without repeating characters. For example, the longest substring without repeating letters for "abcabcbb" is "abc", which the length is 3. For "bbbbb" the longest substring is "b", with the length of 1

Answer 1 : In JAVA Language 

package basicprogram;
 
import java.util.HashSet;
 
public class LongesrSubstring
{
	 public static int lengthOfLongestSub(String p)
		    {
		        int m = p.length();
		        int maxLength = 0;
		        int left = 0;
		        HashSet<Character> set = new HashSet<>();
		
 for (int right = 0; right < m; right++)
		        {
		            while (set.contains(p.charAt(right)))
		            {
		                set.remove(p.charAt(left));
		                left++;
		            }
		            set.add(p.charAt(right));
		            maxLength = Math.max(maxLength, right - left + 1);
		        }
		
  return maxLength;
		    }
		
 public static void main(String[] args) {
		        String input1 = "abcabcbb";
		        String input2 = "bbbbb";
		       
		
  System.out.println("abcabcbb \"" + input1 + "\": " + lengthOfLongestSub(input1));
  System.out.println("bbbbb \"" + input2 + "\": " + lengthOfLongestSub(input2));
		    }
}

Output 

abcabcbb "abcabcbb": 3
bbbbb "bbbbb": 1




Program 2 : Assume there is a website https://agrichain.com which does exactly the same thing as problem 1, it takes the input on home page and then on click of submit button, it navigates to different page where it prints the output for longest substring without repeating letters.
