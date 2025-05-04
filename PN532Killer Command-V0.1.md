# PN532_MISCCMD_UartSetWorkMode 0xAC #
	Param format: mode(1byte) + type(1byte) + index(1byte)
	PN532 -- mode- 01 type- 00 index- 00
	Emulator -- mode- 02 
				type- 01(Mifare1-4B1K) 02(Ntag) 03(15693) 
				index- 0-7(slot number)
	Sniffer -- mode-03
				type- 01(Mifare1-4B1K) 02(Ntag) 03(15693)
				index- 0(sniff without tag) 1(sniff with tag)

## For example: ##

**Set to PN532 mode:**

host: 00 00 FF 05 FB D4 AC 01 00 00 7F 00

PN532Killer ACK: 00 00 FF 00 FF 00

PN532Killer Response Packet: 00 00 FF 03 FD D5 AD 00 7E 00

**Set to Emulator mode: Emulate Mifare1 tag of Slot 0**

host: 00 00 FF 05 FB D4 AC 02 01 00 7D 00

PN532Killer ACK: 00 00 FF 00 FF 00

PN532Killer Response Packet: 00 00 FF 03 FD D5 AD 00 7E 00

**Set to Emulator mode: Emulate 15693 tag of Slot 0**

host: 00 00 FF 05 FB D4 AC 02 03 00 7B 00

PN532Killer ACK: 00 00 FF 00 FF 00

PN532Killer Response Packet: 00 00 FF 03 FD D5 AD 00 7E 00

**Set to Sniffer mode: Sniff Mifare1 without tag**

host: 00 00 FF 05 FB D4 AC 03 01 00 7C 00

PN532Killer ACK: 00 00 FF 00 FF 00

PN532Killer Response Packet: 00 00 FF 03 FD D5 AD 00 7E 00

**Set to Sniffer mode: Sniff Mifare1 with tag**

host: 00 00 FF 05 FB D4 AC 03 01 01 7B 00

PN532Killer ACK: 00 00 FF 00 FF 00

PN532Killer Response Packet: 00 00 FF 03 FD D5 AD 00 7E 00

<font color="red">**Note:Set to the one mode to the other mode, must set to PN532 mode first**</font>

# PN532_MISCCMD_ReadEmulator 0x1C #
# PN532_MISCCMD_WriteEmulator 0x1E #
	Param format:type(1byte) + tagindex(1byte) + sector(1byte) + block(1byte) + data(n bytes)
	type- 01(Mifare1-4B1K)
	tagindex- 0-7(slot number), 17(0x11, sniff tag)
	sector- target sector
	block- target block
	data- block data

## For example: ##

**Write sniff tag's UID:** 

host: 00 00 FF 16 EA D4 1E 01 11 00 00 34 5D 80 C4 2D 88 04 00 C1 85 14 98 5D 80 34 12 59 00

PN532Killer ACK: 00 00 FF 00 FF 00

PN532Killer Response Packet: 00 00 FF 07 F9 D5 1F 01 11 00 00 00 FA 00

host: 00 00 FF 16 EA D4 1E 01 11 FF FF 34 5D 80 C4 2D 88 04 00 C1 85 14 98 5D 80 34 12 5B 00

PN532Killer ACK: 00 00 FF 00 FF 00

PN532Killer Response Packet: 00 00 FF 07 F9 D5 1F 01 11 FF FF 00 FC 00

<font color="red">**Note 1: Set sector 0xFF and block 0xFF to complete the writing process**</font>

<font color="red">**Note 1: Set sector 0xFF and block 0xFF to read the data to the buffer of PN532Killer before reading**</font>

# PN532_MISCCMD_ReadSniffData 0x20 #
	Param format:type(1byte) + tag(1byte) + data
	type- 01(Mifare1-4B1K)
	tag- 0(sniff without tag) 1(sniff with tag)
	data- 20*8 bytes(sniff without tag) 24*4 bytes(sniff with tag)

	data struct(sniff without tag):
	typedef struct {
	uint32_t cuid;
	uint32_t nonce;
	uint32_t nr;
	uint32_t ar;
	uint8_t sector;
	uint8_t keytype;
	} nonces_mfkey32v2;

	data struct(sniff with tag):
	typedef struct {
	uint32_t cuid;
	uint32_t nonce;
	uint32_t nr;
	uint32_t ar;
	uint32_t at;
	uint8_t sector;
	uint8_t keytype;
	} nonces_mfkey64;

## For example: ##
**Read the data of sniffer without tag**

Host：00 00 FF 04 FC D4 20 01 00 0B 00

PN532Killer ACK：00 00 FF 00 FF 00

PN532Killer Response Packet：00 00 FF A4 5C D5 21 01 00

C4 80 5D 34 7A FF 90 6B 0B 8B B9 1D C9 19 9D C1 02 60 00 00

C4 80 5D 34 B3 9D 8D 13 0F F3 83 05 32 7F 03 30 02 60 00 00

C4 80 5D 34 10 2B C7 3B A8 ED E1 BF 7A 68 10 C2 02 60 00 00

C4 80 5D 34 71 46 01 23 E7 C1 6F F9 BC CA 40 45 02 60 00 00

C4 80 5D 34 63 B4 5D 8B AE 92 B1 CD F1 4A 75 19 02 60 00 00

C4 80 5D 34 36 2A 95 73 46 A9 34 67 AA 20 42 0D 02 60 00 00

C4 80 5D 34 46 50 E4 DB 4F DA A8 47 F5 7F 18 15 02 60 00 00

C4 80 5D 34 FF 9F 29 83 F7 B0 6D B9 4E 77 EA F0 02 60 00 00

62 00

**Read the data of sniffer with tag**

Host: 00 00 FF 04 FC D4 20 01 01 0A 00

PN532Killer ACK：00 00 FF 00 FF 00

PN532Killer Response Packet：00 00 FF 64 9C D5 21 01 01

2F 90 9E 7E BB 52 C4 D9 70 5D 71 4D 95 C1 10 F8 F2 E9 1E 2E 02 60 00 00

2F 90 9E 7E D5 13 C3 9A 4C 2D 2B 28 01 CE BB 97 9D 15 17 D7 02 60 00 00

2F 90 9E 7E 5D A9 62 6C 91 10 87 45 A4 E2 BE E4 C6 13 6C B7 02 60 00 00

2F 90 9E 7E 5D A9 62 6C 91 10 87 45 A4 E2 BE E4 C6 13 6C B7 02 60 00 00

BE 00


# PN532_MISCCMD_ReadUserDefData			0x24 #
	Param format:type(1byte) + data
	type- 1(Staticnested)
	data- keyknown(8bytes)+blkknown(1bytes)+typknown(60/61)+targetblock(1bytes)+targettype(60/61)

## For example: ##
Host: 00 00 FF 0F F1 D4 24 01 00 00 FF FF FF FF FF FF 02 60 08 60 43 00

PN532Killer ACK：00 00 FF 00 FF 00

PN532Killer Response Packet：00 00 FF 1A E6 D5 25 00 

A3 FC 3E FC 60 00 90 80 A2 3B 7D 49 85 00 90 80 A2 1D E7 12 48 92 00 -- uid(4) + targetType(1) + nt0(4) + nr0(4) + nt1(4) + nr1(4)


# Special parameter for 15693 #
<font color="blue">**InListPassiveTarget -- Brty- 0x05**</font>

<font color="blue">**InDataExchange**</font>

	6302—80, PN532Killer generate the CRC
	6303—80, PN532Killer generate the CRC

<font color="blue">**InCommunicateThru**</font>

	6302—00, PN532Killer do NOT generate the CRC
	6303—00, PN532Killer do NOT generate the CRC

## For example: ##
**Read UID:**
00 00 FF 09 F7 D4 42 80 00 26 01 00 F6 0A 43 00

**Read single block:**
00 00 FF 11 EF D4 42 80 00 22 20 91 C6 02 B9 50 01 04 E0 08 06 90 43 00

# Special UART baudrate #
	09- 1000000
	0A- 1500000
	0B- 2000000
	0C- 3000000
	0D- 4000000
	0E- 6000000
	0F- 12000000
<font color="red">**baudrate = 12200000/N**</font>