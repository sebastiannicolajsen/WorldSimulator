<p align="center">
    <img width="250px" src="../../../images/theme-1.png"/>
</p>

# Primitive life: Herbivore and Plants (Theme 1)
- [Description](#description)
- [Included input files](#included-input-files)
- [Recommended approach](#recommended-approach)
- [Requirements overview](#requirements-overview)
- [Corrections from the biologist](#corrections-from-the-biologist)

This document contains a description of the first theme for the project in basic programming. Before you start with the tasks, it's important that you have the base project up and running. This is described in the document ITU Simulator – description of library.

This document is structured so that
- **description** gives an insight into what our "mini-world" should be able to support when the theme is completed.
- **Included input files** shows the files the program should be able to load when the theme is completed.
- **Requirements** overview gives an overview of various requirements that need to be supported.
- **Recommended approach** breaks down various requirements and suggests how you can approach the theme from start to finish.

# Description

Nature is a wild place in many ways. There are many different kinds of animals living in many different habitats – some are barren, others are fertile and flourish with grass and plants. In the first theme, we focus on the sweet and simple; green grass and fresh rabbits. In our little world, plants and rabbits live in harmony; the rabbits eat a little grass here and there, have lots of cute offspring. At the same time, grass thrives symbiotically in this small limited world **[1]**. The rabbits enjoy freely digging holes and tunnels that spread across our little square patch. A quiet and calm cycle, where there is peace at night, for then the rabbits sleep in their small holes and tunnels; but who knows where they'll peek out the next morning?

# Included input files

```
t1-1a.txt
t1-1b.txt
t1-1c.txt
t1-2a.txt
t1-2b.txt
t1-2cde.txt
t1-2fg.txt
t1-3a.txt
t1-3b.txt
tf1-1.txt
```

All input files have the following form:

```
N type number 
type min-max
```

N indicates the size of the world. Type is the type of actor / element to be added to the world, e.g. a rabbit (denoted 'rabbit'). Then follows either one number describing exactly how many should be added to the world, or two numbers (with a hyphen in between) giving an interval for how many should be added (i.e. minimum and maximum). Here, a random number of the type should be added (between the interval).

We recommend putting the various input files in the 'data' folder in the provided project.

# Requirements overview

When the following requirements are met, theme 1 is completed. All requirements and input files have an ID to help guide you. Thus, for example, you can advantageously use the input files t1-2cde when solving requirements K1-2c, K1-2d, and K1-2e, i.e. when the number after the hyphen is the same. In the first theme, the requirements are grouped by topics. This will not necessarily be the case later. In addition to the mandatory requirements, optional requirements follow at the bottom of the requirements overview.

## Grass
- **K1-1a**. Grass can be planted when the input files describe this. Grass should just be randomly placed.
- **K1-1b**. Grass can spread.
- **K1-1c**. Animals can stand on grass without anything happening to the grass (Here the NonBlocking interface can be utilized).

## Rabbits
- **K1-2a**. Rabbits can be placed on the map when the input files describe this. Rabbits should just be randomly placed.
- **K1-2b**. Rabbits can die, which results in them being removed from the world.
- **K1-2c**. Rabbits live on grass which they eat during the day, without food a rabbit dies.
- **K1-2d**. Rabbits' age determines how much energy they have.
- **K1-2e**. Rabbits can reproduce.
- **K1-2f**. Rabbits can dig holes, or share existing holes with other rabbits. Rabbits can only be linked to one hole.
- **K1-2g**. Rabbits seek towards their holes when evening comes, where they sleep **[2]**. It is not a requirement that rabbits reach their holes.

## Rabbit holes
- **K1-3a**. Holes can either be inserted when the input files describe this, or dug by rabbits. Holes are randomly placed when they are included in an input file.
- **K1-3b**. Animals can stand on a rabbit hole without anything happening.

## Optional, not mandatory, requirements.
- **KF1-1**. Holes always consist of at least one entrance, however there can be multiple entrances that together form one rabbit tunnel. Rabbits can only dig new exits while they are in their holes.

# Recommended approach

Before you start with the tasks, it's important that you have the base project up and running. This is described in the document which describes the library.

After that, it's very important that you get an overview of the methods belonging to the World class. Specifically, it's important to know and understand: *delete*, *remove*, *getSurroundingTiles*, *getSurroundingEmptyTiles*, *isNight*, *isDay*, *move*, *containsNonBlocking*, *isTileEmpty* and *setTile*. Additionally, you should understand how the *NonBlocking* interface works.

After this, we recommend that you read the good advice in the project description. This advice is always good to follow regardless of where in the process you are.

Next, it is recommended that you perform an object-oriented (OO) analysis as seen in teaching session 19. Here you can advantageously start with *description*, *Included input files* (the actual file content), and *requirements overview*. By looking at the text, the content of the input files, and the various requirements, you can get an overview of which components need to be built, and what functionality they should have. Here you can also start to consider potential relationships between classes (e.g. the need for abstract classes, interfaces, helper classes with static functions, etc.). These would be good elements in the diary part about the theme.

As stated in the project description, not all requirements describe exactly how something should be implemented. It's up to you as a group to determine this. For example, should a rabbit be able to eat grass when it's standing next to it, or on top of it? Remember to document your choices, possibly with comments, and if you feel the choices are very central, this could also be relevant in the first section of the diary or under design choices.

Often, the different requirements can be solved in multiple ways, and some solutions will be easier to approach than others. Talk together, and don't necessarily choose what's hardest for yourselves.

Now you have a rough sketch of what needs to be built, but before you start programming, you should first consider – is there anything in the program you want to refactor, i.e. change? This is not necessarily the case in the first theme, but will become incredibly important for the upcoming themes, as we build on the system. These can also be good elements in the report's part about the theme.

Additionally, you can consider; are there any requirements that don't make particularly good sense? Make a decision about why and how you interpret them, and reflect on this. This is also good content for the diary and report.

After this, you can start implementing and testing the various parts. By tests, we refer to the form of tests the course teaches (unit tests). Test while you implement. The requirements are sorted (for each group of requirements) so that the first requirements are those you should start implementing and testing. However, there will be requirements that require you to have implemented parts of other requirement "groups". Here you can again look towards the good advice in the project description, if they are too overwhelming to start with.

# Corrections from the biologist
**[1]** In practice, this is not symbiosis. When talking about herbivores, it would not be symbiosis or mutualism, unless the rabbits, for example, fart out the seeds from the grass somewhere else (which they don't really do). Symbiosis describes one or more species that are unable to live without the other.

**[2]** In practice, you probably wouldn't call them holes, but rather a 'nest'.
