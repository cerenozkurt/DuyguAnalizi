# DuyguAnalizi
Python ile Duygu Durum Analizi

Duygu analizi birçok alanda önemlidir. Örneğin firmalar müşterileri ile iletişimde onların isteklerini başarılı bir şekilde gerçekleştirebilmek için müşterisinin gerçek duygularının ne olduğunu veyahut sorgu odasında bulunan şahsın doğruları söyleyip söylemediği bilinmek istenir. Bu gibi durumlarda kolaylaştırıcı olması açısıdan duygu analizi tercih edilebilir bir yöntem olabilir. Projenin amacı da duygu analizi için başlangıç seviyesinde de olsa bir adım atmaktır. 
Projenin çalışma prensibi yüklenen resimdeki yüzü algılayıp, algınan yüzün sahip olduğu duygu ifadesini analiz edecek şekildedir. Bu analiz için Kaggle’da bulunan hazır bir data seti olan Facial Expression Recognition Challenge’dan yararlanıldı. Çalışmada Tensorflow Keras, Seaborn, Matplotlib, Pandas kütüphaneleri kullanıldı. Bu data seti programa entegre edildi, data setinin içerisindeki 7 tip duygu ifadesi Evrişimli sinir ağı ile modellendi. Bu modelleme ile elde edilen sonuçlar ile örnek resimler üzerinde testler yapıldı.

Yararlanılan Kütüphaneler;
Numpy kütüphanesi ile datasetinin içerisinde bulunan eğitim verileri pixellerine göre arraylere dizildi.
Pandas kütüphanesi ile gerekli veri seti çalışmaya aktarıldı.
Matplotlib ve Seaborn kütüphaneleri ile analiz işlemlerinin detaylıca görülebilmesi için grafikler çizildi.
Tensorflow, Keras kütüphanesi ile Evrişimli Sinir Ağı Modellemesi kuruldu.

Kullanılan Veri Seti;
Kaggle’da bulunan Facial Expression Recognition Challenge adlı veri setinden yararlanıldı. Bu veri seti Pandas kütüphanesi ile çalışmaya eklendi. Bu veri setinin içerisinde 7 adet duygu durumuna sahip 35887 örnek resim mevcuttur. Bu eğitim setindeki örnek resimler ile yapay bir sinir ağı oluşturuldu ve ortaya bir modelleme çıkarıldı. Bu modelleme ile de kullanıcının programa yüklediği resimlerdeki yüz ve duygular algılanıp analiz edildi.

![image](https://user-images.githubusercontent.com/33186246/159139474-28ca4a1a-1c3c-4661-bfef-dc5cd0aeeefa.png)

Veri setindeki emotion sayılarını gösteren bir grafik.

![image](https://user-images.githubusercontent.com/33186246/159139481-e5766c14-0594-4778-9780-b70014817172.png)

Veri setinde bulunan örneklerin bir kısmı.


Modelleme Aşaması;
İlk olarak veri setinin içindeki bulunan eğitim(train) ve test örnekleri modellemeye uygun hale getirildi.

![image](https://user-images.githubusercontent.com/33186246/159139518-4c69b74d-6f08-4361-8120-b2db3af110e2.png)

Veri seti örnek değerleri.

Daha sonra 6 katmanlı bir evrişimli yapay sinir ağı modeli kuruldu. Katmanlarda ReLu aktivasyon fonksiyonundan yararlanıldı. Çalışmada kullanılan verisetinde çok fazla veri vardır. Bu yüzden çok katmanlı bir sinir ağı kullanıldı. ReLu aynı anda tüm nöronları aktive etmediğinden dolayı daha verimli sonuç vereceği için tercih edildi. Çıkış katmanımızda 7 adet duygu ifadesi olduğu için her duygu sınıfına ait bir olasık döndürmelidir. Bu istekleri karşılayacağı için çıkıl katmanında softmax aktivasyon fonksiyonundan yararlanıldı. Eğitim performansının artması için katmanlarda Dropout kullanılarak ağ modellemesinde sadeleştirmeye gidildi. Modelleme kurulmuş oldu.

![image](https://user-images.githubusercontent.com/33186246/159139540-7f48e101-ceec-4bf3-974f-226a8b3b6706.png)

Evrişimli sinir ağı modeli kurulması.

Kurulan modellemenin çalıştırılma işlemlerine geçildi. Epochs değeri 10, batchSize değeri ise 128 verildi. Olası bir Overfitting’i engellemek için Kerasa ailt EarlyStopping ve ReduceLROnPlateau kütüphanelerinden yararlanıldı. Eğitim sonucu model.h5 adlı dosyaya kaydedildi. Evrişimli sinir ağı modeli çalıştırılmış oldu.

![image](https://user-images.githubusercontent.com/33186246/159139560-f6db083c-e88f-413d-80b8-57bae4623e5f.png)

Evrişimli Sinir Ağı modeli çalıştırılması.


Grafik Analizleri;

Kurulan modellemenin sonucu olarak kayıp ve doğruluk değerleri grafikleştirildi. Grafikte görüldüğü gibi eğitim ve test verilerine göre loss ve acc değerlerinin sonuçları birbirine yakındır. Bunun sonucu olarak başarılı bir modelleme gerçekleşmiştir.

![image](https://user-images.githubusercontent.com/33186246/159139579-e403c606-1d38-4290-becc-9a49329d85bd.png)

Kayıp ve doğruluk grafikleri.


Elbette modellemedeki epochs, batchsize gibi değerleri değiştirerek daha başarılı sonuçlar elde edilebilir. Hiçbir zaman %100 bir başarı sağlanamaz ama her zaman daha fazla başarılı sonuç çıkarmak için bir şans vardır.

![image](https://user-images.githubusercontent.com/33186246/159139589-29475697-ccf8-4cc7-bb27-76e8ab308ac9.png)

Kayıp ve doğruluk sayısal değerleri.

Modellemenin kayıp ve doğruluk değerlerinin sayısal karşılığı resim22.5’da mevcuttur. Train loss ve Test Loss değerleri ile Train Acc ve Test Acc değerleri arasındaki fark ve oran daha net görülmektedir.



Test Sonuçları;
Modelleme sonucu test aşamasında ilk olarak yüklenecek görselde bulunan yüzün konumu face_recognition kütüphanesi kullanılarak algılandı.

![image](https://user-images.githubusercontent.com/33186246/159139603-97be2db6-1625-4a06-84e2-e28b7f7c84af.png)


Daha sonra algılanan yüz kurulan modelleme ağırlıklarına göre analiz edildi ve grafiksel sonuçları ekrana yazdırılması için keras image kütüphanesinden yararlanılarak gerekli kodlar yazıldı.

![image](https://user-images.githubusercontent.com/33186246/159139612-2c9f89da-7aa1-40f5-911e-7142cb747e98.png)


Test sonuçlarını görülmesi için birkaç örnek aşağıdaki gibidir.

![image](https://user-images.githubusercontent.com/33186246/159139624-63d2c7ac-0d95-4936-9370-3640ea806db4.png)

![image](https://user-images.githubusercontent.com/33186246/159139629-c6e916b5-3999-41d7-8ec9-1a67c421e015.png)

![image](https://user-images.githubusercontent.com/33186246/159139630-d1a8e50a-fc20-442c-832f-0a24d5cfdb61.png)

![image](https://user-images.githubusercontent.com/33186246/159139637-a02b65b2-266c-4ad5-8177-8226cbf5f962.png)

