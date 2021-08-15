---
layout: post
title: Labyrinth TDD  
excerpt: "A TDD exercise from SQLi Team to complete in less than 3H"
tags: [TDD, java, architecture, eng]
comments: true
image:
  feature: header/tech/red-green.jpg
---

## Introduction

This is another TDD exercise from SQLi Team to complete in less than 3H.

It was quite challenging, I got stuck at the 5th or the 6th test, I wasn't able to go further without breaking the already passed tests... and this is the point, never trust your feelings in software development, trusts your TDDs instead.

Here is the main TDD class:

{% highlight java %}

public class LabyrinthShould {

    /**
     * each letter represent a room
     * each | represent a gate between two room
     * each $ represent a gate with a sensor on
     **/
    @Test
    public void be_Walkable_Till_The_End() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "C|E", "B$D", "B|E", "E$F", "D$F", "F|G");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("E");
        labyrinth.walkTo("F");
        labyrinth.walkTo("G");
    }

    @Test(expected = IllegalMoveException.class)
    public void refuse_Illegal_Move() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "B$D");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("E"); // room E does not exist in the labyrinth
    }

    @Test(expected = IllegalMoveException.class)
    public void refuse_Move_Without_Path() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "B$D");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("C"); // Can not reach C from B
    }

    @Test
    public void allow_Cyclic_Path() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "C|E", "B$D", "B|E", "E$F", "D$F", "F|G");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("D");
        labyrinth.walkTo("F");
        labyrinth.walkTo("E");
        labyrinth.walkTo("B");
        labyrinth.walkTo("D");
        labyrinth.walkTo("F");
        labyrinth.walkTo("G");
    }

    @Test
    public void allow_Back_And_Forth() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "C|E", "B$D", "B|E", "E$F", "D$F", "F|G");
        labyrinth.popIn("A");
        labyrinth.walkTo("C");
        labyrinth.walkTo("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("D");
    }


    @Test
    public void allow_Walker_To_Close_Passed_Door() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "C|E", "B$D", "B|E", "E$F", "D$F", "F|G");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("D");
        labyrinth.walkTo("F");
        labyrinth.closeLastDoor();
        labyrinth.walkTo("G");
    }

    @Test(expected = DoorAlreadyClosedException.class)
    public void allow_Walker_To_Close_Only_Last_Door() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "C|E", "B$D", "B|E", "E$F", "D$F", "F|G");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("D");
        labyrinth.walkTo("F");
        labyrinth.closeLastDoor();
        labyrinth.closeLastDoor();
        labyrinth.walkTo("G");
    }

    @Test(expected = ClosedDoorException.class)
    public void not_Allow_Closed_Door_Crossing() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "C|E", "B$D", "B|E", "E$F", "D$F", "F|G");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("D");
        labyrinth.closeLastDoor();
        labyrinth.walkTo("F");
        labyrinth.walkTo("E");
        labyrinth.walkTo("B");
        labyrinth.walkTo("D");
        labyrinth.walkTo("F");
        labyrinth.walkTo("G");
    }

    @Test(expected = ClosedDoorException.class)
    public void not_Allow_Turn_Back_Through_Closed_Door() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "C|E", "B$D", "B|E", "E$F", "D$F", "F|G");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        labyrinth.walkTo("D");
        labyrinth.closeLastDoor();
        labyrinth.walkTo("B");
    }

    @Test
    public void follow_Walker() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "B$D", "D$E", "D$F", "F$H", "D$F");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        assertThat(labyrinth.readSensors()).isEqualTo("AB");
        labyrinth.walkTo("D");
        assertThat(labyrinth.readSensors()).isEqualTo("AB;BD");
        labyrinth.walkTo("F");
        assertThat(labyrinth.readSensors()).isEqualTo("AB;BD;DF");
    }

    @Test
    public void follow_Walker_Through_Unmonitored_Path() {
        Labyrinth labyrinth = new Labyrinth("A$B", "A$C", "C|E", "B$D", "B|E", "E$F", "D$F", "F|G");
        labyrinth.popIn("A");
        labyrinth.walkTo("B");
        assertThat(labyrinth.readSensors()).isEqualTo("AB");
        labyrinth.walkTo("E");
        labyrinth.walkTo("F");
        assertThat(labyrinth.readSensors()).isEqualTo("AB;EF");
        labyrinth.walkTo("G");
        assertThat(labyrinth.readSensors()).isEqualTo("AB;EF");
    }
}

{% endhighlight %}

You can find my first solution (under the time pressure) in this [GitHub repo](https://github.com/fayway/LabyrinthTDD){:target="_blank"}

## TODO

Now that all tests are green, next step is to refactor my mess in better SOLID Clean Code.
