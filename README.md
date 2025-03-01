# HyperSpace AI Kurulum

# Sunucumuzu bir güncelleyelim
      sudo apt update -y && sudo apt upgrade -y

# Offical kurulum çekelim
      curl https://download.hyper.space/api/install | bash

#  Screen aç 
      screen -S hyper

# Yetki verelim
      source /root/.bashrc

# Script başlatalım
      aios-cli start

#  Screenden çıkalım (geri girmek istersen screen -r hyper)
      CTRL A + D 

  # Bir daha yetki verelim
      source /root/.bashrc

#  Browserdan veya uygulamadan aldığımız keyi import etmek için dosya oluşturalım. Aşağıdaki kodu girince bomboş bir sayfa açılacak, browserdan export ettiğiniz keyi oraya yapıştıracaksınız.
      nano my.pem


#  Browserdan export ettiğimiz key'i buraya yapıştıralım
      Daha sonra CTRL X + Y ve enter'a basalım yani kaydedip çıkalım

![image](https://github.com/user-attachments/assets/ddd1e6fb-5552-4d0e-8dfb-9fa1d1d063fd)



#  Oluşturduğumuz dosyayı import edelim
      aios-cli hive import-keys ./my.pem

#  Giriş yapalım
      aios-cli hive login

#  Model listesine bakalım
      aios-cli models available
      
![image](https://github.com/user-attachments/assets/dbc9daf5-77c3-430f-b398-f4b42b597776)
      

#  Modelleme indirelim (gördüğüm kadarıyla aşağıdaki model en çok tercih edilen o yüzden değiştirmedim)
      aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf


Daha sonra Tier seçmemiz gerekiyor. Neye göre seçeceğiz? Eğer sunucumuzun GPU memory gücü düşükse 5 yüksekse 1.
1: 30GB
2: 20GB 
3: 8GB 
4: 4GB
5: 2GB

![image](https://github.com/user-attachments/assets/5d042ee5-d886-4c45-b693-2be7310c9ae8)


#  Yukardaki bilgiler ışığında Tier seçelim
      aios-cli hive select-tier 5

#  Bağlantı kuralım
      aios-cli start --connect

#  Tekrardan screen içine girip logları control edelim
      screen -r hyper



**ÇALIŞTIĞINI NASIL ANLARIM?**
Örnek çıktı böyle olmalı:

![image](https://github.com/user-attachments/assets/37795aba-27f2-4e93-a228-af97a690932c)



**Dün gece çalışıyordu birden durdu puan gelmiyor ne yapmam lazım?**

Aşağıdaki kodları tekrar taker taker gir:
- CTRL + C ile screen içi stop
- aios-cli start
- CTRL + A + D
- source /root/.bashrc
- aios-cli hive login
- aios-cli models add hf:TheBloke/phi-2-GGUF:phi-2.Q4_K_M.gguf
- aios-cli hive select-tier 5
- aios-cli start --connect
