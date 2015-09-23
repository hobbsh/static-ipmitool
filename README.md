# static-ipmitool
Static ipmitool binary for ESXi execution

## Purpose
I realize it's pretty shady to download and execute a stranger compiled file, but I promise it's a clean, functioning standalone version of ipmitool. My iDRACs locked me out on my ESXi hosts so I needed a way to send them a cold reset. Hopefully this saves you time/hassle.

ipmitool to the rescue...

I ended up creating a CentOS 4.8 VM to create this and overall it took me a couple hours to fully complete after all was said and done. I'm uploading to save someone else the time/hassle of doing it yourself. 

The process was taken from : http://ewen.mcneill.gen.nz/blog/entry/2015-07-09-static-ipmitool-on-vmware-esxi/

Please note that a couple functions won't work:
```
: warning: Using 'getaddrinfo' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
../lib/.libs/libipmitool.a(ipmi_tsol.o)(.text+0xe34): In function `ipmi_tsol_main':
: warning: Using 'gethostbyname' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
```
## Usage

To reset the iDRAC, first copy the ipmitool.static to your ESXI host. Note that a warm reset won't work. 

Then:

```
~ # ipmitool.static mc reset cold
```
