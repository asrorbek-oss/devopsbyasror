# 🕒 Chrony’ni sozlash (vaqtni sinxronlashtirish xizmati)

### Kirish

Vaqtni aniq sinxronlashtirish zamonaviy Linux tizimlarining to‘g‘ri ishlashi uchun juda muhim. Kerberos autentifikatsiyasi, TLS sertifikatlarini tekshirish, taqsimlangan ma’lumotlar bazalari, loglarni vaqt bo‘yicha moslashtirish va klasterlarni boshqarish kabi xizmatlar tizim soatining aniq ishlashiga bog‘liq.

Rocky Linux operatsion tizimida `chrony` standart NTP (Network Time Protocol) dasturiy yechimi hisoblanadi va eski `ntpd` xizmatining o‘rnini egallaydi.

`chrony`¹ tarmoq ulanishi uzilib turadigan yoki tizimlar tez-tez uyqu rejimiga o‘tib, qayta faollashadigan muhitlarda ishlash uchun ishlab chiqilgan.

Barqaror tarmoq sharoitida `chrony` taxminan 35 mikrosoniya aniqlikka erishadi, `ntpd` esa taxminan 234 mikrosoniya aniqlikni ta’minlaydi.¹ Bundan tashqari, `chrony` apparat vaqt belgilarini (hardware timestamping) va Network Time Security (NTS) texnologiyasini qo‘llab-quvvatlaydi. `ntpd` esa ushbu imkoniyatlarni qo‘llab-quvvatlamaydi.

Ushbu qo‘llanmada Rocky Linux tizimida `chrony` xizmatini sozlashning asosiy jihatlari ko‘rib chiqiladi, jumladan:

* NTP vaqt manbalarini tanlash.
* Vaqt sinxronizatsiyasi bilan bog‘liq muammolarni aniqlash va diagnostika qilish.
* Apparat vaqt belgilarini (hardware timestamping) yoqish.
* `chrony` xizmatini mahalliy NTP server sifatida sozlash.
* Internetga ulanmagan (air-gapped) tarmoqlarda vaqt sinxronizatsiyasini tashkil etish.

## chrony o‘rnatilganligini tekshirish:

```
rpm -q chrony
```
