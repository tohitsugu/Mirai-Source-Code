# Mirai Botnet Client, Echo Loader and CNC source code

This is the source code released from [here](http://hackforums.net/showthread.php?tid=5420472) as discussed in this [Brian Krebs Post](https://krebsonsecurity.com/2016/10/source-code-for-iot-botnet-mirai-released/).

I found 

mirai.src.zip from [VT](https://www.virustotal.com/en/file/68d01cd712da9c5f889ce774ae7ad41cd6fbc13c42864aa593b60c1f6a7cef63/analysis/)

loader.src.zip from [VT](https://www.virustotal.com/en/file/fffad2fbd1fa187a748f6d2009b942d4935878d2c062895cde53e71d125b735e/analysis/)

dlr.src.zip from [VT](https://www.virustotal.com/en/file/519d4e3f9bc80893838f94fd0365d587469f9468b4fa2ff0fb0c8f7e8fb99429/analysis/)

Maybe they are original files.



Configuring_CNC_Database.txt from [pastebin.com/86d0iL9g](http://pastebin.com/86d0iL9g)

Setting_Up_Cross_Compilers.sh from [pastebin.com/1rRCc3aD](http://pastebin.com/1rRCc3aD)

Felicitychou

Chuck:
Merged Felicitychou's additions and setup Vagrant file.
To setup build environment, you just need to "vagrant up"
Also removed obfuscation of table.c, so no need to run "enc" tool anymore
Have modified some shell scripts to install more cross compiler packages and remove errors
modified build.sh to download go packages


steps to setup build environment
 - `git pull`
 - `vagrant up`
 - `vagrant ssh`
 - `cd /vagrant/mirai`
 - `./build.sh`

Steps to create database:
`cat Configure_CNC_Database.txt | mysql -u root --password=password`

Start the CnC
- make a prompt file in ./release
- `cd ./release`
- `sudo ./cnc`

To start making the CnC talking to something, after building the binaries, you'll want to have a second machine. That's why the vagrant VM has two.
I'm not going to waste my time describing this in detail, but basically:
1: Create bare linux vm
2: drop compilex x86 binary
3: make sure your running some kind of DNS spoofer and you've got your IP routing setup right (look at Vagrantfile for some inspiration)
4: Make sure your gateways are dead ended, etc...

