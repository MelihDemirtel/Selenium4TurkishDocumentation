# Uzak Web Sürücüsü
WebDriver'ı yerel olarak kullandığınız şekilde uzaktan kullanabilirsiniz.
Birincil fark, testlerinizi ayrı bir makinede çalıştırabilmesi için uzak bir Web Sürücüsünün yapılandırılması gerektiğidir.
Uzak bir Web Sürücüsü iki parçadan oluşur: Bir istemci ve bir sunucu.
İstemci, WebDriver testinizdir ve sunucu, herhangi bir modern JEE uygulama sunucusunda barındırılabilen basit bir Java sunucu uygulamasıdır.
Bir uzak WebDriver istemcisini çalıştırmak için önce RemoteWebDriver'a bağlanmamız gerekir.
Bunu, URL'yi testlerimizi çalıştıran sunucunun adresine yönlendirerek yapıyoruz. Konfigürasyonumuzu özelleştirmek için istenen yetenekleri belirliyoruz.
Aşağıda, Firefox'ta testlerimizi çalıştırarak uzak web sunucumuz www.example.com'a işaret eden uzak bir WebDriver nesnesini başlatmanın bir örneği verilmiştir.

      FirefoxOptions firefoxOptions = new FirefoxOptions();
      WebDriver driver = new RemoteWebDriver(new URL("http://www.example.com"), firefoxOptions);
      driver.get("http://www.google.com");
      driver.quit();
      
Test yapılandırmamızı daha da özelleştirmek için, istenen diğer yetenekleri ekleyebiliriz.

## Browser Options 
Örneğin, Chrome sürüm 67'yi kullanarak Windows XP'de Chrome'u çalıştırmak istediğinizi varsayalım:

      ChromeOptions chromeOptions = new ChromeOptions();
      chromeOptions.setCapability("browserVersion", "67");
      chromeOptions.setCapability("platformName", "Windows XP");
      WebDriver driver = new RemoteWebDriver(new URL("http://www.example.com"), chromeOptions);
      driver.get("http://www.google.com");
      driver.quit();

## Local File Detector
Yerel Dosya Dedektörü, dosyaların istemci makineden uzak sunucuya aktarılmasına izin verir.
Örneğin, bir testin bir web uygulamasına bir dosya yüklemesi gerekiyorsa, uzak bir WebDriver,
çalışma zamanı sırasında dosyayı yerel makineden uzak web sunucusuna otomatik olarak aktarabilir. Bu, dosyanın testi çalıştıran uzak makineden yüklenmesine izin verir.
Varsayılan olarak etkin değildir ve aşağıdaki şekilde etkinleştirilebilir:

      driver.setFileDetector(new LocalFileDetector());
  
Yukarıdaki kod tanımlandıktan sonra, aşağıdaki şekilde testinize bir dosya yükleyebilirsiniz:

      driver.get("http://sso.dev.saucelabs.com/test/guinea-file-upload");
      WebElement upload = driver.findElement(By.id("myfile"));
      upload.sendKeys("/Users/sso/the/local/path/to/darkbulb.jpg");
      
  
  
