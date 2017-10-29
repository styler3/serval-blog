+++
date = "2012-04-17"
title = "Making Security Simple"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7654943859981216196" itemprop="description articleBody">
One of the major features we are working on for the Serval Project right now is security.  We want secure phone calls, secure MeshMS/SMS and secure data transfer. But the reality is that we have been working on security from the outset, because we know that it is a vital component of any modern communications system, particularly if we are to preserve people's privacy.<br/>
<br/>
One of the very early design decisions was to use public keys are the mechanism for identifying phone users at the network level (at the human levels, it is all phone numbers, so that it remains easy to use).<br/>
<br/>
By using public keys as the network identifier, we get some very nice properties.  By carefully choosing the cryptographic algorithm we are gain the ability to perform a <a href="http://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange">Diffie-Hellman shared secret agreement</a> process.  This makes it possible for any two parties to encrypt their mutual communications, <i>without them having to first establish contact</i>. This provides the same major security benefits (confidentiality, authenticity of communications) of insanely complex systems such as <a href="http://en.wikipedia.org/wiki/IPsec">IPsec</a>, but without the pain.<br/>
<br/>
We have now reached the point where we can perform secure communications over the Serval Overlay Mesh, which is our implementation of this concept, using 256-bit Curve25519 public keys as network addresses, and with a defaults-secure Mesh Datagram Protocol.  This is based on the <a href="http://nacl.cr.yp.to/">NaCl crypto library</a>, and uses CryptoBox authenticated-encryption for unicast traffic, and CryptoSign verified signing for publicly readable broadcast traffic.<br/>
<br/>
Curve25519 makes this feasible, due to the relatively short key length.  In contrast, using RSA we would need 3,072 bit keys for similar security (~128 <a href="http://en.wikipedia.org/wiki/Key_size">bits of security</a>).  Three addresses are required in each packet: source, destination and next-hop.  Using RSA 3,072 bit keys this would be 1,152 bytes -- just for addresses.  Even using insecure RSA 1,024 bit keys the addresses would require 384 bytes. With Curve25519 we need just 768 bits (96 bytes) for addresses. We further improve on this through address abbreviation, where we only send the full addresses occasionally, and use a unique prefix the remainder of the time.  This allows us to reduce the address overhead by 75% or more, thus resulting in a lower address overhead than IPv6, but while gaining the attractive security properties that we have been talking about.<br/>
<br/>
An important distinction between our MDP security layer and IPsec is that that we do not need any key exchange, as the keys are implicitly communicated since the network address <i>is</i> the key.  This is a luxury that IPsec could not make use of, because IPsec was required to be able to be retro-fit into existing IP networks with already-allocated addresses, and geographically allocated addresses.  MDP's your-key-is-your-network-address only makes sense because geographically allocated addresses are not necessary (or even really possible) on a mobile adhoc mesh network.  Also, IPsec relies on third-party authorities to manage key exchange and related functions, and so is not suitable for use in an infrastructure-deprived setting.  MDP's security is not client-server, but rather truly peer-to-peer.<br/>
<br/>
The current state of the MDP security system is that it is operational, but requires some further refinement that we are undertaking, in particular to settle the API.  Nonetheless, it is already surprisingly easy to use MDP to enable secure communications.<br/>
<br/>
So let's see how this all ties together by taking a look at the MDP ping test program that we have written.  You can find the source code <a href="https://github.com/servalproject/serval-dna/blob/master/commandline.c">here</a> as part of the Serval/DNA source on github. The vast majority of this example is in fact to perform the ping function and to report on errors (a common situation for network programming), the actual MDP networking primitives are no more complex than UDP.  So let's take a look.<br/>
<br/>
First, we need to bind to an MDP socket.  MDP uses 32-bit port numbers and 256-bit network addresses. A given node might have more than one network address.  As MDP is implemented as an overlay network, we must talk to the local MDP server on the node to perform all operations.  This is done over a unix-domain socket.  This has the advantage that it can be poll()'d, select()'d or whatever you prefer, just like a normal socket.  So let's start by opening the connection to the MDP server and asking for the list of network addresses:<br/>
<br/>

<a href="https://3.bp.blogspot.com/-Mc9HhFjMlsU/T439ZdugVSI/AAAAAAAAAM0/dYS3Z2gR-fQ/s1600/mdp-get-addrlist.png"><img src="https://3.bp.blogspot.com/-Mc9HhFjMlsU/T439ZdugVSI/AAAAAAAAAM0/dYS3Z2gR-fQ/s400/mdp-get-addrlist.png"/></a>

We start by creating an <span>overlay_mdp_frame</span> structure and populating it with our request.  Here we are asking for any local addresses (SIDs), by making the requested range of SIDs start at the beginning (-1), and include up to a couple of billion entries.  Of course the reply has to fit in a single packet, so the server may respond with only a partial list, which will be indicated by it <span>setting last_sid</span> to the index of the last SID returned, and <span>frame_sid_count</span> to the number of entries returned.

<br/>

We then send the MDP request by calling <span>overlay_mdp_send</span>, with the mdp frame, any flags, in this case <span>MDP_AWAITREPLY</span> that tells the MDP library that we want to send this request, and then wait for a reply from the server, followed by the timeout for that reply (in milliseconds).  So the call in the above example will allow the server up to five seconds to come back with the list of local addresses. The return value of <span>overlay_mdp_send</span> is the the number of MDP frames sent, either for for success or zero for failure.
<br/>
The remainder of the above code checks to make sure that no error has been returned, and that what the server replied with was in fact a list of addresses, as indicated by the packet type being <span>MDP_ADDRLIST</span>.<br/>
<br/>
Once we have the address list, we can then use one of the local addresses to bind our listener to:<br/>

<a href="https://3.bp.blogspot.com/-GESXvAmPLWc/T43_uszarlI/AAAAAAAAAM8/L0HQAWMOHwk/s1600/mdp-bind-addr.png"><img src="https://3.bp.blogspot.com/-GESXvAmPLWc/T43_uszarlI/AAAAAAAAAM8/L0HQAWMOHwk/s400/mdp-bind-addr.png"/></a>

We start by choosing a port, in this case a random port number in the range 0x8000 - 0xffff.  The port numbers are natively 32-bit, however, so you could use much larger port numbers.  Port numbers 0xf0000000 - 0xffffffff are reserved.

<br/>

Moving on to the network address part, we could just set our bind source address to all zeroes like on an IPv4 network, and listen on all local addresses, as illustrated in the disabled line of code, in which case we would not have needed to get the list of local addresses.  Similarly, if we already knew the address we wanted to listen on, then we can simply provide it in the bind <span>sid</span> field.  But it is helpful to illustrate here how to find and bind to a specific local address.

<br/>
We know that the previous call to overlay_mdp_send has returned a list of addresses, and we know that a Serval overlay mesh node always has at least one local address, so we will assume in this example that the server response contains at least one address.  We then copy this address from the list of SIDs into the bind source address field.  We have to do this before we setup the rest of the bind request, because we are reusing the same <span>overlay_mdp_frame</span> structure, and <span>mdp.addrlist</span> and <span>mdp.bind</span> are part of a union that share storage space.  All that then remains is to provide the port number, and call <span>overlay_mdp_send</span> to request that the server make the binding.  If no error has occurred, the binding has been created, and can be used.<br/>
<br/>

<a href="https://2.bp.blogspot.com/-qtud7YP-XIU/T44B30-6DKI/AAAAAAAAANE/mjDimMTbub4/s1600/mdp-ping-prepare-dst-addr.png"><img src="https://2.bp.blogspot.com/-qtud7YP-XIU/T44B30-6DKI/AAAAAAAAANE/mjDimMTbub4/s400/mdp-ping-prepare-dst-addr.png"/></a>

For this ping-over-MDP application we use a sequence number to help filter any old packets that might arrive, and keep track of packet arrival statistics (this is a fairly simplistic implementation of a ping-like service, and lacks a number of important features, but it serves to illustrate the use of MDP sockets just fine).  We then determine the SID we want to ping.  If the string "broadcast" is supplied, we fill the SID with all ones (0xff bytes) to indicate broadcast, and set a flag to remind us that we are broadcasting, just as it does on IPv4 and ethernet.  Else, we store the hexadecimal representation of the address using the <span>stowSid</span> convenience function.  The next step is to actually send ping packets:

<a href="https://4.bp.blogspot.com/-kYFRbcWukxA/T44DPAJ9aAI/AAAAAAAAANM/J2QX9XktHu4/s1600/mdp-ping-send-ping.png"><img src="https://4.bp.blogspot.com/-kYFRbcWukxA/T44DPAJ9aAI/AAAAAAAAANM/J2QX9XktHu4/s400/mdp-ping-send-ping.png"/></a>

This code warns the user that if they are broadcasting that the ping packets will not be encrypted (not that there is anything too private in these packets, but it is nice to inform the user).  We then enter a loop of endlessly sending ping packets.  These data packets are identified by giving them a packet type of <span>MDP_TX</span>.  If they are being broadcast, then the packets must also be marked as not requiring encryption using the <span>MDP_NOCRYPT</span> flag.  As the <span>MDP_NOSIGN</span> flag is not specified, the packet will still be signed, allowing the recipient to reject the packet if it has been tampered with, and to be assured that the packet did in fact originate from the claimed address.

<br/>

We could have done this the other way around, and have the programmer mark when a packet should be encrypted, but that would cause errors of omission to result in security breaches, instead of resulting in accidental employment of full security, which is a much better failure mode.  This passive safety is supported by MDP server checks that will return an error if an impossible combination is employed, e.g., a broadcast packet with encryption.
<br/>
The remainder of the above code simply packs the source and destination addresses and payload (the server rejects any packets with a source address/port combination that has not been bound to), and sends it by the now familiar <span>overlay_mdp_send</span> function.  The next step is to watch for any incoming "pongs":<br/>
<br/>

<a href="https://2.bp.blogspot.com/-h9vomRI3v8I/T44Fbr3FG-I/AAAAAAAAANU/LsNwaOW-1AA/s1600/mdp-ping-get-pongs.png"><img src="https://2.bp.blogspot.com/-h9vomRI3v8I/T44Fbr3FG-I/AAAAAAAAANU/LsNwaOW-1AA/s400/mdp-ping-get-pongs.png"/></a>

This loop waits until one second has passed, and displays any ping-replies (pongs) that arrive.  It uses the <span>overlay_mdp_client_poll</span> function as a convenience over providing the mdp client socket directly to poll or select (although that could be done).  If packets are waiting, it uses <span>overlay_mdp_recv</span> to receive them, and if the received MDP message is indeed a packet (indicated by the <span>MDP_RX</span> type), then the packet is displayed.  The packet type and flags field also tells the receiver whether the arriving packets were signed and/or encrypted.  Signed or auth-crypted packets that have been tampered with are detected and dropped, and so the client never sees them.  To improve passive security for applications that only want to receive authenticated data we may add an option to the MDP bind request to specify that any unsigned packets be dropped and never presented to the client.

<br/>

Below is an example of MDP ping in action, showing that the packets received via the MDP loop-back from the local address (<span>FE83</span>...) are signed but not encrypted (since encryption is not required), and that packets received from a remote host (<span>2447</span>...) were both signed and encrypted:

<br/>

<a href="https://4.bp.blogspot.com/--wkSsfP1r9c/T44HTVQKNII/AAAAAAAAANc/ZwEWHFhevsc/s1600/mdp-ping-run-1.png"><img src="https://4.bp.blogspot.com/--wkSsfP1r9c/T44HTVQKNII/AAAAAAAAANc/ZwEWHFhevsc/s640/mdp-ping-run-1.png"/></a>

<br/>

Notice that nowhere in this program is there any mention of keys (apart from their implicit handling as network addresses), and no key-exchange must be handled, or third-party authority consulted.  Instead, special effort is required to <i>reduce</i> the security of the communications, e.g., for sending broadcast messages.

<br/>

The security is just baked in from the ground up, defaults to on, and can be used anywhere, anytime, as it should be.
<div></div>
</div>