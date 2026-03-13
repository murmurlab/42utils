# Flatpak Yapılandırma Rehberi

Bu doküman, Flatpak uygulamalarının ve verilerinin sistem kotasını doldurmasını önlemek amacıyla `/sgoinfre` alanına taşınması ve yönetilmesi adımlarını kapsar.

## 1. Kurulum ve Yönlendirme (Symlink)

Uygulama dizinini temizleyip `/sgoinfre` alanına sembolik bağlantı oluşturun ve Flathub deposunu ekleyin:

```bash
# Eski dizini silin ve sgoinfre üzerinde yenisini oluşturun
rm -rf ~/.local/share/flatpak
mkdir -p /sgoinfre/$USER/flatpak

# Sembolik bağlantıyı (symlink) kurun
ln -s /sgoinfre/$USER/flatpak ~/.local/share/flatpak

# Flathub deposunu kullanıcı seviyesinde ekleyin
flatpak --user remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

**Doğrulama:**
Aşağıdaki komutla bağlantının doğru kurulduğunu teyit edebilirsiniz:
```bash
ls -ld ~/.local/share/flatpak
# Beklenen Çıktı: ... ~/.local/share/flatpak -> /sgoinfre/USER/flatpak
```

## 2. Uygulama Yönetimi

Gerekli yapılandırma sonrası kurulumlar otomatik olarak `/sgoinfre` alanına yapılacaktır.

```bash
# Örnek Uygulama Kurulumu (Örn: Zen Browser)
flatpak --user install flathub app.zen_browser.zen

# Uygulama Çalıştırma
flatpak run app.zen_browser.zen
```

> **Uyarı (`homemover.sh` Kullanıcıları İçin):**
> Homemover betiği çalıştırılırken, `.local/share` dizininin taşınmasını isteyen soruya **Hayır (`n`)** yanıtını verin. `.local/share/flatpak` halihazırda bir symlink olduğu için iç içe sembolik bağlantılar Flatpak yapısını bozacaktır.

## 3. Sorun Giderme ve Sıfırlama

Flatpak depolarında "No remote refs found" gibi hatalar veya bağlantı bozulmaları yaşanırsa, sistemi tamamen sıfırlamak için şu adımları izleyin:

```bash
# 1. Mevcut tüm uygulamaları kaldırın
flatpak --user uninstall --all

# 2. Hatalı dizinleri/bağlantıları silin
rm -rf ~/.local/share/flatpak /sgoinfre/$USER/flatpak

# 3. Baştan kurulum adımlarını tekrarlayın
mkdir -p /sgoinfre/$USER/flatpak
ln -s /sgoinfre/$USER/flatpak ~/.local/share/flatpak
flatpak --user remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
