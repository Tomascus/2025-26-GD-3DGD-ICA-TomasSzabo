# Simulacrum - Tomas Szabo

## Overview

Simulacrum is a first-person escape room experience built based on nostalgia, mystery. The player wakes inside what appears to be a retro 1990s apartment but gradually discovers through environmental clues and physical puzzle solving that the space is an artificial simulation chamber. The goal is to find three cassette fragments hidden behind three separated puzzles, insert them into cassette players to unlock the exit, and trigger the ending cinematic that reveals the truth of the space.

The experience is intentionally scoped around a single apartment environment as was needed for my CA. The narrative is told through layout, props, lighting, materials, and player discovered audio and visual clues rather than cutscenes or dialogue, making it more raw.

---

## How to Play

1. Explore the apartment: kitchen, living room, and bathroom each contain a hidden puzzle
2. Solve each puzzle to unlock a cassette fragment
3. Collect the fragment and locate cassette player for each cassette
4. Insert correct fragment into each cassette player
5. When all three are inserted the exit cinematic triggers and the simulation ends

The player should never be stuck permanently. All required items remain in inventory once collected and no puzzle state can be broken by wrong interactions (Hopefully :D).

---

## Controls

| Input | Action |
|---|---|
| WASD | Move |
| Mouse | Look |
| E | Interact / Examine / Collect / Modify |
| F | Toggle UV Flashlight |
| H | Shout (immersion / ambient) |

---

## Interaction Verbs

My game uses exactly three interaction verbs as it was required by the assessment.

First is **Examine**, player inspects an object to read its title and description. This triggers camera focus behaviour and an examination sound effect. Used on notes, clue objects, inspectable items, and environmental details.

Next is **Collect**, player picks up a key item into inventory. The world object is hidden on collection, a pickup sound plays, and a subtitle line of self talk appears on screen. Collected items appear in the HUD inventory slots.

**Modify** is where it allows to change the state of the world. At least one Modify interaction per puzzle is gated by a examine or collect. Successful Modify actions trigger visible world state changes, audio feedback, and Niagara particle effects.

---

## Puzzle Overview

### Puzzle 1 — Kitchen: Combination Lock
Located in the kitchen. The player must find a series of numbers hidden on objects around the kitchen, printed on items, written in notes. These numbers form a combination. The player enters the combination into a scifi keypad hidden behind the kitchen counter. Solving it opens a hidden compartment and reveals first cassette fragment.

### Puzzle 2 — Living Room: UV Painting Rotation
Located in the living room. Four paintings hang on the wall. Using the UV flashlight (F key) the player reveals hidden markings on the walls that indicate the correct orientation for each painting. The player interacts with each painting to rotate it to the correct position. When all four paintings match the UV clues, a sound plays and the second cassette fragment spawns in the room.

### Puzzle 3 — Bathroom: Break the Glass
Located in the bathroom. The third cassette fragment is sealed inside a glass display case. The player must find a blunt object elsewhere in the apartment, collect it, and use it to smash the glass case open. This is a gated Modify interaction, the glass cannot be broken without first collecting the correct item. Solving it reveals the third cassette fragment.

### Final — Cassette Players
Three cassette players are placed around the apartment. Each accepts only its matching fragment. Inserting all three triggers the ending cinematic, disables player input, and plays the simulation collapse sequence revealing the space station corridor beyond the fake apartment walls.

---

## Required Unreal Engine Features

### Niagara VFX
`NS_CassetteInsert` I added a simple glitch effect to the cassette players. It triggers on successful fragment input, which directly tied to a modify interaction completing. The effect produces a short burst of bright glitch style sparks at the cassette slot, providing clear world state feedback that the insertion was accepted. This is good for gameplay feedback effect rather than just an ambient decoration.

### Camera Sequence
`SEQ_Ending` is my Level Sequence that triggers when all three cassette players are activated. The sequence cuts to Cine Camera Actor positioned to reveal the exit area, plays through the simulation collapse, and presents the final reveal of the space station corridor beyond the apartment walls. Player input is disabled before the sequence plays and the HUD is removed.

---

## Stage 1 Reflection

For Stage 1 I had the apartment set in a more generic space, somewhere between a bunker and just a standard room. The visual direction was not really decided yet. I was completely unsure about layout, puzzles and the overall concept that would make it captivating, some twist. 

After getting feedback I pushed it toward a proper 1990s retro apartment, teal cabinets, CRT TV, diner furniture, worn wallpaper. That decision changed a lot. Once the setting had a specific decade behind it, the sci-fi elements I was adding like the keypad, the cassette players, the UV markings started feeling genuinely out of place rather than just decorative. That contrast is what the whole experience relies on.

I also changed the narrative framing. Originally the space was described as a bunker style test chamber. I shifted it to a space station simulation, which gave the ending more payoff. When the door opens and shows a corridor that clearly is not an apartment, it lands harder if the player already understands they were never on Earth to begin with and everything was fake all along.

Both changes came from the same realisation, the more specific the world, the more wrong things feel when the simulation starts breaking.

---

## Third-Party Assets and References

### Fab Asset Packs

Fab (2024). *Bodycam Backroom VHS Effect*. Fab. Available at: https://www.fab.com/listings/14e5f29e-26eb-4b7c-82c6-e48e43fd1276 [Accessed 17 May 2025].

Fab (2024). *Mid-Poly Cassette Player – Retro Audio Device*. Fab. Available at: https://www.fab.com/listings/ddc5291c-9d3b-4ab2-a0f7-b8953b4ff977 [Accessed 17 May 2025].

Fab (2024). *Mission to Minerva*. Fab. Available at: https://www.fab.com/listings/1b2deaf4-ab44-4857-a8c9-35b34546c408 [Accessed 17 May 2025].

Fab (2024). *PS1 Style Low Poly Moon*. Fab. Available at: https://www.fab.com/listings/88b7faea-1be0-4c56-80ec-de659308b033 [Accessed 17 May 2025].

Fab (2024). *Sci-Fi Laboratory — Modular Environment Pack*. Fab. Available at: https://www.fab.com/listings/2c22570b-fb29-4742-a1cd-5a86dd911e2a [Accessed 17 May 2025].

Fab (2024). *Stylized House Interior (Kitchen Interior)*. Fab. Available at: https://www.fab.com/listings/ab92e5d3-6db6-4cf3-bff5-c2c98ae8db5b [Accessed 17 May 2025].

Fab (2024). *Survival Character FREE*. Fab. Available at: https://www.fab.com/listings/11d20d01-b764-4936-8163-cb20d05c369e [Accessed 17 May 2025].

Fab (2024). *UV Reveal Flashlight System*. Fab. Available at: https://www.fab.com/listings/03b9d0ae-6ac6-40a4-aace-0059496b3d9c [Accessed 17 May 2025].

### Video Tutorials

HalbotStudios (2024). *How to Create an Interaction System in Unreal Engine 5 | UE5 Interaction Tutorial*. YouTube, 12 September. Available at: https://www.youtube.com/watch?v=7OmgBa-cKro [Accessed 19 May 2025].

(2024). *Create Interaction Icons in Unreal Engine 5 | Step-by-Step*. YouTube. Available at: https://www.youtube.com/watch?v=G855RdtBEak [Accessed 19 May 2025].

### Sound Effects

Pixabay (2024). *Chair Sliding on Carpet — Sound Effect*. Pixabay. Available at: https://pixabay.com/sound-effects/film-special-effects-chair-sliding-on-carpet-90262/ [Accessed 20 May 2025].

Pixabay (2024). *Film Special Effects — Take It*. Pixabay. Available at: https://pixabay.com/sound-effects/film-special-effects-take-it-90781/ [Accessed 20 May 2025].

Pixabay (2024). *Glass Breaking Sound Effect*. Pixabay. Available at: https://pixabay.com/sound-effects/film-special-effects-glass-breaking-sound-effect-240679/ [Accessed 20 May 2025].

Pixabay (2024). *Going to the Next Level — Sound Effect*. Pixabay. Available at: https://pixabay.com/sound-effects/film-special-effects-going-to-the-next-level-114480/ [Accessed 20 May 2025].

Pixabay (2024). *Magic Charge Mana — Sound Effect*. Pixabay. Available at: https://pixabay.com/sound-effects/film-special-effects-magic-charge-mana-2-186628/ [Accessed 20 May 2025].

### Engine Documentation

Epic Games (2025). *Blueprint Visual Scripting*. Unreal Engine 5 Documentation. Available at: https://docs.unrealengine.com/5.0/en-US/blueprints-visual-scripting-in-unreal-engine/ [Accessed 17 May 2025].

Epic Games (2025). *Level Sequences and Cinematics*. Unreal Engine 5 Documentation. Available at: https://docs.unrealengine.com/5.0/en-US/cinematics-and-movie-making-in-unreal-engine/ [Accessed 19 May 2025].

Epic Games (2025). *Niagara Visual Effects System*. Unreal Engine 5 Documentation. Available at: https://docs.unrealengine.com/5.0/en-US/niagara-visual-effects-system-in-unreal-engine/ [Accessed 18 May 2025].

Epic Games (2025). *Substrate Materials*. Unreal Engine 5 Documentation. Available at: https://docs.unrealengine.com/5.0/en-US/substrate-materials-in-unreal-engine/ [Accessed 18 May 2025].

---

## Known Issues

- Some items are hard to interact with, requiring specific positioning, either going further from it or angling.
- Navigation can be hard without prior reading of notes scattered around the map, which help with guidance a bit.
