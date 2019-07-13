---
title: "Using HTML Proofer to Find and Fix Broken Links"
excerpt: "This guide explains how to use an HTML proofer to find broken links, so we can fix them and stop being mad at broken links."
tags: ["ToDo"]
categories: ["Contributors-Guide"]
published: false
---

We all know how much it sucks when links are broken. Especially the internal links we use to navigate within these sites. If you're interested to help out, but wondering if there's an easier way than clicking each link and hunting through the source to fix the reference, this is the guide for you!

I'm assuming you have already gotten a local copy of this site, and are familiar with our [Website Configuration](website-configuration/). Soon there will be a simple and straightforward guide for copying  site and testing our site locally, so you won't have to study that huge guide just to test the waters.

## [gjtorikian/html-proofer](https://github.com/gjtorikian/html-proofer)

>HTMLProofer is a set of tests to validate your HTML output. These tests check if your image references are legitimate, if they have alt tags, if your internal links are working, and so on. It's intended to be an all-in-one checker for your output.
>
>In scope for this project is any well-known and widely-used test for HTML document quality. A major use for this project is continuous integration -- so we must have reliable results. We usually balance correctness over performance. And, if necessary, we should be able to trace this program's detection of HTML errors back to documented best practices or standards, such as W3 specifications.

### Install


```ruby
source 'https://rubygems.org'
gem "minimal-mistakes-jekyll"

gem "jekyll-paginate"
gem "jekyll-sitemap"
gem "jekyll-gist"
gem "jekyll-feed"
gem "jemoji"
gem "jekyll-include-cache"
gem "jekyll-mentions"
gem 'html-proofer'
```

Then you must type `bundle install` from the root of your local copy.

### Test run on Decentralized-id.com

Once installed, you can run Html Proofer as a command-line app. 

There's [a lot of other ways](https://github.com/gjtorikian/html-proofer) to use it, but here's a simle example that gives us some actionable results:

`htmlproofer --disable_external --directory_index_file index.html --empty_alt_ignore ./_site`

*`Running ["LinkCheck", "ScriptCheck", "ImageCheck"] on ["./_site"] on *.html... `*

*`Ran on 152 files!`*

```html
- ./_site/404.html
  *  internally linking to /humanitarian, which does not exist (line 2084)
     <a href="/humanitarian" rel="permalink"></a>
  *  internally linking to /humanitarian, which does not exist (line 3293)
     <a href="/humanitarian" rel="permalink"></a>
  *  internally linking to /id-initiatives/ethereum/uport, which does not exist (line 2565)
     <a href="/id-initiatives/ethereum/uport" rel="permalink"></a>
  *  internally linking to /id-initiatives/ethereum/uport, which does not exist (line 3774)
     <a href="/id-initiatives/ethereum/uport" rel="permalink"></a>
  *  internally linking to /id-initiatives/state-sponsored, which does not exist (line 1785)
     <a href="/id-initiatives/state-sponsored" rel="permalink"></a>
  *  internally linking to /id-initiatives/state-sponsored, which does not exist (line 2994)
     <a href="/id-initiatives/state-sponsored" rel="permalink"></a>
  *  internally linking to /indy-ecosystem, which does not exist (line 1577)
     <a href="/indy-ecosystem" rel="permalink"></a>
  *  internally linking to /indy-ecosystem, which does not exist (line 2786)
     <a href="/indy-ecosystem" rel="permalink"></a>
  *  internally linking to /indy-ecosystem/github, which does not exist (line 2188)
     <a href="/indy-ecosystem/github" rel="permalink"></a>
  *  internally linking to /indy-ecosystem/github, which does not exist (line 3397)
     <a href="/indy-ecosystem/github" rel="permalink"></a>
- ./_site/awesome-decentralized-id/index.html
  *  internally linking to /humanitarian/, which does not exist (line 1014)
     <a href="/humanitarian/">Humanitarian</a>
  *  internally linking to /id-initiatives/indy-ecosystem/literature/, which does not exist (line 1068)
     <a href="/id-initiatives/indy-ecosystem/literature/">Literature</a>
  *  internally linking to /id-initiatives/spid-chain/, which does not exist (line 1075)
     <a href="/id-initiatives/spid-chain/">Spid-chain</a>
  *  internally linking to self-sovereign-identity, which does not exist (line 935)
     <a href="self-sovereign-identity">/DIDecentralized/self-sovereign-identity</a>
  *  linking to /history/#decentralized-identity-foundation, but decentralized-identity-foundation does not exist (line 977)
     <a href="/history/#decentralized-identity-foundation">Decentralized Identity Foundation</a>
  *  linking to /history/#the-end-of-2016, but the-end-of-2016 does not exist (line 975)
     <a href="/history/#the-end-of-2016">The End of 2016</a>
  *  linking to /history/#the-united-nations-sustainable-development-goals, but the-united-nations-sustainable-development-goals does not exist (line 970)
     <a href="/history/#the-united-nations-sustainable-development-goals">The United Nations Sustainable Development Goals</a>
  *  linking to /id-initiatives/bitcoin/#bitnation, but bitnation does not exist (line 1042)
     <a href="/id-initiatives/bitcoin/#bitnation">Bitnation</a>
  *  linking to /id-initiatives/bitcoin/#btcr, but btcr does not exist (line 1040)
     <a href="/id-initiatives/bitcoin/#btcr">BTCR</a>
  *  linking to /id-initiatives/bitcoin/#rwot-btcr, but rwot-btcr does not exist (line 1041)
     <a href="/id-initiatives/bitcoin/#rwot-btcr">RWoT BTCR</a>
  *  linking to /id-initiatives/bitcoin/#spidchain, but spidchain does not exist (line 1043)
     <a href="/id-initiatives/bitcoin/#spidchain">Spidchain</a>
  *  linking to /id-initiatives/ethereum/#assorted-ethereum-apps, but assorted-ethereum-apps does not exist (line 1059)
     <a href="/id-initiatives/ethereum/#assorted-ethereum-apps">Assorted Ethereum Apps</a>
  *  linking to /id-initiatives/ethereum/#cryptonomica, but cryptonomica does not exist (line 1058)
     <a href="/id-initiatives/ethereum/#cryptonomica">Cryptonomica</a>
  *  linking to /id-initiatives/ethereum/#erc-eip, but erc-eip does not exist (line 1053)
     <a href="/id-initiatives/ethereum/#erc-eip">ERC-EIP</a>
  *  linking to /id-initiatives/ethereum/#erc725-735, but erc725-735 does not exist (line 1054)
     <a href="/id-initiatives/ethereum/#erc725-735">ERC725-735</a>
  *  linking to /id-initiatives/ethereum/#jolocom, but jolocom does not exist (line 1056)
     <a href="/id-initiatives/ethereum/#jolocom">Jolocom</a>
  *  linking to /id-initiatives/ethereum/#spidchain, but spidchain does not exist (line 1057)
     <a href="/id-initiatives/ethereum/#spidchain">Spidchain</a>
  *  linking to /id-initiatives/ethereum/#uport, but uport does not exist (line 1055)
     <a href="/id-initiatives/ethereum/#uport">uPort</a>
  *  linking to /standards/#blockcerts, but blockcerts does not exist (line 1008)
     <a href="/standards/#blockcerts">Blockcerts</a>
  *  linking to /standards/#decentralized-key-management-agents, but decentralized-key-management-agents does not exist (line 1006)
     <a href="/standards/#decentralized-key-management-agents">Decentralized Key Managment DKMS</a>
  *  linking to /standards/#did-auth, but did-auth does not exist (line 1005)
     <a href="/standards/#did-auth">DID Auth</a>
  *  linking to /standards/#did-the-decentralized-identifier, but did-the-decentralized-identifier does not exist (line 1001)
     <a href="/standards/#did-the-decentralized-identifier">DID the Decentralized Identifier</a>
  *  linking to /standards/#ethereum-erc-eip, but ethereum-erc-eip does not exist (line 1007)
     <a href="/standards/#ethereum-erc-eip">Ethereum ERC-EIP</a>
  *  linking to /standards/#oasis-xdi-tech-committee-on-github, but oasis-xdi-tech-committee-on-github does not exist (line 995)
     <a href="/standards/#oasis-xdi-tech-committee-on-github">OASIS XDI TC Technical Committee on GitHub</a>
  *  linking to /standards/#schema, but schema does not exist (line 1009)
     <a href="/standards/#schema">Schema</a>
  *  linking to /standards/#verifiable-claims, but verifiable-claims does not exist (line 1002)
     <a href="/standards/#verifiable-claims">Verifiable Claims</a>
  *  linking to /standards/#w3c, but w3c does not exist (line 999)
     <a href="/standards/#w3c">W3C</a>
  *  linking to /standards/#xdi, but xdi does not exist (line 993)
     <a href="/standards/#xdi">XDI</a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>T</strong></a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>G</strong></a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>B</strong></a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>wp</strong></a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>D</strong></a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>F</strong></a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>C</strong></a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>tele</strong></a>
  *  linking to internal hash #contents that does not exist (line 892)
     <a href="#contents"><strong>web</strong></a>
  *  linking to internal hash #contents that does not exist (line 893)
     <a href="#contents"><strong>ϟ</strong></a>
  *  linking to internal hash #contents that does not exist (line 893)
     <a href="#contents"><strong>&gt;</strong></a>
  *  linking to internal hash #contents that does not exist (line 893)
     <a href="#contents"><strong>»</strong></a>
- ./_site/blockchain/bitcoin/index.html
  *  linking to internal hash #Bitnation-and-the-United-Nations that does not exist (line 776)
     <a href="#Bitnation-and-the-United-Nations"><strong>^</strong></a>
- ./_site/blockchain/ethereum/index.html
  *  internally linking to eth-id-github.html#cryptonomica, which does not exist (line 994)
     <a href="eth-id-github.html#cryptonomica">Cryptonomica Github Repos</a>
  *  internally linking to eth-id-github.html#eip---erc, which does not exist (line 903)
     <a href="eth-id-github.html#eip---erc">ERC-EIP on GitHub</a>
  *  internally linking to eth-id-github.html#jolocom, which does not exist (line 969)
     <a href="eth-id-github.html#jolocom">Jolocom Github Repos</a>
  *  internally linking to eth-id-github.html#spid-eth-repos, which does not exist (line 983)
     <a href="eth-id-github.html#spid-eth-repos">Spid-Eth GitHub Repos</a>
  *  trying to find hash of eth-id-github.html#cryptonomica, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/blockchain/ethereum/eth-id-github.html does not exist (line 994)
     <a href="eth-id-github.html#cryptonomica">Cryptonomica Github Repos</a>
  *  trying to find hash of eth-id-github.html#eip---erc, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/blockchain/ethereum/eth-id-github.html does not exist (line 903)
     <a href="eth-id-github.html#eip---erc">ERC-EIP on GitHub</a>
  *  trying to find hash of eth-id-github.html#jolocom, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/blockchain/ethereum/eth-id-github.html does not exist (line 969)
     <a href="eth-id-github.html#jolocom">Jolocom Github Repos</a>
  *  trying to find hash of eth-id-github.html#spid-eth-repos, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/blockchain/ethereum/eth-id-github.html does not exist (line 983)
     <a href="eth-id-github.html#spid-eth-repos">Spid-Eth GitHub Repos</a>
- ./_site/bookmark-donations/index.html
  *  linking to internal hash #main that does not exist (line 145)
     <a href="#main" class="screen-reader-shortcut">Skip to content</a>
- ./_site/code/github/index.html
  *  internally linking to ../index.html#contact, which does not exist (line 1016)
     <a href="../index.html#contact">a message</a>
  *  internally linking to Rebooting-Web-of-Trust.md, which does not exist (line 1366)
     <a href="Rebooting-Web-of-Trust.md">One Page List of RWoT Literature</a>
  *  trying to find hash of ../index.html#contact, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/code/index.html does not exist (line 1016)
     <a href="../index.html#contact">a message</a>
- ./_site/history/index.html
  *  internal image assets/img/chaum-security-without-identification-big-brother.png does not exist (line 784)
  *  linking to internal hash #Bitcoin that does not exist (line 986)
     <a href="#Bitcoin"><strong>&gt;</strong></a>
- ./_site/hyperledger/hgf-2018/index.html
  *  internally linking to Microledgers-Edgechains-Hardman-HGF.md, which does not exist (line 779)
     <a href="Microledgers-Edgechains-Hardman-HGF.md">Microledgers and Edge-Chains - Daniel Hardman - Evernym</a>
  *  internally linking to VerifiableOrganizationsNetwork-HGF.md, which does not exist (line 780)
     <a href="VerifiableOrganizationsNetwork-HGF.md">Verifiable Organizations Network: A Production Government Deployment of Hyperledger Indy</a>
- ./_site/hyperledger/indy/index.html
  *  internally linking to Link-Shorthand, which does not exist (line 845)
     <a href="Link-Shorthand"><strong>tele</strong></a>
  *  internally linking to Link-Shorthand, which does not exist (line 845)
     <a href="Link-Shorthand"><strong>web</strong></a>
  *  internally linking to literature.md#eu-general-data-protection-regulation-act, which does not exist (line 1022)
     <a href="literature.md#eu-general-data-protection-regulation-act">EU General Data Protection Regulation Act</a>
  *  internally linking to literature.md#reports, which does not exist (line 1024)
     <a href="literature.md#reports">Reports</a>
  *  internally linking to literature.md#research-papers, which does not exist (line 1023)
     <a href="literature.md#research-papers">Research Papers</a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 845)
     <a href="#Link-Shorthand"><strong>T</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 845)
     <a href="#Link-Shorthand"><strong>G</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 845)
     <a href="#Link-Shorthand"><strong>B</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 845)
     <a href="#Link-Shorthand"><strong>wp</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 845)
     <a href="#Link-Shorthand"><strong>D</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 845)
     <a href="#Link-Shorthand"><strong>F</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 845)
     <a href="#Link-Shorthand"><strong>C</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 846)
     <a href="#Link-Shorthand"><strong>ϟ</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 846)
     <a href="#Link-Shorthand"><strong>&gt;</strong></a>
  *  linking to internal hash #Link-Shorthand that does not exist (line 846)
     <a href="#Link-Shorthand"><strong>^</strong></a>
  *  trying to find hash of literature.md#eu-general-data-protection-regulation-act, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/hyperledger/indy/literature.md does not exist (line 1022)
     <a href="literature.md#eu-general-data-protection-regulation-act">EU General Data Protection Regulation Act</a>
  *  trying to find hash of literature.md#reports, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/hyperledger/indy/literature.md does not exist (line 1024)
     <a href="literature.md#reports">Reports</a>
  *  trying to find hash of literature.md#research-papers, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/hyperledger/indy/literature.md does not exist (line 1023)
     <a href="literature.md#research-papers">Research Papers</a>
- ./_site/indy-ecosystem/von/index.html
  *  linking to internal hash #Canada that does not exist (line 829)
     <a href="#Canada"><strong>&gt;</strong></a>
- ./_site/literature/index.html
  *  internally linking to /id-initiatives/indy-ecosystem/literature/, which does not exist (line 761)
     <a href="/id-initiatives/indy-ecosystem/literature/">» Sovrin Related Literature</a>
  *  internally linking to rebooting-web-of-trust.md#completed-papers, which does not exist (line 887)
     <a href="rebooting-web-of-trust.md#completed-papers">Completed Papers</a>
  *  internally linking to rebooting-web-of-trust.md#primers, which does not exist (line 881)
     <a href="rebooting-web-of-trust.md#primers">Primers</a>
  *  internally linking to rebooting-web-of-trust.md#rebooting-the-web-of-trust-i, which does not exist (line 889)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-i">Rebooting the Web of Trust I</a>
  *  internally linking to rebooting-web-of-trust.md#rebooting-the-web-of-trust-ii---id2020, which does not exist (line 890)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-ii---id2020">Rebooting the Web of Trust II - ID2020</a>
  *  internally linking to rebooting-web-of-trust.md#rebooting-the-web-of-trust-iii, which does not exist (line 891)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-iii">Rebooting the Web of Trust III</a>
  *  internally linking to rebooting-web-of-trust.md#rebooting-the-web-of-trust-iv, which does not exist (line 892)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-iv">Rebooting the Web of Trust IV</a>
  *  internally linking to rebooting-web-of-trust.md#rebooting-the-web-of-trust-v, which does not exist (line 893)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-v">Rebooting the Web of Trust V</a>
  *  internally linking to rebooting-web-of-trust.md#rebooting-the-web-of-trust-vi, which does not exist (line 894)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-vi">Rebooting the Web of Trust VI</a>
  *  internally linking to rebooting-web-of-trust.md#rebooting-the-web-of-trust-vii, which does not exist (line 895)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-vii">Rebooting the Web of Trust VII</a>
  *  internally linking to rebooting-web-of-trust.md#rwot-workshop-related, which does not exist (line 882)
     <a href="rebooting-web-of-trust.md#rwot-workshop-related">RWoT Workshop Related</a>
  *  internally linking to rebooting-web-of-trust.md#selected-rebooting-web-of-trust-whitepapers, which does not exist (line 879)
     <a href="rebooting-web-of-trust.md#selected-rebooting-web-of-trust-whitepapers">Selected RWoT Whitepapers</a>
  *  internally linking to rebooting-web-of-trust.md#use-cases, which does not exist (line 883)
     <a href="rebooting-web-of-trust.md#use-cases">Use Cases</a>
  *  internally linking to rebooting-web-of-trust.md, which does not exist (line 876)
     <a href="rebooting-web-of-trust.md"><strong>» Rebooting Web of Trust - “complete” Papers, Topics and Advance Readings »</strong></a>
  *  linking to internal hash #assorted-thought-around-identity that does not exist (line 760)
     <a href="#assorted-thought-around-identity">Assorted Thought Around Identity</a>
  *  linking to internal hash #rwot-1 that does not exist (line 901)
     <a href="#rwot-1">RWoT 1</a>
  *  linking to internal hash #rwot-3 that does not exist (line 903)
     <a href="#rwot-3">RWoT 3</a>
  *  linking to internal hash #rwot-4 that does not exist (line 904)
     <a href="#rwot-4">RWoT 4</a>
  *  linking to internal hash #rwot-5 that does not exist (line 905)
     <a href="#rwot-5">RWoT 5</a>
  *  linking to internal hash #rwot-6 that does not exist (line 906)
     <a href="#rwot-6">RWoT 6</a>
  *  linking to internal hash #rwot-7 that does not exist (line 907)
     <a href="#rwot-7">RWoT 7</a>
  *  linking to internal hash #rwot-id2020 that does not exist (line 902)
     <a href="#rwot-id2020">RWoT 2</a>
  *  linking to internal hash #topics-and-advance-readings that does not exist (line 899)
     <a href="#topics-and-advance-readings">Topics and Advance Readings</a>
  *  trying to find hash of rebooting-web-of-trust.md#completed-papers, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 887)
     <a href="rebooting-web-of-trust.md#completed-papers">Completed Papers</a>
  *  trying to find hash of rebooting-web-of-trust.md#primers, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 881)
     <a href="rebooting-web-of-trust.md#primers">Primers</a>
  *  trying to find hash of rebooting-web-of-trust.md#rebooting-the-web-of-trust-i, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 889)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-i">Rebooting the Web of Trust I</a>
  *  trying to find hash of rebooting-web-of-trust.md#rebooting-the-web-of-trust-ii---id2020, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 890)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-ii---id2020">Rebooting the Web of Trust II - ID2020</a>
  *  trying to find hash of rebooting-web-of-trust.md#rebooting-the-web-of-trust-iii, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 891)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-iii">Rebooting the Web of Trust III</a>
  *  trying to find hash of rebooting-web-of-trust.md#rebooting-the-web-of-trust-iv, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 892)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-iv">Rebooting the Web of Trust IV</a>
  *  trying to find hash of rebooting-web-of-trust.md#rebooting-the-web-of-trust-v, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 893)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-v">Rebooting the Web of Trust V</a>
  *  trying to find hash of rebooting-web-of-trust.md#rebooting-the-web-of-trust-vi, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 894)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-vi">Rebooting the Web of Trust VI</a>
  *  trying to find hash of rebooting-web-of-trust.md#rebooting-the-web-of-trust-vii, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 895)
     <a href="rebooting-web-of-trust.md#rebooting-the-web-of-trust-vii">Rebooting the Web of Trust VII</a>
  *  trying to find hash of rebooting-web-of-trust.md#rwot-workshop-related, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 882)
     <a href="rebooting-web-of-trust.md#rwot-workshop-related">RWoT Workshop Related</a>
  *  trying to find hash of rebooting-web-of-trust.md#selected-rebooting-web-of-trust-whitepapers, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 879)
     <a href="rebooting-web-of-trust.md#selected-rebooting-web-of-trust-whitepapers">Selected RWoT Whitepapers</a>
  *  trying to find hash of rebooting-web-of-trust.md#use-cases, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/literature/rebooting-web-of-trust.md does not exist (line 883)
     <a href="rebooting-web-of-trust.md#use-cases">Use Cases</a>
- ./_site/literature/rebooting-web-of-trust/index.html
  *  linking to internal hash #completed-papers-iii that does not exist (line 2146)
     <a href="#completed-papers-iii">Completed Papers III</a>
  *  linking to internal hash #completed-papers-iii that does not exist (line 2180)
     <a href="#completed-papers-iii">Completed Papers III</a>
- ./_site/literature/self-sovereign-identity/evolution-of-ssi/index.html
  *  internally linking to self-sovereign-identity-bill-of-rights.md, which does not exist (line 750)
     <a href="self-sovereign-identity-bill-of-rights.md">Self-Sovereign Bill of Rights</a>
  *  internally linking to ssi-principles-vs-characteristics, which does not exist (line 743)
     <a href="ssi-principles-vs-characteristics">SSI Principles vs. Characteristics</a>
- ./_site/literature/self-sovereign-identity/index.html
  *  linking to internal hash #Decentralized-Identity-Foundation that does not exist (line 846)
     <a href="#Decentralized-Identity-Foundation"><strong>&gt;</strong></a>
- ./_site/organizations/identity-foundation/index.html
  *  linking to internal hash #-decentralized-identity---github that does not exist (line 757)
     <a href="#-decentralized-identity---github">/decentralized-identity - GitHub</a>
  *  linking to internal hash #Decentralized-Identity-Foundation that does not exist (line 783)
     <a href="#Decentralized-Identity-Foundation"><strong>&gt;</strong></a>
- ./_site/organizations/sovrin-foundation/index.html
  *  linking to internal hash #Evernym that does not exist (line 755)
     <a href="#Evernym">Evernym</a>
- ./_site/public-sector/index.html
  *  internally linking to indy-ecosystem/VON.md, which does not exist (line 777)
     <a href="indy-ecosystem/VON.md">/indy-ecosystem/VON.md</a>
- ./_site/sitemap/index.html
  *  internally linking to /humanitarian, which does not exist (line 1582)
     <a href="/humanitarian" rel="permalink"></a>
  *  internally linking to /humanitarian, which does not exist (line 2791)
     <a href="/humanitarian" rel="permalink"></a>
  *  internally linking to /id-initiatives/ethereum/uport, which does not exist (line 2063)
     <a href="/id-initiatives/ethereum/uport" rel="permalink"></a>
  *  internally linking to /id-initiatives/ethereum/uport, which does not exist (line 3272)
     <a href="/id-initiatives/ethereum/uport" rel="permalink"></a>
  *  internally linking to /id-initiatives/state-sponsored, which does not exist (line 1283)
     <a href="/id-initiatives/state-sponsored" rel="permalink"></a>
  *  internally linking to /id-initiatives/state-sponsored, which does not exist (line 2492)
     <a href="/id-initiatives/state-sponsored" rel="permalink"></a>
  *  internally linking to /indy-ecosystem, which does not exist (line 1075)
     <a href="/indy-ecosystem" rel="permalink"></a>
  *  internally linking to /indy-ecosystem, which does not exist (line 2284)
     <a href="/indy-ecosystem" rel="permalink"></a>
  *  internally linking to /indy-ecosystem/github, which does not exist (line 1686)
     <a href="/indy-ecosystem/github" rel="permalink"></a>
  *  internally linking to /indy-ecosystem/github, which does not exist (line 2895)
     <a href="/indy-ecosystem/github" rel="permalink"></a>
- ./_site/specs-standards/index.html
  *  internally linking to eth-id-github.html#eip---erc, which does not exist (line 1099)
     <a href="eth-id-github.html#eip---erc">ERC-EIP on GitHub</a>
  *  internally linking to xdi.html, which does not exist (line 918)
     <a href="xdi.html"><strong>XDI</strong></a>
  *  trying to find hash of eth-id-github.html#eip---erc, but /home/infominer/infomine/didecentral/decentralized-id.com/_site/specs-standards/eth-id-github.html does not exist (line 1099)
     <a href="eth-id-github.html#eip---erc">ERC-EIP on GitHub</a>
- ./_site/specs-standards/xdi/index.html
  *  internally linking to /topics-and-advance-readings/XDI-Graphs-in-IPFS.md, which does not exist (line 825)
     <a href="/topics-and-advance-readings/XDI-Graphs-in-IPFS.md">XDI Graphs in IPFS</a>
  *  linking to internal hash #services that does not exist (line 789)
     <a href="#services">Services</a>
  *  linking to internal hash #xdi-configurations that does not exist (line 783)
     <a href="#xdi-configurations">XDI Configurations</a>
- ./_site/workshops/index.html
  *  internally linking to rebooting-web-of-trust.html, which does not exist (line 770)
     <a href="rebooting-web-of-trust.html"><strong>Rebooting Web Of Trust - Papers and Advance Readings Index</strong></a>
```

`htmlproofer 3.10.2 | Error:  HTML-Proofer found 149 failures!`


So you can see there are a lot of false alerts, but you'll get used to it's common false flags, and over time, we'll figure out which options to use for fine tuning of it's results.

