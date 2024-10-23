<p align="center">
    <img width="250px" src="../../../images/theme-3.png"/>
</p>

# Decomposition: The Fungal Kingdom (Theme 3)

- [Description](#description)
- [Included input files](#included-input-files)
- [Requirements overview](#requirements-overview)
- [Recommended approach](#recommended-approach)
- [Corrections from the biologist](#corrections-from-the-biologist)

This document contains a description of the third theme of the project. This document is structured so that:
- **Description** gives an insight into what our "mini-world" should be able to support when the theme is completed.
- **Included input files** shows the files the program should be able to load when the theme is completed.
- **Requirements overview** gives an overview of various requirements that need to be supported.
- **Recommended approach** breaks down various requirements and suggests how you can approach the theme from start to finish.

# Description
Nature has different phases. An important but often overlooked part of this is decomposition. Decomposers are those that help fertilize nature, and much more. Here, we can clearly recommend the documentary "Fantastic Fungi" or episode two of the documentary series "The Blue Planet". This part of nature ensures that everything runs smoothly! And this is the focus for this week. Maybe we will also encounter parts of the animal kingdom that have recently gained significant attention through games and TV series?

# Included input files
```
t3-1a.txt
t3-1b.txt
t3-1c.txt
t3-2ab.txt
tf3-1a.txt
tf3-2a.txt
tf3-3ab.txt
```
Note regarding input files: Although this week primarily consists of adding things that can "randomly" occur on the map, these are also loaded from files. They are loaded just like animals have been done previously, with the exception of the Cordyceps fungus, where it is also specified which animal it should be attached to:

```
N carcass 1
carcass fungi 1-10
cordyceps rabbit 1
cordyceps wolf 1-5
```

# Requirements overview
When the following requirements are met, theme 3 is completed. Like in last week's theme description, all requirements and input files have an ID to help along the way. The individual requirements this week are larger than before, but there are fewer. In addition to the mandatory requirements, voluntary requirements follow at the bottom of the requirements overview.

- **K3-1a**. Create carcasses that are placed on the map when the input files describe this.
- **K3-1b**. When animals die now, they should leave a carcass. Carcasses can be eaten just like animals could before, but the amount of "meat" depends on the size of the animal that died. Thus, animals are no longer eaten directly when they are killed; instead, the carcass is eaten. All carnivorous animals eat carcasses.
- **K3-1c**. Carcasses deteriorate over time and decompose completely – even if they are not eaten (i.e., they disappear)! They also disappear if they are completely eaten.
- **K3-2a**. In addition to carcasses decomposing, fungi help **[1]**. Thus, fungi can emerge in a carcass **[2]**. This cannot be seen on the map itself, but the fungus lives in the carcass. When the carcass is decomposed (and disappears), the fungus can be seen as a fungus placed on the map where the carcass was **[3]**. To read the input files, you must ensure that a carcass can be loaded with a fungus.
- **K3-2b**. Fungi can only survive if there are other carcasses nearby that they can spread to. If this is not the case, the fungus will also die after some time. The larger the carcass, the longer the fungus will live after the carcass is gone. Since the fungus can release spores, it can reach a bit further than just the surrounding areas.

## Voluntary, non-mandatory requirements
- **KF3-1a**. When a fungus dies, the soil is extra favorable. Therefore, grass appears in these fields when the fungus dies **[4]**.
- **KF3-2a**. Not all types of fungi live on dead animals. There is also another type of fungus (Cordyceps)**[5]**. This fungus spreads to and controls (only) living animals. Their life cycle is the same as the previous fungi; they slowly decompose the animal, and if there is no more of the animal left, the fungus dies soon after. When the fungus has consumed enough of the animal, the animal dies. Since this fungus decomposes the animal while it is alive, there is no carcass after death. The fungus also dies when the animal dies, except for the requirement 
- **KF3-3a**. When Cordyceps' host dies, it attempts to spread to living animals nearby, and only at this time. Again, this fungus can spread a bit further than the surrounding areas as it releases spores.
- **KF3-3b**. When an animal is infected with the Cordyceps fungus, the fungus takes over the animal's actions. The animal therefore does what the fungus determines, which is to seek out other animals of the same species.

# Recommended approach
It is recommended that this week also start with an object-oriented analysis by looking at the text, the content of the input files, and the various requirements. Thus, you have an overview of what needs to be added. This time, it may be difficult to see if there is an opportunity to reuse existing code. However, you will certainly need to modify previous code, and from this, opportunities arise to add additional abstractions. For example, since all animals can be taken over by the same fungus, there should be a refactoring that ensures we can reuse the code around this new behavior. Considerations about this are also good in this week's log. Remember to consider how this affects previous tests and update them as necessary. If you find it difficult to start implementing the fungi, you can start by thinking that fungi do not use the Actor interface until they are placed in the world and until then, act through calls from the animal they have infected. However, there are several ways to implement this. Before you start programming, we will just mention that this week also has several 'invisible' elements that cannot always be seen on the map. Here, you can benefit from looking at the *DynamicDisplayInformationProvider*, which allows changing the appearance of an element during execution. This can be particularly beneficial for these fungi since they do not necessarily exist on the map themselves. If you have not used the interface before, you will probably find it interesting to also use it for previous animals you have implemented. Unit tests are especially important this week, as it can be difficult to determine whether the program behaves as expected. You may need to investigate further what is available in the World class. Maybe there are things you did not use last week that could be good to use this week.

# Corrections from the biologist

**[1]** For example, fungi of the genus Mucor.

**[2]** Normally, one does not often see fungi directly in the decomposition process, as the decomposition of carcasses is usually carried out by insects and bacteria. However, fungi are incredibly good at decomposing plants, etc. For example, your meat products often become rotten (due to bacteria) whereas your bread and fruit are attacked by fungi (mold).

**[3]** When the carcass is decomposed, the fungi will die because their growth substrate is gone. Here, the mission of the fungus is to manage to spread to a new substrate before the carcass is gone. Additionally, it is a large process to decompose a corpse, and several species of fungi fulfill different stages of the decomposition, the same applies to the bacteria and small animals that are also part of the process. See, for example, the article here.

**[4]** Fairy rings are a fun example of the effect of fungi on grass growth.

**[5]** This type is called entomophatogenic fungi, and there are over 1,000 species distributed across several families and orders of fungi. In nature, only insects/arthropods are affected by these. If it were natural, our bears/wolves/rabbits would be safe.

