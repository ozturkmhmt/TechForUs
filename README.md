# TechForUs — Statik + Decap CMS Çok Yazarlı Blog

Profesyonel görünümlü, Cloudflare Pages üzerinde *build gerektirmeyen* (sıfır npm) bir blog starter’ı.
Yazarlar `/admin` sayfasından GitHub ile giriş yaparak yazı ekleyebilir.

## Nasıl Çalışır?
- Yazılar: `content/posts/<slug>.md` (Markdown)
- Anasayfa listesi: `content/posts_index.json`
- `index.html` bu JSON'u okuyup kartları oluşturur, `post.html` ise tek yazıyı render eder.
- CMS: `/admin` (Decap CMS). `admin/config.yml` içinde GitHub repo ayarını güncelleyin.

## Kurulum
1) Bu klasörü bir GitHub reposuna yükleyin (ör. `techforus`).  
2) `admin/config.yml` içindeki `repo: <GITHUB_USERNAME>/techforus` satırını kendi kullanıcı/organizasyon adınızla değiştirin.  
3) Cloudflare Pages → **Create a project** → **Connect to Git** → framework **None**, build **boş**, output **/**.  
4) `/admin` sayfasına girince GitHub auth için GitHub OAuth App gerekebilir. Decap CMS'in GitHub backend'iyle çalışmak için GitHub'da OAuth uygulaması oluşturup callback URL'lerini ayarlayın (veya Cloudflare Pages Functions/Workers ile proxy).

## Yazı Yayın Akışı
- `/admin` → **Posts** → New Post → slug otomatik önerilir → **Publish**.  
- Aynı CMS ekranında **Posts Index** → Liste'ye postun özetini ekleyin (slug eşleşmeli).  
- Commit/push sonrası Cloudflare Pages otomatik deploy eder.

## Notlar
- Harici bağımlılık: `marked` (CDN). İsterseniz vendor JS'yi `assets/` altına ekleyebilirsiniz.
- İleri seviye: GitHub API kullanan bir Cloudflare Worker ile `posts_index.json`'u otomatik oluşturabilirsiniz.
