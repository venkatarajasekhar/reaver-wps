# reaver-wps
## Exploits a security hole in wireless routers and can crack most routers' current passwords with relative ease.

Walk through the steps required to crack a WPA password using Reaver.

First, a quick note: As we remind often remind readers when we discuss topics that appear potentially malicious: Knowledge is power, but power doesn't mean you should be a jerk, or do anything illegal. Knowing how to pick a lock doesn't make you a thief. Consider this post educational, or a proof-of-concept intellectual exercise. The more you know, the better you can protect yourself.

### What You'll Need

You don't have to be a networking wizard to use Reaver, the command-line tool that does the heavy lifting, and if you've got a computer with compatible Wi-Fi, and a few hours on your hands, you've got basically all you'll need. There are a number of ways you could set up Reaver, but here are the specific requirements for this guide:

1. A nearby WPA-secured Wi-Fi network. Technically, it will need to be a network using WPA security with the WPS feature enabled. I'll explain in more detail in the "How Reaver Works" section how WPS creates the security hole that makes WPA cracking possible.
2. A little patience. This is a 4-step process, and while it's not terribly difficult to crack a WPA password with Reaver, it's a brute-force attack, which means your computer will be testing a number of different combinations of cracks on your router before it finds the right one. When I tested it, Reaver took roughly 2.5 hours to successfully crack my password. The Reaver home page suggests it can take anywhere from 4-10 hours. Your mileage may vary.

Put your wireless card into monitor mode: Assuming your wireless card's interface name is `en0`, execute the following command to put your wireless card into monitor mode:
```
sudo airport en0 sniff 1
```

Now, with the BSSID and monitor interface name in hand, you've got everything you need to start up Reaver.

```
reaver -i en0 -b bssid -vv
```
