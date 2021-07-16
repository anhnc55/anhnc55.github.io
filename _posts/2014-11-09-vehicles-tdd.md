---
layout: post
title: Vehicles Door Sensors TDD  
excerpt: "A TDD exercise from SQLi Team used in a recruitment campaign"
tags: [TDD, java, architecture, eng]
comments: true
image:
  feature: header/nature/leaf-red-green.jpg
---

## Description

This is a TDD exercise SQLI Morocco used as a challenge in a [recruitment campaign](http://icancode.sqli.com/participer.html){:target="_blank"}

It's about vehicles and their door sensors. A vehicle is displayed as bellow:

<pre>
        _
door 1 | | door 2
door 3 |_| door 4
</pre>

For example to represent the vehicle with door 2 and 3 as open:

<pre>
          _
door 1   | \ door 2
door 3   /_| door 4
</pre>

In plus, each vehicle has a different consumption according to its Fuel type:

- Diesel: 5%
- Gasoline: 6%
- Hybrid: 3%

## Context

After at least 8 months of full time programming with PHP/Symfony, I needed to get back to Java and keep my brain JVM compiler alive... and it was raining all this weekend :) <br />
So it was a perfect memory-refresh for me and I think it can also play a nice [code kata](https://en.wikipedia.org/wiki/Kata_(programming) ) theme.

## Main test class

{% highlight java %}

public class VehiclesTest {

    private Vehicles vehicles;

    @Before
    public void initVehicles() {
        /**
        VEHICLE_ID:FUEL_TYPE:NUMBER_OF_DOORS
        **/
        vehicles = new Vehicles("CAR:Hybrid:4, TRUCK:Diesel:2, MOTORCYCLE:Gasoline:0");
    }

    @Test
    public void testCar() {
        String report = vehicles.move("CAR", "1 2 3 4", "200 KM");
        Assert.assertEquals("DOORS OK, MOVING. The CAR will consume 6.00 L", report);
    }

    @Test
    public void testTruck() {
        String report = vehicles.move("TRUCK", "1 2", "1000 KM");
        Assert.assertEquals("DOORS OK, MOVING. The TRUCK will consume 50.00 L", report);
    }

    @Test
    public void testMotorCycle() {
        String report = vehicles.move("MOTORCYCLE", "", "50 KM");
        Assert.assertEquals("DOORS OK, MOVING. The MOTORCYCLE will consume 3.00 L", report);
    }

    @Test
    public void testCarFrontRightDoorNotClosed() {
        /***********
         The car should be displayed as below :
           _
          | \
          |_|

         ************/
        String report = vehicles.move("CAR", "1 3 4", "200 KM");
        Assert.assertEquals("DOORS KO, BLOCKED \n"+
                            "  _\n"+
                            " | \\\n"+
                            " |_|", report);
    }

    @Test
    public void testCarBackLeftDoorNotClosed() {
        /***********
         The car should be displayed as below :
           _
          | |
          /_|

        ************/
        String report = vehicles.move("CAR", "1 2 4", "200 KM");
        Assert.assertEquals("DOORS KO, BLOCKED \n"+
                            "  _\n"+
                            " | |\n"+
                            " /_|", report);
    }
}

{% endhighlight %}

You can find my first solution in this [GitHub repo](https://github.com/fayway/ICanCode){:target="_blank"}
