---
title: "Other Elements"
type: docs
weight: 6
---

## Light Ping

### **Design**

**Design Statement:**

**Abstraction:** Light Ping is used to indicate to the player that the guards in the vicinity will be going to that location. It is a light that spreads out to visually show a big effect. Light Ping is used in both distraction and the braziers to signify that the guards are notified.

**Interaction with other elements:**

- **Environment:** The light from the ping starts from the center, and expands into a large dome that fills in the whole room.

- **Distract:** When a distraction lands on the ground, the light sphere expands from the distraction’s point of impact

- **Braizer:** Light Ping activates after turning the wheel and the soul lighting it.

### **Code Overview** 

Event BeginPlay

> **Source image:** image79.png *(media file pending upload: `image79.png`)*

In event beginplay, it creates a dynamic material instance, which lets us change the material in real time.

> **Source image:** image325.png *(media file pending upload: `image325.png`)*

When SpawnPing is called within the BP_LightProjectile, it sets the visibility of the sphere, plays the gong sound, and then sets the activate boolean to True. This allows the logic for the ontick to start.

> **Source image:** image99.png *(media file pending upload: `image99.png`)*

If activated is True, in event tic, it will continuously decrease the Aurora opacity for the material. It will also continuously increase the world scale of the object.

It will stop activated once the actor is destroyed in spawn ping after the 10 second delay.
