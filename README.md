# Project Discovery Subfinder: Kapsamlı Rehber

## Giriş

Subfinder, Project Discovery tarafından geliştirilen güçlü bir subdomain keşif aracıdır. Bu blog yazısında, Subfinder'ın tüm özelliklerini, parametrelerini ve kullanım senaryolarını detaylı bir şekilde inceleyeceğiz.

## Subfinder Nedir?

Subfinder, pasif subdomain keşfi için tasarlanmış hızlı ve güvenilir bir araçtır. Go programlama dili ile yazılmıştır ve çeşitli kaynaklardan subdomain bilgisi toplayarak kapsamlı bir keşif sağlar.

## Kurulum

Subfinder'ı kurmak için aşağıdaki yöntemlerden birini kullanabilirsiniz:

1. Go ile kurulum:
   ```
   go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
   ```

2. GitHub'dan indirme:
   ```
   git clone https://github.com/projectdiscovery/subfinder.git
   cd subfinder/v2/cmd/subfinder
   go build .
   mv subfinder /usr/local/bin
   ```

3. Docker ile kullanım:
   ```
   docker pull projectdiscovery/subfinder:latest
   ```

## Temel Kullanım

Subfinder'ın en basit kullanımı şu şekildedir:

```
subfinder -d example.com
```

Bu komut, example.com için subdomain'leri bulacak ve gösterecektir.

## Subfinder Parametreleri

Subfinder, çeşitli parametrelerle özelleştirilebilir. İşte en önemli parametreler ve açıklamaları:

1. `-d, -domain string`: Taranacak domain'i belirtir.
   Örnek: `subfinder -d example.com`

2. `-dL, -list string`: Taranacak domain'lerin bulunduğu dosya.
   Örnek: `subfinder -dL domains.txt`

3. `-o, -output string`: Sonuçları kaydetmek için dosya adı.
   Örnek: `subfinder -d example.com -o results.txt`

4. `-oJ, -json`: Sonuçları JSON formatında kaydetmek için.
   Örnek: `subfinder -d example.com -oJ`

5. `-oD, -output-dir string`: Sonuçları kaydetmek için dizin.
   Örnek: `subfinder -d example.com -oD ./results`

6. `-r, -resolvers string`: Özel DNS çözümleyicileri dosyası.
   Örnek: `subfinder -d example.com -r resolvers.txt`

7. `-nW, -nw`: Wildcard subdomainleri göstermez.
   Örnek: `subfinder -d example.com -nW`

8. `-t, -threads int`: Eşzamanlı görev sayısı (varsayılan: 10).
   Örnek: `subfinder -d example.com -t 20`

9. `-timeout int`: Zaman aşımı süresi (saniye).
   Örnek: `subfinder -d example.com -timeout 30`

10. `-v, -verbose`: Ayrıntılı çıktı modu.
    Örnek: `subfinder -d example.com -v`

11. `-all`: Tüm kaynakları kullanarak tarama yapar.
    Örnek: `subfinder -d example.com -all`

12. `-recursive`: Recursive subdomain taraması yapar.
    Örnek: `subfinder -d example.com -recursive`

## Gelişmiş Özellikler ve Parametreler

1. `-silent`: Sadece sonuçları gösterir, banner ve diğer bilgileri gizler.
   Örnek: `subfinder -d example.com -silent`

2. `-exclude-sources string`: Belirli kaynakları hariç tutar.
   Örnek: `subfinder -d example.com -exclude-sources dnsdumpster,virustotal`

3. `-max-time int`: Maksimum çalışma süresi (dakika).
   Örnek: `subfinder -d example.com -max-time 10`

4. `-proxy string`: HTTP proxy kullanımı.
   Örnek: `subfinder -d example.com -proxy http://127.0.0.1:8080`

5. `-cs, -collect-sources`: Sadece kaynakları toplar, subdomain'leri çözmez.
   Örnek: `subfinder -d example.com -cs`

6. `-active`: Aktif kaynakları kullanarak tarama yapar.
   Örnek: `subfinder -d example.com -active`

7. `-oI, -ip`: IP adreslerini de çıktıya ekler.
   Örnek: `subfinder -d example.com -oI`

8. `-config string`: Özel yapılandırma dosyası kullanır.
   Örnek: `subfinder -d example.com -config config.yaml`

9. `-raw`: Raw subdomain sonuçlarını gösterir.
   Örnek: `subfinder -d example.com -raw`

10. `-version`: Subfinder sürümünü gösterir.

## Kullanım Senaryoları

1. Basit Subdomain Taraması:
   ```
   subfinder -d example.com
   ```

2. Çoklu Domain Taraması:
   ```
   subfinder -dL domains.txt -o all_subdomains.txt
   ```

3. Ayrıntılı ve JSON Formatında Çıktı:
   ```
   subfinder -d example.com -v -oJ -o example_subdomains.json
   ```

4. Özel DNS Çözümleyiciler ile Tarama:
   ```
   subfinder -d example.com -r custom_resolvers.txt
   ```

5. Tüm Kaynakları Kullanarak Recursive Tarama:
   ```
   subfinder -d example.com -all -recursive
   ```

6. IP Adresleri ile Birlikte Subdomain Taraması:
   ```
   subfinder -d example.com -oI -o subdomains_with_ips.txt
   ```

7. Belirli Kaynakları Hariç Tutarak Tarama:
   ```
   subfinder -d example.com -exclude-sources dnsdumpster,virustotal
   ```

## Subfinder'ın Güçlü Yönleri

1. Hız: Go dilinde yazılmış olması sayesinde çok hızlı çalışır.
2. Çok Kaynaklı: Birçok farklı kaynaktan veri toplayarak kapsamlı sonuçlar sunar.
3. Pasif Tarama: Hedef sisteme doğrudan istek yapmadan çalışabilir.
4. Özelleştirilebilirlik: Çeşitli parametrelerle farklı senaryolara uyarlanabilir.
5. Entegrasyon: Diğer güvenlik araçlarıyla kolayca entegre edilebilir.

## Sınırlamalar ve Dikkat Edilmesi Gerekenler

1. Pasif Tarama Sınırlamaları: Bazı subdomain'ler yalnızca aktif tarama ile bulunabilir.
2. API Limitleri: Bazı kaynaklar API kullanım limitlerine sahip olabilir.
3. Yasal Uyarılar: Subdomain taraması yasal sınırlamalar içerebilir, her zaman izin alınmış domainlerde kullanın.

## Subfinder'ı Diğer Araçlarla Birlikte Kullanma

Subfinder, diğer güvenlik araçlarıyla birlikte kullanıldığında daha etkili olabilir. Örneğin:

1. httpx ile canlı subdomainleri kontrol etme:
   ```
   subfinder -d example.com | httpx
   ```

2. nmap ile port taraması:
   ```
   subfinder -d example.com | nmap -iL -
   ```

3. nuclei ile güvenlik taraması:
   ```
   subfinder -d example.com | nuclei -t nuclei-templates/
   ```

## Sonuç

Subfinder, subdomain keşfi için güçlü, hızlı ve güvenilir bir araçtır. Doğru parametrelerle kullanıldığında, güvenlik testleri, penetrasyon testleri ve bug bounty programları için çok değerli bir kaynak olabilir. Bu rehberde öğrendiklerinizle artık Subfinder'ı etkili bir şekilde kullanabilir ve hedef sistemlerin kapsamını daha iyi anlayabilirsiniz.

Unutmayın, her güçlü araç gibi Subfinder da sorumlu ve etik bir şekilde kullanılmalıdır. İyi keşifler!
