+++
date = "2017-03-01"
title = "Reading and writing the I2C EEPROM connected to an RFD900"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-4997339612359022513" itemprop="description articleBody">
<a href="http://servalpaul.blogspot.com/2017/02/mesh-extender-eeprom-equiped-cable-work.html">As previously described</a>, for the new Mesh Extender we have an I2C EEPROM for encoding regulatory information, e.g., radio permitted frequency and TX power.<br/>
<br/>
Basically, I am building the tools that we will need to program Mesh Extender cables as we build them, and also in the field, to reprogram them as required.<br/>
<br/>
Over the past couple of weeks I have worked on the code for the RFD900+ firmware to be able to read and write the I2C EEPROM, and then to modify our <a href="https://github.com/servalproject/flash-rfd900">flash900 utility</a> to be able to flash not just an RFD900 radio, but also an I2C EEPROM connected via an RFD900 radio.<br/>
<br/>
I've had it mostly working for a while now, but there have been strange problems with accessing certain parts of the EEPROM, and weird intermittent write problems affecting the whole EEPROM. I tried swapping EEPROMs, to confirm that it wasn't a faulty part.<br/>
<br/>
I spoke to the engineering workshop folks here, who suggested that I might need external pull-up resisters to terminate the I2C bus, which fortunately turned out not to be the case, as this simplifies the cable and PCB design process (one of them would have required some extra resisters).<br/>
<br/>
They also had a nice little logic analyser that could understand I2C.  That proved to be super-helpful.  It took me less than an hour to see that the problem was when back-to-back page reads were occurring and the last bit of the last byte read was a zero.  Basically I was failing to implement the NACK required at the end of a multi-byte read sequence.  <br/>
<br/>
I fixed this by inserting a dummy read with NACK, like this:<br/>
<br/>
<span>$ <b>git show 490025c33a3e821aab05055d627d192bb0d186fc               </b></span><br/>
<span>commit 490025c33a3e821aab05055d627d192bb0d186fc                   </span><br/>
<span>Author: gardners &lt;paul@servalproject.org&gt;                         </span><br/>
<span>Date:   Thu Mar 2 14:02:22 2017 +1030                             </span><br/>
<span>                                                                  </span><br/>
<span>    properly terminate sequential read operations                 </span><br/>
<span>                                                                  </span><br/>
<span>diff --git a/Firmware/radio/i2c.c b/Firmware/radio/i2c.c          </span><br/>
<span>index 76fe0be..6e9d68f 100644</span><span>                                     </span><br/>
<span>--- a/Firmware/radio/i2c.c</span><span>                                        </span><br/>
<span>+++ b/Firmware/radio/i2c.c</span><span>                                        </span><br/>
<span>@@ -183,6 +183,9 @@ char _eeprom_read_page(unsigned short address)</span><br/>
<span>     }</span><span>                                                            </span><br/>
<span>   }</span><span>                                                              </span><br/>
<span>                                                                  </span><br/>
<span>+  // Terminate the sequential read</span><span>                               </span><br/>
<span>+  i2c_rx(0);</span><span>                                                     </span><br/>
<span>+</span><span>                                                                 </span><br/>
<span>   i2c_stop();</span><span>                                                    </span><br/>
<span>                                                                  </span><br/>
<span>   return 0;</span><span>                                                      </span><br/>
<span><br/></span>
With that in place, I could suddenly reliably access the whole EEPROM.  In fact, the correct data was always written there, it was just that I couldn't read it.<br/>
<br/>
Following that, I spent a bit of time optimising the EEPROM read and write speed, and also the speed of the flash-rfd900 utility, both for flashing the radio and flashing the EEPROM. <br/>
<br/>
It is now possible to flash an RFD900 radio in about 23 seconds, even when using a USB serial adapter with 16ms latency.  This is a huge improvement on the ~100 - 150 seconds it took previously.<br/>
<br/>
Flashing the I2C EEPROM takes just under 20 seconds, including reading the entire EEPROM once before hand, and once after, to verify that all bytes have been correctly written.<br/>
<br/>
Now I just need to tweak the format of the data that I store in the EEPROM, so that it contains all the information that I need, principally the list of countries a particular cable is suitable for, and increasing the resolution of the frequency parameter from MHz to KHz.
<div></div>
</div>