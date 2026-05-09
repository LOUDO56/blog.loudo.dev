---
Date: 2026-05-09 13:09
Draft: false
Layout: post
Summary: cutscene, camera angle, interaction and story compilation
Title: narrativecraft 2.0 devlog 2
---

hello everyone! new devlog and a BIG one!

## TL;DR

i implemented the following features:
- creating cutscenes
- creating camera angles when a character speaks
- creating interaction zones and points for gameplay
- story now compiles in-game

videos are down!

## cutscene

the last cutscene implementation was... well... not really intuitive. you had to deal with keyframe groups, entering each keyframe to edit values, cross the whole map to find a keyframe... yeah looking back at it, it was a horrible user experience.

so, i refactored it, and it is, for sure, REALLY better and more intuitive.

basically:

- a timeline
- layers
- separated layers
- keyboard shortcuts
- transparent camera (lines drawn for cameras)
- exact camera path

now, it is super easy to create cinematics without headache, it's like [Flashback](https://modrinth.com/mod/flashback) mod, but a lightweight version to allow you to create cutscenes for your stories.

<video controls>
  <source src="/static/assets/devlog-2/cutscene.mp4" type="video/mp4">
</video>

## camera angle

camera angle was also refactored, it's a bit different from the last one with some extra features to make the process easier:
- dialog configuration for a character for a camera
- live dialog data configuration
- transparent camera with name attached on top

the main feature of this refactor is that it's easier to set up camera angles with a precise look at how a dialog will render on a character on this camera specifically, and when the camera is called in the story, it will be rendered like you previously set.

<video controls>
  <source src="/static/assets/devlog-2/camera-angle.mp4" type="video/mp4">
</video>

## interactions

the interactions setup does not really differ from the last version, however it has a better user experience when setting a zone and a point.

- a zone is a specific location that, when the player enters it, plays a certain point in the story from ink
- a point is a small white point to interact with

the point was refactored to a small white point instead of an eye, and you no longer need to aim exactly at the location to make the point appear, you can either show it by distance, or aim radius.

you can also now see names rendered for each entry, making it easier to locate them without losing track.

<video controls>
  <source src="/static/assets/devlog-2/interactions.mp4" type="video/mp4">
</video>

## story

before, compiling a story had to be done through inky, but now, it's over, the story compiles directly **in-game**!
the compiler was ported to java by [bladecoder](https://github.com/bladecoder), thanks for his hard work!

## what's next?

it's still in development, but it's going really great! i think i'm at 70-75%.
the mod also had no crashes (or very few) during development, all thanks to the multiplayer implementation with packets that handles a lot of the mod's behavior really well.

i'm going to set a deadline, but don't count on me to respect it, i'm thinking of releasing the mod in **may** given how advanced it is.

thanks for reading.

## support

if you like my work and effort, donations are always welcome :d [https://ko-fi.com/loudo](https://ko-fi.com/loudo)