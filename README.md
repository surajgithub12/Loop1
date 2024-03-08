# Loop_1


public class ReversalsTotalValidationTest {
    public static void main(String[] args) {
        // Setting system properties for ChromeDriver
        System.setProperty("webdriver.chrome.driver", "/path/to/your/chromedriver");

        // Initialize WebDriver
        WebDriver driver = new ChromeDriver();

       // Navigate to login page   
        driver.get("https://app.tryloop.ai/login/password");
       // Login with valid credentials
        driver.findElement(By.xpath("//input[@type='text']").sendkeys("qa-engineer-assignment@test.com");
        driver.findElement(By.xpath("//input[@type='password']").sendkeys("QApassword123$");
        
        // Login button
        driver.findElement(By.xpath("//button[@margin='normal']").click();
        
        // Navigate to the URL
       // driver.get("https://app.tryloop.ai/chargebacks/stores/view");

        // Or navigate using sidebar
        WebElement 3pChargebacks = driver.findElement(By.xpath("(//span[@class='MuiTypography-root MuiTypography-body1 MuiListItemText-primary css-18euqpt'])[2]"));
        3pChargebacks.click();
        WebElement historyByStore = driver.findElement(By.xpath("(//span[@class='MuiTypography-root MuiTypography-body1 MuiListItemText-primary css-18euqpt'])[5]"));
        historyByStore.click();

         Thread.sleep(4000);

         // Find the Reversals dropdown

         WebElement dropdown = driver.findElement(By.xpath("//div[@class='MuiInputBase-root MuiInput-root MuiInput-underline MuiInputBase-colorPrimary MuiInputBase-formControl  css-1td1g78']")).click();
         
        Select d = new Select(dropdown);
        d.selectByVisibleText("Reversals");

        

        

         

         

