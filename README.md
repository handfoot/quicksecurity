# Handfoot Security Guide

*Last Update: August 12, 2020*

*If you would like to help improve this article, feel free to leave your suggestions in [Issues](https://github.com/handfoot/securitytips/issues/new) or email: handfoot at protonmail dot com*

No computer is perfectly safe, especially if connected to the Internet. This guide is meant to give activists a few tips to increase the security of their desktop computer, using the example of a Mac OS device (although should apply to Windows). Cybersecurity and convenience is a tradeoff, and this guide will try to find a good balance to keep you moderately secure, but still able to use the everyday computing tools you need to conduct activism work. I assume your threat model is medium to intermediate.

If you are actively targeted by the state, you will need to look at more secure options such as using [Tails](https://tails.boum.org/) Linux OS on a USB thumbstick to perform your activism work, and also invest in efforts to keep off the grid. I may write a future article about [Tails](https://tails.boum.org/).

In this guide, we will cover:

- Installing a fresh copy of MacOS with more secure options, such as network safeguards and drive encryption.
- Introduction to accessing the Internet using Containers in Firefox browser to keep different profiles in different silos.
- Using a free secure email service such as [ProtonMail](https://protonmail.com/).
- Setting up a VPN, such as [NordVPN](https://nordvpn.com/).
- Using Tor Browser to browse the internet anonymously.

For those in a rush, you may not want to backup important data, wipe your MacBook and do a clean install, although I strongly recommend that. In that case, please start with the Firefox Containers section, and skip the following Reinstall MacOS section.

## Reinstall a fresh secure copy of MacOS

Follow this excellent guide, [Hardening MacOS](https://blog.bejarano.io/hardening-macos/)
 and try to follow every step.

**Notes about the guide:**

The guide doesn't go into the details in the **Install a fresh copy of macOS** section. When you boot into recovery mode, go into Disk Utility, and delete the existing disk partitions to create a fresh new clean one (See Apple's [instructions](https://support.apple.com/en-gb/guide/disk-utility/dskutl14079/mac)). I recommend choosing Encrypted, but *not* the case-sensitive file system format. Then, proceed to format the boot drive and install macOS into the new file system. If you have issues reinstalling from scratch, or your recovery partition is gone, there is another guide called [How to create a bootable macOS Catalina installer drive](https://www.macworld.com/article/3442597/how-to-create-a-bootable-macos-catalina-installer-drive.html).

In the **First Boot** section of the guide, steps 22 and 23 (*outbound firewall* and *binary whitelisting*) can be considered optional, and only needed for intermediate level security.

In the **Second Boot** section of the guide, we will cover topics such as web browser, VPN, privacy-respecting email, and encrypted email later in this article.

## Firefox Containers

Unfortunately for us, the reality of using the modern Internet is that every service we use will probably try to build a profile of each of their users—to sell us ads, for our convenience (like remembering our purchase history or past search phrases), or simply to spy on us. We will cover the Tor Browser later as a means to browse the Internet anonymously, but for daily Internet use (like going on Facebook, Twitter, Reddit, GitHub, ordering stuff on Amazon, personal Internet banking), we recommend using Firefox as your main browser, and using a *Container* to browse each service separately.

For instance, you may have a personal Twitter account, a Twitter account used for activism, a Facebook account, Spotify account, a personal Amazon account, and Internet banking accounts. Why would you want to use a single profile for all of these different use cases, when we wouldn't know what information can be easily cross-shared between them? By using different container tabs, we can silo our Internet usage into different distinct profiles.

So go right ahead and download the [Firefox](https://www.mozilla.org/en-US/firefox/new/) browser for your desktop, and set that as your default browser. Follow the steps described in this [guide](https://www.lifewire.com/firefox-security-tips-and-tools-2487972) to secure your Firefox browser.

**Notes about the guide:**

The confusing point is that the *‘Facebook Container’* is a different add-on, and not the *Containers* feature I just referred to earlier (the naming a bit confusing naming). Facebook does so much snooping that an add-on was created to stop them. For example, when you log into Spotify, for whatever reason the Facebook login system is accessed even if you don't even have a Facebook account. The *Facebook Container* will try to block such Facebook tracking.

The *Containers* feature, on the other hand, allows you to create siloed profiles. I suggest using different container tabs for different browsing purposes, and do take advantage of the color codes and icons to make each container be distinct. **Make a conscious effort** not to mix up different containers, otherwise you may sign onto your activist Twitter account on the container you normally use for your personal Facebook or Twitter, potentially exposing your personal data across services (but note that if you use the same IP address your identify would be exposed anyways to either your ISP or VPN provider, if you use one).

As per the guide, I recommend installing the NoScript plug-in. This may be a bit of an annoyance, as some sites require pop-up windoes and JavaScript to work, but it is well worth it. They are also commonly used in services like online banking. You can easily temporarily or permanently enable JavaScript or cookies for a particular site. After a while, you kind of get used to this, and realize that it is a good thing to distrust by default.

Note that there is a version of Firefox available on Android and iOS as well.


## Tor Browser

While Firefox is useful for accessing the Internet sometimes with your real identity, or well-known persona (like public figure social media accounts), there are times when you want to use the Internet anonymously. For this purpose, install the [Tor Browser](https://www.torproject.org/) next. Based on a fork of the Firefox browser, it uses The Onion Router to keep your browsing activity as anonymous and untrackable as possible (your real IP address and hence location will be scrambled), although there are things we should take precaution if using Tor Browser.

You can consider using the Tor Browser for anything you want to keep really private, such as conducting research or surveying public articles, or logging into sensitive web email / social media accounts for activism activities. **Important:** If you use the Tor browser to log into, say, your activist Twitter account, and also log into the same account using a normal non-Tor browser, the social media service may be able to identify and *unscramble* you based on their logged IP address information. You should therefore decide whether you will settle on using VPN + Container approach to manage your activist account, or always do it through Tor Browser.

Another risk of Tor Browser (admittedly much less of an issue these days) is that the authorities can detect who is using Tor (via analyzing the exit nodes that connect you to the Tor network), and mark these people as suspicious. In countries like the US when there is a huge number of daily Tor users (in the order of millions), it is less of a risk, but for countries like Hong Kong, where the usage can be in the thousands only, it is advisable to use Tor only after connecting to a VPN in another country.

The only change I recommend after installing Tor is in Privacy & Security section, change the setting from Standard to Safer. Other than that, I wouldn't touch any configurations, as we want to blend in with every other Tor user out there. Never install add-ons in the Tor browser, and don't use it to remember user names or passwords.

Every time you quite the Tor browser, everything is wiped. But during a session if you want to create a new identify, you can easily do so by clicking on the little broom icon next to the address bar.

A note of caution: while all data is routed through the Tor network when using the Tor Browser, data from Internet usage *outside* of the browser is *not* routed through the Tor network. So while you may achieve privacy via encryption, you may still lose anonymity. To deal with this issue, operating systems such as [Tails](https://tails.boum.org/) is designed to route 100% of the data through the Tor network, and designed to be stored on a standalone USB thumbstick, with advanced features like secure memory wipe, etc., ideally used by journalists and activists in high risk countries. More tips about things to be careful about when using Tor [here](https://fossbytes.com/tor-anonymity-things-not-using-tor/).

Note that there is the official version of Tor Browser is available on Android, while the Onion Browser (endorced by the Tor project) is available on iOS.


## Proton Mail account

I recommend setting up a free [ProtonMail](https://protonmail.com/) account, that, as of writing, comes with 500MB of free storage. Personally I use an upgraded plan and pay for the service, but that's up to you. You will need to give them a mobile number for them to send you a verification code to get an account. They claim that the mobile number is not stored, but a secure hash of it is stored to prevent multiple people from creating accounts using one phone number. For a moderate threat model, that should be fine. If you want to be anonymous, you can give them a number from a burner phone / SIM card. Getting a burner phone + SIM card using cash, anonymously is standard procedure (but also quite detailed and must be done carefully) that is outside the scope of this article.

In addition to storing all of your emails in encrypted form deep inside a mountain in Switzerland, ProtonMail also makes it really easy and convenient to secure all email communications, even to non-ProtonMail users and to users without any knowledge of how public-private key encryption schemes (like PGP) work.

For example, after you setup an account, try composing an email to another (private) account. The email composer has an “Encryption” icon you can click on, where you will be prompted to type in a password to secure this email. The recipient of your email can simply click on the message, and be prompted for the password to decrypt it. The password can be communicated via secure means, such as Signal, but make sure each email has a different password. **Important:** Never put sensitive information in the subject of the email as that can be intercepted and may not be subject to encryption.

While the most secure way to email is using local email clients with strong encryption keys, services like ProtonMail can be a really easy way to securely communicate information between journalists, activists, political figures, without having to invest much time and energy on setting up a local encryption email system yourself.

## VPN

The Internet was not designed for privacy. When you use the Internet as-is, anyone can know who you are by identifying you using your IP address. Combined with other meta-data, it is relatively easy to pinpoint exactly who you are to a high degree of accuracy (the entropy of your identify is only 33-34 bits).

In addition to having your IP address exposed, your local ISP will also know every URL you have accessed and likely be keeping a log of the activity of each IP address. You can be sure that governments can request logs for every user in their jurisdiction and the local ISP will most certainly comply with the local authorities.

While getting a VPN service simply migrates the risk from your local ISP to the VPN provider (who may claim not to log anything), I still think you should get one. Chances are, it is easier for the local government to get PCCW to hand over the logs than NordVPN or ProtonVPN (if they even have any), based in other jurisdictions. Using NordVPN, you can also connect up to 6 devices over the VPN, and choose which country's server you want to use for your IP address. This has other benefits as well, like accessing content that restricts you to a country-specific IP address. And as discussed earlier, you want to be using the Tor Browser only after you connect to the Internet through a server outside of your country.

NordVPN is a good overall provider (at the time of writing their service is less than EUR 4/month for 3-years which is a bargain), while ProtonVPN and other providers are more focused on security at the expense of other factors like Internet speed. Some activists may also want to look at where the VPN is based, as some are in 5-eyes countries.

If you want to get a VPN anonymously (although won't be 100% anonymous), you can sign up to NordVPN using your anonymous Proton Mail account, and pay with bitcoin. The discussion of crypto currencies and their management is outside the scope of this article, but I recommend activists to be familiar with the use of bitcoin wallets for keeping funds secure, especially if one is moving across countries, or perhaps one wants to find a way to receive or pay funds outside of the financial system controlled and monitored by an authoritarian government.

## GitHub

[GitHub](https://github.com) is a good tool (with moderate security) for working on projects that may not require a high level of security (such as promotional materials and documents that will soon go public, but not document with sensitive information like activist identities). They give every user a free private account for creative private repositories that can only be accessed by the account holder and their collaborators. GitHub pages is also a good way to serve static webpages, or public documents, like this one. We can simply use markdown to create web pages with content we want to share with others.

You can register for a GitHub account using an anonymous email such as your proton mail.
