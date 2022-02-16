# SOLID-Prensipleri
## Solid Prensipleri İnceleme

Solid Prensipleri 2000 yılında Robert C. Martin tarafından "Design Principles and Design Patterns" adlı makalede tanıtıldı. Bu kavramlar daha sonra Michael Feathers tarafından geliştirilmeye devam edildi. Ve son 20 yılda, bu beş ilke, yazılım yazma şeklimizi değiştirerek nesne yönelimli programlama dünyasında devrim yarattı.

### Peki nedir bu SOLID ve neden kullanılır ? 

Mevcut gereksinimleri karşılayan ve gelecekteki gereksinimleri de kolayca karşılayabilecek kod yazmak her geliştiricinin hedefi olmalıdır. SOLID prensipleri sayesinde, yeniden kullanılabilir, genişletilebilir, sürdürülebilir, ölçeklenebilir ve bakımı kolay bir yapı sağlanması hedeflenir. 

Günlük hayatımızdaki kullanımlarıyla ilgili bazı örneklerle SOLID prensiplerini yaşamımıza indirgeyerek anlatmaya çalışacağım.

İlk olarak S harfimizi ele alalım... 

### Single Responsibility Principle (SRP) 

Single Responsibility Principle namı değer S ilkemiz bizlere her bir sınıfın yalnızca bir görevinin olmasını ve sadece tek bir amaç için değiştirilmesi gerektiğini söyler.
Eğer bir sınıfta değişiklik yapmak için birden fazla sebebimiz varsa prensip ihlal ediliyor demektir.

Diyelim ki aşağıda ki şu işlemleri yapan bir **VeriTabanıIslemleri** sınıfımız olsun...

_Bir veri tabanı bağlantısı açalım._
_Veritabanından veri alalım._
_Verileri harici bir dosyaya yazalım._

Bu sınıfla ilgili sorun, birçok işlemi gerçekleştirmesidir. Şimdi şöyle düşünelim gelecekte aşağıdaki değişikliklerden birinin gerçekleştiğini varsayalım...

_Yeni veritabanına bağlanabiliri._
_Veritabanındaki sorguları yönetmek için ORM'i benimseyebiliriz._
_Çıktı yapısında değişiklikler olabilir._

Yani tüm durumlarda yukarıdaki sınıf değiştirilecektir. Bu da diğer işlemlerin uygulanmasını etkileyebilir dolayısıyla SRP'ye aykırı bir durum söz konusudur.

### Open/Closed Principle

Bir nesne değişime kapalı, gelişime açık olmalıdır. 
Bu prensip sayesinde, var olan kodda değişiklik yaparken yeni potansiyel buglar yaratmamıza engel olmasıdır.
Bir A sınıfı bir geliştirici tarafından yazılmış ve başka bir geliştirici tarafından bir miktar değişiklik istiyorsa, rahatlıkla A sınıfını değiştirerek yapabilmelidir.

**_Şöyle bir düşünecek olursak;_**

_Cebimizdeki telefonu düşünelim, akıllı telefonlarımızın hemen hepsinde uygulama mağazaları vardır, bu mağazalar sayesinde telefonumuzun temel işlevlerini genişletmemize olanak sağlar. Elbette, bazı temel özellikler telefonla birlikte gelir (metin mesajları,gerçek zamanlı aramalar,kamera kullanımı vs.). Ancak uygulama mağazası aracılığıyla yeni genişletmelere erişebilir ve oyun yükleyebilir ya da chat app indirebiliriz. Bunu yapmamıza izin veren mekanizma tamamen bir uzantıdır. Çekirdek sayesinde telefonun kaynak kodunu etkilemeden işlevselliğini değişiklik için kapalı hale getirir. Ancak üzerine istediğimiz geliştirmeyi yapabiliriz._

_Kısacası telefona bir uygulama indirmek için tekrardan işletim sistemini yazmamıza gerek yok._

### Liskov Substitution Principle

Bu ilke, 1987 yılında Barbara Liskov tarafından tanıtıldı. Bu ilkeye göre alt sınıflar, üst sınıfların yerine programın davranışını bozmadan kullanabiliyor olmamız gerekir. Kalıtım alınan sınıfların içindeki bütün özellikler kalıtımı alan sınıfta kullanılmalıdır.

**_Hayatımızdan bir örnek  vericek olursak;_**

_Dövüşçü bir babanın oğlununun dövüş becerilerini babasından miras alması gerektiğinde babasının yerini alabilmesi şeklinde düşünebiliriz, ancak burada önemli olan durum oğul dövüşçü olmak istiyorsa babasının yerini alabilir, ancak çocuk futbolcu olmak istiyorsa kesinlikle aynı aile genetiğini miras almış olsalar bile, babasının yerini alamaz._

### Interface Segregation Principle

Bir sınıf, interface implemente ettiğinde,o interfaceden gelen tüm fonksiyonlar kullanılabilir olmalıdır.
Bir fonksiyon bir interface'e bağlı olmaya zorlanmamalıdır.
Yani ISP ilkesi, daha büyük, daha monolitik bir interface yerine yapılan işe özel interface tercih etmemiz gerektiğini söyler.

**_Gerçek hayattan düşünecek olursak_**

_Her zaman gittiğiniz kafede ve vejeteryan olduğunuzu düşünün, Kafedeki garsonun size vejeteryan, vejeteryan olmayan ürünler,içecekler ve tatlılar içeren bir menü verdi. Bu durumda, siz müşteri olarak, yemediğiniz yemekleri içeren menü kartı değil yalnızca vejeteryan menüleri içeren yemek kartınız olmalıdır.
Burada menü farklı müşteri türleri için farklı olmalıdır. Herkes için ortak veya genel menü kartı, tek bir kart yerine birden çok karta bölünebilir. 

**_Bu ilkenin kullanılması, gerekli değişikliklerin yan etkilerinin ve sıklığının azaltılmasına yardımcı olur._**

### Dependency Inversion Principle

Bir sınıfın, metodun ya da özelliğin, onu kullanan diğer sınıflara karşı olan bağımlılığı en aza indirgenmelidir. Bir alt sınıfta yapılan değişiklikler üst sınıfları etkilememelidir.

Gerçek zamanlı uygulamalar geliştirirken hatırlamanız gereken en önemli nokta, her zaman High-level modülü ve Low-level modülünü mümkün olduğunca gevşek bir şekilde bağlı tutmaya çalışmaktır.

Bir sınıf başka bir sınıfın tasarımını ve uygulamasını öğrendiğinde, bir sınıfta herhangi bir değişiklik yaparsak diğer sınıfı bozma riskini artırır. Bu nedenle, bu yüksek seviyeli ve düşük seviyeli modülleri/sınıfları mümkün olduğunca gevşek bir şekilde bağlı tutmalıyız. Bunun için ikisini de birbirini tanımak yerine soyutlamalara bağımlı hale getirmemiz gerekiyor. 

**_Şöyle bir düşünelim;_**

Televizyon izlemek istiyorsunuz ve kumandayı elinize aldınız ancak kumandanın pilinin bittiğini düşünelim. Uzaktan kumandanızın pile ihtiyacı vardır ancak pil markasına bağlı değildir. İstediğiniz herhangi bir markayı kullanabilirsiniz. Bu nedenle, Tv uzaktan kumandasının marka adıyla gevşek bir şekilde birleştiğini söyleyebiliriz.

**Kısacası; Dependency Inversion prensibi kodunuzu daha fazla yeniden kullanabilir hale getirir.**


