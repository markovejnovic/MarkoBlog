+++
date = "2018-10-01"
tags = ["Android", "Personal", "Phone", "Fiddling"]
title = "Flashing a Chinese Phone"
description = "Installing a clean Android ROM on the Xiaomi Redmi 4"
author = "Marko Vejnovic"
+++

# Introduction

So, about three days ago, I managed to get my hands on a _cheapish_ second hand 
[Xiaomi Redmi Note 4](https://www.gsmarena.com/xiaomi_redmi_note_4-8531.php). 
I didn't really have a phone for almost a year, and [living without a phone in 
China](https://www.forbes.com/sites/ywang/2017/05/15/your-mobile-money-surviving-a-day-in-china-without-cash-or-cards/)
to be very difficult. I decided to buy a cheap phone on [Xianyu](https://2.taobao.com/).

## Buying the phone

After looking around a bit, I concluded that the 
[Xiaomi Redmi 4X](https://www.gsmarena.com/xiaomi_redmi_4_(4x)-8608.php) seemed
to be a good phone for my requirements. I wanted a cheap phone with decent 
specifications and a big battery. So, on [Xianyu](https://2.taobao.com) I found
a person selling the phone, and decided to hit him up.

Well, buying the phone was a mess. Turns out, in China, people hate when you 
ask for the quality of the product you are willing to buy. They call you a 
"looker" from what I understood, which basically means you browse through 
the stuff people are selling and just ask about them without the intention of 
buying. So, the seller got a bit angry at me, but since the pictures of the 
phone seemed alright, I decided to just go for it.

He was selling the device for ¥520 (around $75) and after a bit of haggling, we
agreed on a price of ¥500 (around $70) with included express shipping.

## Getting the phone

Of course, the phone didn't arrive when I expected it to. The seller kept 
asking me if it arrived (since he doesn't get the money until I receive the 
phone), but as much as I checked our campus's mail room, I couldn't find it.
After a bit of inquiry, I did manage to find the phone hidden behind a few 
boxes in the mail room.

So, I open up the box, right, and I turn it on - no issues, smooth performance, 
albeit the operating system [MIUI](http://en.miui.com/) looked horrible. So, at
this point, I'm pretty happy. But, [never settling](https://www.oneplus.com/), 
I decided that I would like to install a clean custom ROM on the phone.

## Unlocking the bootloader

Xiaomi likes to lock the bootloader of their phones because they're afraid 
people will tamper with their phones. Then again, we are in China, after all, 
and given the political situation of the internet in China, it does make sense.

Luckily, it's not that big of a pain to unlock the bootloader! Xiaomi offers a 
piece of software which is supposed to unlock your phone but it requires a 
phone number and an application for unlocking.

I managed to borrow a SIM card from a friend and I downloaded the 
[MI Unlock Tool](https://en.miui.com/unlock/). After a bit of figuring out how 
to enter fastboot mode (a mode in which you can directly write to the phone's 
memory), I pressed the big orange "Unlock" button in the _Mi Unlock Tool_. It 
ran its scan to see if I can unlock, but, sadly, a message popped up - 
"You cannot do this operation more than once every 72 hours". Dang it, guess 
I'd try again in 72 hours.

So today, I repeated the procedure and it worked! Perfect! Unlocked phone!
<img style="width:300px; display:block; margin: 0 auto" 
src="https://img.xda-cdn.com/Mia_3MYgINFXtchrAUh7ASEaBvg=/http%3A%2F%2Fuploads.tapatalk-cdn.com%2F20161213%2F92a8ce16b60e0045d293bc9cf81ac7ad.jpg">

## Installing recovery

So, a typical Android setup has multiple partitions - `/recovery`, `/boot` - 
just like a Linux setup. Well, the bootloader can load from `/recovery` if 
there are issues when starting from `/boot`. The system in `/recovery` has full
access to other partitions, of course, so it is possible to change everything 
in the `/boot` and the `/system` partitions. Because of that, it's necessary to
install a custom `/recovery` software so it's possible to flash `/system` and 
`/boot`.

Currently, the most popular and well-documented option is 
[TWRP](https://twrp.me/). Since I did use it before and didn't have issues with
it, I decided to just stick to it. Flashing the `/recovery` partition turned 
out to be quite easy.

Basically, you'd have to download a `.img` of the custom `/recovery` you want 
to install. Then, you'd just use `fastboot` which would literally write over 
the `/recovery` partition of the phone (similar to `dd`). Simple enough, eh?

So I downloaded the 
[TWRP for `santoni`](https://twrp.me/xiaomi/xiaomiredmi4x.html) (the code name 
of the _Xiaomi Redmi 4(X)_). 
I tried to flash it:
```bash
fastboot flash recovery twrp-santoni.img
```

No errors! Perfect. Now, Xiaomi's have a diagnostic self-check software which 
is run from `/boot`, you need to boot into _TWRP_ and let it overwrite over 
that software so it doesn't run. If you don't do this, next time you boot, 
the diagnostic software is notice that the hash of the `/recovery` partition 
is not right, and then it is going to overwrite `/recovery` with the stock 
_Xiaomi_ one. Luckily, `fastboot` also allows us to reboot the phone such that 
it loads the system from a custom `.img` file:
```bash
fastboot boot custom.img
```
So, I guess we can boot into our custom _TWRP_:
```bash
fastboot boot twrp-santoni.img
```

Except, no, not really. I'd get the error:
```txt
dtb not found
```

A Google search led me to believe that this means that the bootloader cannot 
find the `dtb` which is a data structure which describes undiscoverable 
hardware. Hmm, so I guess the `dtb` is a necessary thing. Why couldn't the 
bootloader find it? Well, the only explanation was that the `dtb` was not in 
the right memory space.

Well, after quite a few hours of looking around the internet as to why this 
might be the way it is it turned out I was an idiot. My phone wasn't a 
_Redmi 4(X)_. It was a _Redmi Note 4(X)_. Instead of using _TWRP_ for my phone,
I was using one which was made for a different phone, and therefore, the 
bootloader could not find the _DT_ blob, because it wasn't in the right address.

Well, then, fastforward to doing all of this again but with the right _TWRP_ 
image, I succeeded.

<img src="https://upload.wikimedia.org/wikipedia/commons/f/fe/TWRP_2.7.0.0.png"
	style="width:300px; display:block; margin:0 auto">

## Custom ROM

Well, from now it was pretty straightforward - get a custom ROM, download it 
to the device's internal storage, get the Google Suite of Apps, and flash 
everything using _TWRP_.

After looking online, I decided to settle down for 
[AOSPExtended](https://www.aospextended.com/), since it seemed to be pretty 
good from what people were saying.

A quick flash of the system and the google suite of apps, I booted into the 
phone!

<img src="/img/rom.jpg" 
style="width:300px; display:block; margin:0 auto">

## Future

Well, for now, I'd definitely say I'm happy with _AOSPExtended_, but I do plan 
on finding a more lightweight ROM, which is more tweaked to my preferences. Who
knows? I might even make my own launcher...
