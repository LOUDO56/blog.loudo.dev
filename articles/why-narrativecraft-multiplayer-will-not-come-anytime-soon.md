---
Date: 2026-03-02 22:31
Draft: false
Layout: post
Summary: narrativecraft next update is slow, and i explain why
Title: why narrativecraft multiplayer will not come anytime soon
---

[français](/p/why-narrativecraft-multiplayer-will-not-come-anytime-soon-fr)

since november 2025, narrativecraft hasn't received any update. here is why.

narrativecraft is a minecraft mod that means a lot to me. i've been working on it for 11 months.

## how narrativecraft evolved

minecraft modding is hard, especially when starting from zero. in april 2025, i began learning with small projects. there is no simple, ready-to-use api. you have to explore, read minecraft source code, and understand both client and server logic.

at first, i did not understand the importance of properly separating client and server code.

once i had enough knowledge, i started narrativecraft, my biggest project so far.

## starting too big with limited knowledge

i developed narrativecraft while still learning. the project became a playground without a clear roadmap. features were added in a random order.

a beta version was released and received positive feedback, but internally the mod was unstable, messy, and full of crashes.

fixing bugs was not enough. the structure itself was flawed, so i decided to rewrite it.

## first rewrite

i rewrote the entire project from scratch for one month and released version 1.0.0.

it was more stable, but still suffered from poor architecture and hard-to-reproduce bugs. after releasing it and publishing a [youtube video](https://www.youtube.com/watch?v=8J2jwnHP7cE) about the development process, i decided to work on the most requested feature: multiplayer.

## the multiplayer problem

i initially ignored packets and proper client-server communication. the mod worked in singleplayer but failed or crashed on servers.

to support multiplayer, packets were required. i began implementing them in january 2026. progress was made, but motivation dropped. working exclusively on this project led to burnout.

in addition, the codebase had become difficult to maintain. reviewing it was discouraging. i decided to rewrite the project again.

## fuck it re-rewrite

the current code is too unstable and poorly structured to extend properly. adding multiplayer and maintaining compatibility across versions is excessively complex.

with the experience gained, i now know exactly how to rebuild narrativecraft with proper multiplayer support and a cleaner, maintainable architecture.

this re-rewrite will take several months. no release date can be announced.

i am still working on the mod. the objective is to deliver a version with solid code, stable multiplayer, and fewer critical issues.

if you want to support the project, you can donate on ko-fi:
https://ko-fi.com/loudo

i will publish progress updates when possible.

for now, please wait.

cya :p