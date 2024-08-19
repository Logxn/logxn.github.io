+++
title = 'The Downfall Of EUCHEATS'
date = 2024-08-13T19:44:43+02:00
draft = true
+++
## 0x1 - Introduction
I like playing video games of all different categories for example racing, moba, adventure or horror just to name a few.
My favourite games however are shooter games, so much so that I started playing my first shooter Counter-Strike: Source when I was at the age of 13.
However at the age of 13, just starting out with those kinds of games, I had to learn the hard way that I simply wasn't skilled enough to compete with other players who were quite older than me at the time.
So my younger self made the decision to start cheating in online video games and continued to do so for a couple of years until I was 18 or so.

![This is me lol](https://media1.tenor.com/m/H6_jv3PzuHQAAAAC/shame-got.gif#center)

Even though I am not cheating in video games anymore, I have made quite a few contacts all around the cheating scene and continue to read and post in different forums that evolve around cheating.
This is where I stumbled upon a thread where a user was discussing that he had received a *HWID*-ban after cheating in a video game and that he bought himself a *HWID-spoofer* and got banned again.
Naturally a discussion started about which *HWID-spoofer* is the best and where to buy them from.

But what exactly is *HWID*, what is an *HWID-ban* and what is a *HWID-spoofer* you might ask.
*HWID* is the abbreviation for *Hardware ID* and is essentially a generated identifier of different components of you system.
Now there are many different identifiers you could possibly choose from - but there are also some pretty crappy ones as well, since you want to generate an identifier that is unique to the person playing.
For example a bad identifier would be the combination out of `CPU Model + GPU Model` because that would just give you an identifier like `i7 13700k + RTX 4070ti` and that surely isn't unique to every player.
However a better example would be taking `the serialnumber of the cpu + the serialnumber of the gpu`, because these are unique to every player.

{{< alert icon="circle-info" iconColor="light-grey">}}
**Info!**<br>
There are better identifiers that can be used for HWIDs but I'll keep it simple.
{{< /alert >}}

These generated identifiers are then sent back to the game developers. Once they catch you cheating they can permanently ban your PC from playing the game until you switch out the affected components (that is if they have chosen an identifier which you can easily replace) and this is commonly referred to as a *HWID-ban*.
To circumvent these kinds of bans, cheaters often use *HWID-spoofers* which do what the name suggests.
However because many games use different kinds of identifiers you either need different spoofers or one spoofer that does it all and that subsequently means that prices for these are high (some sell for $100 for 48h access).


## 0x2 - Who is EUCHEATS
Going back to the forum discussion, a user named [EUCHEATS](https://eucheats.com) advertised their own HWID spoofer.
![EUCHEATS HWID Advertisement](eucheats-advertisement.png)
It didn't take long until another user noted that the author should resort to HWID-spoofers of companys that have a known and good reputation instead of someone calling themselves "EUCHEATS".
EUCHEATS became offended by that an responded with the following:
> How can we be scammers & not trusted? and our post didn't get deleted from [3rd party site outside of the cheating forum] since 2022?

Furthermore they stated:
> Go google us! or Find us on YouTube! We sell cheats since 2019 & no one reported/called us scammers... We were promoted by these youtubers:

And then they listed a bunch of YouTube videos of advertisers promoting the cheats of EUCHEATS.

I saw this as a challenge and decided to see for myself how trustworthy they really are.

### 0x21 - Their Website
![EUCHEATS WEBSITE 1](eucheats-website-1.png)
Upon inspecting the website of EUCHEATS I could instantly see their advertisment for different cheats.
Noticably their website was also filled with different grammar errors, while I don't expect a blog post to be free of grammar errors for non native english speakers, I'd expect a company or individual selling different products to produce a website that is free from grammar mistakes.

![EUCHEATS FOOTER](eucheats-footer.png)
Upon inspecting their footer, I could also notice the same grammar mistakes and poorly written English. Even more noticable was the copyright disclaimer produced by their forum software *XenForo* which includes the timespan 2010-2017, which leads me to believe that either a) the software hasn't been updated in a while and most likely prone to some serious vulnerabilities or b) the software has been pirated, which is more likely, since a XenForo license isn't exactly cheap.

However, I won't judge a book by it's cover and I discovered there was a free version of their cheat that anyone can download and try IF you register on their forums - and that's exactly what I did.

### 0x22 - The Free Cheat Advertisement
![EUCHEATS FREE CHEAT ADVERTISEMENT](eucheats-free-cheat-advertisement.png)
As you can see the cheat in question is a free cheat for the game *CS2* (aka: Counter-Strike formerly Counter-Strike: Global Offensive).
Their advertisement is quite funny, because they state the following:
> Eucheats provides one of the longest running Undetected free CS2 cheats in the scene, our cheats are still undetected by VAC in 2024.

It is a weird statement to make when no one in the cheating scene has ever heard from you and there are - apart from the YouTube advertisements these YouTubers do for a cheap price or a free copy of the cheat - basically no reviews of the software in question.
Further more they state:

> Our Free CS2 Hack has too many CS2 Features rather than other cheat providers. EUCheats provides users the best experience to beat their opponents and of course, our CS2 Hacks are 100% free!

This is quite an exaggeration because the features they provide in the free cheat (ESP aka Wallhack, Aimbot, Bunnyhop, Rank Reveal) are the most common and basic features of a cheat for CS2 with the last feature being a straight up lie because it has already been patched in Counter-Strike: Global Offensive (CSGO).


So let's download and inspect this free cheat shall we? 🕵️

## 0x3 - Their Free Cheat
Upon downloading their cheat my Windows Defender greeted me with all kinds of virus warnings and because I don't trust no name cheat providers to not infect their software with malware I booted up my Windows VM to take a closer look.

### 0x31 - Initial Recon
![FREE CHEAT NAME](free-cheat-name.png)
The downloaded archive `EUCHEATS-FREE.rar` contained a file called `ASUSLEDs.exe`. A little spoiler: This file will be the login client and loader for the cheat. Some of you readers that might have some IT-Security background might know that malware tends to use names for executables that make them less obvious, but the same can be said for cheat developers. A while back this was sufficient for avoiding super simple anti-cheats that simply scanned for names of running executables. Most present day cheat developers will resort to executable names that are filled with random characters which are generated per download or don't even try to hide the name of the loader at all.

![DIE FREE CHEAT](die-free-cheat.png)
Upon inspecting the executable with [Detect it Easy](https://github.com/horsicq/Detect-It-Easy) we can see that the file was protected with Themida/Winlicense(3.XX).
Themida is a protection system against Reverse Engineering and if the newest version was used could potentially be a pain in the ass to remove said protection.
Luckily for us though a most likely pirated version of the product was used (as licenses cost $199) and we can resort to a tool called [mal-unpack](https://github.com/hasherezade/mal_unpack).

![MALUNPACK FREE CHEAT](malunpack-free.png)
As you can see this tool took only around 2 seconds to unpack the whole executable effectively removing the Themida Protector.

![DIE FREE CHEAT 2](die-free-cheat-2.png)
After inspecting the unpacked executable we can find new key informations. First of all the executable in question is also protected by a tool called [.NET REACTOR (guessed v4.8-4.9)](https://www.eziriz.com/dotnet_reactor.htm). Again we can assume that a pirated version of this software was used because the current version of .NET Reactor is v6.9.8.0 and the licensing price also starts at $199. Fortunately for us there is a tool called [de4dot](https://github.com/ret42/RE-Thing?tab=readme-ov-file#deobfuscator--decompiler--unpacker-etc) which has been modded tons of times to include support for various different protectors. The next and final key information we can gather from this newly unpacked exectuable is that it has been written in a .NET programming language (most likely C#). Cleaned and unpacked .NET files are the easiest files to reverse engineer because you almost restore the written code completely instead of relying on pseudo-code when it comes to other languages.

So lets deobfuscate this binary.

![DIE FREE CHEAT 3](die-free-cheat-3.png)
After deobfuscating with de4dot we can see only two protections are left. This guy really used all tools available on the internet to stop people from reverse engineering this piece of software. However this should be enough to take a first look with [dnSpy](https://github.com/dnSpyEx/dnSpy).

### 0x32 - Reverse Engineering
![FREE CHEAT ENTRYPOINT](free-cheat-entry.png)
This piece of code you see is the entry point. I will break it up in smaller parts, rename some function names, variables and explain it.

```csharp
// PSEUDO-CODE !
private void timer_tick(object sender, EventArgs e)
{
    index++;
    if (index >= 10)
    {
        timer.stop();
        string text = new WebClient().DownloadString("https://eucheats.com/FREE/up.txt");
        if (text.Contains("5.2"))
        {
            int button_pressed = (int)MessageBox.Show("EUCHEATS Premium version is now out! Stay safe & checkout our paid hack it's only 5€ per month.\r\n\r\nDo you want to buy it?", "PREMIUM VERSION", MessageBoxButtons.YesNo);
            if (button_pressed == 7) // Button No
            {
                Process.Start("https://eucheats.com/pages/premium-csgo-cheats/");
                picture.Hide();
                Class2.Class3_0.Form2.Show();
                return;
            }
            if (button_pressed == 6) // Button Yes
            {
                Process.Start("https://eucheats.com/account/upgrades");
                picture.Hide();
                Class2.Class3_0.Form2.Show();
                return;
            }
        }
    }
}
```
So first of all when you start the loader you are greeted with a picture of their logo. In this peace of code you can see that there is a `timer_tick()` function, that will get executed every second. For every second we have a variable called `index` which starts at 0 and counts up until it reaches 10. This simply is for making the user think the software is actually loading even if there is nothing to load 🙄.
![FREE CHEAT FAKE LOADING](free-cheat-loading.png)
{{< alert icon="skull-crossbones" iconColor="red" cardColor="orange" textColor="white">}}
**Bad Code Quality!**<br>
Here you can observe the first minor flaw in the software because the check if `index >= 10` is immediatly followed by a `timer.stop()`. So if the timer executes every second and stops at 10 seconds there is no need for a `>=` check. A simple `index == 10` check would've been sufficient.<br>
But don't worry this probably won't be the last flaw we are covering.
{{< /alert >}}


Afterwards the software makes a request to a `up.txt` which is located on the website of EUCHEATS and simply contains a decimal number which should represent the current version of the cheat. If the number still matches *5.2* it will show a popup asking if you want to buy the cheat. 
![FREE CHEAT POPUP](free-cheat-popup.png)
Doesn't matter what you answer in this popup, a wbesite where you can buy the cheat will be opened. If the popup was answered the fake loading screen will be hidden and a new window will be presented.


If the version number doesn't match the hardcoded number the cheat will close and the website of the free cheat will be opened, so a new version can be downloaded.

![FREE CHEAT FORM2](free-cheat-form2.png)
This is the disassembled code that gets loaded if the popup was dismissed and the cheats version number matches with the one of the server. What the author of the code intended to do is generate a HWID for himself. This is logical because cheat developers are interested in money and they want to prevent people sharing the cheat with their friends. So once again a HWID will be used to identify a unique user and to lock one PC to the registered forum account. The author intends to access the [Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/retrieving-a-class) which is a API provided by Windows that has every information about your PC (for example hardware information) stored in a database. Furthermore the author of the code intends to read the [ProcessorId](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-processor) which holds information about what capabilities the CPU has.
{{< alert icon="circle-info" iconColor="light-grey">}}
**Info!**<br>
As we learned previously this isn't a good way to generate a HWID, because the capabilities of a processor is not necessarily unique per user.
{{< /alert >}}

The `processId` is supposed to be stored in a label called `label7` and should be hidden from the user.

{{< alert icon="skull-crossbones" iconColor="red" cardColor="orange" textColor="white">}}
**Code Flaw!**<br>
Here you can observe the second code flaw. I mentioned a couple of times that the code author **intends** to read the `processorId`. Unfortunately the code is wrong as it misses the namespace of the database. Therefore the software presents an error warning when starting up and `label7` will never hold the requested information or let alone be hidden.

![FREE CHEAT ERROR](free-cheat-error.png)
The error message (in German) as explained above.

![FREE CHEAT MENU](free-cheat-menu.png)
Here you can see that `label7` never gets hidden.
{{< /alert >}}

![FREE CHEAT MENU](free-cheat-menu.png)
Here you can see the main menu of the free cheat. It has two tabs "Login" and "Confirmation". Confirmation has the same layout as the login tab and is used to set the HWID of a given user.
This we will inspect next.

![FREE CHEAT CONFIRMATION](free-cheat-confirmation.png)
As you can see from the disassembled code above, the loader makes a request to the backend of EUCHEATS, specifically `handler.php` and passes the supplied username, password and HWID. This triggers the registration of a user in another database that is not linked to the forum account, so why even make a forum account in the first place and a loader if you don't use it properly?
Since I stated above that the HWID never gets generated because of poorly written code, the request will always include `&hwid=label7` which means that every user registers with the same HWID completely defeating the purpose of a HWID check in the first place.

{{< alert icon="skull-crossbones" iconColor="red" cardColor="orange" textColor="white">}}
**Bad Code Quality!**<br>
In the code above you might observe the check that gets triggered before the error message "User Not Found!" is triggered. This check is unnecessarly complicated because it uses multiple functions (`IsNullOrWhitespace()` & `CompareString()`) to check wether invalid entries were made. However `IsNullOrWhitespace()` is sufficient to check if a string is either `null, empty or full of whitespaces`. Furthermore the username will not be compared against any existing forum accounts. Instead it will create an entry in another database which is then used by the login tab.
{{< /alert >}}