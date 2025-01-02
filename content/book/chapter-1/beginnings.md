+++
title = "Beginnings"
description = "Everybody's gotta start somewhere."
date = 2025-01-02
updated = 2025-01-02
draft = false
weight = 410
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "<em>Everybody's gotta start somewhere.</em>"
toc = true
top = false
+++

## Beginning to understand Entity Component Systems

[Bevy Engine](https://bevyengine.org) is an Entity Component System-based game engine written in
Rust. ECS is a topic that's going to come up repeatedly, so let's deal with it initially in two
ways: using my mental model, and using Wikipedia.

### Mental model

I think if you've spent any time working with databases in the past, it helps in forming a mental
picture of what's going on under the hood of an ECS. So let's say this:

- An ECS is an in-memory database, queryable at runtime, that allows representation of game
  objects as database **entities**.
- It stores relationships between **components** on those entities. We can think of the entity as a
  database ID or _row_, and the components as values or _columns_.
- It can query these values by using the entity as an index, or by querying for any entity which
  is associated with a particular component.
- Such queries take place in **systems**, which are just Rust functions with some superpowers.

This is not a complete picture, but it serves as a beginning and that's what we're after when we
start to think in terms of the ECS and what it can do for us.

### Wikipedia

> Entity–component–system (ECS) is a software architectural pattern mostly used in video game
> development for the representation of game world objects. An ECS comprises entities composed from
> components of data, with systems which operate on the components.

The [Characteristics](https://en.wikipedia.org/wiki/Entity_component_system#Characteristics) section
is a good place to start for a basic understanding. It helps to read more than one description of
the same concept.

### Unofficial Bevy Cheat Book

Let's go for a third approach: [Bevy Cheat
Book's](https://bevy-cheatbook.github.io/programming/ecs-intro.html). If you haven't already
discovered this resource, you're missing out. There's a ton of useful content covering a wide
variety of Bevy topics.

### Bevy Quick Start Guide

Finally, let's get a description from the ~horse's mouth~ bird's beak. Have a read of [Bevy's own
description of ECS and its
implementation](https://bevyengine.org/learn/quick-start/getting-started/ecs/).

> ECS is a software pattern that involves breaking your program up into **Entities**,
> **Components**, and **Systems**. **Entities** are unique "things" that are assigned groups of
> **Components**, which are then processed using **Systems**.
>
> For example, one entity might have a `Position` and `Velocity` component, whereas another entity
> might have a `Position` and `UI` component. Systems are logic that runs on a specific set of
> component types. You might have a `movement` system that runs on all entities with a `Position`
> and `Velocity` component.

## Example

Sometimes it's helpful to see the shape of code when forming a mental picture of what's going on.
Here's how we might instantiate a player entity when launching a game:

```rust
// Create a new entity using `spawn`
commands.spawn((
    // Every element in this tuple is a component.
    Name::new("Player"),
    Player,
    player_animation,
    player_sprite,
    Transform::from_translation(Vec3::ZERO),
));
```

Without going into too many specifics just yet, we can see that we're grouping **components**
together in a tuple.

We add a name for the entity and a thing called a _marker component_ that we'll learn more
about later. We provide it with an initial position on the screen using a `Transform`. We're also
adding previously-defined values for some kind of animation, and a sprite.

Behind the scenes, all these are being associated with an **entity** in the ECS. We're going to
continue to use these terms consistently throughout the book to help keep the mental picture clear.

Let's see the shape of a **system** that acts on a player **entity**:

```rust
fn move_player(mut player_transform: Single<&mut Transform, With<Player>) {
    player_transform = Transform::from_translation(Vec3::new(10., 10., 0.));
}
```

This takes the original position of the player and nudges it by 10 pixels in the `x` and `y` axes.
Would we write such a thing in our game? Probably not, it hardly seems flexible! But this is the
shape of basic queries in Bevy systems.

Don't worry if you don't understand everything you see above. Just let it start filtering into your
brain, because we'll be following similar patterns for the rest of this book.
