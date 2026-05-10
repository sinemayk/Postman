// LoginPage.java
public class LoginPage extends BasePage {

    @FindBy(id = "username")
    private WebElement usernameField;

    @FindBy(id = "password")
    private WebElement passwordField;

    @FindBy(id = "login-btn")
    private WebElement loginButton;

    public void login(String username, String password) {
        usernameField.sendKeys(username);
        passwordField.sendKeys(password);
        loginButton.click();
    }
}

// LoginTest.java
public class LoginTest extends BaseTest {

    @Test
    public void validLoginShouldRedirectToHomePage() {
        LoginPage loginPage = new LoginPage(driver);
        loginPage.login("testuser@example.com", "password123");

        Assert.assertTrue(driver.getCurrentUrl().contains("/home"),
            "User should be redirected to home page after login");
    }
}
