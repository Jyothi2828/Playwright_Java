# Playwright Java Example: Launch Chrome Browser

This project demonstrates how to use **Playwright with Java** to launch the Chrome browser, navigate to a website, and retrieve the page title.

## Prerequisites

Make sure you have installed:

- Java (JDK 11 or later)
- Maven
- Eclipse or any Java IDE
- Playwright Java dependencies (can be added via Maven)

## Adding Playwright Dependency

1. Open `pom.xml` by expanding the folder structure in your project.
2. Search and navigate to the `<dependencies>` tag in `pom.xml` .
3. Add the following dependency:

```xml
<!-- https://mvnrepository.com/artifact/com.microsoft.playwright/playwright -->
<dependency>
    <groupId>com.microsoft.playwright</groupId>
    <artifactId>playwright</artifactId>
    <version>1.52.0</version>
</dependency>
```
4. Update the Maven project to apply the changes.

## Code Example

## Under `src/main/java` or `src/test/java` create a package named `TC01_LaunchChrome` , copy the below code and paste into the `TC01_LaunchChrome` package , and execute the program.


```java
package TC01_LaunchChrome;

import com.microsoft.playwright.*;

public class Demo {

    public static void main(String[] args) {

        // Create Playwright object
        Playwright pw = Playwright.create();

        // Get the Chromium browser type
        BrowserType browserType = pw.chromium();

        // Set launch options
        BrowserType.LaunchOptions options = new BrowserType.LaunchOptions();
        options.setChannel("chrome"); // Use Chrome browser
        options.setHeadless(false);   // Open browser in non-headless mode

        // Launch browser with options
        Browser browser = browserType.launch(options);

        // Create a new page
        Page page = browser.newPage();

        // Navigate to URL
        page.navigate("https://www.google.com");

        // Print page title
        System.out.println("Page title: " + page.title());

        // Close browser and Playwright
        browser.close();
        pw.close();
    }
}
```

The Chrome browser will launch and navigate to Google, and the title will be printed in the console.
