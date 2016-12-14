# RASPBERRY PI- ARDUINO ANDROID-CONTROLLED RC-CAR ROVER WITH LIVE VIDEO STREAMING
# ----------------------------- Pi_CAR -----------------------------

[![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/yotubeT1.png)](https://youtu.be/J8r_bX_RNzU)


## Kullan�lan Malzemeler
<br>

Malzeme Ad�| Adet
----| ---- 
Arduino Nano| 1
Raspberry Pi| 1
Raspberry Pi Camera Mod�l�| 1
Wi-Fi Adapt�r| 1
L298N,BTS7960,L293 Motor S�r�c�| 1 yada 2 
DC MOTOR|  2  yada   4
12V Lipo Batarya| 1
Jumper Kablo | ~
Ara� �asi (G�vdesi)| 1
<br>

## Arduino:
### AMA� VE G�REVLER:
*	Arduino motorlar� kontrol etmek amac� ile kullan�lm��t�r.
*	Arduino ile raspberry pi usb �zerinden seri haberle�me yapmaktad�r.
*	Android telefonumuz �zerinde arduino�ya gidecek olan pwm aral��� hesaplan�p g�nderilmektedir.(Gelecek g�ncellemeler ve kullan�c�n�n pwm de�i�kenine daha kolay m�dahale edilmesi i�in)
*	A�a��da Raspberry pi, Raspberry pi Camera, Arduino, L298N Motor S�r�c�,Motorlar ve Bataryan�n devre ba�lant� �emas� g�sterilmi�tir. 

 
### ARDUINO KURULUMU VE PIN BA�LANTI �EMASI

* Arduino 'ya gelen veri do�rudan motorlara gidecek pwm aral��� olarak gelmektedir.PWM de�erinin yan�nda sadece arac�n y�n tayini i�in ` + (ileri)` ve ya `- (geri)` de�erini almaktad�r.
* Yukar�daki durum g�z �n�ne al�narak �e�itli modifikasyonlar yap�labilir.
* PWM aral��� `0-255` aras�ndad�r.
* Telefon �zerinden SA� VE SOL motor pwmlerini ve servo motor a��s�n� String bir �ekilde �rn:  200:200!888 �eklinde al�yoruz. Aradaki iki nokta �st �ste  `:` ve �nlem i�areti `!` ' e g�re b�lerek 3 elemanl� bir dizi olu�turuyoruz.
*  `!` den sonraki de�er, cameran�n ba�l� bulundu�u servo motor'un a�� de�erleridir. Bu �al��mada servo motor kullan�lmam��t�r.<br><br>
**Motor Hareket PWM Geli� Tipi ve Arac�n Durumlar�**<br>
�rn:
*  0:0      //stop
* 200:200     // ileri git. ( 2 motorda 200pwm ile �al���r )
*  -200:-200   //geri git. (2 motorda 200pwm ile �al���r)
*  200:-200   // sol motor 200 pwm ileri, sag motor 200 geri d�ner ( ara� kendi etraf�nda soldan sa�a do�ru d�ner)
* -200:200   // sol motor 200 pwm geri, sag motor 200 ileri d�ner ( ara� kendi etraf�nda sa�dan sola do�ru d�ner)
* 200:100    // ara� sa�a d�necek �ekilde hareket eder.<br><br>
 



[![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/youtbeT2.png)](https://youtu.be/D4ewbO-OGLY)

<p align="center"> <b>L298 - Dual Full Bridge Driver</b>
<img src="https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/wificontrol.png"  />
</p>
<p align="center"> <b>BTS7960 - 43A MOTOR DRIVE</b>
<img src="https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/BTS7960%20fritzing2.png"  />
</p>
<br><br>
* Arduino, Raspberry pi,Raspberry pi camera mod�l�, L298N motor s�r�c�, Motorlar, G�� kayna��n�n ba�lant�lar�n�  yukar�daki resimdeki gibi ger�ekle�tiriniz.
* Yukar�daki �ekildeki gibi arduino pin ba�lant�lar�n� ve raspberry pi ba�lant�s�n�  ger�ekle�tirdikten sonra yapmam�z gereken arduino kodlar�m�z� y�klemek olacakt�r.<br>
**Bunu s�ra ile �u  �ekilde yapabilirsiniz.<br>**

**I.** Arduino kodlar�n�n a��klamalar� ve ne i�e yarad��� ile ilgili detayl� bilgi kodlar�n i�inde mevcuttur.<br>

**II.** `androidToRaspberry.ino` adl� arduino kodumuzu bu [**linteken**](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/tree/master/androidToRaspberryTurkce) indirerek ve �ift t�klayarak a��n�z.<br>

**III.** A��lan proje dosyas�n� arduino' ya y�klemek i�in s�ra ile  sekmelerden `Tools` => `Board`  ve buradan kulland���n�z arduino modelinizi se�iniz.<br><br>


![Screen Shot RA1](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/ra1.png)
<br><br>
**IV.** Tekrar `Tools` sekmesinden takm�� oldu�unuz arduino' nuzun hangi port' a tak�l� oldu�unu g�steriniz.  `Tools` => `port`<br>

**V.** Yukar�daki ad�mlar� ger�ekle�tirdikten sonra �imdi program�m�z� arduino' muza y�kleyebiliriz.Sol �st k��ede `Upload` butonuna basarak y�kleme i�lemini tamamlam�� oluyoruz.<br><br>
![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/ra2.png)
<br><br>

## RASPBERRY PI:
### AMA� VE G�REVLER:

* Raspberry pi camera mod�l� kullanarak g�r�nt�n�n al�nmas� ve raspberry pi �zerinden telefona aktar�lmas�.
* Arduino ve Telefon aras�nda ba�lant�n�n kurulmas�.

### RASPBERRY PI KURULUMU:
Raspberry pi kurulumu olduk�a basittir.�ncelikle,

Win32DiskImager SD karta i�letim sistemi yazd�rmam�z i�in gerekli olan programd�r.
�ndirmek i�in [**T�klay�n�z**](http://www.gezginler.net/indir/win32-disk-imager.html)

## 1. Raspbian ��letim Sistemi �ndirme;
Raspberry pi mize kuraca��m�z ara� kontrol yaz�l�mlar�n�da i�inde bulunduran i�letim sistemini SD karta yazd�mam�z gerekmektedir.Burada D�KKAT edilmesi gereken nokta, a�a��da linkleri verilen i�letim sistemlerini se�erken elinizde bulunan Wi-Fi adapt�rlere g�re 
i�letim sistemini indirmeniz ve sd karta yazd�rman�zd�r.��letim sistemleri ve destekledikleri modemler a�a��da verilmektedir.

### Raspberry Pi 3  ��in indirilebilir i�letim sistemi
Raspberry pi 3 i�in 2 alternatif y�ntemimiz vard�r;<br>

1. si do�rudan raspberry pi �zerindeki dahili Wi-Fi kullanmak. <br>
2. Harici olarak USB Wi-Fi adapt�r kullanmak(Mesafe ve veri h�z� bak�m�ndan tavsiye edilen y�ntemdir. Tabi bu kullanaca��n�z Wi-Fi adapt�re g�re de�i�ebilir.)
<br>

### 1.Pi_CAR'I Raspberry pi 2 i�in ya da  raspberry pi 3'�n �zerindeki dahili Wi-Fi mod�l� kullanarak y�netmek istiyorsan�z.Bu [**linteki**](https://drive.google.com/file/d/0B6yjwSAqPTgfX1dsaVVJZThEN2c/view?usp=sharing) i�letim sistemini indirerek SD karta yazd�r�n�z.



### 2.Pi_CAR'I Raspberry pi 3 '�n  �zerinden harici olarak takt���n�z Wi-Fi mod��� kullarak y�netmek istiyorsan�z.Bu [**linteki**](https://drive.google.com/file/d/0B6yjwSAqPTgfYkhxWEN2dXBIQlU/view?usp=sharing) i�letim sistemini indiriniz.



Bu se�enek i�in elimizde bulunan ve test etti�imiz Wi-Fi cihazlar� ve �ipsetleri
<br>

Test Edilen cihazlar|CHIPSET
---------- | --------
Dark WDN300A5 | RTL8192CU
Tenda UH150 | RT2870/RT3070
AWUS036NH | RT2870/RT3070
<br>

Desteklenen di�er �ipsetler ve cihazlar i�in detayl� bilgi:http://elinux.org/RPi_USB_Wi-Fi_Adapters

## 2. ��letim Sistemini Micro-SD Kart�a Yazd�rma
�ndirdi�imiz imaj dosyas�n� zip i�erisinden ��kar�yoruz. Ard�ndan daha �nce indirdi�imiz win32diskImager program�n� a��yoruz. �maj dosyam�z� belirtilen yerden se�iyoruz.

![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/win32diskimager.jpg)

Sd kart�n�z�n bilgisayara tak�l� oldu�undan emin olduktan sonra Device k�sm�nda g�rebilirsiniz. Ard�ndan Write butonuna t�klay�p yazma i�lemini ba�lat�yoruz. Yazma i�lemi yakla��k 2-3 dk s�rmektedir. Yazma i�leminin bitmesini yeni a��lan pencerede "Write Succesful." yaz�s�n� g�rene kadar bekleyiniz.


![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/Write%20Succesful.png)
## 3.Ba�lant�lar ve �al��t�rma

Yazma i�lemi tamamland�ktan sonra SD kart�n�z� bilgisayardan ��kart�p Raspberry pi'nize takabilirsiniz.
Art�k yapman�z gereken SADECE Raspberry' nize USB �zerinde bir Arduino tak�p  gerekli g�� ve motor s�r�c�leri ba�lant�lar�n� yapt�ktan sonra araca monte etmenizdir.
<br>
Video'lu anlat�m: 
<br>
[![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/youtube%20play2.png)](https://youtu.be/yNLug0DhQlc)

## ANDROID:

### AMA� VE G�REVLER�:
* Raspberry pi ve arduino ile yap�lm�� olan rc-araban�n kontrol�n� sa�lamak.
* Kullan�c� i�in sade ve kolay g�rsel aray�z.
* Raspberry pi �zerinden kamera g�r�nt�s�n� alarak kullan�c�ya g�stermek.

### ANDROID UYGULAMA KURULUMU:
* Uygulaman�n kurulumu son derece basittir. Sadece yap�lmas� gereken **ANDROID GOOGLE PLAY** markette giri� yap�ld�ktan sonra arama kutucu�una, uygulamaya do�rudan eri�mek i�in `com.stackcuriosity.tooght` ve ya uygulama ismi `RC CONTROLLER WITH CAMERA` yazman�z yeterlidir.<br>

### UYGULAMA KULLANIMI VE �PUCULARI  <br>

#### Raspberry pi ba�lant� bilgileri
* Android uygulaman�z� indirdikten sonra sizi a�a��daki gibi bir ekran kar��layacakt�r.Art�k yapman�z gereken �ey sadece arac� kontrol etmek olacakt�r.
<br>
![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/Screenshot_20161208-155537.png)

Uygulaman�n �al��ma prensibini ve tan�t�m�n� k�saca a��klayal�m.

#### UYGULAMA DETAYLARI

##### 1. G�RSEL ARAY�Z�N A�IKLANMASI VE PROGRAMLAMA MANTI�I
* **Uygulamam�z 4 temel esasa dayanmaktad�r.** Bunlar;
  1. Arac�n y�n kontrol�n�n sa�lanmas�.<br>
  2. Kullan�c�ya ara� �zerindeki kameradan canl� g�r�nt�n�n aktar�lmas�.<br>
  3. Arac�n ba�lant� sinyal seviyesi g�stergesi.
  4. Fallow Me (�ok yak�nda).(Arac�n sahibini takip etmesi).<br>
* Bu d�rt temel esasa g�re 
*  Arac�n y�n kontrol�nde kullan�lan mant���n ana detaylar�n� `Arduino` b�l�mde anlatt�k.Android taraf�na bakan k�sm� ile a��klayacak olursak.Android taraf�nda, kullan�c� i�in `Seek bar (H�z ayar�)` , `Kamera A�ma / Kapama` ,`Wi-Fi durum g�stergesi`  ve `Y�n tu�lar�` mevcuttur.<br> ![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/Screenshot_description_githup.png)<br>
*  **Seek bar(H�z ayar�)** 15 dilimden olu�maktad�r ve h�z katsay�s� 17'dir.Yani seek bar' �n herbir hareketi pwm'de 17'nin katlar� �eklinde bir oynama yapmaktad�r.Seek bar 5. kademede ise �retilen pwm= 5*17 = 85 'tir.
*  **Men� tu�lar� (Kamera A�/Kapa ve WiFi G�stergesi)** Seekbar '�n yan�nda yer alan di�er ara� kontrol fonksiyonlar�;<br> Kamera g�r�nt�s�n� ara� �zerinden almam�za yarayan Kamera a�ma ve kapatma butonu " ![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/ic_eye.png) A� ", " ![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/ic_eye_off.png) KAPAT ", Ayn� �ekilde uygulamam�z�n Raspberry Pi �zerinde olu�turdu�umuz Wi-Fi a�a ba�lan�p ba�lan�lmad���n� g�steren bir g�sterge." ![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/ic_wifi_on.png) BA�LI DE��L", " ![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/ic_wifi_off.png) BA�LI "
*  **Y�n tu�lar�** seek bar(H�z ayar�)'dan al�nan verinin y�nlere ayr�lmas�n� sa�lar. Arac�n gidi� y�n�ne g�re pwm de�erinin ba��na `+` ve ya `-` i�areti getirilir. **�rn;**<br><br>
 200:200     // ileri git. ( 2 motorda 200pwm ile �al���r )<br>
 -200:-200   //geri git. (2 motorda 200pwm ile �al���r)<br>
 200:-200   // sol motor 200 pwm ileri, sag motor 200 geri d�ner ( ara� kendi etraf�nda soldan sa�a do�ru d�ner)<br>
 -200:200   // sol motor 200 pwm geri, sag motor 200 ileri d�ner ( ara� kendi etraf�nda sa�dan sola do�ru d�ner)<br>
 200:100    // ara� sa�a d�necek �ekilde hareket eder.<br><br> 
 * **Sinyal Seviye G�stergesi** Bu g�sterge telefon ile ara� aras�ndaki  ba�lant�n�n sinyal kalitesini ve uzakl��a g�re de�i�en sinyal �ekim seviyesinin kullan�c�ya g�sterilmesini sa�lar.

##### 2.SA�'A VE SOL'A D�N��LERDE HASSAS�YET
* Arac�m�z�n sa� �a�raz ve sol �apraz hareketleri yaparken d�n�� yap�lacak taraftaki motorlar�n pwm de�erleri d���r�l�r ve b�ylece motorlar�n daha yava� d�nmesi sa�lan�r.Bu sayede ara� istenilen hassasiyette �arpraz d�n��leri ger�ekle�tirebilir.**Bu d�n�� hareketlerinin hassasiyet ayarlamas� kullan�c�ya b�rak�lm��t�r.**
* �apraz d�n��lerin hassasiyetinin hesaplanmas�nda kullan�lan form�l : **`PWM DE�ER� - (PWM DE�ER� / PWM ORANI)`** 'd�r.
* PWM ORANI varsay�lan olarak `2` gelmektedir.
* PWM ORANI ayar�n�, kontrol ekran�n da sa� �st k��ede `Ayarlar` butonundan tekrar `Ayarlar` sekmesine basarak ula�abilirsiniz.<br>![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/device-2016-07-07-230804.png)<br>![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/device-2016-07-07-230848.png)<br><br>
* Girebilece�inz PWM ORANI aral��� **minimum ve maksimum olarak 1-4 aras�nda integer ve double tipinde** de�erlerdir.
 


### UYGULAMA ICON 'UMUZ:

![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/raspi_car.png)




## TEST V�DEO:
[![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/images/testvd1.png)](https://youtu.be/qbkH2KFcKqw)
[![Screen Shot](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/play_video2.png)](https://youtu.be/CT-hgXIPRIk)
<br><br>



-------------------------------------------------------------------------------------
<br><br>

#KISA VE �ZET KURULUM<br><br>
<p align="center"> <b>DETAYLI B�LG� VE  VE KURULUM AYRINTILARI ���N L�TFEN SAYFA BA�INDAN BA�LAYINIZ !!</b>
<img src="https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/raw.gif" alt="DETAYLI ANLATIM VE KURULUM" align="middle" />
</p>

## **ADIM 1:**
<br>
 1.Pi_CAR'I Raspberry pi 2 i�in ya da  raspberry pi 3'�n �zerindeki dahili Wi-Fi mod�l� kullanarak y�netmek istiyorsan�z.Bu [**linteki**](https://drive.google.com/file/d/0B6yjwSAqPTgfX1dsaVVJZThEN2c/view?usp=sharing) i�letim sistemini indirerek SD karta yazd�r�n�z.
<br>


 2.Pi_CAR'I Raspberry pi 3 '�n  �zerinden harici olarak takt���n�z Wi-Fi mod��� kullarak y�netmek istiyorsan�z.Bu [**linteki**](https://drive.google.com/file/d/0B6yjwSAqPTgfYkhxWEN2dXBIQlU/view?usp=sharing) i�letim sistemini indiriniz.
<br>

## **ADIM 2**
Arduino kontrol yaz�l�m�n� Bu [**linteken**](https://github.com/zafersn/WiFi-RC-Controller-With-Camera/tree/master/androidToRaspberryTurkce) indirerek
Arduino' ya y�kleyiniz.

## **ADIM 3**
Android kontrol yaz�l�m�da  Bu [**linteken**](https://play.google.com/store/apps/details?id=com.stackcuriosity.tooght) indirerek
telefonunuza  y�kleyiniz.
<br><br><br>
**ve  i�lem tamam arduino motor s�r�c�leri aras�ndaki ba�lant�lar� do�ru yapt�ysan�z art�k arac� kontrol etmeye ba�layabilirsiniz.**

<p align="center">
 <a href="https://play.google.com/store/apps/details?id=com.stackcuriosity.tooght"><img src="https://github.com/zafersn/WiFi-RC-Controller-With-Camera/blob/master/V2.0/images/Google.png"/></a>
</p>

