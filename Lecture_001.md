- Date: 08/02/2022
- Author: **@_dave**
- Topic: `Digital Assets Management Best Practices: How to Securely Manage Digital Assets`.

## Lecture 001

Great 

Glad we have some people joining us.
I want to welcome @everyone to 2022
This is our first community event this year
Like @Ameenah rightly [said](https://discord.com/channels/917010077154680902/917018045015293952/940550396840128514),
we are kickstarting 101-tuesdays as our weekly community engagement event
so in this maiden edition of this event, we will be discussing: 

Digital Assets Management Best Practices: How to Securely Manage Digital Assets.

Yeah some of us participated in the last meet up, where we introduced some concepts regarding non-custodial management of digital assets.
Just to clarify we would use digital asset and crypto interchangeably. I will be building on our previous convo.
As we proceed, it's note worthy to state that self-sovereignty is the basis upon which crypto thrives, you are your own bank.

There is absolutely no need to rely on 3rd-parties.
In the conventional financial system, we rely on banks as well as other trusted-parties to help us facilitate transactions.
In blockchain, we rely on battle-tested cryptography, the of concept you are your own bank comes with a lot of responsibilities.

Fraudulent schemes have taken more sophisticated dimensions and continue to bedevil the entire crypto ecosystem. 
Given that crypto wallets can be accessed by simple entry of corresponding mnemonic phrase/private keys, 
an understanding of some common schemes used to trick unsuspecting users into exposing their sensitive wallet credentialss is key to preventing unauthorized access
and assets theft.

The importance of security cannot be overemphasized.
So let me pause a bit and say this, as we continue, please I would like everyone @here to contribute, you can add emojis. 
There will be opportunity for us to ask questions, so feel free to do so when it's time for questions.
I want this to be engaging as much as possible.


Ok.

To use non-custodial asset, you must download and install a non-custodial wallet.
Several non-custodial wallets exist. Prominent ones include:
- Metamask: which is pretty popular https://metamask.io/
- Trust:  https://trustwallet.com/
- imToken: https://token.im/
- Coinbase: https://www.coinbase.com/wallet
- Coin98: https://coin98.com/wallet
- Rainbow, Coin98, Argent wallets e.t.c 
 
 These are non-custodial wallets because a mnemonic phrase/private key is generated upon  wallet creation which 
 allows you sign cryptographic signatures when executing transactions.
And like we elaborated on the previous meetup, the generated mnemonic phrase must be safely backed up (written down carefully in the right sequential order)
and stored carefully offline far from the reach of prying 3rd-parties.
Anyone that accesses your mnemonic phrase/private key has full access to import your wallet in any non-custodial wallet and spend any asset in your
wallet without your consent at will.

That being said, I will like to talk about: 
#### Some common schemes used by malicious actors and how we can guard against these.

1. **Phishing attacks**: Scammers commonly deploy cloned websites, look-alike emails to trick users into exposing their confidential information. 
These bad actors may pose as official representatives of popular blockchain projects by sending unsolicited emails containing malicious links which
redirects users to fraudulent sites where their confidential information is requested on unfounded basis.

2. **Questionable over-the-counter trades and giveaways**: In an attempt to induce unsuspecting users to subtly expose their mnemonic phrases/private keys
on phoney platforms, malicious actors propose juicy over-the-counter offers. This scheme which is usually promoted on social media is solely intended
to part with users’ hard-earned money. Every offer that prompts you to enter your confidential wallet information as a means of unlocking bounties/airdrop rewards
or multiplying your assets is fraudulent and should be avoided. 

Remember, if it is too good to be true then there is urgent need to exercise extreme caution. 
Any platform that requests your wallet credentials (mnemonic phrase, private key, wallet password) under any guise is malicious.


#### How to Stay Safe
- Always refer to official websites of known blockchain projects as it remains the go-to reference for resources on wallet security
(double-check the individual characters of the platform's URL to ensure you’re not visiting a phishing website).

- All attempts requesting you to provide your sensitive wallet credentials should be considered as fraudulent and disregarded forthwith.

- Never trust third-party platforms promoting airdrop campaigns on behalf of recognized blockchain projects without verifying from official 
sources platforms, official website, Twitter account, official Medium post are common means via which projects disseminate information to the community.

- Refrain from submitting your email address recklessly on airdrop promotion websites/platforms.

- Never attempt to install imToken app on a rooted device as it poses serious threat to the safety of your assets.

- Keep your wallet credentials offline; do not key in your mnemonic phrase into computers with active internet connection. 

- Never reveal your mnemonic phrase to anyone including persons claiming to be representatives of blockchain projects.

- Lock your smart phone at all times in order to restrict access. 

- Further fortify the security of your wallet by enabling the touch/face ID functionality in the security settings of your app. 

#### Final Notes

> For developers, before you push your solidity code, always double-check your config files to ensure you've safely added your private key in your .gitignore file
so that you don't make the terrible mistake of pushing your code containing your valued wallet credentials to GitHub.

> I'd strongly suggest that you avoid using your main wallet to deploy contracts. 
It's best practice to create and use dev wallet where you have only what you need for successful contract deployment when deploying to mainnet.


So with these, we've come to the end of this segment.
The floor is open for everyone @here to ask questions.
If there are areas that require clarification, please feel free to draw my attention to them. 
I'm here, waiting for questions.





_Published by @IBS_
