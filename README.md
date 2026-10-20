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

- **Calligraphic line** (on by default): the line swells and thins like a broad-nib pen.
- **Strokes**: slender tapered strokes running parallel to the line on the outside of each bend (the default), ticks, a ladder (strokes on both sides), feathered strokes that taper toward the ends, or a double line.
- **In the pattern**: stars, dots, moons, crescents and small Eyes of Horus that grow out of the line on thin tendrils, at its corners, past its end and beside it, with one more in its hollow. A crescent cups the start ring, and small stars tip the end bar.
- **Eye**: the Eye of Horus (wadjet) or the Eye of Providence. It sits at the top of the frame, or appears large and faint behind the sigil.
- **Ring ornament**: the eight moon phases, the seven classical planets, the twelve zodiac signs, sun rays or stars. The word's letters decide where the ring starts, so each word gets its own arrangement.
- **Crescents and stars** at the four quarters and diagonals, outside the frame.

## Drawing

On screen the sigil is drawn as a pen would draw it. The frame comes first. Then the pen sets down at the start ring and travels the line, and the parallel strokes appear as it passes. Each ornament grows out of the line and is drawn stroke by stroke. Ornaments are pure line work, with hatching where a shape would otherwise be filled. **Draw again** replays the drawing. Exports are always the finished image.

## Фабрика вероятностей (прототип)

`factory/index.html` is a separate prototype: an incremental game about automating chance. Open it in a browser; it needs no build either.

You build a recipe from machines (reroller, max of two, summator) on top of a die. Income is the expected value of the output times the roll rate. Distributions are computed exactly; outcomes are really random, and the histogram on screen converges to the theoretical curve. Precision contracts pay for a low σ/E, and prestige resets the factory for bits earned by the entropy it produced. After research, a betting table lets you bet on the mean of the next M outputs against a bookmaker whose estimate lags behind your recipe and carries sampling noise; the Kelly research computes the optimal stake and can bet automatically. A second prestige, Asymptote, awards α for every order of magnitude of outputs (from 10⁷); α makes an unchanged recipe "age" into an income multiplier and boosts bits. The Galton board research drops each outcome through a peg triangle along an honest path into its histogram bucket. Add `?speed=50` to the URL to speed up time for testing.
