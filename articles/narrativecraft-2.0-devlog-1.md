---
Date: 2026-03-25 13:09
Draft: false
Layout: post
Summary: recording system implemented, api and starting cutscene editor
Title: narrativecraft 2.0 devlog 1
---

hello everyone! and now this is the first devlog (real one), and i've made really good progress.

## recording

the first step was to recreate the recording system. the implementation process is similar to the previous version, but the file format has changed.

before, data was stored in `.json` files. this was not optimized because actions are recorded every tick (each game update), and storing everything as strings resulted in very large file sizes.

to solve this, i created a custom file format called `.ncr`.

instead of storing data as strings, it is now stored as raw bytes. this significantly reduces file size and allows faster and more efficient processing for the mod.

this implementaion was highly inspired from the work of [mt-1006](https://github.com/mt1006) from the mod [Motion Capture](https://github.com/mt1006/mc-mocap-mod)!

## playback client-side

for multiplayer compatibility, i implemented a system that allows playback to be visible only to specific players.

some actions can now be executed client-side using packets. this makes it possible to play a sequence for only one player without affecting others.

the way it works is the following:
- when an entity is created on the server, it is immediately removed (killed) for all non-target players  
- for the target player, the entity is spawned using packets so it only exists on their client  

<video controls>
  <source src="/static/assets/narrativecraft-devlog-1/playback-client-side.mp4" type="video/mp4">
</video>

### current issue

while this works, there's actions that are hard to fully do client-side such as right-clicking a block. if a fake player press a button for exemple, doing this only client-side is a bit harder than expected, before finding a solution for now the right click block action will be only rendered server-side for everyone on the server.

## api

i created an api that allows developers to register their own recording actions.

this makes it possible to extend the system for custom needs, and to add compatibility with other mods such as [EmoteCraft](https://modrinth.com/plugin/emotecraft) or [BetterCombat](https://modrinth.com/mod/better-combat) without modifying the core mod.

i also added an event bus so developers can listen to recording-related events and implement custom behavior.

currently available events:
- RecordStartEvent  
- RecordStopEvent 
- RecordSaveEvent  

more events will be added later, including events related to ink action execution.

it will also be possible to register custom ink actions through the api, but this part is planned for later.

## cutscene

the current focus is the cutscene system.

this part will be a complete refactor with a brand new ui and a different workflow for creating cutscenes.

instead of placing cameras in the world and manually editing them, the new system will provide:
- a dedicated timeline  
- layered tracks  
- keyframes that can be placed and edited directly in the interface  

this will make the whole process more visual and easier to manage.

this is a large feature and will take significant time to complete, as it involves building the ui, handling keyframe interpolation and paths, and muuuuch mooooore.

## track commits

i didn't say it on the last post, but you can track the progress on the [dev branch](https://github.com/LOUDO56/NarrativeCraft/tree/rerewrite)

## support

if you like my work and effort, donation are always welcome :d [https://ko-fi.com/loudo](https://ko-fi.com/loudo)