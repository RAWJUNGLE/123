Ручная установка клиента M8C (Dirtywave M8) для клонов игровых консолей R36S (a.k.a K36). Да это клон, клона. 

У вас должна быть установлена ArkOS_K36_v2.0_011182025
Вам потребуется wifi свисток, usb hub с дополнительным питанием, клавиатура (не rgb), usb type-c -> usb 2.0 переходник. 
Подключите всё это к K36. 
Включите K36, зайдите в пункт OPTIONS, включите WIFI, после подключения, включите Enable Remote Services.
Далее выйдете в главное меню и нажмите START, далее Quit, Quit Emulation Station
Вы попадёте в консоль, нажмите на клавиатуре ALT + F4
Login: ark
Password: ark (пароль никак не отображается, вводите без ошибок) 
Дальше вручную заполняйте комманды которые привидены ниже. 


Manualy setup M8C Client for clones R36S (a.k.a K36). Yes this is clone of clone

You must have the following installed ArkOS_K36_v2.0_011182025
You will need a wifi dongle, usb hub with additional power, keyboard (not RGB), usb type-c -> usb 2.0 adapter
Connect it all to the K36. 
Turn on K36, go to OPTIONS, turn on WIFI, after connecting, turn on Enable Remote Services.
Next, go to the main menu and click START, then Quit, Quit Emulation Station
You will be taken to the console, press ALT + F4 on the keyboard.
Login: ark
Password: ark (the password is not displayed in any way, enter it without errors) 
Then manually fill in the commands that are shown below.


 


```
git clone https://github.com/RAWJUNGLE/123.git
cd 123
chmod 777 install_headers.sh 
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

ENJOY 

AUTOSTART M8 ONLY 
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
enjoy! 

