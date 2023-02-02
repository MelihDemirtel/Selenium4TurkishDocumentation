# Selenyum 4'e Yükseltin
Hala Selenium 3 kullanıyor musunuz? Bu kılavuz, en son sürüme geçmenize yardımcı olacaktır!
Resmi olarak desteklenen dillerden birini (Ruby, JavaScript, C#, Python ve Java) kullanıyorsanız, Selenium 4'e yükseltmek zahmetsiz bir işlem olmalıdır.
Birkaç sorunun olabileceği bazı durumlar olabilir ve bu kılavuz bunları çözmenize yardımcı olacaktır.
Proje bağımlılıklarınızı yükseltme adımlarını inceleyeceğiz ve sürüm yükseltmenin getirdiği önemli kullanımdan kaldırmaları ve değişiklikleri anlayacağız.

## Selenium 4'e yükseltmek için izleyeceğimiz adımlar şunlardır:
### 1.Test kodumuzu hazırlıyoruz
### 2.Bağımlılıkları yükseltme
### 3.Olası hatalar ve kullanımdan kaldırma mesajları

# Test Kodumuzu Hazırlıyoruz 
Selenium 4, eski protokol desteğini kaldırır ve varsayılan olarak W3C WebDriver standardını kullanır. Çoğu şey için, bu uygulama son kullanıcıları etkilemeyecektir.
Başlıca istisnalar **Capabilities** ve **Actions** sınıfıdır.

# Capabilities 

Test yetenekleri W3C uyumlu olacak şekilde yapılandırılmamışsa, bir oturumun başlatılmamasına neden olabilir. 
W3C WebDriver standart özelliklerinin listesi aşağıdadır:

### *browserName*
### *browserVersion (replaces version)*
### *platformName (replaces platform)*
### *acceptInsecureCerts*
### *pageLoadStrategy*
### *proxy*
### *timeouts*
### *unhandledPromptBehavior*

Standart Capabilities'lerin güncel bir listesi [W3C WebDriver](https://www.w3.org/TR/webdriver1/#capabilities)'da bulunabilir.

## Eski Sürüm

      DesiredCapabilities caps = DesiredCapabilities.firefox();
      caps.setCapability("platform", "Windows 10");
      caps.setCapability("version", "92");
      caps.setCapability("build", myTestBuild);
      caps.setCapability("name", myTestName);
      WebDriver driver = new RemoteWebDriver(new URL(cloudUrl), caps);

## Yeni Sürüm

      FirefoxOptions browserOptions = new FirefoxOptions();
      browserOptions.setPlatformName("Windows 10");
      browserOptions.setBrowserVersion("92");
      Map<String, Object> cloudOptions = new HashMap<>();
      cloudOptions.put("build", myTestBuild);
      cloudOptions.put("name", myTestName);
      browserOptions.setCapability("cloud:options", cloudOptions);
      WebDriver driver = new RemoteWebDriver(new URL(cloudUrl), browserOptions);
      
# Find element(s) utility methods in Java  

Java bağlamalarındaki (arayüzlerdeki) öğeleri bulmaya yarayan yardımcı yöntemler, FindsByyalnızca dahili kullanım için tasarlandıkları için kaldırılmıştır.
Aşağıdaki kod örnekleri bunu daha iyi açıklıyor.

*findElement* ile tek bir eleman bulma.

## Eski Sürüm

      driver.findElementByClassName("className");
      driver.findElementByCssSelector(".className");
      driver.findElementById("elementId");
      driver.findElementByLinkText("linkText");
      driver.findElementByName("elementName");
      driver.findElementByPartialLinkText("partialText");
      driver.findElementByTagName("elementTagName");
      driver.findElementByXPath("xPath");

## Yeni Sürüm

      driver.findElement(By.className("className"));
      driver.findElement(By.cssSelector(".className"));
      driver.findElement(By.id("elementId"));
      driver.findElement(By.linkText("linkText"));
      driver.findElement(By.name("elementName"));
      driver.findElement(By.partialLinkText("partialText"));
      driver.findElement(By.tagName("elementTagName"));
      driver.findElement(By.xpath("xPath"));
      
*findElements* ile birden çok öğe bulma.

## Eski Sürüm

      driver.findElementsByClassName("className");
      driver.findElementsByCssSelector(".className");
      driver.findElementsById("elementId");
      driver.findElementsByLinkText("linkText");
      driver.findElementsByName("elementName");
      driver.findElementsByPartialLinkText("partialText");
      driver.findElementsByTagName("elementTagName");
      driver.findElementsByXPath("xPath");

## Yeni Sürüm

      driver.findElements(By.className("className"));
      driver.findElements(By.cssSelector(".className"));
      driver.findElements(By.id("elementId"));
      driver.findElements(By.linkText("linkText"));
      driver.findElements(By.name("elementName"));
      driver.findElements(By.partialLinkText("partialText"));
      driver.findElements(By.tagName("elementTagName"));
      driver.findElements(By.xpath("xPath"));

# Bağımlılıkları Yükseltme (Upgrading Dependencies)

Selenium 4'ü yüklemek ve proje bağımlılıklarınızı yükseltmek için aşağıdaki alt bölümleri kontrol edin.

## Java
Selenium'u yükseltme işlemi, hangi derleme aracının kullanıldığına bağlıdır. Maven ve Gradle olan Java için en yaygın olanları ele alacağız.
Gereken minimum Java sürümü hala 8'dir.

## Maven 

## Eski Sürüm

      <dependencies>
        <!-- more dependencies ... -->
        <dependency>
          <groupId>org.seleniumhq.selenium</groupId>
          <artifactId>selenium-java</artifactId>
          <version>3.141.59</version>
        </dependency>
        <!-- more dependencies ... -->
      </dependencies>

## Yeni Sürüm

      <dependencies>
          <!-- more dependencies ... -->
          <dependency>
              <groupId>org.seleniumhq.selenium</groupId>
              <artifactId>selenium-java</artifactId>
              <version>4.4.0</version>
          </dependency>
          <!-- more dependencies ... -->
      </dependencies>

Değişikliği yaptıktan sonra , dosyanın *pom.xml* bulunduğu dizinde *mvn clean compile* çalıştırabilirsiniz.

## Gradle

## Eski Sürüm

      plugins {
          id 'java'
      }
      group 'org.example'
      version '1.0-SNAPSHOT'
      repositories {
          mavenCentral()
      }
      dependencies {
          testImplementation 'org.junit.jupiter:junit-jupiter-api:5.7.0'
          testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.7.0'
          implementation group: 'org.seleniumhq.selenium', name: 'selenium-java', version: '3.141.59'
      }
      test {
          useJUnitPlatform()
      }

## Yeni Sürüm

      plugins {
          id 'java'
      }
      group 'org.example'
      version '1.0-SNAPSHOT'
      repositories {
          mavenCentral()
      }
      dependencies {
          testImplementation 'org.junit.jupiter:junit-jupiter-api:5.7.0'
          testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.7.0'
          implementation group: 'org.seleniumhq.selenium', name: 'selenium-java', version: '4.4.0'
      }
      test {
          useJUnitPlatform()
      }

Değişikliği yaptıktan sonra , dosyanın *build.gradle* bulunduğu dizinde *./gradlew clean build* çalıştırabilirsiniz.

Tüm Java sürümlerini kontrol etmek için [MVNRepository](https://mvnrepository.com/artifact/org.seleniumhq.selenium/selenium-java) adresine gidebilirsiniz .

# Olası Hatalar ve Kullanımdan Kaldırma Mesajları
Selenium 4'e yükselttikten sonra karşılaşabileceğiniz kullanımdan kaldırma mesajlarının üstesinden gelmenize yardımcı olacak bir dizi kod örneğini burada bulabilirsiniz.

## Java
### Beklemeler ve Zaman Aşımı (Waits and Timeout)
Timeout, Zaman Aşımı'nda alınan parametreler, (long time, TimeUnit unit) to expect (Duration duration).

## Eski Sürüm

      driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
      driver.manage().timeouts().setScriptTimeout(2, TimeUnit.MINUTES);
      driver.manage().timeouts().pageLoadTimeout(10, TimeUnit.SECONDS);

## Yeni Sürüm

      driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
      driver.manage().timeouts().scriptTimeout(Duration.ofMinutes(2));
      driver.manage().timeouts().pageLoadTimeout(Duration.ofSeconds(10));
      
Waits artık farklı parametreler bekliyor. *WebDriverWait* saniye ve milisaniye cinsinden *Duration* parametre bekliyor.

## Eski Sürüm
      new WebDriverWait(driver, 3)
      .until(ExpectedConditions.elementToBeClickable(By.cssSelector("#id")));

      Wait<WebDriver> wait = new FluentWait<WebDriver>(driver)
        .withTimeout(30, TimeUnit.SECONDS)
        .pollingEvery(5, TimeUnit.SECONDS)
        .ignoring(NoSuchElementException.class);

## Yeni Sürüm

      new WebDriverWait(driver, Duration.ofSeconds(3))
        .until(ExpectedConditions.elementToBeClickable(By.cssSelector("#id")));

        Wait<WebDriver> wait = new FluentWait<WebDriver>(driver)
        .withTimeout(Duration.ofSeconds(30))
        .pollingEvery(Duration.ofSeconds(5))
        .ignoring(NoSuchElementException.class);

# Merging Capabilities Artık Çağıran Nesneyi Değiştirmiyor
Artık merge (birleştirme) işleminin sonucunun atanması gerekiyor.

## Eski Sürüm

      MutableCapabilities capabilities = new MutableCapabilities();
      capabilities.setCapability("platformVersion", "Windows 10");
      FirefoxOptions options = new FirefoxOptions();
      options.setHeadless(true);
      options.merge(capabilities);

## Yeni Sürüm

      MutableCapabilities capabilities = new MutableCapabilities();
      capabilities.setCapability("platformVersion", "Windows 10");
      FirefoxOptions options = new FirefoxOptions();
      options.setHeadless(true);
      options = options.merge(capabilities);
