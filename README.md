# Using pyserial to connect to esp8266

Found out that `screen` doesn't seem to want to play with `/dev/tty.Repleo-CH341*` so using pyserial as an old school terminal. Another option is coolterm but this seems to handle the escape characters better.

From https://d1workshop.readthedocs.io workshop.

Driver from https://www.mac-usb-serial.com (best €8 I've spent :)).

```sh
$ pipenv install  # pyserial

$ pipenv shell --fancy

$ python -m serial.tools.list_ports
/dev/cu.Bluetooth-Incoming-Port
/dev/cu.MALS
/dev/cu.Repleo-CH341-00203214
/dev/cu.SOC
/dev/cu.usbserial-143220
5 ports found

$ python -m serial.tools.miniterm /dev/cu.Repleo-CH341-00203214 115200 --raw

# blank screen? Try ctrl + c and hitting enter a few times
>>>

# ctrl + ] to exit
```

# Funny outputs

You might see something like this, I hit `ctrl+c` then enter a few times and waited for a timeout (guessign a network connection):

```
...mojibake...
...onnecting to network.

# ctrl+c
Traceback (most recent call last):
  File "boot.py", line 18, in <module>
KeyboardInterrupt:
Traceback (most recent call last):
  File "main.py", line 5, in <module>
  File "env_mon.py", line 20, in <module>
OSError: -2

# enter
# enter
>>>
>>>
>>>
```
