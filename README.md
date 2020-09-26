# Security Guide

*Last Update: August 2020*

No computer is perfectly safe, especially if connected to the Internet. This guide is meant to give activists a few tips to increase the security of their desktop computer, using the example of a Mac OS device (although should apply to Windows). Cybersecurity and convenience is a tradeoff, and this guide will try to find a good balance to keep you moderately secure, but still able to use the everyday computing tools you need to conduct activism work. I assume your threat model is medium to intermediate.

If you are actively targeted by the state, you will need to look at more secure options such as using [Tails](https://tails.boum.org/) Linux OS on a USB thumbstick to perform your activism work, and also invest in efforts to keep off the grid. I may write a future article about [Tails OS](https://tails.boum.org/).

**Summary**&nbsp; In this guide, we recommend doing the following things, and will cover each of them:

- Installing a fresh copy of MacOS with more secure options, such as network safeguards and drive encryption.
- Introduction to accessing the Internet using Containers in Firefox browser to keep different profiles in different silos.
- Using a free secure email service such as [ProtonMail](https://protonmail.com/).
- Setting up a VPN, such as [NordVPN](https://nordvpn.com/) or the more expensive [ProtonVPN](https://protonvpn.com/) which gives you a bundle deal with ProtonMail.
- Using Tor Browser to browse the Internet anonymously.


## Secure your MacOS


We will go through a list of steps to secure your MacOS. This section is based on the guide called [Hardening MacOS](https://blog.bejarano.io/hardening-macos/).

### Reinstall fresh copy of MacOS after formatting the hard disk.

For those in a rush, you may not want to backup important data, wipe your MacBook and do a clean install, although I strongly recommend that. In that case, you can skip this section.

To format your hard disk and install a fresh copy of MacOS, hit command-R after reboot, and you can follow the menu to erase your current hard disk (the boot drive, or main hard disk), and reinstall MacOS on that empty drive. All data will be gone from the boot drive. Note that the recovery partition on your mac can be an older version of MacOS, in which case you can install it, and then upgrade to the most recent version after installation.

(*Optional*)&nbsp; Before reinstalling MacOS, go to the Utilities > Firmware Password Utility and consider setting up a firmware password to protect your data should it be lost or stolen.


### Post installation steps

Follow each of these steps after you have reinstalled MacOS from scratch. If you are in a rush and didn't do that, at least follow the following steps:

- Go to System Preferences > Software Update and consider enabling automatic updates (if you are not comfortable enabling this, consider at least turning on security updates by going into Advanced… and checking Install system data files and security updates)

- Go to System Preferences > Security & Privacy > General and set Require password after sleep to immediately or 5 seconds

- Go to System Preferences > Security & Privacy > Firewall and turn on the firewall

- Go to System Preferences > Security & Privacy > Firewall > Firewall Options… and check Block all incoming connections

- Go to System Preferences > Security & Privacy > Privacy > Location and uncheck Enable Location Services

- Go to System Preferences > Security & Privacy > Privacy > Analytics and uncheck Share Mac Analytics

- Go to System Preferences > Sharing and anonymize the computer’s name (**important**), this name can be see by those connected to the same network as yours

- Go to System Preferences > Sharing and turn off every service (turn on only when using it and disable afterwards)

- Go to System Preferences > Spotlight > Search Results and uncheck Spotlight Suggestions and Allow Spotlight Suggestions in Look up

- Go to System Preferences > General and uncheck Allow Handoff between this Mac and your iCloud devices

- Go to System Preferences > Bluetooth and turn off Bluetooth (turn on only when using it and disable afterwards)

- Go to Finder > Preferences > Advanced and check Show all filename extensions

- Block malicious domain names using the /etc/hosts file (use StevenBlack's [hosts](https://raw.githubusercontent.com/StevenBlack/hosts/master/hosts) file with nearly 30K entries)

- Go to System Preferences > Security & Privacy > FileVault and turn on FileVault (note: may take some time)

- Secure FileVault when on sleep: (do this inside of a terminal)

```
sudo sh -c 'pmset -a destroyfvkeyonstandby 1; pmset -a hibernatemode 25; pmset -a powernap 0; pmset -a standby 0; pmset -a standbydelay 0; pmset -a autopoweroff 0'
```

**Important**&nbsp; FireVault is a disk encryption feature that will encrypt the contents of your hard disk, making it difficult to extract the data (without being able to login with your password), if your computer is taken away.

- Go to System Preferences > Security & Privacy > Privacy > Contacts/Calendars/Reminders/Photos and remove any apps that shouldn’t have access to any of those folders, if any

- Go to System Preferences > Security & Privacy > Privacy > Camera/Microphone and remove any app you don’t want to have access to the camera or microphone, if any

- Go to System Preferences > Security & Privacy > Privacy > Full Disk Access and remove any app you don’t want to have full-disk access, if any

- Go to System Preferences > Security & Privacy > Privacy > Advertising, check Limit Ad Tracking and click Reset Advertising Identifier


## Firefox Containers

Unfortunately for us, the reality of using the modern Internet is that every service we use will probably try to build a profile of each of their users—to sell us ads, for our convenience (like remembering our purchase history or past search phrases), or simply to spy on us. We will cover the Tor Browser later as a means to browse the Internet anonymously, but for daily Internet use (like going on Facebook, Twitter, Reddit, GitHub, ordering stuff on Amazon, personal Internet banking), we recommend using Firefox as your main browser, and using a *Container* to browse each service separately.

For instance, you may have a personal Twitter account, a Twitter account used for activism, a Facebook account, Spotify account, a personal Amazon account, and Internet banking accounts. Why would you want to use a single profile for all of these different use cases, when we wouldn't know what information can be easily cross-shared between them? By using different container tabs, we can silo our Internet usage into different distinct profiles.

So go right ahead and download the [Firefox](https://www.mozilla.org/en-US/firefox/new/) browser for your desktop, and set that as your default browser. I'm basing the settings on this [guide](https://www.lifewire.com/firefox-security-tips-and-tools-2487972) to secure your Firefox browser, but will suggest things slightly different.

### Privacy and Security Settings

The first thing you should do is click on “≡” button on the top right corner of your browser, and then select *Preferences*. Afterwards, select *Privacy & Security*.

- Go to “Firefox Data Collection and Use” and make sure *Allow Firefox to send technical and interaction data to Mozilla*, *Allow Firefox to install and run studies*, and *Allow Firefox to send backlogged crash reports on your behalf* are not selected.

- In “Send web sites a “Do Not Track” signal that you don’t want to be tracked” select *Always*.

*Optional:* Select *Strict* for “Enhanced Tracking Protection”

### Install Add-ons

Click on ≡ again and then select Add-ons. Install the following add-ons (enable also in Private Windows when promted):

- DuckDuckGo Privacy Essentials

- DuckDuckGo

- HTTPS Everywhere

- Privacy Badger

- uBlock Origin

- Cookie AutoDelete

- Decentraleyes

- Facebook Container

- Firefox Multi-Account Containers

*Optional:* As per the  [guide](https://www.lifewire.com/firefox-security-tips-and-tools-2487972), installing the NoScript plug-in only for high security (it will change your browsing habits), although I recommend it if you are willing to change your habits. This may be a bit of an annoyance, as some sites require pop-up windows and JavaScript to work, but it is well worth it. They are also commonly used in services like online banking. You will need to be used to (easily) temporarily or permanently enable JavaScript for a particular site. After a while, you kind of get used to this, and realize that it is a good thing to distrust by default.


### Change Search Engine to DuckDuckGo

To avoid getting constantly tracked by Google, I recommend using DuckDuckGo for your search engine. You can always use Google / Gmail if you want on case-by-case basis. The first thing you should do is click on “≡” button on the top right corner of your browser, and then select *Preferences* then *Search*. Make sure DuckDuckGo is the default search engine. It should be the case already after “DuckDuckGo Privacy Essentials” add-on has been installed.

### Use Containers

The *Containers* feature allows you to create siloed profiles for Internet browsing. I suggest using different container tabs for different browsing purposes, and do take advantage of the color codes and icons to make each container be distinct. **Make a conscious effort** not to mix up different containers, otherwise you may sign onto your activist Twitter account on the container you normally use for your personal Facebook or Twitter, potentially exposing your personal data across services (but note that if you use the same IP address your identify would be exposed anyways to either your ISP or VPN provider, if you use one).

Go to File, New Container Tab, and Manage Containers. I would delete all the existing settings, and start creating different containers for different use cases. I would have a few of them to silo my Internet browsing, such as:

- One for each social media account, and keeping activist accounts in different containers to personal accounts.

- Google-related services (YouTube, Gmail, Google Docs, etc). You may want to set up one for personal Google services, and one for activism related work, if you have another set of Google accounts for activism.

- Different containers for Protonmail, online banking, Bitcoin-related.

- Services like Amazon, Dropbox, Spotify do a lot of tracking, so make sure they are in different Containers. Spotify also tries to access your Facebook login that the Facebook container will prevent.

If you use NoScript add-on, your settings can also be different in each container. For instance, in my case, my Google container will allow Javascript code from Google sites to run, but other containers will disable Javascript from Google sites, to keep Google from tracking activities of other business.

The confusing point is that the *‘Facebook Container’* is a different add-on, and not the *Containers* feature I just referred to earlier (the naming a bit confusing naming). Facebook does so much snooping that an add-on was created to stop them. For example, when you log into Spotify, for whatever reason the Facebook login system is accessed even if you don't even have a Facebook account. The *Facebook Container* will try to block such Facebook tracking.


## Tor Browser

While Firefox is useful for accessing the Internet sometimes with your real identity, or well-known persona (like public figure social media accounts), there are times when you want to use the Internet anonymously. For this purpose, install the [Tor Browser](https://www.torproject.org/) next. Based on a fork of the Firefox browser, it uses The Onion Router to keep your browsing activity as anonymous and untrackable as possible (your real IP address and hence location will be scrambled), although there are things we should take precaution if using Tor Browser.

You can consider using the Tor Browser for anything you want to keep really private, such as conducting research or surveying public articles, or logging into sensitive web email / social media accounts for activism activities.

**Important**&nbsp; If you use the Tor browser to log into, say, your activist Twitter account, and also log into the same account using a normal non-Tor browser, the social media service may be able to identify and *unscramble* you based on their logged IP address information. You should therefore decide whether you will settle on using VPN + Container approach to manage your activist account, or always do it through Tor Browser.

Another risk of Tor Browser (admittedly much less of an issue these days) is that the authorities can detect who is using Tor (via analyzing the exit nodes that connect you to the Tor network), and mark these people as suspicious. In countries like the US when there is a huge number of daily Tor users (in the order of millions), it is less of a risk, but for countries like Hong Kong, where the usage can be in the thousands only, it is advisable to use Tor only after connecting to a VPN in another country.

**Important**&nbsp; If you are using Tor in a country with [high usage](https://metrics.torproject.org/userstats-relay-country.html), the authorities may be able to detect and identify that you are using Tor even though they cannot see what you are browsing in the Tor network, and may put you on a list. Hong Kong has around 6,000 active Tor users (connected to Tor network via a HK IP Address), which isn't that much to track. For this reason, I recommend connecting to Tor only after you have connected to a US or Canada VPN server.

The only change I recommend after installing Tor is in Privacy & Security section, change the setting from Standard to Safer. Other than that, I wouldn't touch any configurations, as we want to blend in with every other Tor user out there. Never install add-ons in the Tor browser, and don't use it to remember user names or passwords.

Every time you quit the Tor browser, everything is wiped. But during a session if you want to create a new identify, you can easily do so by clicking on the little broom icon next to the address bar.

A note of caution: while all data is routed through the Tor network when using the Tor Browser, data from Internet usage *outside* of the browser is *not* routed through the Tor network. So while you may achieve privacy via encryption, you may still lose anonymity. To deal with this issue, operating systems such as [Tails OS](https://tails.boum.org/) is designed to route 100% of the data through the Tor network, and designed to be stored on a standalone USB thumbstick, with advanced features like secure memory wipe, etc., ideally used by journalists and activists in high risk countries. More tips about things to be careful about when using Tor [here](https://fossbytes.com/tor-anonymity-things-not-using-tor/).

Note that there is the official version of Tor Browser is available on Android, while the Onion Browser (endorced by the Tor project) is available on iOS.


## ProtonMail account

I recommend setting up a free [ProtonMail](https://protonmail.com/) account, that, as of writing, comes with 500MB of free storage. Personally I use an upgraded plan and pay for the service, but that's up to you. You will need to give them a mobile number for them to send you a verification code to get an account. They claim that the mobile number is not stored, but a secure hash of it is stored to prevent multiple people from creating accounts using one phone number. For a moderate threat model, that should be fine. If you want to be anonymous, you can give them a number from a burner phone / SIM card. Getting a burner phone + SIM card using cash, anonymously is standard procedure (but also quite detailed and must be done carefully) that is outside the scope of this article.

In addition to storing all of your emails in encrypted form deep inside a mountain in Switzerland, ProtonMail also makes it really easy and convenient to secure all email communications, even to non-ProtonMail users and to users without any knowledge of how public-private key encryption schemes (like PGP) work.

![Encryption](/img/use_protonmail_encryption.cleaned.png)

### Use the Encryption feature

After you setup an account, try composing an email to another (private) account. The email composer has an “Encryption” icon you can click on, where you will be prompted to type in a password to secure this email. The recipient of your email can simply click on the message, and be prompted for the password to decrypt it. The password can be communicated via secure means, such as Signal, but make sure each email has a different password. The recipient can also securely reply to your email if it is sent this way.

**Important**&nbsp; Never put sensitive information in the subject of the email as that can be intercepted and may not be subject to encryption.

While the most secure way to email is using local email clients with strong encryption keys, services like ProtonMail can be a really easy way to securely communicate information between journalists, activists, political figures, without having to invest much time and energy on setting up a local encryption email system yourself.

## VPN

The Internet was not designed for privacy. When you use the Internet as-is, anyone can know who you are by identifying you using your IP address. Combined with other meta-data, it is relatively easy to pinpoint exactly who you are to a high degree of accuracy (the entropy of your identify is only 33-34 bits).

In addition to having your IP address exposed, your local ISP will also know every URL you have accessed and likely be keeping a log of the activity of each IP address. You can be sure that governments can request logs for every user in their jurisdiction and the local ISP will most certainly comply with the local authorities.

While getting a VPN service simply migrates the risk from your local ISP to the VPN provider (who may claim not to log anything), I still think you should get one. Chances are, it is easier for the local government to get PCCW to hand over the logs than NordVPN or ProtonVPN (if they even have any), based in other jurisdictions. Using NordVPN, you can also connect up to 6 devices over the VPN, and choose which country's server you want to use for your IP address. This has other benefits as well, like accessing content that restricts you to a country-specific IP address. And as discussed earlier, you want to be using the Tor Browser only after you connect to the Internet through a server outside of your country.

NordVPN is a good overall provider (at the time of writing their service is less than EUR 4/month for 3-years which is a bargain), while ProtonVPN and other providers are more focused on security at the expense of other factors like Internet speed. Some activists may also want to look at where the VPN is based, as some are in 5-eyes countries.

**Important**&nbsp; Unless you have good reasons to, don't connect to VPN servers in Hong Kong.

If you want to get a VPN anonymously (although won't be 100% anonymous), you can sign up to NordVPN using your anonymous Proton Mail account, and pay with bitcoin. The discussion of crypto currencies and their management is outside the scope of this article, but I recommend activists to be familiar with the use of bitcoin wallets for keeping funds secure, especially if one is moving across countries, or perhaps one wants to find a way to receive or pay funds outside of the financial system controlled and monitored by an authoritarian government.

## GitHub (Optional)

[GitHub](https://github.com) is a good tool (with moderate security) for working on projects that may not require a high level of security (such as promotional materials and documents that will soon go public, but not document with sensitive information like activist identities). They give every user a free private account for creative private repositories that can only be accessed by the account holder and their collaborators. GitHub pages is also a good way to serve static webpages, or public documents, like this one. We can simply use markdown to create web pages with content we want to share with others.

You can register for a GitHub account using an anonymous email such as your proton mail.

---

*If you would like to help improve this article, feel free to leave your suggestions in [issues](https://github.com/handfoot/securitytips/issues/new), or email handfoot at protonmail dot com*
