---
Date: 2026-03-08 18:46
Draft: false
Layout: post
Summary: showing what i've done so far
Title: narrativecraft 2.0 devlog 0
---

hello everyone! i present you devlog 0. this one is mainly here to show what i've done so far.

## the refactor

narrativecraft version 1.0.0 was already a refactor meant to improve the codebase and reduce crashes. i did make several changes at the time, but the reality is that the project was still suffering from bugs and crashes because i didn't follow proper software architecture practices.

version 2.0.0 is therefore a second, deeper refactor with clearer goals:

- rebuild the codebase from scratch to make it maintainable and easier to contribute to as an open source project  
- implement a proper multiplayer system  
- improve readability and long-term stability of the code  

so far the results are great. i followed a new architecture approach to improve maintainability, but for now i'll mostly show the visible parts for people who don't really care about the code itself.

## first look at the new screens and multiplayer

the main focus of this update is multiplayer. i've successfully implemented the foundations that make it possible, starting with data synchronization.

basically, every chapter, scene, and other narrative data is synchronized between the server and the clients dynamically.

<video controls>
  <source src="/static/assets/narrativecraft-devlog-0/preview-mutliplayer.mp4" type="video/mp4">
</video>

as you can see, two minecraft instances are connected to the same dedicated server, and the data updates in real time.

if you downloaded the mod before, you might also notice that the menu screen has changed. i'm rebuilding it completely from scratch.

the previous menu reused and duplicated a lot of code from mojang's internal screens. that made the code difficult to maintain, because mojang occasionally updates those screens internally and it would break my implementation or require heavy adjustments.

the new system allows me to have my own menu with custom features such as:

- a breadcrumb navigation on the left side  
- better pagination with the ability to skip multiple pages  
- a search bar (coming soon) to filter entries more easily  

having my own screen system will also make it much easier to update the mod to newer minecraft versions.

## what's next

the next step is implementing the recording system.

the goal is to record players and mobs with a new recording format that stores animation and movement data in a much lighter and more efficient way.

that's it for now. if you're a developer, you might want to keep reading the next section :p

## structure

this refactor introduces a new structure designed to keep the code maintainable while allowing clean and flexible data transfer.

the old implementation relied heavily on class inheritance.

for example, to display chapters in the ui i had to create a dedicated screen class for chapters. that screen contained custom button behaviors. then i had to do the same thing again for scenes, and again for other entry types.

over time this quickly became difficult to maintain because each entry type required its own specialized implementation.

the same problem appeared with network packets.

when i started experimenting with multiplayer for version 1.1.0, i had around 6 or 7 different entry types inheriting from `NarrativeEntry.java`. that meant creating a different packet class for each entry type and registering each one separately on both fabric and neoforge.

that approach quickly became painful to maintain.

## registry pattern

to avoid repeating the same mistake, i spent some time thinking about a better solution and eventually moved to a registry pattern.

the idea is simple: instead of creating multiple hardcoded implementations, a single system can dynamically select the correct behavior based on the entry type.

for example, the screen shown earlier is now a single generic screen capable of displaying any `NarrativeEntry.java` subclass. however, each entry type can still define its own button behaviors.

to make this possible, i created a registry where each entry type registers its own ui behavior implementation.

for example, the edit button opens the correct edit screen based on the `NarrativeEntry.java` type. since each entry type can define additional fields, the edit screen also adapts to the entry implementation.

the registry class is called `ClientNarrativeUIActionRegistry.java`, and the behavior interface is `ClientNarrativeUIAction`.

```java
public interface ClientNarrativeUIAction<T extends NarrativeEntry> {

    AbstractNarrativeEntryEditScreen<T> showEditScreen(T entry, Screen lastScreen);

}
```

then i implement it for `Chapter.java`:

```java
public class ClientChapterNarrativeUIAction implements ClientNarrativeUIAction<Chapter> {

    @Override
    public AbstractNarrativeEntryEditScreen<Chapter> showEditScreen(Chapter entry, Screen lastScreen) {
        return entry == null ? new ChapterEntryEditScreen(lastScreen) : new ChapterEntryEditScreen(entry, lastScreen);
    }
}
```

and finally register it:

```java
ClientNarrativeUIActionRegistry.getInstance().register(Chapter.class, new ClientChapterNarrativeUIAction());
```

with that in place, the edit screen can be opened dynamically like this:

```java
// "item" inherits from NarrativeEntry

Button editButton = Button.builder(Component.literal("✎"), b -> {
    minecraft.setScreen(
            ClientNarrativeUIActionRegistry.getInstance().showEditScreen(item, this));
})
.bounds(x + buttonWidth - 15, y, 20, 20)
.build();
```

## packets

for packets i switched to a polymorphic packet approach.

instead of creating one packet class per entry type, a single packet structure can transport different data types. the packet contains the information needed to determine which entry type it represents.

once received, the system uses a registry mentioned earlier to determine the correct class and handle the data properly.

this allows the networking system to stay generic and avoids creating and registering a large number of packet classes for each narrative entry type.

cya!