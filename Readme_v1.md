## Ev Yapımı UPS / Schottky (Şotki) Diyot ile..

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;12v 500mah beslemeye sahip Asus modemime yaptığım ev yapımı ups çalışmamı paylaşıyorum.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Öncelikle anlatılanlar sadece amatör bir çalışma olup örnek amaçlı paylaşılmaktadır. Bu tür uygulamalarda iyice araştırıp veya uzmanlara danışarak uygulama yapmanızı tavsiye ederim.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Birçok araştırmadan sonra amatör olarak hazırladığım bu düzenek ile modem sadece wifi kullanımı halinde 4 saati aşkın bir sürede çalışmıştır. 
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Batarya, komponent ve diğer ekipmanı Altınkaya isimli bir firmadan aldığım siyah plastik bir kutu içerisine monte ettim. Kutu ile uğraşacağınız bu tür işlemler için bir hobi dril seti edinmenizi ayrıca tavsiye ederim.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Sizde öneri, görüş ve fikirlerinizi paylaşarak bu ve benzeri projelerde bana ve bir çok insana destek olabilirsiniz. Bilgi paylaştıkça çoğalır..
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Faydalı olması dileği ile ..

### Gereksinimler
- 2 adet 1N5819 schottky diyot (modemin ihtiyacı 1 amper üzerinde olacak ise dayanımı daha yüksek bir diyot seçmekte fayda vardır)
- 2.5mm dişi power jack (2.5mm örnektir, modem adaptöründen gelen jack hangi boyutta ise)
- 2.5mm erkek power jack (2.5mm örnektir, modemin girişindeki jack hangi boyutta ise)
- TP4056 batarya şarj modülü. (Eğer mikro şarj girişi kullanılmayacaksa yine Usb B, mini yada mikro breadboard modülü eklenebilir)
- MT3608 Step-up voltaj regülatörü
- XW228DKFR4 (spbkbs-10) batarya pil göstergesi (kullanımı opsiyonel)
- 2 adet 18650 3.7v 3200mah lion pil (mah değeri isteğe göre değişebilir)
- 2 adet 18650 pil yatağı
- 1 adet switch yada on off button (kullanımı opsiyonel)

### Bağlantı Şeması
![alt text](schema.png)

### Çalışma Şekli
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Öncelikle; 12v modem adaptöründen gelen akım (S1) şotki diyotundan (D2) geçerek yine modeme gidişi sağlanır. Bu şebeke elektriğinin direk modeme geçişi içindir.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Diğer hatta geçecek olursak; 5v adaptörden gelen akım (S2) TP4056 (U1) ile bataryalara yönelir. Batarya ya durumunu gözlemlemek için direk batarya pil göstergesi (LED1) bağlanır.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Batarya üzerinden çıkan elektrik ise switch üzerinden (SW1) yükseltici regülatöre (U2) geçer.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Regülatör (U2) üzerindeki trimpottan yapılan ayar vasıtasıyla 12V düzeyine çıkan akım diğer şotki diyotuna (D1) geçerek 12v adaptör gücü ile birleşerek modeme gider.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Şotki diyotunun buradaki faydası bataryadan gelen elektiğin pozitifi ile modem adaptörü üzerinden gelen elektiğin pozitifinin birbirlerine akmasını yani ters polarizasyonu engelemektir.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bu durumda aktif-aktif mantık ile 2 farklı akım kaynağından beslenen modem çalışmaktadır. Bu 2 akım kaynağından herhangi biri çekildiğinde modem çalışmaya devam edecektir. 
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Bizim işimize yaran kısmı elektrik kesintisinde adaptör üzerinden akan akım kesilir fakat aktif olan diğer batarya akımı modemin çalışmaya devamını sağlar.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Son olarak aynı akıma sahip iki güç kaynağından hangisinin öncelikli kullanılacağı konusunda güç kaynaklarının gerilimi büyük olan baskın olmaktadır. 
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Projemde bunu sağlayabilmek için adaptörü 12v <b>2 amper</b> tercih ettim. Bunu anlamak için; bataryadan gelen akımın gerilimi olan 6400mah ve ayrıca diyelim ki tp4056 (U1) şarj için 1000mah olarak ekstra gerilim gönderiyor olsun, bunlar sırasıyla tp4056 (U1) ile %7, pil göstergesi ile 5mah, 12v'a yükselirken doğal kayıp olarak %3.24, yükselten regülatör (U2) ile %3 kayıp ve şotki diyotu (D1) üzerinden %1 kayıp ile totalde 12v 1971 mah seviyesinde hesapladım ve <b>2 amper</b> adaptör ilgili batarya gerilimini bastırmakta yeterli olduğunu gözlemledim. (Sağlaması; ((6400 + 1000 - 5) / 1.07) / (12 / 3.7) / 1.07 / 1.01 şeklindedir.)

### Fotoğraflar
![alt text](front.png)
![alt text](top.png)
![alt text](in.png)

### Öneri ve Uyarılar
- Batarya pil göstergesi gayet parlak bir ışığa sahiptir. Işıktan rahatsız olabileceğiniz bir yerde bulunacak ise ekranına küçük bir film parçası ekleyerek ışığı azaltabilirsiniz.
- Özellikle TP4056 bataryaları şarj ederken ciddi oranda ısınabilmekte olup çipler üzerine bir yada birkaç küçük soğutucu kullanımı faydalı ve gerekli olabilir.
- MT3608 ile voltaj ayarlamasını yapmadan önce adaptörden gelen voltajı şotki diyotundan geçtikten sonra ölçerek tesbit edin ve akabinde bu regülatörden çıkacak gücü yine diğer diyottan çıktıktan sonra ölçerek ayarlayın, bu şekilde daha net ayarlama yapabilirsiniz.
- MT3608'den daha yüksek güçte (2, 3 ve 4 amper çıkışı olan regülatörler gibi) regülatörler kullanırsanız modemin ihtiyacından fazla bir gücü sağlayacak ve bataryalar kat ve kat daha hızlı bitebilir.
- Bu tür komponent, batarya ve ekipmanı ısınma kaynaklı oluşabilecek sorunlardan dolayı ilk birkaç kullanımda gözlem altında tutunuz. 
- Switch yada butonun mantığı ise tüm fişleri çekip bu upsi boşa çıkarttığınızda dahi bataryadan geçen akım regülatöre akmaya devam edecek ve kaynak tüketimi olmasa bile zamanla bataryanın tükenmesine sebep olacaktır. Aradaki gücün kesilmesi yapıyı maintenance etmek için en iyi yöntemdir.
