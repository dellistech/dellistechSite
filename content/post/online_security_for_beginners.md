---
title: "Online Security for Beginners"
date: 2023-01-26T14:09:37-07:00
draft: false
---


*"Hey, you're good with computers, right?"*

Every person who works in tech knows that conversations that start like this have no happy ending. You've got one of two solutions here: Either play dumb
(*"Nope, what's a computer?"*), or prepare yourself for the story about the weird thing their phone or printer does. And heaven help you if it's an app
idea or a question about crypto-currency. 

I happen to work in cybersecurity, so I also get the odd smattering of *"Can you get into my ex's Facebook?"* or *"A guy on the radio said I needed a VPN. 
Which one should I get?"*  

While it might be worth it to get into some of those in depth a little later, I did want to share a resource I've used for those general 
questions about how to not be an easy target for most online attacks, which is this article titled "Security Guidelines for Congressional Campaigns." I'll 
summarize the points below and add some updates because the site seems to be down at time of writing. But the most recent web archive of the page is 
[here.](https://web.archive.org/web/20220507021158/https://techsolidarity.org/resources/congressional_howto.html) These are ranked in rough order of priority, 
and are stripped down to just the actionable steps, so don't worry about the theory behind them.

** Disclaimer: This is all advice for "good enough" personal online security against your run-of-the-mill scammers and opportunistic hackers. There's a lot
of nuance here, and there are exceptions for all the advice listed below, but these are a solid start for minimizing your attack surface as an individual 
with normal tech skills. I'm not focusing on government or nation-state level actors here. Good fences make good neighbors, but your garden fence isn't 
going to keep out a SWAT team. **  

## 1. Updates

Keep everything up to date. That means you should be checking for updates on your phone, your computer, and your browser. Take a few minutes to learn where
you can check for updates on the software you use, as well as what update pop-ups typically look like. If an update pop-up looks different than you've seen 
before, take note of what it claimed to be updating, close the pop-up and check that program for updates manually. Fake update pop-ups are a pretty common 
malware distribution channel, so proceed with care. 

## 2. Anti-Virus

Somewhat counter-intuitively, remove these, as they generally create more problems than they solve. The one exception is Windows Defender, which comes baked
in to Windows. It's safe to use, and actually pretty effective at securing your PC. 

## 3. Email

Email is absolutely critical to defend, because it tends to hold the keys to the kingdom. All those "Forgot your password?" links on every site you regularly
visit will send a link to your email. So if a hacker gets access to your email, they have access to everything. For that reason, you are going to want to use 
Gmail for your personal email, and use Chrome for your browser to check it. 

Enable 2FA when logging into your email. (More on 2FA and MFA later.)

Don't allow any apps permissions to read or write to your email inbox.

Email is also not suitable for highly sensitive conversations. Have them in person, or use Signal for end-to-end encryption. (More on Signal later.)

## 4. Attachments

Attachments are the #1 way targeted attacks occur, so you need to be extremely careful how you handle them. Even emails from a known sender are a risk, so here
is the hierarchy of ways to view an email attachment, from safest to most risky:

- Open the attachment on your phone. At time of writing, malware is less likely to work on your phone than your PC.
- Save the attachment directly to Google Drive, then view it from there. On a PC, hovering over the attachment in Gmail, you'll see a "save in Google Drive" icon.
This will keep the attachment from running on your PC when you view it.
- Download the attachment to disk, then upload it to Google Drive, being careful to not open the file before uploading it, and deleting it locally afterwords.
- Double-clicking the attachment. This is the most likely to lead to infection. Never do this. 

## 5. Phone

This one is controversial, but by and large, iPhones are more secure than Android. Most of the arguments I've heard to the contrary have more to do with concerns
about Silicon Valley mass-surveillance marketing or concerns of government involvement, and most of the alternative solutions are either impractical ("ditch 
the smartphone entirely,") or require more tech knowledge than I think most people have ("Use a custom firmware on an Android phone.") Feel free to debate me on 
Twitter if you feel strongly about it.

For everyone else, just make sure you have an iPhone that is still receiving updates (iPhone 8 or newer). It's much safer to do the majority of your work on your
phone than on your PC, so it is always better to read email, use Signal, and surf the web on your phone.

Make sure you set up the lock screen with at least a 6 key code or password. TouchID or FaceID are both safe to use, but Siri is not. It can leak information even 
when your phone is locked. Apple Wallet is safe to use as well.

When doing online work on your phone, it is usually better to use cellular data than to connect to public WiFi. If your data plan is limited or your reception is 
spotty and you need to connect to WiFi, you should use a Virtual Private Network (VPN). (More about VPNs later.)

## 6. Passwords

This is going to sound like common knowledge, but password re-use is really bad. We all know this, but we also keep using the same one or two passwords for 
everything. I'm guilty of it myself. So, here are some tips to be better at that.

- **Use a password manager.** [1Password](https://1password.com/), [BitWarden](https://bitwarden.com/) or [Lastpass](https://www.lastpass.com/) are a few of the 
options that seem to balance ease of use with security, with features like syncing your password vault on your mobile as well as generating and storing strong, 
unique passwords. It's also a good idea to enable Multi-factor Authentication on any of your options. This makes it a little less likely to lose access to everything
in the event that your email account is compromised. 

- **Don't try to remember your passwords.** If you can remember your password, it's likely breakable using modern techniques. Use a good password generator and save
the passwords in a password manager.

- **Think about writing your passwords down.** Again, this might be controversial, but if you are more worried about scammers and hackers online than people that 
might break into your home, it may be better to keep your passwords off the computer entirely. It's still better to use a password generator to choose your passwords
in the first place, but the extra effort to keep them offline does eliminate the possibility of [hackers getting your entire password vault by targeting your 
password manager.](https://techcrunch.com/2022/12/22/lastpass-customer-password-vaults-stolen/)


## 7. Multi-factor Authentication

Enable 2 Factor Authentication (2FA) or Multi-Factor Authentication (MFA) where ever you can. Especially on email and your password manager. Also where ever possible,
try to use a hardware token for your second factor, like a Yubikey, RSA token, or an authentication app. [Google Authenticator](https://apps.apple.com/us/app/google-authenticator/id388497605) or [Authy](https://apps.apple.com/us/app/twilio-authy/id494168017) are two popular choices for apps. 
**You should prefer these to SMS authentication whenever possible.**

## 8. Laptop

Remember that your phone is always more secure than your laptop, so do as much of your work there as you can. Make sure that your laptop is running the most up-to-date
version of the operating system, and check for updates frequently. 

**Never plug USB drives into your computer.** This is another extremely common attack vector. If you need to share files, it's much safer to upload them to Google Drive
and send a link to the file to the person you are sharing the files with. 

You should set up full-disk encryption on your laptop. This will keep your files safe if your laptop is stolen. This will, however, make it impossible to recover your 
files if you forget the password, so make sure the recovery keys that are created when you set up disk encryption are written down and stored in a safe place. 

If possible, consider a Chromebook over a Mac or Windows laptop. Chromebooks are extremely locked down and can really only run the Chrome browser, which makes them 
much safer for the average user. 

### On VPNs

VPNs are only necessary if you are frequently traveling and are using public WiFi, such as at coffee shops or public libraries. If you only use your laptop at home or 
work, a VPN is not usually needed.

## 9. Text Messages

You should use [Signal](https://apps.apple.com/us/app/signal-private-messenger/id874139669) for all your text messages and group chat. It is end-to-end encrypted and 
the company cannot see anything sent between users. Avoid using other messaging apps.

## 10. Social Media

- Remove your phone number from Facebook.
- Enable 2FA or MFA on any site that allows it.
- Assume that anything posted or sent, even in private messages, could one day be public.
- Move any private conversations to Signal. 

## 11. Browser 

- You should use Chrome as the default browser on your laptop.
- Check for updates frequently, and install them as soon as they are available. 
- Install the uBlock Origin and Privacy Badger browser plugins. Avoid other plugins. 
- You should avoid using the TOR browser, but TOR itself is fine to use if set up properly. (If you don't know about TOR, you probably don't need it. Look out for a 
future write up here.)
- On your iPhone, it's okay to use Safari. 
- Use Incognito Mode by default.






