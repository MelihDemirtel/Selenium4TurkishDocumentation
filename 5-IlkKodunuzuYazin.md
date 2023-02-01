# İlk Selenium Kodunuzu Yazın
Selenyum betiği oluşturmak için adım adım talimatlar.

Selenium'u yükledikten ve Sürücüleri yükledikten sonra , Selenium kodunu yazmaya hazırsınız.

# Sekiz Temel Bileşen
Selenium'un yaptığı her şey, bir şeyler yapmak için tarayıcı komutlarını göndermek veya bilgi istekleri göndermektir.
Selenium ile yapacaklarınızın çoğu, şu temel komutların birleşimidir:

## 1. Oturumu başlatın

        WebDriver driver = new ChromeDriver();
        
### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java#L17" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>
        
## 2. Tarayıcıda işlem yapın
Bu örnekte bir web sayfasına gidiyoruz.

        driver.get("https://www.selenium.dev/selenium/web/web-form.html");  
        
### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java#L18" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>
         
## 3. Tarayıcı bilgilerini isteyin
Tarayıcı hakkında pencere tutamaçları, tarayıcı boyutu / konumu, tanımlama bilgileri, uyarılar (including window handles, browser size / position, cookies, alerts,)
vb. dahil olmak üzere talep edebileceğiniz bir dizi bilgi vardır.

        String title = driver.getTitle();
        
### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java#L20" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>
 
## 4. Bekleme Stratejisi Oluşturun
Kodu tarayıcının mevcut durumuyla senkronize etmek Selenium'daki en büyük zorluklardan biridir ve bunu iyi yapmak ileri düzeyde bir konudur.
Temel olarak, öğenin yerini belirlemeye çalışmadan önce sayfada olduğundan ve onunla etkileşime girmeden önce öğenin etkileşimli bir durumda olduğundan emin olmak istersiniz.
Örtük bir bekleme nadiren en iyi çözümdür, ancak burada gösterilmesi en kolay olanıdır, bu yüzden onu yer tutucu olarak kullanacağız.

        driver.manage().timeouts().implicitlyWait(Duration.ofMillis(500));
        
### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java#L23" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>
 
## 5. Bir öğe bulun 
Çoğu Selenium oturumundaki komutların çoğu öğeyle ilgilidir ve önce bir öğe bulmadan biriyle etkileşim kuramazsınız.

        WebElement textBox = driver.findElement(By.name("my-text"));
        WebElement submitButton = driver.findElement(By.cssSelector("button"));

### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java#L25-L26" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>

## 6. Öğe üzerinde harekete geçin
Bir öğe üzerinde gerçekleştirilecek yalnızca birkaç eylem vardır , ancak bunları sık sık kullanacaksınız.

        textBox.sendKeys("Selenium");
        submitButton.click();

### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java#L28-L29" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>

## 7. Öğe bilgilerini isteyin 
Öğeler , istenebilecek birçok bilgiyi depolar.

        String value = message.getText();

### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java#L32" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>

## 8. Oturumu sonlandırın
Bu, varsayılan olarak tarayıcıyı da kapatan sürücü işlemini sonlandırır. Bu sürücü örneğine daha fazla komut gönderilemez.

        driver.quit();
        
### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java#L35" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>

# Her şeyi bir araya getirelim
Bu 8 adımı, bir test çalıştırıcısı tarafından yürütülebilecek eksiksiz bir komut dosyasında birleştirelim.

    package dev.selenium.getting_started;

    import org.junit.jupiter.api.Test;
    import org.openqa.selenium.By;
    import org.openqa.selenium.WebDriver;
    import org.openqa.selenium.WebElement;
    import org.openqa.selenium.chrome.ChromeDriver;

    import java.time.Duration;

    import static org.junit.jupiter.api.Assertions.assertEquals;

    public class FirstScriptTest {

    @Test
    public void eightComponents() {
        WebDriver driver = new ChromeDriver();
        driver.get("https://www.selenium.dev/selenium/web/web-form.html");

        String title = driver.getTitle();
        assertEquals("Web form", title);

        driver.manage().timeouts().implicitlyWait(Duration.ofMillis(500));

        WebElement textBox = driver.findElement(By.name("my-text"));
        WebElement submitButton = driver.findElement(By.cssSelector("button"));

        textBox.sendKeys("Selenium");
        submitButton.click();

        WebElement message = driver.findElement(By.id("message"));
        String value = message.getText();
        assertEquals("Received!", value);

        driver.quit();
    }  }

### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/FirstScriptTest.java" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>
