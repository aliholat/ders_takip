# Ders Takip PWA

## Ne yapıyor?
- Haftalık ders programını oluşturur.
- Bir derse dokununca şu durumları kaydedebilirsin:
  - Ders iptal oldu
  - Vaktinde gidildi
  - Biraz geç gidildi
  - Baya geç gidildi
  - Derse gitmedim
- Seçili hafta için genel yüzdeyi gösterir.
- Tüm kayıtlar için toplam yüzdeyi gösterir.
- Her ders için ayrı ayrı haftalık ve toplam yüzdeleri gösterir.
- Önceki/sonraki haftalara gidip eski kayıtları düzenleyebilirsin.
- Verileri tarayıcının localStorage alanında saklar.
- JSON yedek dışa aktarma / içe aktarma vardır.
- PWA olarak telefona ana ekrana kurulabilir.

## Puanlama
- Vaktinde: 100
- Biraz geç: 80
- Baya geç: 50
- Gitmedim: 0
- İptal: hesaba katılmaz

Bu oranlar index.html içindeki STATUS sabitinden kolayca değiştirilebilir.

## Çalıştırma
Sadece index.html dosyasını açarsan ana özellikler çalışır.
PWA kurulumu ve service worker için dosyaları bir web sunucusundan açmak gerekir.

Basit test için:
1. Klasörde terminal aç.
2. `python -m http.server 8000`
3. Tarayıcıda `http://localhost:8000` aç.

Telefon için en kolay dağıtım:
- GitHub Pages
- Netlify
- Vercel

## Önemli: Telefon-PC senkronizasyonu
Bu ilk sürüm veriyi cihaz/tarayıcı içinde saklar.
Telefon ve PC aynı veriyi otomatik görmez.

Gerçek senkronizasyon için sonraki adım:
- Supabase veya Firebase
- Kullanıcı hesabı
- Bulutta schedule + attendance kayıtları
- Aynı hesapla telefon ve PC'den ortak veri


## Aynı dersin birden fazla oturumu
Aynı ders iki farklı gün veya saatteyse:
- Ders adı alanına aynı ana adı yaz: `SSD1`
- Oturum / grup adı alanına ilk kayıt için `Sabah`
- İkinci kayıt için yine `SSD1`, oturum adı `Öğlen`

Böylece:
- SSD1 Sabah ayrı takip edilir.
- SSD1 Öğlen ayrı takip edilir.
- Ders Bazında bölümünde ikisi birleşerek tek bir SSD1 genel oranı oluşturur.


## Veriler nereye kaydolur?
Bu sürümde ders programı ve devam kayıtları tarayıcının `localStorage` alanında tutulur.
Normal kullanımda bilgisayarda ayrıca bir `.db` veya veri dosyası oluşturulmaz.

PWA olarak kurulduğunda tarayıcı uygulamanın HTML/ikon gibi dosyalarını Cache Storage içinde önbelleğe alabilir.

Uygulamadaki **Tüm Verileri Sil** düğmesi:
- ders programını siler,
- devam kayıtlarını siler,
- localStorage ve sessionStorage verilerini temizler,
- uygulama önbelleklerini silmeye çalışır,
- service worker kaydını kaldırır.

Telefonun veya bilgisayarın ana ekranına yüklenmiş PWA simgesi işletim sistemi tarafından tutulduğu için simgeyi tamamen kaldırmak için uygulamayı ayrıca kaldırmak gerekebilir.
