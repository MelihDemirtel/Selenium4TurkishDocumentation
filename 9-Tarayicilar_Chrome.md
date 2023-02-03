# Chrome'a Özgü İşlevsellik
Bunlar, Google Chrome tarayıcılarına özgü capabilities (yetenekler) ve özelliklerdir.
Varsayılan olarak Selenium 4, Chrome v75 ve üstü ile uyumludur. Chrome tarayıcı sürümünün ve chromedriver sürümünün ana sürümle eşleşmesi gerektiğini unutmayın.

## Seçenekler
Tüm tarayıcılarda ortak olan yetenekler, [Seçenekler](https://github.com/MelihDemirtel/Selenium4TurkishDocumentation/blob/master/7-TarayiciSecenekleri.md) sayfasında açıklanmıştır .
Chrome'a özgü yetenekler, Google'ın [Yetenekler ve ChromeSeçenekleri](https://chromedriver.chromium.org/capabilities) sayfasında bulunabilir.
Tanımlanmış temel seçeneklerle bir Chrome oturumu başlatmak şuna benzer:

        ChromeOptions options = new ChromeOptions();
        driver = new ChromeDriver(options);
        
### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk//examples/java/src/test/java/dev/selenium/browsers/ChromeTest.java#L18-L19" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>
 
Aşağıda, farklı yeteneklere sahip birkaç yaygın kullanım örneği verilmiştir:

## Argümanlar
**args** parametresi, tarayıcı başlatılırken kullanılan Komut Satırı Anahtarlarının bir listesi içindir. Yaygın olarak kullanılan bağımsız değişkenler arasında 
**--start-maximized** ve **--headless=new** bulunur.

Seçeneklere bir bağımsız değişken ekleyin:

        ChromeOptions options = new ChromeOptions();
        options.addArguments("--headless=new");
        driver = new ChromeDriver(options);
        
### GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk//examples/java/src/test/java/dev/selenium/browsers/ChromeTest.java#L24-L26" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>
 
