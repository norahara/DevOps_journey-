## Disk quota - nazariy va amaliy 

### < Nazariy qism />

- Disk quota nima? 💿

> Disk quotasi bu foydalanuvchilar yoki guruhlar uchun diskdan foydalanish cheklovini qo`yadi nimaga kerak deyilganda bular serverlarni bir foydalanuvchi tomonida to'ldirib tashlashni oldini olib server qulash xavfini kamaytiradi 
misol uchun serverda 10 GB joy bor agar disk quotalanmasa bir foydalanuvchi uni to'ldirib qo'yishi va server ishdan chiqishi mumkin

- Disk quotasi nimani va qanday cheklaydi deyilgan savol javobi quyidagicha:

  Disk quota odatda 2 xil resursni cheklaydi:
  
  1. Block quota (disk hajmi)
  2. Inode quota (fayllar soni) 

  Inode — bu fayl haqidagi ma’lumotlar pasporti 📄
Faylning o‘zi EMAS, balki uning tavsifi.
  Inode nimalarni saqlaydi?

    1. Fayl hajmi

    2. Egasini (owner)

    3. Ruxsatlari (permissions)

    4. Yaratilgan / o‘zgartirilgan vaqti

    5. Diskda qayerda joylashgani (qaysi blocklarda)

  ![inode](./images/T1.png) 

  Inode tartib raqami (har bitta fayl bitta inode)

  ![inode](./images/T12.png) 

  2️⃣ Disk block nima?

    Disk block — bu diskdagi real joy, fayl ma’lumoti saqlanadigan qism 📦

     Fayl ma’lumotlari (text, video, rasm) shu yerda yotadi

        O‘lchami odatda:

                4KB

                8KB
                
    Muommo chiqaruvchi vaziyat shundaki Inode yoki Blockning ikklasidan bittasi tugashi ham xotirada joy qolmaganlik xatosini chiqaradi

### < Amaliy qism />

    - Disk quotalarini sozlash

Disk quotalarini o`rnatish uchun /etc/fstab fayliga o'zgartirish va qo'shimchalar qo'shiladi Undan oldin bir nechta amallar bajarilishi kerak 

  Men bu o`rganishim davomida quyidagi vazifalarni bajardim bular:
  - logic volume lar bilan ishlash
  - file systemni disklarga ajratish
  - /var /home kabi fayllarni alohida disklarga ajratish
  - disk quotalarni tayinlash 
  - userlarga diskdan foydalanish uchun cheklov o`rnatish

  filesystem ni o`rganish jarayoni shularni tajriba qilib ko'rdim

### logic volume lar bilan ishlash
  - Diskni tekshirish

  ![image](./images/T13.jpg) 

  - /var katalogi uchun 5g disk ajratish quyidagi buyruq orqali

  > lvcreate -L 5G -n var_lv ubuntu-vg

  ![image](./images/T14.jpg) 

  - filesystem  berish uchun: 
  > mkfs.ext4 /dev/ubuntu-vg/var_lv

  ![image](./images/T15.png)

  - yangi diskni vaqtinchalik katalogga mount qilish bu /var katalogini ustiga yozilib ma'lumotlar o'chib ketishini oldini oladi.

  ![alt text](./images/T16.png) 
