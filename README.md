## PN532 NFC RFID Modul V3
<img src="https://github.com/jingx23/PN532/blob/main/pn532.png" width="250" />

### macOS Setup
1. Open the command line
2. `brew install libnfc`
3. `nfc-list`</br>
    Note down the serial port e.g. `pn532_uart:/dev/tty.usbserial-1440`. If your device is not listed check if you connected the **TXD** and **RXD** wire correctly.
4. `cd /usr/local/Cellar/libnfc/1.8.0/etc/nfc`
5. Open `libnfc.conf`
6. Add the following lines (use for `device.connstring` the serial port from step **3.**) </br>
    ```
    device.name = "PN532 NFC Board"
    device.connstring = "pn532_uart:/dev/tty.usbserial-1440"
    ```
7. Now everything should be setted up and if you place an nfc badge on the module it should be found by `nfc-poll`
