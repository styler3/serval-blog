+++
date = "2016-12-07"
title = "More details about the Mesh Extender prototype PCBs"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7490266070392683118" itemprop="description articleBody">
I have been asked if I can share the current design documents for the Mesh Extender prototypes, which of course I am happy to do.  I have also confirmed with RF Design who are our PCB design partners (they also make the nice RFD900 / RFD868 radios that we use), that we can share the current schematics as well.<br/>
<br/>
<b>Please remember that all of this information is provisional, and subject to change.</b><br/>
<br/>
Any feedback and suggested improvements welcome.<br/>
<br/>
The images below have all been uploaded at 300dpi, so click on the image to see in higher resolution.<br/>
<br/>
<h2>
Jumpers and headers</h2>
The first the silk-screen, showing the various connectors:<br/>
<br/>

<a href="https://3.bp.blogspot.com/-fsM1pRg4B50/WEfTsR4mIFI/AAAAAAAAGBo/gKE7CD4mXAoh0l307r0jVt-6HJ6IlzQvgCLcB/s1600/MeshExtenderPCB_1.0_SilkScreen.png"><img src="https://3.bp.blogspot.com/-fsM1pRg4B50/WEfTsR4mIFI/AAAAAAAAGBo/gKE7CD4mXAoh0l307r0jVt-6HJ6IlzQvgCLcB/s640/MeshExtenderPCB_1.0_SilkScreen.png"/></a>
<br/>
<br/>
<br/>
<div class="page" title="Page 1">
<div class="layoutArea">
<div class="column">
<span>Note that the only LEDs on the unit at the moment are on the ethernet connectors, so take care in working out whether the unit has power or not. We may put an inline LED in the power cable to make it easier to see if it is powered up or not.  Adding LEDs to the injection-moulded housing would increase costs a lot, and make it harder to achieve the IP65/66 rating we are aiming for.</span><br/>
<span><br/></span>
<span>Going through the headers and jumers from left to right, </span><br/>
<h4>
1. Internet of Things / Mesh of Things Interfaces</h4>
<span><b>O1</b> is opto-coupled input 1, </span><b>O2</b><span> is opto-coupled input 2, and </span><span><b>R</b> is the relay-driver output.</span><br/>
<span>I.e., there are two inputs and one output that have some sort of electrically protected interface for IoT/Mesh of Things type applications.</span><br/>
<br/>
<span>We have allowed some extra flexibility,  not just for during the development phase, on where they will actually connect, i.e., to the GPIOs on the radio module (<b>R</b> position), or to GPIOs on the Ath9k in the Domino Core module (<b>D</b> position).  </span><span>For</span><span> </span><b>R</b><span>,</span><span> </span><b>O1</b><span> </span><span>and</span><span> </span><b>O2</b><span> </span><span>the centre pin goes to the relay or optocoupler, and the jumper connects this to either (or possibly both if you had some strange need to do so) the radio module or Ath9k GPIO.  </span><span>The final decision on which position we default to on shipped units will occur as we continue the development process.</span><br/>
<h4>
2. Options for powering the device</h4>
<span><b>VIN</b> is for selecting the input power type as automotive (i.e. DC supply or lead acid battery
connection) or solar panel input. </span><br/>
<span><br/></span>
<span><u>Note to self #1:</u> I'll have to check with RFDesign, if it possible for us to make this selection available on one of the external connectors, so that you don't have to open the unit to make this change.  We could, for example, lose one of CTS or RTS on the UART, in order to make this selection possible externally</span><br/>
<span><br/></span>
<span>For battery charging, you need to select the battery chemistry internally:</span><br/>
<span><b>LiPO</b> Sets the output charge voltage for charging a 2s LiPO4 battery (as there is no support on the charger IC for load balancing of the cells this type is not recommended)</span><br/><span><b>LiFePO</b> Sets the output charge voltage for charging a 2s LiFePO4 battery</span><br/><span><b>Lead</b> Sets the output charge voltage for the charging a 12V lead acid battery</span><br/>
We will likely make this default to LiFePO, or possibly Lead, but of course it can be easily changed by opening the unit and moving a jumper.<b><br/></b><br/>
<b><br/></b>
<b>3. Connectivity and debugging</b><br/>
<b><br/></b>
<b>USB</b><span> is the breakout header for the micro USB connector, in case people want to connect some other device to it.</span><br/>
<span><br/><b>JTAG</b> is the programmer port for the Domino module.</span><br/>
<span><br/></span>
<span>By default, you need to have a cable on the DB25 connector, in order to tie the Radio and Ath9k serial ports together.  This is on purpose, as it allows for use of an external radio connected by a special cable, that can just re-route the UART from the Ath9k to the external radio.  This is how we intend to allow easy connection to HF radios, for example.  If for some reason you want to operate the device without a cable on the DB25, but still want to bridge the UART to the radio interface, there are some pads just above the DB25 connector that can be soldered to short-circuit the UART connection, so that it doesn't require a cable to complete the circuit.</span></div>
</div>
</div>
<h2>
Schematics</h2>

<a href="https://4.bp.blogspot.com/-sfN1bctIA_8/WEfTr84lk2I/AAAAAAAAGBg/UPzjXTh60TAJQzuNidvsN82sg47Bd7VYQCLcB/s1600/MeshExtenderPCB_1.0_Schematic_Main.png"><img src="https://4.bp.blogspot.com/-sfN1bctIA_8/WEfTr84lk2I/AAAAAAAAGBg/UPzjXTh60TAJQzuNidvsN82sg47Bd7VYQCLcB/s640/MeshExtenderPCB_1.0_Schematic_Main.png"/></a>
<br/>
The main thing to note here are the pinouts of the DB25 and DB15 connectors.<br/>
<b><br/></b>
<b>These are subject to change! </b><br/>
<b><br/></b>
All six GPIOs of the RFD900 are exposed on the DB25 connector. These will be used by the radio firmware to check which regulatory domain it is in, and thus, what the allowed frequency and power level is.  It will also share this information (in the form of the 6-bit value) with the Ath9k, where it will be used to tell the firmware updater whether it is allowed to accept 3rd-party firmware or not.<br/>
<br/>
As these values are supplied by the cable, it will be possible for research and development purposes to make your own cable that does not tell the firmware updater to block 3rd-party firmware, even if you received the unit with a cable for a regulatory domain where this is normally enforced.<br/>
<br/>
Anyway, the current pinouts:<br/>
<br/>
<h3>
1. DB25 - Power and Radio connector</h3>
<div>
Going from left to right on the connector:</div>
<div>
<br/></div>
<div>
1 - GND</div>
<div>
14 - GND</div>
<div>
2 - RFD_IO2 (A GPIO from the RFD900/868 radio)</div>
<div>
15 - RFD_IO6 (A GPIO from the RFD900/868 radio)</div>
<div>
3 - RFD_IO3 (A GPIO from the RFD900/868 radio)</div>
<div>
16 - RFD_IO1 (A GPIO from the RFD900/868 radio)</div>
<div>
<div>
4 - RFD_IO4 (A GPIO from the RFD900/868 radio)</div>
</div>
<div>
17 - RFD_IO5 (A GPIO from the RFD900/868 radio)</div>
<div>
5 - Domino_TX_H (UART TX line on Ath9k module. Should ordinarily be connected to pin 18)</div>
<div>
<div>
18 - RFD_TX (UART TX line on RFD900 module. Should ordinarily be connected to pin 5) </div>
<div>
6 - RFD_RX (UART RX line for the RFD900 module. Should ordinarily be connected to pin 19)</div>
<div>
19 - Domino_RX_H (UART RX line on Ath9k module. Should ordinarily be connected to pin 6)</div>
</div>
<div>
<u>Note to self #2:</u> Check if UART lines are around the right way here, or if we need to move them, to ensure that UART bridging can be achieved with just solder blobs between adjacent pins.</div>
<div>
7 - RFD_RTS</div>
<div>
20 - RFD_CTS</div>
<div>
8 - Ath9k CTS</div>
<div>
21 - Ath9k RTS</div>
<div>
<u>Note to self #3:</u> Do we really need CTS/RTS lines, and are they also paired the right way around?</div>
<div>
9 - Domino Ath9k GPIO0</div>
<div>
22 - Domino Ath9k GPIO1</div>
<div>
10 - Battery negative (-) pole</div>
<div>
23 - Battery centre pole for two-cell configurations (Lithium batteries only?)</div>
<div>
11  -Battery positive (+) pole</div>
<div>
24 - Solar/Automotive power GND</div>
<div>
12 - Solar/Automotive power positive (+) pole</div>
<div>
25 - GND</div>
<div>
13 - +5V</div>
<br/>
The UART connections to the Ath9k go through a <a href="http://www.ti.com/lit/ds/symlink/txb0104.pdf">TXB0104</a> level converter, making them 5V tolerant.<br/>
<br/>
The +5V line (on both the DB25 and DB15 connectors) can be either used to supply a modest amount of power to some external device, or to supply power to the board.  Thus a minimal DB25 power connector would simply connect the +5V and GND, e.g., from a USB cable, and short the appropriate pairs of pins to connect the UART of the radio module to the Ath9k, and optionally short pins to GND or +5V as required to encode the appropriate radio regulatory domain.<br/>
<h3>
2. DB15 Utility / IoT / Mesh of Things connector</h3>
<div>
Again, from left to right.</div>
<div>
<br/></div>
<div>
Note that on the prototype PCBs this connector is on the opposite side of the PCB to the DB25 connector.  This is not how it will be in the production units.  I expect that we will be able to re-route the connector without changing the pinout, but nothing is certain yet.</div>
<div>
<br/></div>
<div>
15 - +3.3V</div>
<div>
7 - Opto-isolated input 1</div>
<div>
8 - Domino GPIO14 (no protection)</div>
<div>
14 - Domino GPIO13 (no protection)</div>
<div>
6 - Opto-isolated input 2</div>
<div>
10 - Domino GPIO26 (no protection)</div>
<div>
13 - GND</div>
<div>
5 - Domino GPIO27 (no protection)</div>
<div>
2 - GND</div>
<div>
12 - Relay P3 (The centre-pole of the integrated 5V relay)</div>
<div>
4 - Domino GPIO17 (no protection)</div>
<div>
9 - Domino GPIO15 (no protection)</div>
<div>
11 - Relay P5 (The normally disconnected pole of the integrated 5V relay)</div>
<div>
3 - Domino GPIO16 (no protection)</div>
<div>
1 - +5V</div>
<div>
<br/></div>
<div>
It should be stressed that the GPIO lines on this connector <i>have no electrical protection whatever, and connect directly to the Ath9k on the Core Domino module.  </i>We have exposed them to provide the maximum flexibility possible with this device.</div>
<div>
<br/></div>
<div>
Regarding the relay: </div>
<div>
<br/></div>
<div>
<div>
The relay itself is an <a href="http://www.farnell.com/datasheets/1717938.pdf">IMC03</a>, which is rated up to 240V and loads of up to ~60VA, and could thus potentially directly switch low-power loads, however, we would recommend using it only as a staging relay, to something larger externally, e.g., a low-cost automotive relay if you were planning on switching low-voltage equipment.</div>
</div>
<div>
<br/></div>
<div>
When the relay is activated (via the XLNA pin from the Ath9k, or the IO2 line from the RFD radio module), then pins 11 and 12 will be connected, or disconnected otherwise.  This facility can be used to drive higher-voltage relays externally, e.g., to actuate controllers of various kinds.  </div>
<div>
<br/></div>
<br/>

<a href="https://2.bp.blogspot.com/-ySz4zNEbLmw/WEfTr1iDi3I/AAAAAAAAGBc/Ma4AOA6eLZYoFQCsT3bA2hyTRygVo7mrwCLcB/s1600/MeshExtenderPCB_1.0_Schematic_ModemInterface.png"><img src="https://2.bp.blogspot.com/-ySz4zNEbLmw/WEfTr1iDi3I/AAAAAAAAGBc/Ma4AOA6eLZYoFQCsT3bA2hyTRygVo7mrwCLcB/s640/MeshExtenderPCB_1.0_Schematic_ModemInterface.png"/></a>
<br/>

<a href="https://4.bp.blogspot.com/-xuRpAKyFo5Y/WEfTr5oNMXI/AAAAAAAAGBk/qW5MC7p2EKweMaqCXEPclkPNPJDTTNBUwCLcB/s1600/MeshExtenderPCB_1.0_Schematic_Part2.png"><img src="https://4.bp.blogspot.com/-xuRpAKyFo5Y/WEfTr5oNMXI/AAAAAAAAGBk/qW5MC7p2EKweMaqCXEPclkPNPJDTTNBUwCLcB/s640/MeshExtenderPCB_1.0_Schematic_Part2.png"/></a>
<br/>

I'll post more information about the Mesh Extender design itself as time allows.

<br/>

In the meantime, it would be great if someone were interested in starting creating a page for the Serval Mesh Extender 1.0 to the <a href="https://wiki.openwrt.org/toh/start">OpenWRT hardware table</a>, so that we can collect and maintain the appropriate information there, and look at creating a relevant target in the OpenWrt DD build system, as I'd greatly prefer if we can include the Mesh Extender in OpenWRT's supported hardware.
<br/>
<div></div>
</div>