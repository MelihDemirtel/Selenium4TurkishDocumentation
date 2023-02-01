WebDriver kullanarak bir test paketi oluşturmak, birkaç bileşeni anlamanızı ve etkili bir şekilde kullanmanızı gerektirecektir. 
Yazılımdaki her şeyde olduğu gibi, farklı kişiler aynı fikir için farklı terimler kullanır. 
Aşağıda, bu açıklamada terimlerin nasıl kullanıldığına dair bir döküm bulunmaktadır.

# Terminoloji

## API: 
Uygulama Programlama Arayüzü. Bu, WebDriver'ı değiştirmek için kullandığınız "komutlar" kümesidir.

## Library(Kitaplık):
API'leri ve bunları uygulamak için gerekli kodu içeren bir kod modülü. Kitaplıklar, her bir dil bağlamasına özeldir, örneğin Java için .jar dosyaları, .NET için .dll dosyaları vb.

## Driver(Sürücü): 
Gerçek tarayıcıyı kontrol etmekten sorumludur. Çoğu sürücü, tarayıcı satıcıları tarafından oluşturulur. 
Sürücüler genellikle, test paketini yürüten sistemde değil, tarayıcının kendisiyle birlikte sistemde çalışan çalıştırılabilir modüllerdir. 
(Ancak bunlar aynı sistem olabilir.) NOT: Bazı kişiler sürücülerden proxy olarak söz eder.

## Framework(Çerçeve):
WebDriver paketleri için destek olarak kullanılan ek bir kitaplık. Bu çerçeveler, JUnit veya NUnit gibi test çerçeveleri olabilir. 
Cucumber or Robotium gibi doğal dil özelliklerini destekleyen çerçeveler de olabilirler. 
Çerçeveler ayrıca test edilen sistemin manipüle edilmesi veya yapılandırılması, veri oluşturulması, test kehanetleri vb. görevler için yazılabilir ve kullanılabilir.

En azından, WebDriver bir sürücü aracılığıyla bir tarayıcıyla konuşur. İletişim iki yönlüdür: WebDriver, 
komutları sürücü aracılığıyla tarayıcıya iletir ve bilgileri aynı yoldan geri alır.

# Host-1:
<p align="left"> <a href="https://www.selenium.dev/documentation/overview/components/" target="_blank" rel="noreferrer"> <img src="https://www.selenium.dev/images/documentation/webdriver/basic_comms.png" alt="host1" width="792" height="366"/> </a> </p>

Google'ın Chrome/Chromium'u için ChromeDriver, Mozilla'nın Firefox'u için GeckoDriver vb. sürücü, tarayıcıya özeldir. 
Sürücü, tarayıcıyla aynı sistemde çalışır. Bu, testlerin yürütüldüğü sistemle aynı olabilir veya olmayabilir.

Yukarıdaki bu basit örnek doğrudan iletişimdir. Tarayıcıyla iletişim, Selenium Sunucusu veya RemoteWebDriver aracılığıyla uzaktan iletişim de olabilir. 
RemoteWebDriver, sürücü ve tarayıcı ile aynı sistemde çalışır.

# Host-2:
<p align="left"> <a href="https://www.selenium.dev/documentation/overview/components/" target="_blank" rel="noreferrer"> <img src="https://www.selenium.dev/images/documentation/webdriver/remote_comms.png" alt="host2" width="792" height="366"/> </a> </p>

Uzaktan iletişim, her ikisi de ana sistemdeki sürücüyle konuşan Selenium Server veya Selenium Grid kullanılarak da gerçekleştirilebilir.

# Host-3:
<p align="left"> <a href="https://www.selenium.dev/documentation/overview/components/" target="_blank" rel="noreferrer"> <img src="https://www.selenium.dev/images/documentation/webdriver/remote_comms_server.png" alt="host3" width="792" height="366"/> </a> </p>

# Frameworks
WebDriver'ın yalnızca bir işi vardır: yukarıdaki yöntemlerden herhangi biri aracılığıyla tarayıcıyla iletişim kurmak. WebDriver test hakkında hiçbir şey bilmez.
Bir şeyleri karşılaştırmayı, başarılı veya başarısız olduğunu söylemeyi bilmez ve kesinlikle raporlama veya Given/When/Then dilbilgisi hakkında hiçbir şey bilmez.

Burada çeşitli çerçeveler devreye giriyor. En azından, dil bağlarıyla eşleşen bir test çerçevesine ihtiyacınız olacak, örneğin .NET için NUnit, Java için JUnit, Ruby için RSpec, vb.

Test çerçevesi, WebDriver'ınızı ve testlerinizdeki ilgili adımları çalıştırmaktan ve yürütmekten sorumludur.
Bu nedenle, aşağıdaki görüntüye benzediğini düşünebilirsiniz.

# Framework:
<p align="left"> <a href="https://www.selenium.dev/documentation/overview/components/" target="_blank" rel="noreferrer"> <img src="https://www.selenium.dev/images/documentation/webdriver/test_framework.png" alt="framework" width="792" height="366"/> </a> </p>

Cucumber gibi doğal dil çerçeveleri/araçları, yukarıdaki şekildeki Test Çerçevesi kutusunun bir parçası olarak bulunabilir.
