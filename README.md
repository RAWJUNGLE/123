M8C для клонов игровых приставок Data Frog R36S (a.k.a. K36) [Подробнее о клонах](https://handhelds.miraheze.org/wiki/R36S_Clones)

M8C for clones of video game consoles Data Frog R36S (a.k.a. K36) [Learn more about clones](https://handhelds.miraheze.org/wiki/R36S_Clones)

Готовый образ для SD-карты объёмом 32GB доступен по ссылке -  [GOOGLE DRIVE](https://drive.google.com/file/d/1UfzRb_OIGDza3Qki4kZj9Egg8YcPl2uP/view?usp=drive_link)

A ready-made image for a 32GB SD card is available at the link - [GOOGLE DRIVE](https://drive.google.com/file/d/1UfzRb_OIGDza3Qki4kZj9Egg8YcPl2uP/view?usp=drive_link)

Есть проблемы со звуком и задержками, если вы знаете как исправить, напишите мне в issue.
There are problems with sound and delays, if you know how to fix it, write to me in the issue.

Ручная установка клиента M8C (Dirtywave M8) для клонов игровых консолей R36S (a.k.a K36). Да это клон, клона. 

У вас должна быть установлена ArkOS_K36_v2.0_011182025
Вам потребуется wifi свисток, usb hub с дополнительным питанием, клавиатура (не rgb), usb type-c -> usb 2.0 переходник. 
Подключите всё это к K36. 
Включите K36, зайдите в пункт OPTIONS, включите WIFI, после подключения, включите Enable Remote Services.
Далее выйдете в главное меню и нажмите START, далее Quit, Quit Emulation Station
Вы попадёте в консоль, нажмите на клавиатуре ALT + F2
Login: ark
Password: ark (пароль никак не отображается, вводите без ошибок) 
Дальше вручную заполняйте комманды которые привидены ниже. 


Manualy setup M8C Client for clones R36S (a.k.a K36). Yes this is clone of clone

You must have the following installed ArkOS_K36_v2.0_011182025
You will need a wifi dongle, usb hub with additional power, keyboard (not RGB), usb type-c -> usb 2.0 adapter
Connect it all to the K36. 
Turn on K36, go to OPTIONS, turn on WIFI, after connecting, turn on Enable Remote Services.
Next, go to the main menu and click START, then Quit, Quit Emulation Station
You will be taken to the console, press ALT + F2 on the keyboard.
Login: ark
Password: ark (the password is not displayed in any way, enter it without errors) 
Then manually fill in the commands that are shown below.




```
git clone https://github.com/RAWJUNGLE/123.git
cd 123
chmod 777 install_headers.sh 
./install_headers.sh 
git clone https://github.com/laamaa/m8c.git
cd 
```
```
sudo apt-get remove libserialport0 libserialport-dev
sudo apt-get install libtool
sudo apt-get install autoconf
```
```
git clone git://sigrok.org/libserialport
cd libserialport
chmod 777 autogen.sh
./autogen.sh
./configure
make
sudo make install
```
```
sudo ln -s /usr/local/lib/libserialport.so.0.1.0 /usr/lib/libserialport.so.0.1.0
sudo ln -s /usr/local/lib/libserialport.so.0 /usr/lib/libserialport.so.0
```
```
cd /123/m8c
make
```
```
sudo nano /home/<username>/.local/share/m8c/config.ini
edit audio = false to true
ctrl+x, y, enter
```
```
sudo adduser <username> dialout
sudo reboot
```

```
cd /123/m8c/
./m8c
```


AUTOSTART M8C ONLY (Автозапуск только M8C)
```
sudo systemctl disable emulationstation
sudo nano /etc/rc.local
```
```
add script  
alsaloop -P hw:0,0 -C hw:1,0 -t 200000 -A 5 --rate 44100 --sync=0 -T -1 -d
/home/<username>/123/m8c/m8c
ctrl+x, y, enter
```
```
sudo chmod +x /etc/rc.local
sudo systemctl start rc-local
```

Если вы хотите избавиться от треска (If you want to get rid of crackles)
Добавьте строку в скрипт (Add a line to the script) rc.local 
```
sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```
до строки (before the line) alsaloop

Выйти обратно в консоль SELECT + R3 (кнопка на джойстике)

Exit back to the console SELECT + R3  (button on the joystick)

r / select+start+opt+edit = перезагрузка дисплея, если появятся искажения 

r / select+start+opt+edit = reset display (if glitches appear on the screen, use this)

Появтся задержка в работе, имейте ввиду. (There will be a delay in work, keep in mind.)

Еще нужно зайти в alsamixer, в консоли пишите просто alsamixer и проведите такие же настройки как на фото (навигация влево/вправо, вверх/вниз переключение, M - mute)

You also need to log in to alsamixer, just write alsamixer in the console and make the same settings as in the photo. (left/right navigation, up/down switching, M - mute)

![alsamixer](https://github.com/RAWJUNGLE/123/blob/main/pic/photo_2025-02-20%2000.42.29.jpeg?raw=true)
![alsamixer2](https://github.com/RAWJUNGLE/123/blob/main/pic/photo_2025-02-20%2000.42.31.jpeg?raw=true)

