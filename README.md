# microcom

microcom - A minimalistic terminal program

ctrl-T  it's captured by the window manager and it's not posible to open menu at gnome or mate window managers.
ctrl-\ has been repaced with ctrl-T because using microcom under gtk terminal it's drop the combination key ctrl+\ and others, so menu was never opened.
I also provided a MICROCOM_MENU_KEY envinroment value in order to set your favorite key to open the menu, so you can run as it :

``` 
MICROCOM_MENU_KEY='L' microcom -p /dev/<device_name>
```

```
SYNOPSIS
       microcom [-d] [-f] [-p devfile|-t host:port] [-s speed]
       microcom -c interface:rx_id:tx_id
       microcom -h

DESCRIPTION
       This manual page documents briefly the microcom command.

       microcom  is  a is a minimalistic terminal program for accessing devices (e.g. switches) via a serial connection.  It features connection via RS232 serial interfaces
       (including setting of transferrates) as well as in `telnetmode' as specified in rfc2217 and a (Linux specific) can mode.

       The escape character to enter the program menu is crtl-L (^L). There are several commands available, among them quit (to exit microcom), exit (to return to  normal  mode)
       and speed (to set terminal speed)

OPTIONS
       microcom follows the usual GNU command line syntax, with long options starting with two dashes (`-'). A summary of options is included below.

       -d     output debugging info to stdout.

       -f     ignore an already existing lock file.

       -p devfile, --port=devfile
              use the specified serial port device (default /dev/ttyS0).

       -s speed, --speed=speed
              use specified baudrate (default 115200).

       -t host:port, --telnet=host:port
              work in telnet (rfc2217) mode.

       -c interface:rx_id:tx_id, --can=interface:rx_id:tx_id
              work in CAN mode (default: can0:200:200)

       -h, --help
              Show help.

AUTHOR
       This manual page was written by Uwe Kleine-König based on work initially done by Alexander Reichle-Schmehl.

```

INSTALLING 

Microcom uses autoconf and libreadline-dev so you must to install it, run autoconf, ./configure and make 

```
apt-get install autoconf libreadline-dev

autoconf
./configure
make

```
TROUBLESHOOTING

autoconf could fail, run `autoreconf -i` to build the configure file  
