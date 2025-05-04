# PN532Killer
PN532Killer, it's a PN532 Emulator,NFC Emulator,Sniffer.

20250504:

PN532Killer-V1.0-20250425.bin

Support 15693 UID save to slot;

Support set UART baudrate up to 12M;

20250407:

PN532Killer-V1.0-20250406.bin

Support automatic switch the host interfaces -- USB/BLE

20250209:

PN532Killer-V1.0-20250204A.bin

Emulator support Mifare-1 7B mode and 15693 two subcarriers mode

20241125:

PN532Killer-V1.0-20241123.bin

Support staticnested attack:

20241105:

PN532Killer-V1.0-20241030.bin

Support 15693 InCommunicateThru:
Change the block size of Gen2 ISO15693 Tag
Change UID of Gen2 ISO15693 Tag

Support Mifare-1 7B read&write

20241009:

PN532Killer-V1.0-20241005.bin, Bug of read ISO15693 emulator multiple blocks fixed, and support TagInfo App.

20240928:

PN532Killer-V1.0-20240925.bin, Forced revert to the USB-UART is supported

Press and hold “Enter” key for 5 seconds, the red led flash on, then release key.

20240915:

PN532Killer-V1.0-20240903.bin, support BLE&LF Extension

Support BLE and APP MTools BLE

Support Read&Emulate EM4100

Support Read ID(Mifare 1 & EM4100) Save to Slot

App: MTools BLE -- https://apps.apple.com/cn/app/mtools-ble/id1531345398

20240519:

PN532Killer-V1.0-20240511-CH343P.bin, the working mode can be set to Reader mode, Emulator mode, Sniffer mode by UART Command 

20240504:

PN532Killer-V1.0-20240504-CH343P.bin, Add support for ISO15693 read&write&emulate

Android App: MTools -- https://play.google.com/store/apps/details?id=tk.toolkeys.mtools&hl=en&gl=US

20240412：

PN532Killer-V1.0-20240412-CH343P.bin, Improve the detection limits to increase read&write distance and reduce the BER.

20240324：

PN532Killer-V1.0-20240324-CH343P.bin, it can run on NFC Emulator&PN532Killer.

Collect nonce at 2X speed than PN532 at baud rate 460800(libnfc limits it).

20240305：

PN532Killer-V1.0-20240304-CH343P.bin, it can run on NFC Emulator.

Software--MifareOne Tool：nested authentication attack、HardNested authentication attack

Software-PN532Killer Tool-Sniffer：sniffer for decrypt Mifare 1 tag(mfkey64&mfkey32v2)

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

PN532Killer，模拟PN532读写14443A/B卡片，同时也支持读写15693卡片；

PN532Killer，可以用于模拟14443A卡片(Mifare&Ntag)、15693卡片；

PN532Killer，可以用于嗅探读写器(14443A&15693)和卡片之间的交互数据。

基于AD156的PN532Killer V1.1

通信协议兼容PN532，可以利用MifareOne Tool、RFID Tools等软件操作各类NFC卡片。UART波特率支持115200，最高可支持至3M，提高卡片操作速度；

扩展协议支持：读写15693卡片、模拟Mifare 1卡片、模拟Ntag卡片、模拟15693卡片、支持卡片嗅探

在板固件升级。固件可在NFC Emulator上运行；

硬件预留低频卡扩展接口。
