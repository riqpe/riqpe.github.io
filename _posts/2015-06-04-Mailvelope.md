---
layout: post
title: How to set up and use PGP encryption on your browser
permalink: Mailvelope
---
###How to set up and use PGP encryption on your browser

First off some disclaimers here. The method explained below will only work on Google Chrome and Mozilla Firefox. It utilizes the [OpenPGP.js] library, which implements PGP in JavaScript. Much issues with such implementation has been raised, some of which can be solved by delivering it as a browser extension. Others still remain, and for perfect security, these implementations ought to be avoided.

[Mailvelope] is an extension that integrates directly into the web mail user interface. It is available for both Google Chrome and Mozilla Firefox, from their respective repositories, and by downloading the extension from either [AMO] or [Chrome Web Store] you get a signed package that ensures its integrity and origin. Go ahead and install the extension now.

Before you can start using the extension in any meaningful way, you must first generate or import a key pair. A key pair consists of a public key that you may, and should share with anyone, and a secret key used for signing and decrypting. The secret key must stay secret, and known only by you. With this key, anyone can decrypt and read all emails encrypted by the public key, and use it to sign messages and files with your name. Click on the Mailvelope button and open settings. From settings navigate to a panel titled Generate Key. Here you should input your full name and email that are included in your keys. Make your password strong, as this is the only thing that prevents people from using your private key if you were to misplace it. I recommend using a generated [passphrase] as they are easier to remember, yet long enough prevent all but the most sophisticated of attacks. Do _not_ forget this password, as it is not possible to recover it. To manage all your passwords (you do use a different one everywhere, right?), you can use a password manager such as [KeePass]. After you press Submit, your key pair will be generated. This might take some time depending on the size of the key.

You can see your keys in the Display Keys panel. From here you can export your keys by clicking on the information button of the key you want to export. You must share your public key so that people can send you encrypted messages. How you do this is up to you, but to make it simple for people to find it, you should upload it to a key server, such as [SKS]. On the website you upload your public key, and search for other peoples public keys. The key server is synchronized with other key servers, which means that after a while your key is available globally. In addition you should export your private key and keep a copy somewhere safe. Mailvelope keeps your keys in the browser's LocalStorage, which could get erased.

To encrypt emails to others, you must first get the PGP key of the recipient and once again, how they will deliver it is up to them. Once you have it, you can import it from Mailvelope's settings' Import Keys tab. Simply paste the keys to the field and click Import. If the keys were correctly formed, they will now be visible on Display Keys, and available for use when encrypting emails and verifying signatures.

Sending encrypted emails with Mailvelope is simple. Anytime you start writing an email on any of the supported providers, a small pen and paper symbol is shown on the top right corner of the text field. By clicking it, a small window is opened. You can continue writing your email here if you wish, but you might as well use your web mail providers composing window until you are finished with the message. Once you are finished with your message, click the pen and paper symbol and select Encrypt to select your recipients. Always include yourself in the recipients list, as otherwise you will not be able to decrypt the message yourself. Finally, click on Ok and your PGP encrypted message is shown. To replace the original message with it, click on Transfer. You may now send the email as you normally would. Notice that the subject field is not encrypted. Be careful what you write there.

When receiving encrypted email, Mailvelope will automatically recognize the PGP encrypted message and cover it with a partially see-through overlay. Clicking the overlay will open a small window requesting the password for your secret key. After typing in your password and clicking Ok, the decrypted message is shown.

And that's it! Short and sweet. This solution is far from being ideal and leaves much to be desired. In addition to the security concerns, much of the common PGP functionality is missing. Encryption of attachments is currently not supported, and neither is signing of encrypted messages. There is also no simple way to generate a revocation certificate as of yet. However, the ease of use is unparalleled, as you do not need to install any additional software and can continue using your web mail as you have so far.

[OpenPGP.js]: http://openpgpjs.org/
[Mailvelope]: https://www.mailvelope.com/
[KeePass]: http://keepass.info/
[SKS]: https://sks-keyservers.net/
[AMO]: https://addons.mozilla.org/
[Chrome Web Store]: https://chrome.google.com/webstore
[passphrase]: http://world.std.com/~reinhold/diceware.html
