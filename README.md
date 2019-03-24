
***************************************************************************************************************************************
**2019.3.15 Update log：**

1. Add acc, gps, temperature&humidity sensor test code. It will send lora data after start. When send '1' to it via ble, it will stop lora send and test sensors.

2. Remove sleep mode transitorily. User can open it with api "(void)sd_power_system_off(void)" in main loop in main.c.  
***************************************************************************************************************************************
**2019.2.14 Update log：**

1. Add sleep mode and power consumption is less than 1.8mA. When config the lora parameter and restart, node will send test data "123" to your server and go to sleep 2s later. If want to wake up moudle, just shake it and the acc will generate interrupt to reset the moudle repeatly the send work.

2. All debug functions including log are turned off in sleep mode.

3. If want to change the sensitivity of acc interrupt, change the macro LIS3DH_INT1_SENS in custom_board.h 

***************************************************************************************************************************************
***************************************************************************************************************************************
**2018.11.14 Update log：**

1. Fix button problem. There are three buttons on the board, sw1,sw2,sw3. Sw3 if for reset distinctively and sw1, sw2 are left to users.
You can do own work here instead of the log print now.

***************************************************************************************************************************************
***************************************************************************************************************************************
**2018.11.13 Update log：**

1. Debug US915, button exists some problem and in debugging. Now all data can be sent to gateway via BLE. If send "Acc", moudle will send accelerate data. Or the other data will be unvarnished transmission. 

2. Test details of scan demo is in \RAK813_LoRaNode\Doc\RAK815(RAK813 BreakBoard) User Manual V1.1.pdf

***************************************************************************************************************************************
***************************************************************************************************************************************
**2018.11.9 Update log：**

1. Add scan demo. Before use, copy the file under Scan_Demo to LoRaWAN_Demo and replace.
2. Test details of scan demo is in \RAK813_LoRaNode\Doc\RAK815(RAK813 BreakBoard) User Manual V1.1.pdf

***************************************************************************************************************************************
# RAK813_LoRaNode

**1. Overview**

  The project is for RAK815(RAK813 breakboard), as a LoRa node. The features of RAK813 module are below:
 
   Long Range LoraWAN operating in the 433MHz, 470MHz, 863 MHz or 928 MHz frequency bands
  
     FCC Frequency range 902MHZ~928MHZ
     
     CE Frequency range 863MHZ~870MHZ
     
     MIC Frequency range 920MHZ~928MHZ
     
     KCC Frequency range 920MHZ~923MHZ
     
   Support Lora Point to Point communication in all the band
  
   Small size and low power, sleep current down to 2uA
  
   High Receiver Sensitivity: LoRa down to -146 dBm， BLE down to -96dBm
  
   TX Power: LoRa adjustable up to +14 dBm high efficiency PA, max PA boost up to 20dbm, BLE -20 to +4 dBm in 4 dB steps
  
   Building in both TX and RX filter
  
   Building in TCXO for high frequency stability
  
   FSK, GFSK, and LoRa Technology modulation
  
   IIP3 = -11 dBm
  
   Up to 15 km coverage at suburban and up to 5 km coverage at urban area
  
  

**2. Feature**
  
  The firmware support:
  
   BLE
  
   Accelerate sensor/GPS/temperature sensor/humidity sensor/LCD
  
   2 reserved button(SW1 and SW2) and 2 LEDs for user definition 
  
   LoRa access: OTAA and APB
  
   power supply: micro usb or battery(individual)
  
  More details are shown in \RAK813_LoRaNode\Doc\RAK815(RAK813 BreakBoard) Datasheet V1.1.pdf
  
  
**3. How to use**

  3.1 Project
  
  The path is :....\RAK813_LoRaNode\Keil5
  
  3.2 Sdk download
  
  Use nRFgo Studio to download sdk, at .....\RAK813_LoRaNode\nRF_Lib\components\softdevice\s132\hex\s132_nrf52_5.0.0_softdevice.hex
  
  3.3 Build project and flash to board
  
  You can do some adaption before compile like frequency bands or OTAA or ABP parameters of LoRa.
  
  More details are shown in \RAK813_LoRaNode\Doc\RAK815(RAK813 BreakBoard) User Manual V1.1.pdf
  
**4. Test**
  
  We provide two way to test the LoRA node. 
  
  4.1 Unvarnished transmission 
  
  RAK815 connect to LoRa gateway hang in TTN via OTAA, and connect to a phone via BLE with nordic official mobile APP “nRF Connect”. Before test, send config command which includes parameters of gateway to RAK815 via BLE like below:
  lora_cfg:dev_eui=xxxxxxxxxxxxxxxx&app_eui=xxxxxxxxxxxxxxxx&app_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&dev_addr=xxxxxxxx&nwkskey=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&appskey=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
  
  And then press SW3 to reset. it will connect gateway automatically. All log will be shown via serial port (power supply) like below:
  
  ![image](https://github.com/RAKWireless/RAK813_LoRaNode/blob/master/Doc/img/com_log.png)
  
  When it shows OTAA Join Success, send "123456" to RAK815 via BLE and log will show. Meanwhile the server will receive data.
  
  ![image](https://github.com/RAKWireless/RAK813_LoRaNode/blob/master/Doc/img/ble_transparent%20transmission.png)
  
  4.2 Sensor data transmission
  
  When press button SW1, it will get data of acceleration and send to gateway and log will show. Meanwhile the server will receive data.
  
  ![image](https://github.com/RAKWireless/RAK813_LoRaNode/blob/master/Doc/img/button_upload_accelerate.png)
  
  More details are shown in \RAK813_LoRaNode\Doc\RAK815(RAK813 BreakBoard) User Manual V1.1.pdf
