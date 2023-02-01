Bir Selenyum kitaplığı kurun

Favori programlama diliniz için Selenyum kütüphanesini kurmak.
Öncelikle otomasyon projeniz için Selenium bağlamalarını kurmanız gerekir. Kitaplıkların kurulum süreci, kullanmayı seçtiğiniz dile bağlıdır.

Dile göre gereksinimler

Java için Selenium kitaplıklarının kurulumu, bir oluşturma aracı kullanılarak gerçekleştirilir.

Maven
pom.xmlProje dosyasında bağımlılığı belirtin :

        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.8.0</version>
        </dependency>
        
# GitHub'daki kodu kontrol edin::
<p align="left"> <a href="https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/pom.xml#L22-L26" alt="github1" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>

Gradle
build.gradleProje dosyasındaki bağımlılığı şu şekilde belirtin testImplementation:

    testImplementation 'org.seleniumhq.selenium:selenium-java:4.8.0'
    
# GitHub'daki kodu kontrol edin:
<p align="left"> <a href="[https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/pom.xml#L22-L26](https://github.com/SeleniumHQ/seleniumhq.github.io/blob/trunk/examples/java/build.gradle#L13)" alt="github2" target="_blank" rel="noreferrer"> <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="40" height="40"/> </a> </p>
  
