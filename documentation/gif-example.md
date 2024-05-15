# To kaniner og en ulv går ind på en bar...

<p align="center">
    <img src="../images/gif.gif"/>
</p>

Eksemplet her består af fire klasser; **Rabbit**, **Wolf**, **Carcass**, samt **Main**. Det anbefales du kigger mod introduktionsguiden på forsiden skulle du være i tvivl om hvordan dette program skrives. Vi vedhæfter herunder koden til de tre klasser:

## Main
Hovedformålet med denne klasse er blot at opstarte en verden (her med størrelsen 5x5 og sikre de rigtige størrelsesindstillinger og varigheden af animationer) og dertil at placere de tre dyr til at starte med. Derudover registrerer vi også ikonet for **Carcass** klassen (som er at finde under *resources*).

```java
import java.awt.Color;

import itumulator.executable.DisplayInformation;
import itumulator.executable.Program;
import itumulator.world.Location;
import itumulator.world.World;

public class Main {

    public static void main(String[] args) {
        int size = 5;
        Program p = new Program(size, 800, 75);

        World w = p.getWorld();

        w.setTile(new Location(0, 0), new Rabbit());
        w.setTile(new Location(2, 2), new Rabbit());
        w.setTile(new Location(4, 1), new Wolf());

        p.setDisplayInformation(Carcass.class, new DisplayInformation(Color.PINK, "carcass-small"));

        p.show();
    }
}
```
## Carcass
**Carcass** klassen er blot en klump kød, der langsomt forsvinder (over fem iterationer af simuleringen). 

```java
import itumulator.simulator.Actor;
import itumulator.world.World;

public class Carcass implements Actor {
    int amount = 5;

    @Override
    public void act(World world) {
        amount--;
        if(amount == 0) world.delete(this);
    }   
}
```

## Rabbit
**Rabbit** er en klasse der repræsenterer kaniner der blot tilfældigt bevæger sig rundt på tomme pladser i nærheden af dem, med mindre det er nat (hvori de sover). Dertil knytter vi to forskellige ikoner til når kaniner sover / er vågne (ved at implementere **DynamicDisplayInformationProvider**). Dertil kan en kanin spises, hvorefter den erstattes på kortet med et **Carcass**.

```java
import java.awt.Color;
import java.util.ArrayList;
import java.util.List;
import java.util.Random;

import itumulator.executable.DisplayInformation;
import itumulator.executable.DynamicDisplayInformationProvider;
import itumulator.simulator.Actor;
import itumulator.world.Location;
import itumulator.world.World;

public class Rabbit implements Actor, DynamicDisplayInformationProvider {
    boolean isNight = false;
    Random r = new Random();


    @Override
    public void act(World world) {
        isNight = world.isNight();
        if(isNight) return;
        List<Location> neighbours = new ArrayList<>(world.getEmptySurroundingTiles());
        if(neighbours.size() > 0) {
            Location next = neighbours.get(r.nextInt(neighbours.size()));
            world.move(this, next);
        }
    }

    public void eat(World world){
        Location l = world.getLocation(this);
        world.delete(this);
        world.setTile(l, new Carcass());
    }

    @Override
    public DisplayInformation getInformation() {
        if(isNight){
            return new DisplayInformation(Color.BLACK, "rabbit-small-sleeping");
        } else {
            return new DisplayInformation(Color.GRAY, "rabbit-small");
        }
    }
   
}
```

## Wolf
Den sidste klasse er ulven, som spiser kaniner der er omkring den, og ellers bevæger sig frit rundt ligesom kaninen. Tilsvarende sover ulven også om natten, hvilket vi sørger for sker visuelt ved at implementere **DynamicDisplayInformationProvider**.

```java
import java.awt.Color;
import java.util.ArrayList;
import java.util.List;
import java.util.Random;

import itumulator.executable.DisplayInformation;
import itumulator.executable.DynamicDisplayInformationProvider;
import itumulator.simulator.Actor;
import itumulator.world.Location;
import itumulator.world.World;

public class Wolf implements Actor, DynamicDisplayInformationProvider {
    boolean isNight = false;
    Random r = new Random();

    @Override
    public void act(World world) {
        isNight = world.isNight();
        if(isNight) return;
        List<Rabbit> rabbits = new ArrayList(world.getAll(Rabbit.class, world.getSurroundingTiles()));
        if(rabbits.size() > 0) {
            rabbits.get(0).eat(world);
            return;
        } 
        List<Location> neighbours = new ArrayList(world.getEmptySurroundingTiles());
        if(neighbours.size() > 0) {
            Location next = neighbours.get(r.nextInt(neighbours.size()));
            world.move(this, next);
        }
    }

    @Override
    public DisplayInformation getInformation() {
        if(isNight){
            return new DisplayInformation(Color.BLUE, "wolf-small-sleeping");
        } else {
            return new DisplayInformation(Color.GREEN, "wolf-small");
        }
    }   
}
```
