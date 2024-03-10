# Loop_1


public class ReversalsTest {
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

        // Find all rows in the table
        List<WebElement> rows = driver.findElements(By.xpath("//table[@class='MuiTable-root css-l6sbfr-MuiTable-root']//tr"));

        // Initialize arrays to store monthly totals
        double[] monthlyTotals = new double[7];
        double[] grandTotalRow = new double[7];

        // Extract data from the table
        for (int i = 1; i <= 7; i++) { // Iterate through the 7 months
            for (int j = 1; j <= 9; j++) { // Iterate through the 9 locations
                // Find the cell corresponding to the location and month
                WebElement cell = driver.findElement(By.xpath("//table[@class='MuiTable-root css-l6sbfr-MuiTable-root']//tr[" + (j + 1) + "]/td[" + (i + 1) + "]"));
                // Remove non-numeric characters
                String cellText = cell.getText().replaceAll("[^0-9.]", ""); 
                // Parse cell value to double
                double value = cellText.isEmpty() ? 0 : Double.parseDouble(cellText); 
                // Add the value to the corresponding monthly total
                monthlyTotals[i - 1] += value; // Add the value to the corresponding monthly total
            }
        }

      // Extract Grand Total row data
        WebElement grandTotalRowElement = driver.findElement(By.xpath("(//table[@class='MuiTable-root css-l6sbfr-MuiTable-root']//tr)[13]"));
        List<WebElement> grandTotalCells = grandTotalRowElement.findElements(By.tagName("td"));
        for (int i = 1; i <= 7; i++) {
            String cellText = grandTotalCells.get(i).getText().replaceAll("[^0-9.]", ""); // Remove non-numeric characters
            grandTotalRow[i - 1] = Double.parseDouble(cellText); // Parse cell value to double
        }

        // Verify monthly totals with Grand Total row
        boolean dataConsistent = true;
        for (int i = 0; i < 7; i++) {
            if (monthlyTotals[i] != grandTotalRow[i]) {
                dataConsistent = false;
                break;
            }
        }

        if (dataConsistent) {
            System.out.println("Data is consistent. Monthly totals match Grand Total row.");
        } else {
            System.out.println("Data is inconsistent. Monthly totals do not match Grand Total row.");
        }

        // Close the WebDriver session
        driver.quit();
    }
}



         

         

