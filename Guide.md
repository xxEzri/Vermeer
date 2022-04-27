# Table of Contents
1. [Introduction and Hardware Configuration](#introduction-and-hardware-configuration)
	1. [CPU cooler](#cpu-cooler)
	2. [Motherboard](#motherboard)
	3. [RAM](#ram)
	4. [Graphics card](#graphics-card)
	5. [Some testing methodology](#methodology)
3. [Overall performance](#overall-performance)
	1. [Overall performance at specification](#overall-performance-at-specification)
	2. [Overall performance with RAM overclocking](#overall-performance-with-ram-overclocking)
	3. [Performance gains from RAM overclocking](#performance-gains-from-ram-overclocking)
	4. [Overall 3.4ghz IPC comparison](#overall-3.4ghz-ipc-comparison)
	5. [6core vs 8core CCD scaling](#core-scaling)
4. [Individual game benchmarks](#individual-game-benchmarks)
	1. [Ashes of the Singularity](#ashes-of-the-singularity)
	2. [Civilization VI](#civilization-vi)
	3. [Cyberpunk 2077](#cyberpunk-2077)
	4. [Factorio](#factorio)
	5. [Final Fantasy XIV Endwalker](#final-fantasy-xiv-endwalker)
	6. [Forza Horizon 5](#forza-horizon-5)
	7. [Gemcraft: Frostborn Wrath](#gemcraft-frostborn-wrath)
	8. [Horizon Zero Dawn](#horizon-zero-dawn)
	9. [Kerbal Space Program](#kerbal-space-program)
	10. [OSRS Runelite 117HD](#osrs-runelite-117hd)
	11. [Rainbow 6: Siege](#rainbow-6-siege)
	12. [Shadow of the Tomb Raider](#shadow-of-the-tomb-raider)
	13. [Starcraft 2](#starcraft-2)
	14. [Stellaris](#stellaris)
	15. [The Riftbreaker](#the-riftbreaker)
	16. [Tiny Tina's Wonderlands](#tiny-tinas-wonderlands)
	17. [Total War: Warhammer II](#total-war-warhammer-ii)
	18. [World of Warcraft](#world-of-warcraft)

# Introduction and Hardware Configuration
Guide v1.01.

o/ Aeryn here!

This is my first attempt at a more formal guide (covering the performance of the 5800x3d, 5900x, memory scaling for both and 6c vs 8c CCD scaling). It's been a surprising amount of work and so i'm releasing as-is and will continue to polish and add information over time.

## CPU cooler

I used an Arctic Liquid Freezer II 420 with the offset mounting position and a controlled ambient temperature of around 23c for the Precision Boost tests.

## Motherboard

The motherboard is an x570 Aorus Master with the bios F34 (AGESA 1203B) for the 5900x / F36c (AGESA 1206B) for the 5800x3d. This second AGESA has a couple of problems including a 1900fclk hole, but is required for the x3d to work properly.

## RAM

The RAM is a pair of dual-rank sticks, also known as 2x2R which is top tier for overclocking performance, best all-around and also the best performing option within stock specifications. It is G.Skill Samsung 8gbit B-die - F4-3200C14-16GTZN.

There are two profiles used:

A: JEDEC-3200 2x2R, the best memory performance supported within the CPU specification with as much polish as allowed to give it the best possible shot. Also somewhat comparable to a bad XMP/DOCP - it may have worse primaries, but the dual-rank-per-channel configuration and a few tweaked options under the hood give it an edge.

**When this profile is used on the charts below, it will be called " - JEDEC".**

![enter image description here](https://i.imgur.com/HNcx5om.png)
-----------

B: My daily overclock which has every accessible timing and several other parameters tweaked for optimal performance while retaining rock solid stability and reliability. It is capable of passing tests such as TM5 w/ Anta777's Extreme1 profile for 12+ hours and shows pretty much the best safe and reliable performance which is available from the DRAM.

This configuration was proven stable at 3800 and then stepped down to 3733 without changes.

**When this profile is used on the charts below, it will be called " - RAM" or specifically mention the overclock in order to indicate that overclocked RAM is used.**

![enter image description here](https://i.imgur.com/j3OEKLo.png)
---

## Graphics Card
The graphics card is an RTX 3080 with some tuning and the driver version 511.65.

## Methodology

I almost entirely avoided GPU bottlenecking by focusing on settings which were very easy for the graphics card to run. This generally means flat low settings, but some settings such as crowd density in Cyberpunk 2077 are turned up as these impact the CPU much more than other parts of the system. When these settings are used, they are explicitly mentioned. Avoiding bottlenecks elsewhere gives a better picture of what the CPU is truly capable of in order to better understand the microarchitecture and scaling both now and in the future. I also plan to gather data on higher settings which can have more CPU demand, but require careful monitoring and planning for correct measurement.

Turning up other settings may only hurt performance so you can consider the raw performance values in the game charts to be a ceiling for achievable performance when the mentioned settings are enabled. Which settings hurt CPU performance and by how much varies a lot game-to-game but is tuneable by the user.

I took measurements both at stock specifications and with a RAM overclock seperately. All gaming CPU's benefit massively from RAM overclocking at the moment, but some benefit many times more greatly than others. The 5800x3d stands out of the pack as a CPU which excels even with bad memory; the rest of the Vermeer lineup is much more reliant on a custom memory overclock and Cezanne or Alderlake are even more so still. Using different memory configurations shifts the absolute and relative performance of these CPU's quite massively! You can see below how the relative performance of even the 5800x3d and 5900x changes when this memory overclock is applied.

I focused on testing games which may respond to CPU/cache/mem performance and didn't bother testing some games which are known not to do so; this is not meant to be a perfect reflection of what the 5800x3d or 5900x does on *every* game; it's moreso designed to figure out where and what the scaling is with a limited amount of benchmark runs available. Several of these titles had never been tested with an x3d before i ran them, so nobody knew how they would behave. To interpret the data most accurately it should be treated as a subset of CPU/cache/mem sensitive games or looked at on a game-by-game basis to examine performance for that particular game.

# Overall Performance
## Overall Performance at Specification
![enter image description here](https://i.imgur.com/VJ08fzr.png)
There are some great gains here, but high variability in responsiveness. Some games are able to achieve much better L3 cache hit rates and run away with performance. Others already had good hit rates, have data access patterns which aren't effectively cachable either way or are severely bound elsewhere in the core.

As you can see later, more than a few also prefer an 8-core CCD to a 6-core one. This doesn't just create leads in a 6c12t vs 8c16t scenario (which is indicative of general core scaling), but it also frequently shows up in 8t16t vs 6c12t + 6c12t with the dual-CCD models.

There are regressions in clock speed which affect the cores (including their L1+L2 caches) and the L3 cache as well as an additional L3 latency penalty of around +9% when measured by clock cycles. These undoubtedly hurt everything on the list but at the same time, pretty much everything on there is finding at least a fringe benefit from the tripled L3 cache capacity which offsets this and claws performance back.



## Overall Performance with RAM overclocking
![enter image description here](https://i.imgur.com/1g8X2Rk.png)
## Performance gains from RAM overclocking

![enter image description here](https://i.imgur.com/yqixrHs.png)
Here you can see those massive RAM scaling differences that i was talking about. I think that it's well worth using good memory on either CPU - or their competitors - but if you don't know or care about which secondary timing does what on your RAM then getting the CPU that does the best without tuning all of that is certainly a good play.

## Overall 3.4ghz IPC comparison
![enter image description here](https://i.imgur.com/7xgdBRt.png)
The only option for a clock-for-clock comparison with the 5800x3d was to disable Precision Boost - this locks that CPU at 3.4ghz, a value which is matchable with the 5900x. It's a very low clock however compared to the regular game clocks of mid 4ghz and this distorts the picture somewhat.

This clock speed reduction seems to favor the 5900x a bit over the 5800x3d. I think that the reasons for that are twofold:

1: The 5900x is more memory limited, but by slowing the core while leaving the RAM performance intact we reduce that bottleneck.

2: The 5800x3d is getting higher L3 cache hitrates, but the L3 cache runs on the core clock. By slowing the core clock we're also slowing its huge pool of L3 cache and hurting latency/bandwidth there.

This is evident in the way that the x3d loses to the 5900x in Civ 6 at a static 3.4ghz, but it manages a narrow win at stock clocks even though the 5900x is gaining more clockspeed than the x3d is.

# Core Scaling
![enter image description here](https://i.imgur.com/XGQ716F.png)
Generally there are sizeable gains when going from 6c12t to 8c16t on the x3d. A few losses at the bottom, but they're on the games with very low thread counts and high variability - error margins can explain most of it. Boost clocks also seemed slightly higher with core #7 and #8 turned off in the BIOS.
# Individual Game Benchmarks
## Ashes of the Singularity
### Performance
![enter image description here](https://i.imgur.com/j3dSGmX.png)
I used the GPU benchmark as it loads the CPU in a way which is more reflective of actual gameplay.

The 5800x3d is ahead by 37% here with stock RAM or by 20% with overclocked RAM.

### 3.4ghz IPC
![enter image description here](https://i.imgur.com/Gm1XxUq.png)
## Civilization VI
### Performance
![enter image description here](https://i.imgur.com/Sett0Ps.png)
Standard turn time benchmark - vry flat performance.

### 3.4ghz IPC
![enter image description here](https://i.imgur.com/R9GG9vk.png)
Some hints of responsiveness to L3 cache latency here, but given the lack of overall response to increased cache capacity or to memory overclocking i guess that the L3 hit rate on the 5900x is already excellent.

## Cyberpunk 2077
### Performance
![enter image description here](https://i.imgur.com/qawuSE7.png)
I used the menu benchmark here with minimal settings but maxed crowd density to get a picture of the limits of each CPU. Some settings (especially RT) hurt CPU performance and will lower framerates further.

There's a 32% performance lead here for the 5800x3d with stock memory, down to +16% with overclocked.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/6XrwLV7.png)
## Factorio
### Performance
![enter image description here](https://i.imgur.com/StrBlKg.png)
Some of the strongest scaling on show here. The relative performance and scaling characteristics are sensitive to the size of the map and the type of buildings on it though - the x3d's lead narrows even as this very same map is scaled up and it starts to respond more to RAM overclocking again, as much as +19% before slowing to the 60UPS realtime limit.

### 3.4ghz IPC
![enter image description here](https://i.imgur.com/aOoUkdr.png)
## Final Fantasy XIV Endwalker
### Performance
![enter image description here](https://i.imgur.com/Jcpaf1x.png)
A 24% lead with stock RAM, dropping to 15% with overclocked.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/hIz57oy.png)
## Forza Horizon 5
### Performance
![enter image description here](https://i.imgur.com/RvZit0K.png)
The 3080 doesn't seem to like this one. It's hitting a performance wall and becoming GPU limited with the x3d's performance even with a rendering resolution of 360p.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/H5JBvMO.png)
## Gemcraft: Frostborn Wrath
### Performance
![enter image description here](https://i.imgur.com/NczPQPj.png)
This game is not super popular but it's a fun and extraordinarily CPU-limited tower defense game.

I started up an endurance map with the modifier to send additional creeps and then queued 352 waves all at once, measuring the time that it took for them to kill me. This depends on the game simulation speed and scales with all manner of CPU performance.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/t3i20DP.png)
## Horizon Zero Dawn
### Performance
![enter image description here](https://i.imgur.com/cREaKQx.png)
15% improvement at stock, 9% with RAM OC. A bit more on the lows as usual.

### 3.4ghz IPC
![enter image description here](https://i.imgur.com/nrPCfMp.png)
## Kerbal Space Program
### Performance
![enter image description here](https://i.imgur.com/XfxEjV4.png)
I took a huge craft (1300 parts), blew it apart and counted the time required for the launch timer to settle and reach t+10 seconds.

Margin for error is rather high here due to the chaotic and non-deterministic nature of the simulation, but scaling trends are strong enough to establish favor for the x3d and for RAM overclocking. Don't take any specific value too seriously.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/42hwFx9.png)
## OSRS Runelite 117HD
### Performance
![enter image description here](https://i.imgur.com/IIaEDjd.png)
We use the Draynor wheat and potato fields as a standard benchmark for the 117HD plugin as it contains hundreds of animated and dynamic models - the biggest problem for performance. It's also extremely reproducible.

A picture with a simple average and a 1% low can't convey how much of a dream this is to play with. The x3d's larger L3 cache fails to elevate averages much sometimes, but it removes or heavily mitigates engine microstutter at all times which turns it into a completely different game.

Here's a frametime chart from CapFrameX which shows how radically the lows have been improved:
![enter image description here](https://i.imgur.com/az8Vcic.png)
Additionally, some brief testing has shown substantial gains elsewhere in the game such as a 395>542 average FPS increase on top of the improved lows in Mt Karuulm.

### 3.4ghz IPC
![enter image description here](https://i.imgur.com/aLar5Aj.png)
The microstutter just missed the 1% mark here because FPS was lower. CapFrameX shows that the advantage for the x3d increased to 30-50% from around 0.8 to 0.1 percentile.
## Rainbow 6: Siege
### Performance
![enter image description here](https://i.imgur.com/ZY9lqqF.png)
Pretty flat performance, but the x3d does it without RAM OC.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/iJpJTsV.png)
## Shadow of the Tomb Raider
### Performance
![enter image description here](https://i.imgur.com/Nx1pkYN.png)
+47% at stock, +29% with RAM OC
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/OJlMzBF.png)
## Starcraft 2
### Performance
![enter image description here](https://i.imgur.com/1n2ktVC.png)
Some other reviews have shown greater differences. I think that one factor in that is the x3d lowering the cost of some elevated settings such as Physics which i did not test the 5900x with, but i have to look into this more.

[The game certainly runs very well on the most taxing CPU settings. It didn't have much trouble handling 1000 supply battles with various unit compositions in realtime, which used to be unthinkable.](https://streamable.com/ldie1w)
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/lqPK0wu.png)
## Stellaris
### Performance
![enter image description here](https://i.imgur.com/HlnBkLu.png)
Big lead for the 5800x3d here. I realised after running the 5900x numbers however that this was not the best metric to use - with every passing day, the simulation becomes more complex and thus takes longer for the next days. Simulating an extra 20% days might thus take 30% more CPU time and unfairly punish the CPU's which were progressing through the simulation more quickly. To remedy this, i took note of how far the stock 5900x was able to simulate within its time period and then timed how long it took for the x3d profiles to catch up to that point. This resulted in the following chat with massive leads across the board for the x3d.

![enter image description here](https://i.imgur.com/INHoqOa.png)
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/gknnJYD.png)
## The Riftbreaker
### Performance
![enter image description here](https://i.imgur.com/Fx4Lo1P.png)
There are a number of metrics here; the most important ones for smoothness and gameplay are the Simulation rate and the 1% low frametime.

Riftbreaker is a game which scales onto 12 and even 16 cores, but core and cache/memory performance is of paramount importance and there's a clear 5800x3d>5900x>5800x tier list.

### 3.4ghz IPC
![enter image description here](https://i.imgur.com/xwlTkw1.png)
## Tiny Tina's Wonderlands
### Performance
![enter image description here](https://i.imgur.com/Fwb4n13.png)
22% lead at stock, 17% with RAM OC.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/R8HNhav.png)
## Total War: Warhammer II
### Performance
![enter image description here](https://i.imgur.com/fD1pzmk.png)
I need to run Battle benchmarks too. I started to bench TWH2 when i had a 3900x and back then the Campaign benchmark did about 250fps at best, so this has quickly scaled into "running too fast to care" territory but some battles may be more intensive and important.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/7TSFqPV.png)
## World of Warcraft
### Performance
![enter image description here](https://i.imgur.com/gBnTlSJ.png)
Another massive, transformative improvement when going to the x3d. Up to 68% faster than the 5900x (stock) or +29% (RAM OC). When you multiply this with the >50% gains from Matisse to Vermeer, performance has moved really far really quickly.
### 3.4ghz IPC
![enter image description here](https://i.imgur.com/gERpfFi.png)
