# 🎮 Week 0 — Game Dev Track

### COPS Summer of Code

> **Deadline:** 24 May EOD &nbsp;|&nbsp; **Engine:** Unity (2022.3 LTS version) &nbsp;|&nbsp; **Language:** C#

---

## Before You Begin

### Install & Setup

1. Download **Unity Hub** → [unity.com/download](https://unity.com/download)
2. Install **Unity 2022.3 LTS** (or later) via Unity Hub
3. Create a new project → **3D (Universal)** template
4. Open the project in your IDE of choice (VS Code recommended)

---

## Sub Task — "Hello World" Scene

> **Goal:** Prove you've got the basics down. Get comfortable with the editor, write some C#, and make sure your build pipeline works.

### Checklist

- [ ] Create a scene containing a **Cube** and a **Sphere**
- [ ] The **Cube** moves back and forth smoothly using `Vector3.Lerp`
- [ ] The **Sphere** changes color when you press the **`C` key**
- [ ] Successfully build the project and export it as a **standalone folder**

---

### Instructions

#### 1. Setting up the scene

Start in the **Hierarchy** panel — this is where all your GameObjects live. Unity has built-in 3D primitives (Cube, Sphere, etc.) that you can add directly from the right-click menu. Once they're in the scene, use the **Inspector** to position them so they don't overlap.

Every object that needs behaviour needs a **C# Script** attached to it. Create scripts from the Project window and drag them onto the object, or use **Add Component** in the Inspector.

#### 2. Lerp movement on the Cube

`Vector3.Lerp(a, b, t)` returns a point between `a` and `b`, where `t` is a value from 0 to 1 — think of it as a percentage of the journey.

```csharp
Vector3.Lerp(pointA, pointB, t);
// t = 0   → returns pointA
// t = 0.5 → returns the midpoint
// t = 1   → returns pointB
```

Your job is to figure out: how do you make `t` move from 0 to 1 and then back to 0, continuously, over time? Think about what `Time.deltaTime` gives you and how you might use it to drive `t` each frame.

> **Things to look up:** `Time.deltaTime`, `Mathf.Clamp01`, `transform.position`

#### 3. Color change on the Sphere

Unity's `Input` class lets you detect keypresses. There's a difference between a key being **held down** vs. being **pressed once** — make sure you use the right one so the color only changes at the moment you press `C`, not every frame it's held.

To change an object's color at runtime, you need to access its `Renderer` component and set a property on its `material`. Have a look at what `GetComponent<>()` does and how `Color` works in Unity.

```csharp
// A random float between 0 and 1 — useful for generating random colors
Random.value
```

> **Things to look up:** `Input.GetKeyDown`, `GetComponent<Renderer>()`, `material.color`, `Color`

#### 4. Building the project

Once everything works in the editor, go to **File → Build Settings**. Make sure your scene is listed under **Scenes in Build** (add it if not), select your platform, hit **Build**, and point it to an output folder. Run the exported executable to confirm it works outside the editor — don't skip this step.

---

## Main Task — Solvable Rubik's Cube

> **Goal:** Build a fully interactive 3×3 Rubik's Cube in Unity that a player can manipulate and solve by hand. This tests your ability to think spatially, manage object hierarchies, and apply rotations correctly.
>
> **Out of scope for this week:** auto-shuffle and auto-solver. Focus on correct manual interaction.

### Checklist

- [ ] A 3×3×3 Rubik's Cube rendered in the scene
- [ ] All 6 faces can be rotated via keyboard input
- [ ] Rotations animate smoothly (no instant snapping)
- [ ] The cube state stays correct — pieces track their positions accurately after multiple moves
- [ ] Clean, readable, well-commented code
- [ ] Successful standalone build

---

### Instructions

#### 1. Read before you build

This is not a task you should dive into blind. Read the [Tolga Durman tutorial](https://tolgadurman.com/blog/how-to-rubiks-cube-in-unity) fully before writing any code. Understand the approach at a conceptual level first — then start building.

The single most important idea in the whole implementation:

> Each of the 26 visible pieces (cubies) is a child GameObject. To rotate a face, you **temporarily re-parent** the 9 cubies on that face to an empty pivot object, rotate the pivot, then un-parent the cubies back to the cube root.

Draw this out on paper if it helps. Once you truly understand _why_ this works, the code will follow naturally.

#### 2. Plan your GameObject hierarchy

Before touching any code, think about how your scene should be structured. You need a root object for the whole cube, 26 individual cubie objects, and a way to handle rotations cleanly.

Sketch the parent-child relationships first:

```
CubeRoot
├── Cubie (×26)
└── Pivot  ← empty object, used temporarily during rotations
```

Think about: how will you name or identify each cubie? How will you know which cubies belong to a given face?

#### 3. Learn the notation

Standard Rubik's Cube moves have names. Before writing any input code, understand what the letters mean by reading the [ruwix.com notation guide](https://ruwix.com/the-rubiks-cube/notation/):

| Letter | Face          |
| ------ | ------------- |
| U      | Up (top)      |
| D      | Down (bottom) |
| L      | Left          |
| R      | Right         |
| F      | Front         |
| B      | Back          |

A prime symbol (`'`) means counter-clockwise. How might you represent clockwise vs. counter-clockwise in code without writing two separate rotation functions?

#### 4. Building the cube

You need 26 cubies arranged in a 3×3×3 grid (the invisible center core piece doesn't need to exist). Think about how you'd use a loop to place them at the right positions — each axis (x, y, z) runs from -1 to 1 in steps of 1.

Each cubie needs colored faces. Think about how materials work in Unity — can one cubie have different materials on different faces?

#### 5. Selecting which cubies belong to a face

When the player presses a key to rotate the top face, you need to know which 9 cubies are on that face. Think about what all 9 cubies on the top face have in common about their position in the world.

Unity's `Vector3.Dot` can help you check a cubie's position along a specific axis:

```csharp
// Returns how far along 'axis' this position sits
Vector3.Dot(cubie.localPosition, axis)
```

What value would you expect this to return for cubies on the top face if your cube is centered at the origin?

#### 6. Animating the rotation

Instant 90° snaps feel bad. You want to animate the rotation smoothly over a short duration. Look into **Coroutines** in Unity — they let you spread work across multiple frames, which is exactly what animation needs.

```csharp
// A coroutine pauses here each frame and resumes the next
yield return null;
```

Think about: what do you need to know at the start of the rotation (initial state) and at the end (target state)? How does `Quaternion.Lerp` differ from `Vector3.Lerp`?

> **Important:** What happens if the player presses another key while a rotation is already in progress? You need to think about how to handle that.

#### 7. Bonus polish (not required, but fun)

- Move counter UI
- On-screen controls legend
- Reset to solved state
- Camera orbit on mouse drag

---

## Resources

| Resource                                                                                                                        | What it covers                                                        |
| ------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| [Rubik's Tutorial Series — Parts 1–7](https://youtube.com/playlist?list=PLuq_iMEtykn-ZOJyx2cY_k9WkixAhv11n&si=KOQj5WGjm4wuP0NQ) | A Tutorial on how to build a Rubik's Cube                             |
| [Vector3.Lerp – Unity Docs](https://docs.unity3d.com/ScriptReference/Vector3.Lerp.html)                                         | Smooth interpolation between positions                                |
| [Raycast Video](https://www.youtube.com/watch?v=B34iq4O5ZYI&pp=ygUNcmF5Y2FzdCB1bml0eQ%3D%3D)                                    | Raycast explanation video                                             |
| [Physics.Raycast – Unity Docs](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)                                   | Casting a ray from the camera to detect what the mouse is pointing at |
| [Rubik's Cube Notation – ruwix.com](https://ruwix.com/the-rubiks-cube/notation/)                                                | Face names and move directions                                        |
| [Rubik's Cube in Unity – Tolga Durman](https://tolgadurman.com/blog/how-to-rubiks-cube-in-unity)                                | Architecture, rotation logic, cubie management                        |

> **How to approach the videos:** Watch **Parts 1–5** before anything else — they cover everything you need for the Main task. **Parts 6 and 7** are Out of context for this assignment but are well worth watching.

> **A note on Raycasting:** The Tutorial Series uses `Physics.Raycast` to detect which face the mouse is clicking on — this is how the cube knows which face to rotate. A raycast fires an invisible ray from the camera through the mouse cursor into the scene and reports what it hits. You'll encounter this when reading the tutorial, so skim the Unity docs linked above to get familiar with the concept before you need it.

---

## Tips for the Week

- **Start with the warm-up**, even if it feels easy. The build pipeline check is real — many people hit issues only at export time.
- **Understand before you build.** For the Rubik's Cube especially, time spent reading and planning will save you hours of debugging.
- **Commit often.** Small, frequent commits mean you can roll back when something breaks.
- **It doesn't have to be perfect.** A cube where 5 faces rotate correctly is better than no cube. Ship what you have.
- **Ask for help early.** If you're stuck for more than 30 minutes on the same problem, reach out.

---

_Good luck — and have fun!_
