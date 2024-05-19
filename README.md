# PN532Killer
PN532Killer, it's a PN532 Emulator,NFC Emulator,Sniffer.

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
