Supported devices are listed here [https://fprint.freedesktop.org/supported-devices.html](https://fprint.freedesktop.org/supported-devices.html)
Check if your device id. Run `lsusb` copy the id (the sixth column of the output) and search it on the website. In my case, it was 27c6:639c
![lsusb](/img/Screenshot%20from%202023-11-17%2011-09-08.png)
Let's proceed to the installation:
1- Search for the package fprint `apt search fprint`
![apt search fprint](/img/Screenshot%20from%202023-11-17%2009-51-06.png)
2- Install fprintd `sudo apt install fprintd` in my case it was already installed
![apt install frpintd](/img/Screenshot%20from%202023-11-17%2009-53-17.png)
3- Install the library/module PAM module `sudo apt install libpam-fprintd`
![apt install libpam](/img/Screenshot%20from%202023-11-17%2009-54-28.png)
4- Tell the system to use the fingerprint reader `sudo pam-auth-update`. make sure "Fingerprint authentication" is selected, then select "Ok" to save.
![pam auth update](/img/Screenshot%20from%202023-11-17%2010-01-20.png)
5- Add or enroll your fingers print `fprintd-enroll -f [finger]` so you can do `fprintd-enroll -f right-index-finger`
![add your finger prints](/img/Screenshot%20from%202023-11-17%2010-36-15.png)
*If omitted, it will default to the right index finger. Once run, press a finger on the sensor several times from several different angles. When the program exits, you are done.*
[finger] can be one of:
```bash
  left-thumb
  left-index-finger
  left-middle-finger
  left-ring-finger
  left-little-finger
  right-thumb
  right-index-finger
  right-middle-finger
  right-ring-finger
  right-little-finger
```
6- Test it! run 'fprintd-verify' enjoy!
