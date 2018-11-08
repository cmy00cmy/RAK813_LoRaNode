# RAK813_LoRaNode

**1. Overview**

  The project is for RAK815(RAK813 breakboard), as a LoRa node. The components are below:
 
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
   Accelerate sensor 
   2 reserved button(SW1 and SW2) for user definition
  
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
