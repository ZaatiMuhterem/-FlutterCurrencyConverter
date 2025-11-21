



# KUR DÖNÜŞTÜRÜCÜ FLUTTER UYGULAMASI
- [Proje Hakkında](#proje-hakkında-)
- [Kullanılan_Paketler](#kullanılan-paketler)
- [Ekranlar_ve_Bileşenler](#ekranlar-ve-bileşenler)
- [Fonksiyonlar](#fonksiyonlar)
- [API_Detayları](#api-detayları)
- [Ekran_Görüntüleri](#ekran-görüntüleri)
- [Geliştirme_Notları](#geliştirme-notları)
- [Lisans](#lisans)



## Proje Hakkında 
Bu Flutter uygulaması, güncel döviz kurlarını internetten çekerek kullanıcıya TL bazlı dönüştürme imkanı sunar.
Uygulama, exchangeratesapi.io API'sini kullanır ve kullanıcı dostu bir arayüz ile dövizleri görüntüler.
- Platform: Flutter (Android  & İOS)
- Veri kaynağı:exchangeratesapi.io
- Kurlar : TL bazlı
- Özellik : Canlı kur çekme ve dönüştürme,listeleme

## Kullanılan Paketler
- `http` : İnternetten veri çekmek için
- `dart:convert` : JSON verisini parse etmek için
- `flutter/material.dart` : UI geliştirme
`pubspec.yaml` dosyasına ekleyin:
```
dependencies:
  flutter:
    sdk:flutter:
    http: ^1.6.0
```
## Ekranlar ve Bileşenler
- Ana Sayfa : Uygulamanın giriş noktası  ve StatefulWidget olarak tasarlanmış
- UI Bileşenleri : AppBar,Textfield,DropdownButton,Text,ListView,CircularProgressIndicator
    
## Fonksiyonlar
- `_verileriInternettenCek()` : API den döviz kurlarını çeker,Base kuru TL ye çevirir,`_oranlar` Map ini günceller`setState()` ile UI yi günceller
- `_hesapla()` : TextField'daki değeri alır ,Seçilen döviz kurunu kullanarak TL karşılığını hesaplar,`_sonuç` değişkenini günceller.
- `_buildKurTextField()`: kullanıcının miktar girdiği alan,değişiklik olduğunda `_hesapla` çalışır.
- `_buildKurDropdown()` : mevcut kurlar listelenir , seçim değiştiğinde `_hesapla` çalışır.
## API Detayları
- URL : `https://api.exchangeratesapi.io/v1/latest?access_key=<API_KEY>`
- Response Örneği:
```{
  "success": true,
  "timestamp": 1519296206,
  "base": "EUR",
  "date": "2021-03-17",
  "rates": {
      "AUD": 1.566015,
      "CAD": 1.560132,
      "CHF": 1.154727,
      "CNY": 7.827874,
      "GBP": 0.882047,
      "JPY": 132.360679,
      "USD": 1.23396
  }
}
```
- TL bazlı kur hesaplanması:
```tlKuru = baseTlKuru / secilenKur```
## Ekran Görüntüleri
<p float="left">
  <img src="assets/screenshot1.png" width="250" style="padding-right: 20px;"/>
  <div style="width: 2px; height: 250px; background-color: #000; margin: 0 20px;"></div><img src="assets/screenshot2.png" width="250" style="padding-right: 20px;"/>
</p>

## Geliştirme Notları
- `initState()` içinde `_verileriInternettenCek()` çağrılarak uygulama açılırken veri çekilir.
- Kullanıcı dostu UI için `Padding` , `SizedBox`ve `Expanded` kullanıldı.
- Döviz listesi sonsuz uzunlukta olabileceği için `ListView.builder`  tercih edildi.

## Lisans
Bu proje MIT Lisansı ile lisanslanmıştır. İstediğiniz gibi kullanabilir ve geliştirebilirsiniz.
