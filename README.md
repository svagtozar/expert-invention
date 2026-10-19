# Sigillum

Sigillum turns a word or an intention, in Russian or English, into a sigil. The same word always gives the same sigil.

Open `index.html` in a browser. There is no build step and nothing to install. You can also serve the folder with `python3 -m http.server` and open http://localhost:8000.

## How a sigil is made

1. **Letters.** The text is uppercased. Ё becomes Е and Й becomes И. Ъ, Ь, spaces, digits and punctuation are dropped. The app keeps the alphabet that has the most letters in the text and ignores letters from the other one.
2. **Reduction (Austin Spare's method).** Vowels are removed: `AEIOU` in English, `АЕИОУЫЭЮЯ` in Russian. If the word has no consonants, its vowels are kept. Then repeated letters are removed, keeping each letter's first appearance. For example, Свобода → СВБД and Courage → CRG.
3. **Placement on a circle.** Pick one of three methods:
   - **Rose wheel**: the alphabet is spread over three concentric rings.
   - **Weave**: the whole alphabet sits on one circle.
   - **Numerology**: each letter becomes a Pythagorean number from 1 to 9, placed on a nine-point circle.
4. **The line.** The remaining letters are joined in order with angular, flowing (Catmull-Rom) or arc segments. The line starts at an open ring and ends with a bar.
5. **Finishing.** You can add mirror or radial symmetry, a frame (ring, double ring, letter ticks or a ring with the word written on it), a glow and an ink colour. You can also show the construction underneath.

Export the result as SVG or as a 2048px PNG, or copy the SVG code.

## Ornaments

These are optional and deterministic, and they are included in every export.

- **Strokes**: short dashes running parallel to the line (the default), ticks, a ladder (strokes on both sides), feathered strokes that taper toward the ends, or a double line.
- **In the pattern**: stars, dots, moons, crescents and small Eyes of Horus placed by the line itself, at its corners, past its ends, beside it and in its hollow. They are placed so they never touch the line.
- **Eye**: the Eye of Horus (wadjet) or the Eye of Providence. It sits at the top of the frame, or appears large and faint behind the sigil.
- **Ring ornament**: the eight moon phases, the seven classical planets, the twelve zodiac signs, sun rays or stars. The word's letters decide where the ring starts, so each word gets its own arrangement.
- **Crescents and stars** at the four quarters and diagonals, outside the frame.
