# YANKB
Yet Another Networking Blog

**The networking winds are'a blowing and the CLI is being replaced by a technicolor text editor and Python loops!**

---
### GNS3 and Juniper vMX

**I just have to post this somewhere so that other zealous network engineers with a desire to try for themselves, the things that they are reading about, in a sandbox environment.** Juniper has to be, for myself, one of the best Network OS's that I have ever used ( Cisco... sorry, you're not fun ). I only ever had a chance to really use it at a previous employer's live network. As a result, I had to try out all of the fun MPLS tricks that I was reading about, when working in this previous employers Service Provider network. 

SO! ( skipping to the point of this post and for the sake of brevity ) I began to create MPLS labs in GNS3 ( as is my custom ) but quickly began to become disappointed right around the point when it was time to run some nifty little MPLS traceroute commands on my virtual MX (vMX). It so sucked! All of the step by step tedious work of setting up an link-state IGP (OSPF, not IS-IS), BGP-MP, blah-blah-blah, I in the end hit a terrible wall. My labels were note being switched by my delicious vMX LSRs. **What to do...?**

I hit the Google up and read, read, asked, and read. In the end, I came accross some great resources. Check for yourself after reading this post. Trust me.

The Problem:
- I followed the GNS3 website instructions and had issues with the forwarding plane. Yes, I could configure the vMX in GNS3 just fine and getting routing working ( Routing Engine ) but when it came time to label switch ( Forwaring Engine ), NO LUCK

IF you follow GNS3 site intructions, using vMX version 14.1R(whatever) then you just might have the kind of problems that I have described. My configuration ended up looking like this ( not working ):

( insert image here of bad configuration )

Simple fix! ( that I figured out a long time ago, forgot, and struggled again, and then finally figured it out )
- **change the virtual network adapter settings in the vMX GNS3 template to: "Paravirtualized Network I/O (virtio-net-pci)"**

( insert image here of changed adapters )


How-to setup Juniper vMX according to GNS3, and other sites:
- GNS3 site: https://docs.gns3.com/144QvvLxBT69_fv-pPHf4etc5xjdItiA_a8s8gVmSTDk/index.html
- http://networklab.in/simulation/juniper-vmx-router-on-gns3-legacy-version/
