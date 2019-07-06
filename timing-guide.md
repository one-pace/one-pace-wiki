## Lines
## Line length
Lines may never be over two rows. Lines that exceed two rows should be rephrased or split into two.

## Character dialogue
Each line may only contain one character's dialog. If multiple characters are speaking at the same time, use the Secondary style.

## Infoboxes
### Dialogue
1. For dialogue during infoboxes and captions, if the dialogue line is one line, put it under the infobox with vertical alignment `0`.
2. If the dialogue line is two lines. Place it at the top with `\an8`.

### Captions
1. Captions are to use the `Captions` style (See above).
2. For character infoboxes that are placed bottom centre, put the captions above the infobox, closely matching the line breaks and the font sizes in the Japanese text inside the infobox.
3. For location infoboxes, make sure the caption fits horizontally within the infobox, then place it either above or below the infobox (never to the side). Make sure the font size and line breaks match the Japanese text inside the infobox.

## Italics
Some lines sometimes have wrapped italics (Especially thoughts). Make sure to remove these since the Thoughts style itself manages styling such as italics. To remove wrapped italics in Aegisub, select the lines with the wrapped Italics and press Ctrl+H. Tick "Use regular expressions" and "Limit to Selected Rows", and in the "Find what" textbox, input this regex: `(^\{\\i(1|0)?\}|\{\\i(1|0)?\}$)`.
