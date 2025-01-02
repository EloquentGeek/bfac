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

> An ECS is an in-memory database, queryable at runtime, that allows representation of game objects
> as database entities. It stores relationships between components on those entities. We can think
> of the entity as a database ID or _row_, and the components as values or _columns_. We query these
> values by using the entity as an index, or by querying for any entity which is associated with a
> particular component. Such queries take place in _systems_, which are just Rust functions with
> some superpowers.

This is not a complete picture, but it serves as a beginning and that's what we're after when we
start to think in terms of the ECS and what it can do for us.

### Wikipedia

> Entity–component–system (ECS) is a software architectural pattern mostly used in video game
> development for the representation of game world objects. An ECS comprises entities composed from
> components of data, with systems which operate on the components.

The [Characteristics](https://en.wikipedia.org/wiki/Entity_component_system#Characteristics) section
is a good place to start for a basic understanding.

## Example

Sometimes it's helpful to see the shape of code when forming a mental picture of what's going on.
Here's how we might instantiate a `Player` when launching a game:

```rust
commands.spawn((
    Name::new("Player"),
    player_animation,
    player_sprite,
    Transform::from_xyz(Vec3::ZERO),
));
```

Without going into specifics just yet, we can see that we're grouping **components** together in a
tuple. We add a name for the entity, and provide it with an initial position on the screen. We're
also adding previously-defined values for some kind of animation, and a sprite. Behind the scenes,
these are being associated with an **entity** in the ECS. We're going to continue to use these terms
consistently throughout the book to help keep the mental picture clear.

Don't worry if you don't understand everything you see above: it will all become devastatingly
familiar later.
