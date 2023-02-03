# Tarayıcı Seçenekleri
Bu capabilities'ler tüm tarayıcılar tarafından paylaşılır. Selenium 4'ten itibaren, tarayıcı seçenekleri sınıflarını kullanmalısınız.
Uzak sürücü oturumları için, hangi tarayıcının kullanılacağını belirlediği için bir tarayıcı seçenekleri örneği gereklidir.

## browserName
Bu yetenek, belirli bir oturum için tarayıcı adını ayarlamak için kullanılır. Belirtilen tarayıcı uzak uçta kurulu değilse, oturum oluşturma başarısız olur.

## browserVersion
Bu capability isteğe bağlıdır, bu uzak uçta mevcut tarayıcı sürümünü ayarlamak için kullanılır.
Örneğin, yalnızca 80'in yüklü olduğu bir sistemde Chrome sürüm 75'i sorarsanız, oturum oluşturma başarısız olur

## pageLoadStrategy
Üç tür sayfa yükleme stratejisi mevcuttur. Sayfa yükleme stratejisi, aşağıdaki tabloda açıklandığı gibi *document.readyState'i* sorgular:

| Strategy	| Ready State |	Notes |
|-----------|-------------|-------|
|normal | complete | Varsayılan olarak kullanılır, tüm kaynakların indirilmesini bekler |
|eager	| interactive |	DOM erişimi hazır, ancak resimler gibi diğer kaynaklar hâlâ yükleniyor olabilir |
|none	| Any |	WebDriver'ı hiç engellemez |

Bir belgenin *document.readyState* özelliği, geçerli belgenin yükleme durumunu açıklar.

URL aracılığıyla yeni bir sayfaya gezinirken, varsayılan olarak WebDriver, belge hazır durumu tamamlanana kadar bir gezinme yöntemini
(örneğin, driver.navigate().get()) tamamlamayı erteleyecektir. Bu, özellikle Hazır Durumu tamamen geri döndükten sonra içeriği dinamik olarak yüklemek için
JavaScript kullanan Tek Sayfa Uygulamaları gibi siteler için sayfanın yüklenmesinin tamamlandığı anlamına gelmez.
Bu davranışın, bir öğeye tıklamanın veya bir form göndermenin sonucu olan gezinme için geçerli olmadığını da unutmayın.

Otomasyon için önemli olmayan varlıkların (ör. resimler, css, js) indirilmesinin bir sonucu olarak bir sayfanın yüklenmesi uzun sürüyorsa,
oturumu hızlandırmak için **normal** olan varsayılan parametreyi **eager** veya **none** olarak değiştirebilirsiniz.
Bu değer tüm oturum için geçerlidir, bu nedenle bekleme stratejinizin dalgalanmayı en aza indirmek için yeterli olduğundan emin olun.

## normal (default)
      import org.openqa.selenium.PageLoadStrategy;
      import org.openqa.selenium.WebDriver;
      import org.openqa.selenium.chrome.ChromeOptions;
      import org.openqa.selenium.chrome.ChromeDriver;

      public class pageLoadStrategy {
        public static void main(String[] args) {
          ChromeOptions chromeOptions = new ChromeOptions();
          chromeOptions.setPageLoadStrategy(PageLoadStrategy.NORMAL);
          WebDriver driver = new ChromeDriver(chromeOptions);
          try {
            // Navigate to Url
            driver.get("https://google.com");
          } finally {
            driver.quit();
          }
        }
      }
      
## eager
      import org.openqa.selenium.PageLoadStrategy;
      import org.openqa.selenium.WebDriver;
      import org.openqa.selenium.chrome.ChromeOptions;
      import org.openqa.selenium.chrome.ChromeDriver;

      public class pageLoadStrategy {
        public static void main(String[] args) {
          ChromeOptions chromeOptions = new ChromeOptions();
          chromeOptions.setPageLoadStrategy(PageLoadStrategy.EAGER);
          WebDriver driver = new ChromeDriver(chromeOptions);
          try {
            // Navigate to Url
            driver.get("https://google.com");
          } finally {
            driver.quit();
          }
        }
      }
      
## none
      import org.openqa.selenium.PageLoadStrategy;
      import org.openqa.selenium.WebDriver;
      import org.openqa.selenium.chrome.ChromeOptions;
      import org.openqa.selenium.chrome.ChromeDriver;

      public class pageLoadStrategy {
        public static void main(String[] args) {
          ChromeOptions chromeOptions = new ChromeOptions();
          chromeOptions.setPageLoadStrategy(PageLoadStrategy.NONE);
          WebDriver driver = new ChromeDriver(chromeOptions);
          try {
            // Navigate to Url
            driver.get("https://google.com");
          } finally {
            driver.quit();
          }
        }
      }
      
## platformName
Bu, uzak uçtaki işletim sistemini tanımlar ve işletim sistemi platformNameadını döndürür. Bulut tabanlı sağlayıcılarda, ayar platformNameişletim sistemini uzak uçta ayarlar.

## acceptInsecureCerts (Güvenli Olmayan Sertifikaları Kabul Et)
Güvenli olmayan sertifika hatası, uzaktan kontrol edilen tarayıcı herhangi bir sertifika uyarısına çarptığında oluşan bir WebDriver hatasıdır.
Bu genellikle süresi dolmuş veya geçersiz bir TLS sertifikasına sahip bir web sitesine gitmenin sonucudur.
Geçersiz sertifikalara örnek olarak kendinden imzalı, iptal edilmiş ve kriptografik olarak güvenli olmayan sertifikalar verilebilir.
Web tarayıcıları, sunucuyla iletişim tehlikeye gireceğinden, bozuk sertifikalara sahip etki alanlarına giden trafiği engeller ve engeller.
Test ortamlarında bile sertifika kontrollerini devre dışı bırakmak yerine sertifika durumunun düzeltilmesi şiddetle tavsiye edilir.

### Örnek Python Kodu
      from selenium import webdriver
      from selenium.common import exceptions

      session = webdriver.Firefox()
      try:
          session.get("https://self-signed.badssl.com/")
      except exceptions.InsecureCertificateException as e:
          print("Hit insecure cert on {}".format(session.current_url)
### Output
      Hit an insecure cert on https://self-signed.badssl.com/

WebDriver, oturum süresi boyunca sertifika kontrollerini devre dışı bırakmak için bir acceptInsecureCerts yeteneği sunar, ancak kullanımının kesinlikle tavsiye edilmediğini ve yaygın olarak test ortamının bir zayıflığı olarak görüldüğünü vurgulamak önemlidir.

## timeouts
Bir WebDriver oturumu, kullanıcının komut dosyalarını çalıştırma veya tarayıcıdan bilgi alma davranışını kontrol edebildiği belirli bir oturum zaman aşımı aralığı ile uygulanır.
Her oturum zaman aşımı, aşağıda açıklandığı gibi farklı zaman aşımlarının bir kombinasyonu ile yapılandırılır:

### Script Timeout (Komut Dosyası Zaman Aşımı)
Geçerli bir tarama bağlamında yürütülmekte olan bir komut dosyasının ne zaman kesintiye uğratılacağını belirtir.
WebDriver tarafından yeni bir oturum oluşturulduğunda varsayılan 30.000 zaman aşımı uygulanır.

### Page Load Timeout (Sayfa Yükleme Zaman Aşımı)
Geçerli göz atma bağlamında bir web sayfasının yüklenmesi gereken zaman aralığını belirtir.
300.000 varsayılan zaman aşımı, WebDriver tarafından yeni bir oturum oluşturulduğunda uygulanır. 
Sayfa yükleme, belirli/varsayılan bir zaman çerçevesini sınırlıyorsa, komut dosyası *TimeoutException* tarafından durdurulur.

### Implicit Wait Timeout (Örtülü Bekleme Zaman Aşımı)
Bu, elemanların yeri belirlenirken örtük eleman konum stratejisi için beklenecek zamanı belirtir.
Varsayılan zaman aşımı 0, WebDriver tarafından yeni bir oturum oluşturulduğunda uygulanır.

