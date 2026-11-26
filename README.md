# AMD EPYC VPS: Why Entry Plans Cost $3.89 to $18 a Month, What Backups and Windows Licences Add, and How to Pick Between Milan and Genoa

Entry-level AMD EPYC VPS plans currently run from **$3.89 to $18 a month**, a spread of more than four times for machines that all advertise EPYC cores and NVMe storage. Three items on the spec sheet explain most of that gap: the EPYC generation behind the vCPU, the RAM you get per core, and how much transfer and backup service ships with the plan.

What follows is the verified price band across five providers, the charges that only show up after checkout, and a rule for matching a tier to a workload. SixtyNet's own plan list could not be verified for this article, so nothing below is presented as a SixtyNet quote; the table section explains how to use the market figures against whatever quote you receive.

> **Quick pick:** a website, a mail server or a handful of containers fits in 1 core and 2 GB of RAM, and 2 GB machines start at **€3.99 a month**. Take the smallest tier that covers your transfer, then put the difference into backups or a second node. 👉 [Check SixtyNet's current EPYC VPS plans and pricing](https://sixtynet.net/aff.php?aff=39)

## The plan table, and what could not be verified

SixtyNet's public plan data did not come back in a checkable form when this article was prepared on 15 November 2026. Plan names, prices, locations and backup terms for that provider are therefore absent, and no figure here should be read as its报价. The table below covers the verified market in the same band, which is the reference you need for judging any EPYC quote.

| Provider | Plan | vCPU | RAM | NVMe | Price |
| --- | --- | --- | --- | --- | --- |
| Arct Cloud | cvm.pico | 1 | 1 GB | 15 GB | $3.89/mo |
| Evolushost | Nano | 1 | 2 GB | 32 GB | €3.99/mo |
| LightNode | Start | 1 | 2 GB | 50 GB | $7.71/mo |
| Evolushost | Micro | 2 | 4 GB | 64 GB | €7.99/mo |
| VPSGator | AM1 | 1 | 3 GB | 40 GB | €13.95/mo |
| LightNode | Agency | 2 | 4 GB | 50 GB | $14.70/mo |
| Catalyst Host | Starter | 4 | 8 GB | 60 GB | $18/mo |
| Evolushost | Core | 8 | 16 GB | 256 GB | €31.99/mo |
| Catalyst Host | Ultimate | 8 | 48 GB | 400 GB | $115/mo |
| Evolushost | Tera | 32 | 96 GB | 1,536 GB | €127.99/mo |

This is a selection, not a full catalogue. Evolushost lists nine plans from €3.99 to €127.99, Catalyst Host six from $18 to $115, LightNode four from $7.71 to $52.70, VPSGator six from €13.95 to €120. Euros and dollars are not converted here, so compare within a currency or do the conversion yourself on the day you buy.

Transfer allowances vary more than the prices do: 1 TB of outbound traffic on the Arct entry plan, 3 TB on Evolushost's cheapest, up to 100 TB on its 32-core plan. VPSGator prints "∞" in its bandwidth column with no fair-use details on the page, which is not a number you can plan capacity against.

## Why one AMD EPYC VPS costs four times another

Generation first. Arct Cloud publishes which EPYC family sits behind each tier: Cost Optimized and General Purpose run **EPYC Milan 7003 at up to 3.7 GHz**, while High Performance moves to **EPYC Genoa 9004 with DDR5 memory**, starting at $11.99/mo. Evolushost names the host CPU outright: **EPYC 9654, 96 cores and 192 threads, 384 MB L3**, DDR5 ECC, Samsung PM9A3 PCIe 4.0 enterprise NVMe, Mellanox cards carrying a 40 Gbit uplink on every plan. Catalyst Host advertises a 4.0 GHz boost clock but does not name the EPYC model or generation anywhere on its plan page, so you cannot tell from the page which generation you are buying.

Second, memory per core. The headline prices mislead if you read them as "the same thing, cheaper":

- Arct's $3.89 buys 1 GB, so about **$3.89 per GB of RAM**
- Evolushost's €3.99 buys 2 GB, about **€2.00 per GB**
- LightNode's $7.71 buys 2 GB, about **$3.86 per GB**
- Catalyst's $18 buys 8 GB, about **$2.25 per GB**

The cheapest sticker in the group carries the highest memory cost per GB. A 1 GB box is fine for a static site, a WireGuard endpoint or a monitoring agent; it struggles the moment you add a database and a queue worker on the same machine. If your workload needs 4 GB, the "$3.89 provider" costs you $15.56 for the same memory that Evolushost sells for €7.99 with twice the cores.

Third, shape. Catalyst's $18 plan hands you 4 vCPU and 8 GB, four times the core count of the entry tiers, plus 20 Gbps of network and a 99.9% SLA. Different product for a different buyer.

One caveat on all of these vCPU counts: they are shared slices of a host, not dedicated cores. Arct states plainly that its plans are shared, so a noisy neighbour running a sustained compile affects you at the edges. If you need guaranteed cores, you are shopping for bare metal, not a VPS.

## The charges that appear after checkout

This is where the four-fold price gap stops mattering and the real monthly number takes over.

**Backups.** Arct charges **20% of the server's monthly price** for automatic daily backups, which turns a $3.89 plan into $4.67 and a $52.70 plan into $63.24. Manual snapshots cost **$0.04 per GB per month**, are available for Linux images only, and only in certain locations. Evolushost includes no customer backups at all: its daily backups exist to restore its own infrastructure, and the FAQ tells you to run your own, for example to a storage box. A provider that bundles free daily backups is the exception, not the rule, and the ones that do tend to be smaller operations running their own racks.

**Windows.** Arct requires 2 or more vCPU for a Windows Server image and includes administrator RDP. Evolushost offers Windows Server 2019, 2022 and 2025 on every plan except the Nano, but as an **evaluation edition good for 180 days**, activated with your own licence, extendable a few times with the rearm command. A Windows VPS without a licence is a 180-day trial, and the licence can cost more per year than the server.

**Overage.** Evolushost slows the port when you pass the included traffic and expects you to buy an upgrade. Arct counts only outbound transfer; inbound is free and does not touch the allowance. If you run backups, mirrors or media pulls, inbound-free is worth more than a bigger headline quota.

**Billing cycle.** Catalyst's annual prices are exactly ten times the monthly rate ($180 for the $18 plan, $1,150 for the $115 plan), so prepaying a year buys two months. That is a real discount if you intend to stay, and a $180 commitment if you do not.

👉 [Open SixtyNet's EPYC VPS range to compare its backup and Windows terms](https://sixtynet.net/aff.php?aff=39)

## AMD EPYC VPS or Ryzen 9 VPS?

Same vendor, different core. Arct runs a Ryzen 9 line at **up to 5.7 GHz from $11.99/mo**, and Evolushost's Ryzen 9 9950X carries the higher clock per core. Evolushost's own guidance is that the Ryzen box suits game servers, websites and anything that runs on few threads, while the EPYC plans give more cores and RAM for the money plus a 40 Gbit uplink.

Practical version: a Minecraft server, a single busy WordPress site or a latency-sensitive API answers faster on a high-clock Ryzen core. A CI runner, a Docker host with eight containers, a database with a large buffer pool or a VPN concentrator with many sessions wants cores and RAM, and EPYC delivers more of both per euro.

## Match the tier to the workload

**Small sites, mail, Docker hosts, CI runners, VPN gateways.** Evolushost's own list names these as the fit for its EPYC line, and its Nano to Mini range (€3.99 to €15.99, 2 to 8 GB RAM, 3 to 7 TB traffic) covers them. A €7.99 Micro with 2 cores, 4 GB and 5 TB handles a mail server plus a couple of containers without breathing hard.

**CPU-heavy builds, batch jobs, data processing.** Arct's High Performance tier exists for this: Genoa 9004 with DDR5 from $11.99/mo. The generation matters more than the core count here, since DDR5 memory bandwidth and newer cores move real workloads faster than two extra Milan vCPUs.

**Many applications, larger databases, heavier traffic.** The 16 to 96 GB range. Evolushost's Core at €31.99 gives 8 cores, 16 GB and 15 TB; its Tera at €127.99 gives 32 cores and 96 GB. Catalyst's Business and Enterprise tiers ($58 and $85) sit in the same territory with 24 and 32 GB.

**Somewhere in between.** LightNode's four plans are the simplest ladder: $7.71, $14.70, $27.70, $52.70 for 2, 4, 8 and 16 GB, with storage fixed at 50 GB NVMe across all four. Convenient if you want to resize without re-planning storage; limiting if you need 200 GB of disk on a small box.

## Questions that decide the purchase

### Is there a minimum contract?

Evolushost states one month, prepaid, and cancellation means not paying the next invoice or cancelling in the client area. Nothing is owed beyond the period already paid. The other providers examined here do not publish a minimum term on their plan pages.

### Can I upgrade later?

Evolushost says you can move to a larger or smaller plan at any time, and will build a custom configuration if none fits. Arct resizes without changing the IP address or losing data. Both are worth confirming in writing before you migrate a production site.

### Are backups included?

No at Evolushost, by explicit policy. 20% of the monthly price at Arct, plus $0.04/GB/month for manual snapshots. Budget for it; an unrestored backup after a bad deploy costs more than the surcharge.

### Can I install Windows?

Yes on most plans, but check both the vCPU minimum and the licence. Arct wants 2+ vCPU; Evolushost excludes only the Nano and ships an evaluation edition.

### Do I need to pass KYC, and can I pay with crypto?

Evolushost states no mandatory KYC and accepts Bitcoin, Ethereum, Monero, Litecoin, Dash and USDT alongside cards, PayPal and bank transfer. It also provisions in about 15 minutes after payment and will mount a custom ISO if you open a ticket.

### What happens if I exceed the transfer allowance?

Evolushost slows the port and sells additional traffic. Arct counts egress only, so inbound-heavy workloads have more headroom than the quota suggests.

### Is there a refund or a free trial?

None of the five providers examined here published a refund window or a trial on the pages checked. Assume the first invoice is not coming back and start with a monthly term.

## The buying rule

Sort yourself into one line and the choice gets short:

- **1 site, a few containers, under 3 TB of traffic:** the €3.99 to $7.71 band. Paying $18 for 8 GB you will not fill is the most common mistake in this market.
- **Build jobs, CI, anything CPU-bound:** a Genoa/DDR5 tier, from $11.99 at Arct, or 4 vCPU and 8 GB at $18 with Catalyst if you want cores over generation.
- **More than 32 GB of RAM:** Evolushost's 96 GB plan at €127.99 or Catalyst's 48 GB at $115.
- **Game server or a single-threaded app:** Ryzen 9, from $11.99, up to 5.7 GHz.

Before paying, confirm two things in writing: whether backups cost extra and how much, and whether a Windows licence is included or assumed. Those two line items decide whether a cheap plan stays cheap in month three.

👉 [Compare SixtyNet's EPYC VPS plans against these figures before you order](https://sixtynet.net/aff.php?aff=39)
