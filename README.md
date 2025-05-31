# AgriChain

Problem 1: Program for the following:
Given a string, find the length of the longest substring without repeating characters. For example, the longest substring without repeating letters for "abcabcbb" is "abc", which the length is 3. For "bbbbb", the longest substring is "b", with the length of 1

Answer 1: In the JAVA Language 

package basicprogram;
 
import java.util.HashSet;
 
public class LongestSubstring
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


############################################################################################################################################################################################

Program 2: Assume there is a website https://agrichain.com which does exactly the same thing as problem 1, it takes the input on the home page and then on click of submit button, it navigates to different page where it prints the output for the longest substring without repeating letters.

Answer 2. 

Manual Test Cases

Test Case ID	                       Description	                                                Expected Result
TC_01	                Verify UI alignment of input field and submit button	                 Elements should be properly aligned
TC_02                  	Check behavior when no internet connection	                         User should get browser error
TC_03	                Check responsiveness on mobile, tablet, and desktop	                 UI should adapt to screen size

Automation Test Cases

Test Case ID	                     Description	                                                Expected Result
TC_01	                  Input a valid string "abcabcbb" and submit	                          Output should be abc
TC_03	                  Input string with all unique characters "abcdef"	                  Output should be abcdef

Selenium Automation Framework Folder Structure (Maven + TestNG)

agrichain-automation/
│
├── pom.xml               → Project file to manage dependencies 
├── testng.xml            → Configuration file to run the test cases
│
├── src/
│   ├── main/
│   │   └── java/
│   │       ├── base/
│   │       │   └── BaseTest.java        → Contains setup and cleanup code (open/close browser)
│   │       │
│   │       ├── drivers/
│   │       │   └── DriverFactory.java   → Code to launch the browser (Chrome, Safari, etc.)
│   │       │
│   │       ├── pages/
│   │       │   ├── HomePage.java        → Page class for homepage (input, submit button)
│   │       │   └── ResultPage.java      → Page class for result page (shows output)
│   │       │
│   │       └── utils/
│   │           └── ConfigReader.java    → (Optional) To read from config file (like URL, browser)
│
│   └── test/
│       └── java/
│           └── tests/
│               └── DummyTest.java       → Sample test case to check output of input string



Web Automation Script (Java + Selenium + TestNG)

Test Case Automated: TC_01 - Input a valid string "abcabcbb" and verify output is "abc"

package drivers;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class DriverFactory {
    public static WebDriver driver;

    public static WebDriver initDriver() {
        driver = new ChromeDriver();
        driver.manage().window().maximize();
        return driver;
    }

    public static void quitDriver() {
        driver.quit();
    }
}


