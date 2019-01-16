# mm_Exercise
selenium_Java_Example


package pages;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.support.PageFactory;

public class ValueObjects {
	
	public ValueObjects (WebDriver driver) {
		
		PageFactory.initElements(driver, this);
		
	}
	
	@FindBy (id="txt_val_1")  
	public WebElement Value1;
	
	@FindBy (id="txt_val_2")
	public WebElement Value2;
	
	@FindBy (id="txt_val_3")
	public WebElement Value3;
	
	@FindBy (id="txt_val_4")
	public WebElement Value4;
	
	@FindBy (id="txt_val_5")
	public WebElement Value5;
	
	@FindBy (id="txt_ttl_val")
	public WebElement TotalBalance;
	
}
