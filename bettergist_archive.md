I run the Bettergist Collector, which archives every single PHP packagist project, 
since April 2019, now on a bi-weekly basis.

Internally, I now have 400,000+ PHP packages' git repos, substantially more than 
the currently-alive PHP project count of 365,000+ (because I've been running the 
archive since 2019).

## The Internal Setup

The way I've been handling this for large institutional clients is:

1. I use [Gitea](https://about.gitea.com/) to host them all for free, on-premise, 
using a custom Gitea API app I made for the process.
2. Bettergist since Jan 2022 stores everything as a shallow-cloned git repo, which 
(using complex commands) my script converts into full-remote repos which are 
imported to gitea via #1.
3. For dead projects archived prior, a simple script creates a git repo and 
imports via #1.
4. The gitea is hosted on dedicated servers, containing access to bi-weekly 
updated clones of the entire PHP Packagist system, including dead packages.
5. The companies use [a custom packagist URL config](https://packagist.com/docs/setup) 
to pull in that private Bettergist Archive instead of traditional packagist.
6. Once a quarter, the entire PHP packagist archive is compressed and stored both 
on-site, AWS S3, Mega.nz, and on USB drives dispersed on three continents 
(Texas, Colombia, and the UAE).
7. A custom Composer plugin package can be installed on their repos that reports
to the Bettergist Collector which composer packages are currently being actively
used by clients (installs within the last year). It then include each archived
version of those active packages in the active git repo.

## Reasons companies pay for the access:

1. All of their PHP dependencies are guaranteed to be present now and in the future,
irrespective of the wishes of the authors (pursuant to the rights of the open source
license).
2. It is much more immune to supply-side attacks: Because of the bi-weekly archival
schedule, usually supply-side attacks are discovered and remedied before the archive
has taken place.
3. It is much, much, much faster in various countries. For instance, there is an
Alibaba Cloud instance that is over 500% faster when accessed from that instance,
because it is inside of China's Great Firewall.
4. It is largely immune to any particular country's IP irregularities, being hosted
in Colombia, Germany, China, and Singapore.

## Access to the Bettergist packagist repo:

This service is currently only offered to publicly-traded corporations with market caps
of at least $1 Billion dollars. This is to ensure a limited number of clients and the 
highest tier of service.

Access costs **$5/developer/month**, paid per year, with a 30 day trial period and 
a 60 day money-back guarantee for any reason.

The goals of this project are primarily not for-profit but for the secure archiving of
every open source PHP project published via Packagist.org, for the greater posterity
of human civilization, particularly in an edge-case such as the shutdown of GitHub, or
even a grid-down event.

## Purchasing The USB

You can submit a request to purchase a USB drive of every reachable project + dead 
projects in PHP's Packagist database by [messaging me](https://twitter.com/hopeseekr) 
on Twitter / X.

* **Archive Size:** 112.1 GB compressed / 471.5 GB uncompressed
* **Saved Dead Packages:** 18,995 (82,805 github stars, 30,622,705 installs)

The USB contains every PHP Packagist package downloadable since January 2022,
and 98%+ available since April 2019, updated once per quarter.

It also contains the latest PHP source code for PHP v5.6 through 8.4, along with a compressed
docker image of Ubuntu 22.04 with complete devtools installed, permitting you to compile PHP from 
scratch in the event of a full-on collapse, or recovery of the USB drive thousands of years into
the far future.

The current price is $4,715.00 USD, payable via bank wire, Zelle, Bitcoin, Ethereum, $USDT, etc.

An archive of the Top 1 Million most-installed NPM packages is also available.

## Use Cases for The USB

### Extinction Level Event Protection

You can have a relatively uptodate archive of the a huge percent of the PHP Open Source ecosystem
self-hosted on your own USB stick (if 512 GB or higher) or your hard drive.

This means you can code PHP completely off-grid, off-network, and in a verifiable clean-room
environment, suitable for Dark Labs, Beyond Top Secret blackops dev sites, any of the offworld
bases and outposts, and even the interstellar spacecraft that we don't officially have; all without
risk of detection of that deep space signal that couldn't possibly exist.

In the event of a grid-down [**fire sale event**](https://diehard.fandom.com/wiki/Fire_Sale) where
the Internet is offline or destroyed (EMP attack, supervolcano erruption, astroid impact, alien
invasion, etc.), you can help rebuild society by preserving your own copy of the PHP open source
ecosystem.

The USB drive contains everything you need to get a modern PHP stack both compiled and running on
the latest Ubuntu LTS, along with instructions.

So if you are an archivist at heart, consider buying one and burying it underground or something.
Photographic proof of it being secured underground in suitable fireproof, waterproof, EMP-resistant
packaging will result in you being refunded all but the first $250 (manufacturing, shipping, and USB cost).

### Snapshot Over Time (Collectible)

By regularly purchasing the USB drives, you can grab a snapshot of the PHP ecosystem over time.
This will become increasingly valuable as a collectible, per historic norms, for the same reason
that 40 year-old McDonald plastic straws are currently being sold for thousands of dollars.
![McD's straw for $2,620 on 2024-08-23](https://github.com/user-attachments/assets/e8eedaa6-be83-48d1-8385-6d498f2961df)

But this is even more valuable. You can, for instance, compare the coding practices of 2019 to 2025.

### AI Training / LLM Model Generation

Beyond the obvious of being able to instantly train an LLM Foundation Model against all of the 
open source PHP source instantly, you can pair it with exclusive access to the Bettergist API
for targetted training of already pre-ranked data.

The Bettergist Collector project also contains the Bettergist Analyzer.

This CLI analyzes every single PHP package once per quarter:
 - disk space
 - PHP stats (lines of code, number of classes, methods, lines per class, lines per method, etc.)
 - PHPStan best error level with no errors / warnings.
 - Has PHPUnit tests?
 - Do the PHPUnit tests pass?
 - PHP Mess Detector results (clean code?)
 - GitHub Stars
 - Composer installs
 - and much  more.

With all of this readily-available data via the Bettergist REST API, you, too, can quickly
and efficiently build an LLM Foundation Model off of existing open source engines that will
be able to code in PHP with much more fidelity and expertise than even GitHub CoPilot (*), 
at least subjectively, from our own clients' testimonies.
