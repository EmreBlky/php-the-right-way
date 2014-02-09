---
title: İsim Uzayları (Namespaces)
isChild: true
---

## İsim Uzayları (Namespaces) {#isim_uzaylari_namespaces_title}

Daha öncede bahsedildiği üzere PHP topluluğu bir sürü geliştiriciden oluşmaktadır. Bu nedenle bazı durumlarda bir kaç farklı kütüphane aynı isimde kullanılmış olabilir. İki kütüphane aynı isim uzayında oldukları zaman çakışırlar ve bu da fatal error gibi sorunlara veya exceptionlara neden olur.

_İsim uzayları_ bu sorunu çözmektedir. PHP referans kılavuzunda da açıklandığı gibi, isim uzayları işletim sistemlerindeki klasörler ile karşılaştırılabilir. Aynı isimdeki iki dosya nasıl farklı klasörlerde bulunabilirsa, aynı şekilde aynı isimdeki iki sınıf farklı İsim Uzayları altında aynı isimde bulunabilmektedir.

Diğer geliştiricilerin geliştirdiği kütüphaneler ile çakışma korkusu yaşamadan geliştirme yapabilmeniz için isim uzaylarını kullanmak sizin yararınıza olacaktır.

[PSR-0][psr0] İsim Uzayları konusuna değinmiştir ve birbiri ile uyumlu (tak-ve-kullan kod) standart dosyalar, sınıflar ve isim uzayları düzeni kurmayı amaçlamaktadır.

* [İsim Uzayları hakkında][namespaces]
* [PSR-0 hakkında][psr0]

[namespaces]: http://php.net/manual/tr/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
