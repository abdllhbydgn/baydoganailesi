# Baydoğan Ailesi sitesi — çalışma kuralları ve harita

Canlı: https://abdllhbydgn.github.io/baydoganailesi/ (GitHub Pages, statik). İki dosya: `index.html` (ana sayfa) ve `soyagaci.html` (soyağacı).
Dosyalarda büyük base64 resimler (logo) var — **tamamını okuma**; `grep -n` ile bul, uzun satırları `awk '{print substr($0,1,200)}'` ile kısaltarak oku.

## Kurallar
- **Logoya dokunma.** Firestore'daki fotoğrafları ve soyağacı verisini silme/bozma.
- Fotoğraflar ve soyağacı **yalnız aile yöneticisine** açık: `FAMILY_ADMINS = ['abdllhbydgn@gmail.com']` (iki dosyada da). Misafire: fotoğraf yerinde "Üzgünüz, aileden olmadığınız için fotoğrafları göremezsiniz", soyağacında "Bu bölüme giriş izniniz yoktur".
- Firebase projesi `baydogan-ailesi` Arapça sitesiyle ortak (Arapça verileri `ar_*` koleksiyonlarında). Aile verisi: `photos` (base64 fotoğraf belgeleri), `soyagaci_persons`. Kurallar Firebase konsolunda; okuma da yalnız yöneticiye.
- Dal `claude/selam-pwr5q1` → commit → push → main'e PR → birleştir. Kullanıcıya Türkçe açıkla, 2–3 dk sonra Ctrl+F5 de. Commit/PR metnine model adı yazma.

## Harita
- `index.html`: CSS `<style>` (sonunda "CANLI TEMA" bloğu: aurora, altın tozları, ikonlar, sayaçlar, kilit panelleri). JS: `FAMILY` (aile kartları), `watchPhotos` (yalnız yöneticide fotoğraf aboneliği), `renderAllPhotos`, `uploadPhoto`, `onAuthStateChanged`, `showFamilyNotice` (soyağacı uyarısı), `liveTheme`.
- `soyagaci.html`: `seedData()` (e-Devlet kayıtlarından kişiler), `load()` (yerel önbellek + bulut), `startTree`/`lockTree`/`#treeGate` (erişim kilidi), `render()`.
