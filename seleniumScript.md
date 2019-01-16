# mm_Exercise
selenium_Java_Example


 package pomdesign;

import static org.testng.Assert.assertEquals;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;

import io.github.bonigarcia.wdm.WebDriverManager;

import pages.ValueObjects;

public class ValueObjectTest {
WebDriver driver;
ValueObjects values;	
	
	@BeforeClass
	public void setUp() {
		
		WebDriverManager.chromedriver().setup();
		driver = new ChromeDriver();
		driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
		driver.get("https://www.exercise1.com/values ");
	}
  
	@Test 
	public void theRightCountOfValuesTest() {
		values = new ValueObjects (driver); 	
		assertEquals(values.Value1.getText(), "$122,365.24");
		assertEquals(values.Value2.getText(), "$599.00");
		assertEquals(values.Value3.getText(), "$850,139.99");
		assertEquals(values.Value4.getText(), "$23,329.50");
		assertEquals(values.Value5.getText(), "$566.27");
	}	
	@Test
	public void greaterThanZeroTest() {
		values = new ValueObjects (driver);

		String items [] = new String [] { values.Value1.getText() , values.Value2.getText(), values.Value3.getText(),values.Value4.getText(),values.Value5.getText() };
		
		for (int i = 0; i < items.length; i++) {
			
			int itemsResult = Integer.parseInt(items[i].replace(",", "."));
			
			//System.out.println(itemsResult);
			
			if (itemsResult >0) {
				
				Assert.assertTrue(true);
				
			}else {
				
				Assert.assertTrue(false);	
			}	
		}	
	}
	
	@Test
	public void totalBalanceTest () {
		values = new ValueObjects (driver);

		assertEquals(values.TotalBalance.getText(), "$1,000,000.00");
			
	}
	
	@Test
	public void sumOfValuesTest () {
		
		values = new ValueObjects (driver);
		
	
		String items [] = new String [] { values.Value1.getText() , values.Value2.getText(), values.Value3.getText(),values.Value4.getText(),values.Value5.getText() };
	
	int sum = 0;
	
	for (int i = 0; i < items.length; i++) {
		
		int itemsResult = Integer.parseInt(items[i].replace(",", "."));
		
		sum = sum + itemsResult;
		
		System.out.println(sum);	
	}	
		assertEquals(sum, "$1.000.000.00");	
	
	}
}







