## PN532 NFC RFID Modul V3
<img src="https://github.com/jingx23/PN532/blob/main/pn532.png" width="250" />

### macOS Setup
1. Open the command line
2. `brew install libnfc`
3. `nfc-list`</br>
    Note down the serial port e.g. `pn532_uart:/dev/tty.usbserial-1440`. If your device is not listed check if you connected the **TXD** and **RXD** wire correctly.
    You can also check the **tty** and see where the usbserial adapter is connected to with `ls /dev/tty*`
4. `cd /usr/local/Cellar/libnfc/1.8.0/etc/nfc`
5. Open `libnfc.conf`
6. Add the following lines (use for `device.connstring` the serial port from step **3.**) </br>
    ```
    device.name = "PN532 NFC Board"
    device.connstring = "pn532_uart:/dev/tty.usbserial-1440"
    ```
7. Now everything should be setted up and if you place an nfc tag on the module it should be found by `nfc-poll`


### Read/Write NDEF messages
To be able to read or write NDEF messages you can use the command line tool `libfreefare`.

1. Open the command line
2. `brew install libfreefare`
3. Create a textfile for example `helloWorld.txt`and add the following content `Hello NFC World!`
4. Place an nfc tag on the modul and execute the following command:</br>
   `mifare-classic-write-ndef -y -i helloWorld.txt`
5. Now the message should be written on to the tag and you can read it from there with:</br>
   `mifare-classic-read-ndef -y -o readdata.txt`

### Links
http://nfc-tools.org/index.php/Main_Page

http://nfc-tools.org/index.php?title=Libnfc:Arduino

