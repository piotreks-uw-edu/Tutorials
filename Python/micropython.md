# install
pip install pyserial
pip install esptool

# list_ports, show ports with connected devices
python -m serial.tools.list_ports

### erase flash
esptool.py --port COM6 erase_flash

### flash
# esptool.py --port COM6 --baud 115200 write_flash --flash_size=detect -fm dio 0 ESP8266_GENERIC-20231227-v1.22.0.bin
esptool.py --port COM6 --baud 460800 write_flash --flash_size=detect -fm dio 0 ESP8266_GENERIC-20231227-v1.22.0.bin

# connect withou putty
py -m serial.tools.miniterm COM6 115200

#after connecting to the devices
import webrepl_setup
>>> (password: password)


### The WiFi password when you connect to the MicroPython access point is "micropythoN".


### Default address for WEB_REPL:
ws://192.168.4.1:8266
