# GNOME Theming Rehberi

Bu doküman, kısıtlı yetkilere sahip ortamlarda (Örn: 42 Okulları) GNOME masaüstü özelleştirme adımlarını içerir.

## 1. Hazırlık ve Dizinlerin Oluşturulması

Sistemin temaları ve ikonları yerel kullanıcı seviyesinde tanıması için gerekli dizinleri oluşturun:

```bash
mkdir -p ~/.themes ~/.icons
```
> **Not:** İndirdiğiniz arşivleri (.zip, .tar.gz vb.) dışa aktarıp, indirdiğiniz içeriğin türüne göre `~/.themes` (GTK/Shell Temaları) veya `~/.icons` (İkon/İmleç Setleri) dizinlerine taşımanız yeterlidir.

## 2. Özel Tema Oluşturma (Themix/Oomox)

Kendi renk paletinizi oluşturmak isterseniz **Themix** (eski adıyla Oomox) kullanabilirsiniz. Kurulum için Flatpak'in `/sgoinfre` üzerinde yapılandırıldığından emin olun (Bkz: `flatpak/flatpak.md`).

```bash
# Kurulum
flatpak --user install flathub com.gitlab.themix_project.Oomox

# Çalıştırma
flatpak run com.gitlab.themix_project.Oomox
```

> Themix üzerinden temanızı oluşturup **Export Theme** butonuna tıklayarak doğrudan `~/.themes` dizinine aktarabilirsiniz.

## 3. GNOME Eklentileri (Extensions)

Shell temasını (üst panel, dock ve uygulama menüleri) değiştirebilmek için **User Themes** eklentisi zorunludur.

1. `extensions.gnome.org` adresinden veya **Extensions** uygulaması üzerinden **User Themes** eklentisini aktif konuma getirin.
2. *Önerilen ek eklentiler:* **Dash to Dock** (Özelleştirilebilir dock), **Blur My Shell** (Panel bulanıklaştırma).

## 4. Temaların Uygulanması

1. **GNOME Tweaks** uygulamasını açın. (Sistemde yüklü değilse okul ortamında genelde bulunur).
2. **Appearance (Görünüm)** sekmesine gidin.
3. İlgili bölümlerden yüklediğiniz bileşenleri seçin:
   - **Applications:** GTK (Pencere/Uygulama) teması
   - **Icons:** İkon seti
   - **Cursor:** İmleç teması
   - **Shell:** Panel ve menü teması (Sadece User Themes aktifken çalışır)
