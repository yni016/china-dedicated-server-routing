# China Optimized Dedicated Server: Which Route Tier You're Actually Renting, What Bandwidth Really Costs, and Whether You Still Need an ICP Filing

A "China optimized dedicated server" is sold under at least four different network labels, and two machines with identical CPUs can differ by three times in price depending on which one you get. Two things decide whether you're overpaying: the route tier the box sits on, and the amount of bandwidth bundled with it. A third decides whether the setup is usable at all for your case: where the personal data of mainland users ends up stored.

What follows covers the route labels, the pricing mechanics that actually move a quote, the ICP and PIPL rules that Hong Kong hosting does not exempt you from, and three checks to run before you pay. AkkoCloud's China-facing lineup is the reference point; a handful of competitor listings appear at the end as a sanity check on price levels.

> **Quick verdict:** for a site, API or app serving mainland users with monthly transfer in the low terabytes, start on a CN2 GIA cloud instance rather than a dedicated box. AkkoCloud's San Jose entry configuration is listed at **¥50/month**, with the 1 vCPU / 2 GB tier at about **¥110/month (US$16.45)**. Single-tenant hardware only pays off when you need your own kernel, IPMI, and disks: the dedicated listing is a London dual EPYC 7552 with 512 GB RAM and 10×1TB SSD at **¥33,000/month**.
> 👉 [See AkkoCloud's current CN2 GIA plans and prices](https://bit.ly/akkocloud)

## The plans AkkoCloud lists

AkkoCloud is a China-facing host (its site footer dates the brand to 2019) running China Telecom CN2 GIA routing out of San Jose, Frankfurt and London, with VPS instances, dedicated servers and colocation. Support runs on Chinese-language tickets and a Telegram community, and checkout takes Alipay alongside international methods.

The grid below reproduces the plan list as compiled from AkkoCloud's order pages by public plan trackers in October 2026. Prices and stock in this segment move monthly, so treat the live order page as authoritative. Where a tracker did not record a disk size or an included transfer figure, the cell says so rather than guessing.

| Plan | vCPU / RAM / disk | Port and transfer | Price | Order |
| --- | --- | --- | --- | --- |
| San Jose CN2 GIA entry | 1 / 512 MB / 10 GB SSD | 300 Mbps / 500 GB | ¥50 per month | [View plan](https://bit.ly/akkocloud) |
| San Jose KVM-CN2-B1 | 1 / 2 GB / not listed | 1 Gbps / metered | ¥110 per month (US$16.45) | [View plan](https://bit.ly/akkocloud) |
| San Jose KVM-CN2-B2 | 1 / 2 GB / not listed | 1 Gbps / metered | ¥233 per month (US$34.85) | [View plan](https://bit.ly/akkocloud) |
| San Jose KVM-CN2-C1 | 1 / 2 GB / not listed | 1 Gbps / metered | ¥388.88 per month (US$58.16) | [View plan](https://bit.ly/akkocloud) |
| San Jose KVM-CN2-D1 | 2 / 4 GB / not listed | 1 Gbps / metered | ¥588.88 per month (US$88.07) | [View plan](https://bit.ly/akkocloud) |
| San Jose KVM-CN2-E1 | 4 / 8 GB / not listed | 1 Gbps / metered | ¥888.88 per month (US$132.94) | [View plan](https://bit.ly/akkocloud) |
| San Jose KVM-CN2-F1 | 4 / 8 GB / not listed | 1 Gbps / metered | ¥1,188.88 per month (US$177.81) | [View plan](https://bit.ly/akkocloud) |
| San Jose KVM-CN2-U1 | 2 / 2 GB / not listed | 30 Mbps unmetered | ¥1,200 per month (US$179.47) | [View plan](https://bit.ly/akkocloud) |
| London CN2 GIA annual special | 1 / 768 MB / 15 GB SSD | 300 Mbps | ¥449 per year | [View plan](https://bit.ly/akkocloud) |
| Frankfurt CN2 GIA | configured on the order page | not published | not published | [View plan](https://bit.ly/akkocloud) |
| London dedicated server | dual EPYC 7552 / 512 GB RAM / 10×1TB SSD | not published | ¥33,000 per month | [View plan](https://bit.ly/akkocloud) |

Three things in that table need a warning attached.

B1, B2 and C1 all carry 1 vCPU and 2 GB, yet they are priced at ¥110, ¥233 and ¥388.88. The compiled data doesn't record what separates them. On China-optimized hosts the usual discriminator is the included transfer allowance or a guaranteed-versus-shared port, so ask support for the monthly GB and port guarantee on each of the three before picking the cheapest.

Annual promotional variants in the same family have been listed at ¥449 to ¥699 per year, and the third-party writeups disagree about which configuration sits at which price. One assigns ¥699/year to a 1 GB / 20 GB configuration with 1,200 GB monthly transfer; the tracker assigns ¥449/year to the entry annual plan. Confirm the exact annual spec and renewal price on the live cart, because annual specials are where renewal jumps tend to hide.

The dedicated listing is a single configuration. Nothing in the public material describes a Hong Kong option, a DDoS-protection tier, or a refund window, so those are questions for sales rather than assumptions you can make from the page.

## What the route labels actually mean

China Telecom's CN2 GIA is the Global Internet Access product on its Next Carrier Network 2 backbone, announced as AS4809 with AS23764 handling the international leg. It is an SLA-backed internet access product, which is the distinction that matters: CN2 GT sits on the same backbone family without that service guarantee, and plain ChinaNet transit (AS4134, the "163" route) carries everyone else's traffic and behaves accordingly at 8pm.

China Mobile's international arm, CMI and its successor CMIN2, announce as AS58807. China Unicom contributes three paths you'll see in marketing copy: AS9929 is the premium one, AS4837 is the ordinary international route, and AS10099 covers its global arm. Count them and you get the seven direct routes that vendors like to list: 163, CN2, 4837, 10099, 9929, CMI and CMIN2.

Labels get mixed because the line is often a filter at checkout rather than a separate product family. The same chassis can be sold as "Enterprise CN2" with CN2 GIA plus CMIN2, "Mainland optimized VIP" with first-generation direct routes on all three carriers, and "International BGP" with no China optimization at all, at three different prices. When a page says "China optimized" and nothing else, it has told you nothing you can verify.

## Bandwidth sets the price, not core count

Look at what vendors bundle rather than what they clock. One Hong Kong and Seoul operator includes 10 Mbps of China-direct bandwidth on a Hong Kong CDIA plan and 30 Mbps on the Seoul equivalent, while its global BGP plan includes 100 Mbps in Hong Kong and 1 Gbps in Los Angeles. A Hong Kong host sells an E3-1230 v3 with 16 GB and a 100 Mbps global port at $199/month. A US provider's enterprise CN2 line starts at $98.10/month for an E3-1230 with 16 GB and a 30 Mbps unmetered port and climbs to $314.10/month for dual Gold 6133 with 64 GB.

AkkoCloud's own grid makes the same point inside one product family. KVM-CN2-U1 gives you 2 vCPU and 2 GB on a 30 Mbps unmetered port for ¥1,200/month. KVM-CN2-B1 gives you 1 vCPU and 2 GB on a metered 1 Gbps port for ¥110/month. One extra core costs roughly eleven times as much when the port is unmetered.

Do the arithmetic on an inclusive port before you compare quotes. A saturated 10 Mbps port moves about 3.2 TB in a month; 30 Mbps moves roughly 9.7 TB. If your monthly egress is 5 TB and the quote includes 10 Mbps, you are not buying a server, you are buying an upgrade conversation.

Metered plans invert the tradeoff. The 1 Gbps port on the San Jose metered tiers is a burst ceiling, not a promise, and the included transfer is what you'll hit first. One writeup of these plans describes the allowance as bidirectional, meaning uploads count against the same pool as downloads. Confirm the accounting direction before sizing anything.

## No ICP filing outside the mainland, but PIPL still applies

A server in Hong Kong, San Jose or London needs no ICP filing to serve a public website to mainland visitors. That part is accurate and it is why offshore hosting is popular. A server inside the mainland does need one: an ICP filing for a non-commercial site, or a commercial ICP licence if you sell goods or services, and Chinese ISPs are required to block an unlicensed site after a grace period. Organisations outside the mainland need a mainland entity (a WFOE, joint venture or representative office) to file at all, and a commercial licence requires a local company or a joint venture with foreign ownership under 50%. Apps have needed their own filing since September 2023, separately from any website filing.

None of that touches the data question. China's Personal Information Protection Law has been in force since November 2021 and Article 3 gives it extraterritorial reach over processing the personal data of people in China. Storing mainland users' data on an overseas server counts as an outbound transfer under Article 38, which requires a valid mechanism such as the Greater Bay Area Standard Contracts, plus separate consent under Article 39. Article 40 requires critical information infrastructure operators and high-volume handlers to keep personal data inside China. Hong Kong's PDPO applies on top of that to data held locally.

The practical consequence: a Hong Kong or London box solves the filing problem and creates a transfer problem. If your project stores names, phone numbers, ID numbers or payment details of mainland users, the server choice is the small part of the decision, and the answer may be a mainland deployment with the filing done properly. AkkoCloud's locations are all outside the mainland, so this applies to every plan in the table above. Get the compliance read from someone qualified; no host can supply it.

## How to verify a route before you pay

Ask for a test IP in the location you're buying and run MTR from your own network between 20:00 and 23:00 Beijing time, when the cross-border links are under peak load. A route that looks clean at 10am tells you nothing.

Read the AS path, not the label. A genuine CN2 GIA path shows AS4809 or AS23764 in the trace. China Mobile optimization shows AS58807. Unicom premium shows AS9929, and AS4837 is the ordinary route that gets relabeled as "direct" in a lot of copy. If the trace falls back to generic transit in either direction, the outbound and return paths may not match, so ask whether the optimization is bidirectional.

Third-party writeups of AkkoCloud's San Jose location list a test IP of 45.9.10.146 and a 1000 MB test file hosted on a San Jose subdomain of the provider's site. Confirm with support that both are current before you build a decision on them.

The reason to bother: a 2020 study published on the APNIC Blog found 79% of 400 inbound connections into China ran below 1 Mbps. Congestion at the border is the norm, not an edge case, and "China optimized" as a label is not evidence against it.

👉 [Open AkkoCloud's plan pages to check port and transfer figures](https://bit.ly/akkocloud)

## Who should not buy this

If your data has to stay in mainland China, no offshore host in this category works, including AkkoCloud. You need a mainland deployment plus the filing.

If your audience is global with a thin mainland slice, CN2 GIA is a premium you won't recover. Standard international BGP at a fraction of the price will serve the same users.

If you're running a brochure site or a personal project with a few hundred GB of monthly transfer, a dedicated server is the wrong shape entirely. The London dual EPYC box at ¥33,000/month exists for virtualization hosts, large databases and single-tenant isolation work. Spending that on a WordPress site buys nothing you can measure.

If you need a /24 of IPv4 for site clusters or multi-account operations, treat it as a separate purchase line. A Hong Kong provider prices the same E3-1230 v3 chassis at $199/month with one IP and $318/month with 253 usable IPv4 addresses. That premium has nothing to do with latency, and AkkoCloud's public listings don't show IP-block options, so ask directly.

Latency expectations deserve a reset too. A 15 ms figure to mainland China circulates in this market, but it comes from one vendor describing its own Hong Kong and Tokyo nodes. Neither San Jose nor London sits in that class; London especially is a long physical path from Shanghai, and it's the right choice for a European team needing clean China return routing, not for a Shanghai audience needing 20 ms.

## Competitor listings, for price context only

Prices below are what the pages showed when reviewed in October and November 2026. They change, and none of these figures should be read as a quote you'll get today.

| Provider | Location | Verified specification | Listed price | Network notes |
| --- | --- | --- | --- | --- |
| RAKsmart (Enterprise CN2) | not stated on the page | E3-1230 / 16 GB / 1 TB HDD / 30 Mbps unmetered | $98.10/mo (list $109) | CN2 GIA + CMIN2, test IP and MTR offered |
| RAKsmart (Enterprise CN2) | not stated on the page | dual Gold 6133 / 64 GB / 1 TB NVMe / 30 Mbps unmetered | $314.10/mo (list $349) | same |
| IMIDC | Hong Kong | E3-1230 v3 / 16 GB / 1 TB SATA / 100 Mbps global | $199/mo | CN2 GIA, native IP, no ICP filing |
| IMIDC | Hong Kong | same chassis + /24 (253 IPv4) | $318/mo | same |
| IMIDC | Hong Kong | dual Gold 6388 / 512 GB / 8×1 TB SSD + /24 | $899/mo | same |
| NCCK | Hong Kong, Seoul, Los Angeles | Xeon Gold 6138, IPMI on every box | no public price list | CDIA includes 10 Mbps (HK) or 30 Mbps (Seoul); LA global BGP includes 1 Gbps; 99.9% SLA with credits |
| Ucartz | Hong Kong | quoted per request | no public price list | 99.9% SLA; expert support billed at $8 per 15 minutes or $28 per hour |
| DMIT (third-party compilation) | LA, Tokyo, Hong Kong | LAX Premium from $29.90/mo with 3,000 GB on a 10 Gbps port | Tokyo $39.90, Hong Kong $79.90 | 99% SLA with tiered credits; 3-day / 30 GB refund window |

Read that table for one thing: $98 to $314 a month buys a 30 Mbps China-optimized dedicated box at one provider, $199 buys 100 Mbps global in Hong Kong at another, and the difference between those two numbers is bandwidth and route grade, not silicon.

## Picking a plan

Match the plan to the constraint that actually binds you.

**A site, API or bot serving mainland users, budget first:** the San Jose CN2 GIA entry plan at ¥50/month, moving to the 1 vCPU / 2 GB tier at ¥110/month once 512 MB stops being enough. Both are cloud instances on the same routing, which is the honest answer for most readers of this keyword.

**Media, downloads, or traffic you can't forecast:** the unmetered 30 Mbps tier at ¥1,200/month. It costs more than the metered 1 Gbps plans with similar cores, and that's the point: you're buying a guaranteed port instead of a burst ceiling and a transfer countdown.

**Your own kernel, IPMI, big disks, virtualization host:** the London dual EPYC 7552 with 512 GB RAM and 10×1TB SSD at ¥33,000/month. Ask what the port and transfer allowance are, because the public listing doesn't say.

**A European team that needs clean China return routing:** Frankfurt or London, configured on the order page. Prices aren't published for Frankfurt, so this one starts with a ticket.

Four things to confirm in writing before paying, whichever you choose: whether IPMI or KVM console access is included or an add-on, what DDoS protection is standard, what the refund window and its conditions are, and what the renewal price is after any promotional term. The public listings reviewed here don't state a refund policy, and that's exactly the kind of term you want in writing rather than inferred.

👉 [Start from AkkoCloud's plan list and confirm renewal pricing](https://bit.ly/akkocloud)
