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

Rocky Linux tizimida vaqtni sinxronlashtirish uchun standart `/etc/chrony.conf` konfiguratsiya fayli mavjud bo‘lib, u tizim o‘rnatilgandan so‘ng vaqt sinxronizatsiyasini ishlatishga tayyor holatda taqdim etiladi.

Quyida Rocky Linux 10 uchun standart RPM paketi bilan birga keladigan konfiguratsiya keltirilgan.

```
cat /etc/chrony.conf
```

{% hint style="info" %}
## `Use public servers from the pool.ntp.org project.`

## `Please consider joining the pool (https://www.pool.ntp.org/join.html).`

`pool 2.rocky.pool.ntp.org iburst`

## `Use NTP servers from DHCP.`

`sourcedir /run/chrony-dhcp`

## `Record the rate at which the system clock gains/losses time.`

`driftfile /var/lib/chrony/drift`

## `Allow the system clock to be stepped in the first three updates`

## `if its offset is larger than 1 second.`

`makestep 1.0 3`

## `Enable kernel synchronization of the real-time clock (RTC).`

`rtcsync`

## `Enable hardware timestamping on all interfaces that support it.`

`#hwtimestamp *`

## `Increase the minimum number of selectable sources required to adjust`

## `the system clock.`

`#minsources 2`

## `Allow NTP client access from local network.`

`#allow 192.168.0.0/16`

## `Serve time even if not synchronized to a time source.`

`#local stratum 10`

## `Require authentication (nts or key option) for all NTP sources.`

`#authselectmode require`

## `Specify file containing keys for NTP authentication.`

`#keyfile /etc/chrony.keys`

## `Save NTS keys and cookies.`

`ntsdumpdir /var/lib/chrony`

## `Specify directory for log files.`

`logdir /var/log/chrony`
{% endhint %}
