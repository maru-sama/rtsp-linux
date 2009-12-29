Disclaimer: 
===========

This software is provided as is. I take no responsibility if it destroys your
data or opens up a security hole on your firewall. That said, I have yet to
hear something about this happening.

I did not create this code myself, most was written by Tom Marshall, later on
Harald Welte and then Steven van Acker ported it to the new 2.6 netfilter API.
I just picked up this code in 2007 and made it compile and hopefully work with
the new changed netfilter API.

Bugs: 
=====

Of course there are. One of the most important ones, is that you MUST NOT
filter outgoing connections otherwise the reply packes go missing. I tried to
figure out, why the _expect call is not taking care of the outgoing connections
but I was not able to figure this out. I gladly welcome patches that fix this
and other bugs.

Build Instructions: 
===================

Have the kernel source ready in some place and NF_CONNTRACK_NAT enabled in the
configuration otherwise you will get an error during make. The Kbuild setup
looks in /lib/modules/\`uname -r\`/build for the source. 

If the source is located in another place set the KERNELDIR environment
variable accordingly.

After that a:

	* make 
	* make modules_install (as root)

should be enough.  
Then do a "modprobe nf_nat_rtsp" as root and try to connect to a RTSP
service.

