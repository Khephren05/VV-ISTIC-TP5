# Random Wikipedia walker

Using Selenium, create a small program that, starting from the main page https://www.wikipedia.org/, walks trough a sequence of random links and takes a snapshot of the last page.
The process is as follows:

 1. Navigate to the main page https://www.wikipedia.org/
 2. Select a random link in the page
 3. Navigate to the link
 4. Repeat steps 2 to 3 until you have visited 10 different pages
 5. Take a snapshot of the current page and save it

Include the code of the walker and the snapshot in this document.

## Answer

[Lien vers le code](../TP_SELENIUM_WALKER_V2/src/main/java/ExerciceUn)

```java
package ExerciceUn;

import io.github.bonigarcia.wdm.WebDriverManager;
import org.openqa.selenium.chrome.ChromeDriver;

import java.io.IOException;


public class MainApp {



    public static void main (String[] args) throws InterruptedException, IOException {
        WebDriverManager.chromedriver().setup();
        WalkyWalker myWalker = new WalkyWalker(new ChromeDriver(),"https://fr.wikipedia.org/wiki/Wikip%C3%A9dia:Accueil_principal");
        myWalker.walk(10);
    }


}
``` 
```java
package ExerciceUn;

import org.apache.commons.io.FileUtils;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

import java.io.File;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;
import java.util.Random;

public class WalkyWalker {
    WebDriver driver;
    String initLink;

    public WalkyWalker(WebDriver webyDriverou,String initLink ){
        this.driver= webyDriverou;
        this.initLink=initLink;
        this.driver.get(this.initLink);
    }

    public void walk(int amountOfJumps) throws IOException {
        Random randomito = new Random();
        for(int i = 0; i<amountOfJumps; i++){
                List<WebElement> allLinks = driver.findElements(new By.ByTagName("a"));
                int int_random = randomito.nextInt(allLinks.size());
                WebElement myLink =allLinks.get(int_random);
                try{
                    myLink.click();

                }catch (ElementNotInteractableException e){
                    i--;
                }
        }
        takeScreenShot();
    }

    public void takeScreenShot() throws IOException {
        File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
        FileUtils.copyFile(scrFile, new File("./screenshot.png"));
    }
}
```