# ESPhome for deye
ESPhome configuration for monitoring and control of Deye inverters in Home Assistant.
This include all addresses i could see relevant from the inverter.
![image](https://user-images.githubusercontent.com/22115157/211201343-1d54cada-4b2c-40b0-88c4-faf31e17fead.png)

## Supported devices
Made specially for Deye 3phase low voltage inverters
* SUN-12K-SG04LP3(confirmed)
* SUN-8K-SG04LP3
* SUN-6K-SG04LP3
* SUN-5K-SG04LP3

## Unsupported devices
Sunsync & other 1phase inverters as they use different addresses and have different modbus port. Those inverters are not allowed in Denmark where i live because of a rule of maximum 16A for 1phase equitment.
I can only refer to this powerforum thread. https://powerforum.co.za/topic/8646-my-sunsynk-8kw-data-collection-setup/

## Requirements
* ESP32
* TTL To RS485 Module with automatic flow control

## Installation
1. Create your esp32 in esphome in home assistant
2. Upload the your basis config via. usb from pc.
3. Test wireless upload
4. Copy all content (make sure you have your wifi ssid&password in the secrets)
5. Edit the sensors in the config if you like
6. Upload wireless

## Hardware diagram
RX / TX between esp and ttl converter way have to be swapped. This seems to be a little different from espboard to espboard.
If it dosent communicate(RX/TX led both blinking) Try swap rx/tx on the esp.

I powered the esp32 from CN2 pin 7&8 with 12V into a USB converter.
(BE AWARE THAT IF YOU POWER OFF THE INVERTER REMOTELY, YOU CANT POWER IT UP AGAIN REMOTELY AS THE POWER TO THE ESP IS GONE)

![esp32 rs485_bb](https://user-images.githubusercontent.com/22115157/211201233-f5fe9189-e6b3-4ee1-9baa-48068f078127.jpg)

## Home assistant user interface
For the card i use for the time of use settings like the inverters interface. Use the add-on "multiple entity row" from HACS and inspiration from my configuration of it below.
* https://github.com/klatremis/esphome-for-deye/blob/main/time%20of%20use%20card


## Added Time of Use Card based on Voltage
If you are using User Defined Batteries you have to use the voltage. I added the nesseccary ModBus registers and Use Card template

### Time of Use Card - SOC based
![image](https://github.com/TheSmartGerman/esphome-for-deye/assets/9676982/680d9f9c-1146-4e8a-9e0a-75c91c5300c9)


## Added GenPort Settings & Monitoring
Set Mode of GenPort
In case of SmartPort use: Controll Start and Stop Voltage. 

![image](https://github.com/TheSmartGerman/esphome-for-deye/assets/9676982/bcb91ec1-208d-4e51-8f90-955606a1f915)


## Added ESP32 Debugging
Monitor ESP32 resources

![image](https://github.com/TheSmartGerman/esphome-for-deye/assets/9676982/e056c1c7-8388-4aeb-bf58-4720be67b9e4)


## Other interesting Forks
ESP8266 for Deye
* https://github.com/pvprodk/esp8266-for-deye

