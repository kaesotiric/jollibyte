---
Title: JolliByte
Authours: Edrielle Mateo, Kate Nabo
Date: Fall 2026
---

# Overview

JolliByte is a timed, state transitioning game inspired by cooking fever and Jollibee. Cook delicious meals from the Philippines.

## Domain Model
``` mermaid
classDiagram
    class FoodItem{
        - item: Food
        - itemState: FoodState
        - cookingTime: int 
        - servedState bool

       %% Getters
        + getItem() string
        + getState() string
        + getTime() int
        + isPackaged() bool 
       %% Setters
        + package() bool
       %% if the current state is PACKAGED, then it can be served
    }
    class DrinkItem{
        - item: Drink
        - cookingTime: int 
        - isFilled: bool

        %% Getters
        + getItem() string
        + getTime() int
        + isFilled() bool 
       %% Setters
        + fill() bool
       %% if the current state is FILLED, then it can be served
    }
    class CookingStation{
        - appliance: Appliance
        - cookingItem: FoodItem
        - cookingTime: int 
        - occupied: bool

       %% Getters
        + getAppliance() string
        + isOccupied() bool
        + getTime() int
       %% Setters
        + changeOccupation() void
    }
    class Customer{
        - order: List~string~
        - orderTime: int

        + getOrder() List~string~
    }
    class Orders{
        - orders: List~Customer~
        + decreaseTime() void
    }


    class Appliance{
        <<enumeration>>
        FRYER
        POT
        BOARD
        FOUNTAIN
    }
    class AssemblyTable{
        <<enumeration>>
        SAUCE
        CHEESE
        HOTDOG
    }
    class Food{
        <<enumeration>>
        SPAGHETTI
        CHICKEN
        FRIES
        BURGER
        PEACHPIE
    }
    class Drink{
        <<enumeration>>
        PINEAPPLE
        CALAMANSI
    }
    class FoodState{
        <<enumeration>>
        RAW
        FRIED
        BOILED
        CHOPPED
        ASSEMBLED 
        PACKAGED 
        BURNT
    }
```

## Flow of Interaction

## Implementation

(Here's where we write about how we've been implementing this project)

1. New customer comes in (is created), they come with their own order (can include minimum of 1 food item, and maximum of 1 drink item). Order begins decreasing as soon as the customer arrives (decrement is constant, but the total patience time of the customer depends on what they're ordering and how many items they're ordering -> each item has their own cooking time).
2. Food items are created by click/dragging on an food item area. Different food items require different methods of cooking. All food items need to be packaged in order to be served.
3. Two drink items are already created in the beginning, and are replenished once 1 out of 2 drink items have been filled, and clicked/dragged to an appropriate spot (either they are served or thrown into the trash). One drink will always be PINEAPPLE and the other will always be CALAMANSI, but they can only been served once filled.
4. 

### Game Engine: Godot
### Language: C#
### Testing: Vitest

Some things to note about C#

* Uses camelCase
* Similar to Java:
``` C#
using System;
namespace MyApplication
{
  enum Level
  {
    Low,
    Medium,
    High
  }
  class Program
  {
    static void Main(string[] args)
    {
      Level myVar = Level.Medium;
      if(myVar == Level.High){
      	Console.WriteLine(myVar);
      }
      else{
        Console.WriteLine("nope");
      }
    }
  }
}
```

