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
