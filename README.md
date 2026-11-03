# racknerd uptime: what the SLA fine print actually covers, what real-world monitoring shows, and how to pick a plan that stays online

RackNerd's real-world uptime is solid for a budget host. Independent monitoring puts its 30-day average around **99.993%** — roughly 30 seconds of downtime a month — and long-term users typically report between 99.9% and 99.99%. But there's a catch most reviews skip: the official SLA only covers network and power, and it does not promise anything about your individual VPS staying online. This article walks through what the SLA actually says, what independent monitoring has recorded, how to read RackNerd's status page without panicking, and which of the current plans makes sense for your setup.

> **Quick picks**
> Most people searching "racknerd uptime" are deciding whether a cheap annual VPS is safe to rely on. The short version: for blogs, dev environments, bots, VPN endpoints, and small sites, yes — the 1 GB annual special at **$21.99/year** is the most popular plan and renews at the same price for life. 👉 [See the 1 GB plan's current specs and price](https://my.racknerd.com/aff.php?aff=11397&pid=952)
> If downtime costs you money every minute it happens, RackNerd is the wrong tool — more on that below.

## What RackNerd's 99.999% uptime SLA actually covers

RackNerd's SLA promises 99.999% availability for two things: network transit and power, measured monthly. It does not guarantee that your individual virtual machine stays online. This is the single most misunderstood part of the "racknerd uptime" question, and it changes how you should interpret everything else.

The compensation terms are specific. If either network or power availability drops below 99.999% in a given month and your cumulative downtime exceeds one hour, you can request an account credit worth 2% of that service's monthly fee for each additional hour of downtime, capped at 50% of the monthly fee. Credits are calculated in one-hour increments and must be requested within 30 days. To put 99.999% in perspective: on a 30-day month, that allows about 26 seconds of unavailability.

Then there's the fine print that matters more than the headline number:

- **Hypervisor reboots don't count.** If the physical node hosting your VPS restarts and your VM goes down with it, that's not a SLA-eligible event. The SLA covers the network and power feeds, and RackNerd's own status page notes that 99% of incidents affect only a single hypervisor/node.
- **Scheduled and emergency maintenance is excluded**, with a monthly cap of 180 minutes, announced in advance on the status page.
- **The claim window is 30 days.** Miss it and the credit is gone.

So the honest framing is: RackNerd commits to keeping the lights on and the pipes connected at 99.999%, and your VM's actual availability depends on which physical node you happen to land on — something you don't get to choose at checkout.

## What RackNerd's real-world uptime looks like

Measured at the VPS level, real-world uptime lands between 99.9% and 99.99% for most long-term users, which is respectable for plans that start around $22 a year. The spread of available data is worth looking at, because the numbers vary by time window and measurement method.

One independent review site's monitoring recorded a 30-day average of **99.993%** — about 30 seconds of downtime per month, well past the 99.9% industry baseline (which works out to roughly 8.7 hours of downtime a year). For comparison, 99.99% equals about 52 minutes of downtime a year.

Longer windows tell a more honest story. One reviewer ran a Black Friday promotional VPS continuously for 14 months and measured 99.93% — about 6.1 hours of total downtime across three incidents: two short network blips under 30 minutes, and one datacenter-level outage of roughly five hours in August 2025. Another long-term test on a 2 GB KVM VPS in the Los Angeles DC-02 facility, probed every minute with UptimeRobot for about 14 months, came in at **99.97%**, or around 2.5 hours of cumulative downtime a year. Community monitoring data generally clusters in the same 99.9%–99.99% band, with a few users in quieter locations reporting a full year at 100%.

Two patterns show up consistently in that data. Small annual plans (1–4 GB RAM) tend to be the most stable, while 8 GB+ plans sit on busier host nodes and wobble slightly more. And most failures are short — a few minutes of node-level unavailability — rather than hours-long outages.

## How to read the status page (and why aggregate numbers can mislead)

RackNerd runs a public status page at status.racknerd.com, and reading it correctly will save you a lot of unnecessary worry. The page tracks each datacenter separately, and a "Partial Outage" label usually means one physical host machine is having a bad day — not that the whole facility is down. The company's own guidance on the page says most incidents stay isolated to specific nodes without impacting the entire location. There's also an official YouTube tutorial for finding which node your VPS is on, so you can check whether a reported issue actually affects you.

Third-party aggregators paint a noisier picture, and it helps to understand why. One monitoring service that tracks RackNerd's status page feed recorded 336 incidents over the past 90 days and computed a "95.55% uptime" figure. That number counts every node-level blip across dozens of datacenter components — including events that never touched your VPS — so it dramatically understates what a single customer experiences. The same feed shows a typical incident lasts about 5 minutes.

That said, the incident log isn't all noise. Recent entries include a Chicago datacenter degradation on October 28 that ran 33 hours (the longest in the past year), shorter 13–20 minute degradations in Chicago and New York on October 31, and an ongoing Los Angeles degradation as of November 1. Over the trailing twelve months, New York recorded the most incidents (18), followed by San Jose (11), Chicago (10), and Los Angeles (9). Location genuinely matters: Chicago has had a cluster of node-level trouble recently, while Seattle and Dallas have been quieter.

One practical gap: RackNerd has no built-in uptime monitoring, so you'll need your own. Uptime Kuma or a similar free monitor pointed at your VPS takes ten minutes to set up and gives you data you can actually act on.

## RackNerd plans and pricing

The current VPS Specials lineup is annual-billing KVM VPS, all with full root access, a 1Gbps port, one dedicated IPv4, RAID-10 SSD storage, instant provisioning, and RackNerd's ctrl control panel (reboots, reinstalls, HTML5 VNC console, one-click apps, firewall rules). Every special is "lifetime recurring" — RackNerd's own FAQ states you can renew at the same rate for as long as you keep the service, so the price below is the price you'll keep paying.

| Plan | CPU / RAM | Storage | Monthly traffic | Price | Order |
| --- | --- | --- | --- | --- | --- |
| 1 GB (most popular) | 1 vCPU / 1 GB | 20 GB SSD | 3 TB | **$21.99/yr** | [Order the 1 GB plan](https://my.racknerd.com/aff.php?aff=11397&pid=952) |
| 2 GB | 2 vCPU / 2 GB | 35 GB SSD | 5 TB | **$35.99/yr** | [Order the 2 GB plan](https://my.racknerd.com/aff.php?aff=11397&pid=953) |
| 4 GB | 3 vCPU / 4 GB | 60 GB SSD | 7 TB | **$59.99/yr** | [Order the 4 GB plan](https://my.racknerd.com/aff.php?aff=11397&pid=954) |
| 6 GB | 6 vCPU / 6 GB | 100 GB SSD | 12 TB | **$89.99/yr** | [Order the 6 GB plan](https://my.racknerd.com/aff.php?aff=11397&pid=955) |
| 8 GB | 7 vCPU / 8 GB | 150 GB SSD | 20 TB | **$119.99/yr** | [Order the 8 GB plan](https://my.racknerd.com/aff.php?aff=11397&pid=956) |

All plans can be deployed in roughly 20 locations: Los Angeles, San Jose, Seattle, Utah, Chicago, Dallas, New York, New Jersey, Atlanta, Tampa, Miami, Ashburn, Montreal, Toronto, London, Amsterdam, Strasbourg, Frankfurt, Dublin, and Singapore. Los Angeles and the French locations can be requested with up to 100 free IPv6 addresses via a support ticket after ordering.

Beyond the specials, there's a standard KVM VPS line with monthly billing: 512 MB (30 GB SSD, 500 GB traffic) at $26.99/year, 1 GB (50 GB, 1 TB) at $17.99/month, 2 GB (75 GB, 2 TB) at $20.59/month, 4 GB (130 GB, 3 TB) at $24.59/month, 6 GB (170 GB, 4 TB) at $27.59/month, 8 GB (220 GB, 5 TB) at $36.59/month, and 12 GB (300 GB, 6 TB) at $55.99/month. 👉 [Check the full plan list and current prices](https://bit.ly/RacKnerd) — monthly billing is also the safer way to test the service, since VPS purchases are generally non-refundable (refunds are handled case by case, and there's no standard money-back guarantee to lean on).

One more thing the pricing doesn't tell you: the ctrl panel includes one-click apps, and their memory requirements are the real plan-selector for AI workloads. n8n and Coolify run fine from 2 GB; Ollama, AnythingLLM, LibreChat, and Hermes Agent want at least 4 GB; OpenClaw needs 8 GB.

## Which plan stays online for your use case

Pick by workload and location, and the uptime question mostly takes care of itself. The monitoring data gives a few usable rules:

- **Blog, portfolio, or small personal site:** the 1 GB plan at $21.99/year is enough. Don't pay for more RAM you won't use.
- **Dev/test environments and Discord bots:** also 1 GB. These workloads shrug off a five-minute blip, which is what most incidents amount to.
- **Small production site or WordPress with real traffic:** 2 GB or 4 GB. The 4 GB tier also unlocks the one-click AI apps.
- **Self-hosting AI tools (Ollama, AnythingLLM, LibreChat):** 4 GB minimum, and 8 GB if you want OpenClaw.
- **Running two things that must not go down together:** open a small second VPS in a different datacenter instead of buying one bigger box. Since you can't pick your physical node at checkout, splitting across two locations is the only real hedge against node-level failures.

Location matters as much as plan size. Los Angeles has the best latency for Asian traffic (CN2 routing is available there) but is also the busiest and most node-volatile location — the current degraded event is there. Seattle and San Jose often deliver nearly the same latency from the US West with less crowding. For European audiences, Amsterdam, London, and the French and Irish locations are stable, though stock comes and goes.

## Who should skip RackNerd

If your service loses money every minute it's offline — payment processing, a storefront doing real revenue, anything with a contractual availability requirement — a budget unmanaged VPS without a per-machine SLA is the wrong foundation. The measured 99.9%–99.99% range means accepting somewhere between 52 minutes and 8.7 hours of annual downtime, and the SLA won't pay you back for most of it, since node reboots and maintenance don't qualify. That's a structural limit of cheap KVM hosting generally, and RackNerd is upfront about being unmanaged; for production-critical work, you want a provider offering a contractual per-instance SLA, or a multi-node setup with health checks and failover.

Also worth knowing before ordering: support is ticket-only with a claimed average first response under 10 minutes (one long-term reviewer confirms first responses arrive roughly that fast, though actual fixes can take longer as tickets escalate), OS updates and security patches are entirely your job, and migrating between datacenters later requires a support ticket and some downtime — so choose the location carefully the first time.

## FAQ

**Does RackNerd compensate for downtime?**
Only for network or power outages beyond the 99.999% monthly commitment, and only if cumulative downtime that month exceeds one hour. Compensation is 2% of the monthly fee per additional hour, capped at 50%, and must be requested within 30 days. A single VPS going down because its host node rebooted doesn't qualify.

**What does 99.9% uptime mean in actual minutes?**
99.9% allows about 8.7 hours of downtime per year, 99.99% about 52 minutes, and 99.993% roughly 30 seconds a month. Independent monitoring puts RackNerd's recent 30-day average at the last of those three.

**Can I check if my VPS is affected by an incident?**
Yes. RackNerd's status page lists issues per datacenter and per node, and there's an official video tutorial for finding your VPS's node name so you can compare it against reported incidents.

**Does the cheap annual price go up at renewal?**
No. The VPS specials are lifetime recurring — you renew at the same rate for as long as you keep the service, which is why the first-year price and the renewal price are the same number in the table above.

## Before you order

Two things decide whether racknerd uptime will be a non-issue for you: where you deploy and what you deploy. Pick a datacenter close to your users that isn't the most crowded option (Seattle or San Jose instead of LA if latency is similar for you), set up your own uptime monitor, and match the plan to your actual memory needs rather than to the biggest discount. If your workload fits — blogs, bots, dev boxes, VPN endpoints, self-hosted tools — the 1 GB annual special remains the entry point most people should start with. 👉 [Order the 1 GB annual special and pick your datacenter at checkout](https://my.racknerd.com/aff.php?aff=11397&pid=952)
