# 🍔 Swiggy Automation

An end-to-end Selenium WebDriver automation script that simulates a complete food ordering workflow on Swiggy - from login to checkout.

## 📋 Overview

This Java-based automation project demonstrates the complete user journey on the Swiggy food delivery platform, including authentication, location setup, restaurant search, cart management, and checkout process. The script uses Selenium WebDriver to interact with web elements and simulate real user behavior.

## ✨ Features

- **User Authentication**: Automated login with phone number and manual OTP entry
- **Location Management**: Set delivery location with area search and selection
- **Restaurant Search**: Search for specific restaurants and browse menus
- **Cart Operations**: Add items to cart and modify quantities
- **Address Management**: Add and save delivery addresses with custom details
- **Checkout Flow**: Navigate through the complete checkout process to payment page
- **Smart Waits**: Strategic thread sleeps for page loading and element rendering
- **JavaScript Execution**: Page scrolling using JavascriptExecutor
- **Actions Class**: Advanced interactions using Selenium Actions

## 🛠️ Technologies Used

- **Java** - Core programming language
- **Selenium WebDriver** - Browser automation framework
- **ChromeDriver** - Chrome browser automation
- **Maven** - Build and dependency management

## 📦 Prerequisites

Ensure you have the following installed:

- **Java Development Kit (JDK)** 8 or higher
- **Maven** 3.6+
- **Google Chrome** (latest version)
- **ChromeDriver** (matching your Chrome version)
- Active internet connection
- Valid Swiggy account with registered phone number

## 🔧 Installation

1. **Clone the repository**:
```bash
git clone https://github.com/atayashraf/SwiggyAutomation.git
cd SwiggyAutomation
```

2. **Install dependencies**:
```bash
mvn clean install
```

3. **Configure ChromeDriver**:
   - Download ChromeDriver from [https://chromedriver.chromium.org/](https://chromedriver.chromium.org/)
   - Add ChromeDriver to your system PATH, or
   - Set the driver path in code:
   ```java
   System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
   ```

## 💻 Usage

### Configuration

Before running the script, update the following variables in `SwiggyAutomation.java`:

```java
String phoneNumber = "9876543210";          // Your registered phone number
String deliveryLocation = "Bengaluru";      // Your city/location
String restaurantName = "Domino's Pizza";   // Restaurant to search
String doorFlatNumber = "101, Tech Park";   // Flat/Door number
String landmark = "Near Main Road";         // Nearby landmark
```

### Running the Automation

**Option 1: Using Maven**
```bash
mvn exec:java -Dexec.mainClass="org.example.SwiggyAutomation"
```

**Option 2: Using IDE**
- Open the project in IntelliJ IDEA or Eclipse
- Navigate to `SwiggyAutomation.java`
- Right-click and select "Run"

**Option 3: Command Line**
```bash
javac -cp "path/to/selenium-jars/*" src/main/java/org/example/SwiggyAutomation.java
java -cp "path/to/selenium-jars/*:src/main/java" org.example.SwiggyAutomation
```

### Manual Intervention Required

⚠️ **OTP Entry**: The script pauses for 15 seconds during login to allow manual OTP entry in the browser. Enter the OTP you receive via SMS/email when prompted.

## 🎯 Automation Workflow

The script executes the following steps:

### Step 1: Login 🔐
- Opens Swiggy homepage
- Clicks on login button
- Enters phone number
- Waits for manual OTP entry (15 seconds)
- Submits OTP

### Step 2: Set Delivery Location 📍
- Clicks on location selector
- Searches for specified city
- Selects location from suggestions
- Skips detailed address entry

### Step 3: Search Restaurant 🔍
- Navigates to search page
- Enters restaurant name
- Selects restaurant from results
- Opens restaurant menu

### Step 4: Add to Cart 🛒
- Scrolls to menu items
- Adds item to cart
- Handles customization popups

### Step 5: Manage Cart 📦
- Views cart
- Increases item quantity
- Handles repeat order prompts

### Step 6: Enter Delivery Address 🏠
- Adds new delivery address
- Enters flat/door number
- Adds landmark
- Selects address type (Home)
- Saves address

### Step 7: Proceed to Payment 💳
- Navigates to checkout
- Reaches payment page
- Closes browser

## 📁 Project Structure

```
SwiggyAutomation/
│
├── src/
│   └── main/
│       └── java/
│           └── org/
│               └── example/
│                   └── SwiggyAutomation.java
│
├── pom.xml
└── README.md
```

## 🧪 XPath Locators Used

The script uses XPath for element identification:
- Login button
- Phone input field
- Location search box
- Restaurant search
- Cart buttons
- Address form fields
- Payment checkout button

## ⚙️ Key Components

### WebDriver Initialization
```java
WebDriver driver = new ChromeDriver();
driver.manage().window().maximize();
```

### JavascriptExecutor for Scrolling
```java
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript("window.scrollBy(0,1250)");
```

### Actions Class for Complex Interactions
```java
Actions actions = new Actions(driver);
actions.moveToElement(skipAddress).click().perform();
```

## ⚠️ Important Notes

- **Manual OTP Entry**: The script requires manual OTP input during login
- **XPath Dependency**: Uses absolute XPaths which may break if Swiggy updates their UI
- **Wait Times**: Uses `Thread.sleep()` for synchronization (not recommended for production)
- **Single Session**: Script runs once and closes the browser
- **Network Dependent**: Requires stable internet connection

## 🔮 Future Enhancements

- [ ] Implement explicit waits (WebDriverWait) instead of Thread.sleep()
- [ ] Use relative XPaths or CSS selectors for better stability
- [ ] Add error handling and try-catch blocks
- [ ] Implement Page Object Model (POM) design pattern
- [ ] Add TestNG/JUnit for test execution and reporting
- [ ] Create properties file for configuration
- [ ] Add screenshot capture on failures
- [ ] Implement logging framework (Log4j)
- [ ] Add support for multiple browsers
- [ ] Create automated OTP handling (if API available)

## 🐛 Troubleshooting

**Issue**: `ElementNotInteractableException`
- **Solution**: Increase wait times or check if element is visible/enabled

**Issue**: `NoSuchElementException`
- **Solution**: Verify XPath is correct and element exists on the page

**Issue**: ChromeDriver version mismatch
- **Solution**: Download ChromeDriver matching your Chrome browser version

**Issue**: OTP timeout
- **Solution**: Increase the wait time beyond 15 seconds if needed

## 📝 Dependencies

Add to your `pom.xml`:

```xml
<dependencies>
    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>4.15.0</version>
    </dependency>
</dependencies>
```

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -m 'Add improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

## 📜 License

This project is for educational purposes only. Ensure compliance with Swiggy's Terms of Service and robots.txt before use.

## 👤 Author

**Atay Ashraf**
- GitHub: [@atayashraf](https://github.com/atayashraf)


## ⚖️ Disclaimer

This automation script is created for educational and testing purposes only. Users should:
- Have explicit permission to automate the website
- Comply with Swiggy's Terms of Service
- Not use for unauthorized activities or load testing
- Respect rate limits and fair usage policies

---
