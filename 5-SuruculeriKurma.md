# Tarayıcı sürücülerini yükleyin

Bir tarayıcının otomatikleştirilmesine izin vermek için sisteminizi ayarlama.

WebDriver aracılığıyla Selenium, Chrome/Chromium, Firefox, Edge ve Safari gibi piyasadaki tüm büyük tarayıcıları destekler.
Mümkün olduğunda, WebDriver, tarayıcının yerleşik otomasyon desteğini kullanarak tarayıcıyı çalıştırır.

# Sürücüleri Kullanmanın Dört Yolu

# 1. Selenyum Yöneticisi (Beta)
Selenium v4.6

Selenium Manager, Selenium'u kutudan çıkar çıkmaz çalıştırmak için bir çalışma ortamı elde etmenize yardımcı olur.
Selenium Manager'ın Beta 1'i, PATH. Ekstra yapılandırma gerekmez. Selenium Manager'ın gelecekteki sürümleri, gerekirse tarayıcıları bile indirecektir.

# 2. Sürücü Yönetim Yazılımı

Çoğu makine tarayıcıyı otomatik olarak günceller, ancak sürücü güncellemez. 
Tarayıcınız için doğru sürücüyü aldığınızdan emin olmak için size yardımcı olacak birçok üçüncü kişi kitaplığı vardır.

# WebDriverManager'ı içe aktarın:
<p align="left"> <a href="https://github.com/bonigarcia/webdrivermanager" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="host1" width="40" height="40"/> </a> </p>

        import io.github.bonigarcia.wdm.WebDriverManager;

# Çağrı setup():

        WebDriverManager.chromedriver().setup();

        WebDriver driver = new ChromeDriver();
        
# GitHub'daki kodu kontrol edin:
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/src/test/java/dev/selenium/getting_started/InstallDriversTest.java#L17-L19" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="host1" width="40" height="40"/> </a> </p>

# 3. PATH Ortam Değişkeni

Bu seçenek öncelikle sürücünün manuel olarak indirilmesini gerektirir.

# Bağlantılar için Hızlı Referans Bölümüne bakın.
<p align="left"> <a href="https://www.selenium.dev/documentation/webdriver/getting_started/install_drivers/#quick-reference" target="_blank" rel="noreferrer"> <img src="https://cdn-icons-png.flaticon.com/512/61/61044.png" alt="reference" width="40" height="40"/> </a> </p>

Bu, kodunuzu güncellemek zorunda kalmadan sürücülerin konumunu değiştirmek için esnek bir seçenektir.
Her makinenin sürücüleri aynı yere koymasını gerektirmeden birden çok makinede çalışır.
Sürücüleri zaten içinde listelenen bir dizine yerleştirebilir veya bir dizine yerleştirip içine ekleyebilirsiniz.

Hangi dizinlerin PATHaçık olduğunu görmek için bir Terminal açın ve şunu çalıştırın:

        echo $PATH

Sürücünüzün konumu zaten listelenen bir dizinde değilse, PATH'e yeni bir dizin ekleyebilirsiniz:

        echo 'export PATH=$PATH:/path/to/driver' >> ~/.bash_profile
        source ~/.bash_profile

Sürücüyü başlatarak doğru eklenip eklenmediğini test edebilirsiniz:

        chromedriver

Eğer PATH yukarıda doğru yapılandırılmışsa, sürücünün başlatılmasıyla ilgili bazı çıktılar göreceksiniz:

        Starting ChromeDriver 95.0.4638.54 (d31a821ec901f68d0d34ccdbaea45b4c86ce543e-refs/branch-heads/4638@{#871}) on port 9515
        Only local connections are allowed.
        Please see https://chromedriver.chromium.org/security-considerations for suggestions on keeping ChromeDriver safe.
        ChromeDriver was started successfully.

Ctrl+C tuşuna basarak komut isteminizin kontrolünü yeniden kazanabilirsiniz.

# 4. Sabit Kodlanmış Konum 

Yukarıdaki Seçenek 3'e benzer şekilde, sürücüyü manuel olarak indirmeniz gerekir.

# Bağlantılar için Hızlı Referans Bölümüne bakın.
<p align="left"> <a href="https://www.selenium.dev/documentation/webdriver/getting_started/install_drivers/#quick-reference" target="_blank" rel="noreferrer"> <img src="https://cdn-icons-png.flaticon.com/512/61/61044.png" alt="reference2" width="40" height="40"/> </a> </p>

Konumun kodun kendisinde belirtilmesi, sisteminizdeki Ortam Değişkenlerini çözmenize gerek kalmaması gibi bir avantaja sahiptir,
ancak kodu çok daha az esnek hale getirme dezavantajına sahiptir.

        System.setProperty("webdriver.chrome.driver","/path/to/chromedriver");
        ChromeDriver driver = new ChromeDriver();
