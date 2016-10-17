# Python USB

```sh
>>> print dev
DEVICE ID 1d6b:0003 on Bus 002 Address 001 =================
 bLength                :   0x12 (18 bytes)
 bDescriptorType        :    0x1 Device
 bcdUSB                 :  0x300 USB 3.0
 bDeviceClass           :    0x9 Hub
 bDeviceSubClass        :    0x0
 bDeviceProtocol        :    0x3
 bMaxPacketSize0        :    0x9 (9 bytes)
 idVendor               : 0x1d6b
 idProduct              : 0x0003
 bcdDevice              :  0x310 Device 3.1
 iManufacturer          :    0x3 Linux 3.10.98-poky-edison+ dwc-xhci
 iProduct               :    0x2 xHCI Host Controller
 iSerialNumber          :    0x1 dwc3-host.2
 bNumConfigurations     :    0x1
  CONFIGURATION 1: 0 mA ====================================
   bLength              :    0x9 (9 bytes)
   bDescriptorType      :    0x2 Configuration
   wTotalLength         :   0x1f (31 bytes)
   bNumInterfaces       :    0x1
   bConfigurationValue  :    0x1
   iConfiguration       :    0x0 
   bmAttributes         :   0xe0 Self Powered, Remote Wakeup
   bMaxPower            :    0x0 (0 mA)
    INTERFACE 0: Hub =======================================
     bLength            :    0x9 (9 bytes)
     bDescriptorType    :    0x4 Interface
     bInterfaceNumber   :    0x0
     bAlternateSetting  :    0x0
     bNumEndpoints      :    0x1
     bInterfaceClass    :    0x9 Hub
     bInterfaceSubClass :    0x0
     bInterfaceProtocol :    0x0
     iInterface         :    0x0 
      ENDPOINT 0x81: Interrupt IN ==========================
       bLength          :    0x7 (7 bytes)
       bDescriptorType  :    0x5 Endpoint
       bEndpointAddress :   0x81 IN
       bmAttributes     :    0x3 Interrupt
       wMaxPacketSize   :    0x4 (4 bytes)
       bInterval        :    0xc
>>> 
```