git clone https://github.com/RAWJUNGLE/123.git
cd 123
chmod 777 install_headers.sh 
git clone https://github.com/laamaa/m8c.git
cd 

sudo apt-get remove libserialport0 libserialport-dev
sudo apt-get install libtool
sudo apt-get install autoconf
sudo apt-get install jackd2

sudo usermod -a -G audio <username>

git clone git://sigrok.org/libserialport
cd libserialport
chmod 777 autogen.sh
./autogen.sh
./configure
make
sudo make install

sudo ln -s /usr/local/lib/libserialport.so.0.1.0 /usr/lib/libserialport.so.0.1.0
sudo ln -s /usr/local/lib/libserialport.so.0 /usr/lib/libserialport.so.0

cd/123/m8c
make

sudo nano /home/<username>/.local/share/m8c/config.ini
edit audio = false to true
ctrl+x, y, enter

sudo adduser <username> dialout
sudo reboot

jackd -d alsa -d hw:M8 -r44100 -p512 &
alsa_out -j m8out -d hw:0 -r 44100 &
jack_connect system:capture_1 m8out:playback_1
jack_connect system:capture_2 m8out:playback_2

cd /123/m8c/
./m8c

ENJOY 

AUTOSTART M8 ONLY 

sudo systemctl disable emulationstation
sudo nano /etc/rc.local

add script  /home/<username>/123/m8c/m8c
ctrl+x, y, enter

sudo chmod +x /etc/rc.local
systemctl start rc-local

enjoy! 

known issue: 
Audio not work on reboot console
