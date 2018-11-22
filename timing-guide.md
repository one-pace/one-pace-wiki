# Table of Contents

- [1. Grammar](#1-grammar)
  * [1.1. Naming convention](#11-naming-convention)
    + [1.1.1. Devil Fruits](#111-devil-fruits)
    + [1.1.2. Characters](#112-characters)
    + [1.1.3. Events](#113-events)
    + [1.1.4. Locations](#114-locations)
    + [1.1.5. Titles & Epithets](#115-titles--epithets)
    + [1.1.6. Navy Grammar](#116navy-grammar)
    + [1.1.7. Abilities](#117-abilities)
    + [1.1.8. Other](#118-other)
  * [1.2. Sentence spacing](#12-sentence-spacing)
  * [1.3. Honorifics](#13-honorifics)
  * [1.4. Ellipses](#14-ellipses)
  * [1.5. Attacks](#15-attacks)
    + [1.5.1. Fading](#151-fading)
  * [1.6. Character set](#16-character-set)
- [2. Standards](#2-standards)
  * [2.1. Language](#21-language)
  * [2.2. Numbers](#22-numbers)
  * [2.3. Others](#23-others)
- [3. Styling](#3-styling)
  * [3.1. Aegisub Styles](#31-aegisub-styles)
  * [3.2. Lines](#32-lines)
  * [3.3. Credits](#33-credits)

# 1. Grammar
## 1.1. Naming convention
### 1.1.1. Devil Fruits
Translated to English, while keeping the double noun, like Rubber-Rubber Fruit. The hyphen is always present in the name of the fruit and attack. Furthermore, while Japanese names are translated, exceptions are made for specifically Japanese attacks such as Zoro's Onigiri or Katakuri's Mochi.

- Chop-Chop Fruit
- Flower-Flower Fruit
- Memo-Memo Fruit
- Mochi-Mochi Fruit
- Rubber-Rubber Fruit
- Soul-Soul Fruit
- Smoke-Smoke Fruit

### 1.1.2. Characters
- Aladine
- Avalo Pizarro
- Beer VI
- Bell-mère
- Belo Betty
- Binks' Sake
- Black Leg Sanji
- Bon Kurei
- Buchi
- Camie
- Carmel
- Carue
- Catarina Devon
- Charlos
- Charlotte Brûlée
- Charlotte Dragée
- Charlotte Katakuri (Dogtooth is BULLSHIT)
- Charlotte Linlin/Big Mom
- Charlotte Mont d'Or
- Charlotte Yuen
- Chouchou
- Dracule "Hawk Eye" Mihawk
- Eustass "Captain" Kid
- Fishman/Fishmen
- Five Elders
- Flampe
- Fukurou
- Gekko Moriah
- Gomorrah
- Ham Burger
- Hatchan/Hachi
- Iceburg
- Jinbe
- Kaidou
- Kalifa
- Karasu
- Kashi
- King Baum
- Koby
- Kohza
- Lindbergh
- Marshall D. Teach
- Mary Geoise (Mariejois reborn)
- Merman/Mermen
- Morley
- Nefertari
- Pappag
- Portgas D. Ace
- Roshwan Kingdom
- Rosward
- Sadi
- Sanjuan Wolf
- Sentomaru
- Shakuyaku (Shakky nickname)
- Shalria
- Sham
- Shiliew
- Sodom
- Squard
- Sterry
- Vasco Shot

### 1.1.3. Events
 - Summit War

### 1.1.4. Locations 
- Cacao Island
- Cocoyasi Village
- Dressrosa
- Tarai Current
- Water 7
- Wheat Island

### 1.1.5. Titles & Epithets
- Dengeki Blue
- Four Emperors
- (Royal) Warlord(s)
- Pirate King

### 1.1.6. Navy Grammar
- The Navy
- A Navy ship
- Admiral Kizaru
- He's an admiral
- Vice Admiral Smoker
- Smoker is a vice admiral

### 1.1.7. Abilities
- Boundman/Tankman/Snakeman
- Gear Fourth
- Gear Second
- Gear Third

### 1.1.8. Other
- Belly
- Poneglyph
- Transponder Snail

## 1.2. Sentence spacing
Sentences are separated by a single space.

## 1.3. Honorifics
All honorifics are italicized, along with the associated dash.

## 1.4. Ellipses
Lines ending with ellipses (...) must not continue the ellipsis on the following line.

* Correct: `"My name is..."` / `"Luffy!"`
* Incorrect: `"My name is..."` / `"... Luffy!"`

## 1.5. Attacks
### 1.5.1. Fading
*Note: Only relevant to attacks that don't use Karaoke Effects.*

Attack fades are **150 milliseconds** long and should end in an exclamation mark, depending on the vocal exclamation. Example: `{\fad(150,150)}Rubber-Rubber Balloon!`. If there is a pause in the attack, split the line into two, ending the first line in an ellipsis. Both lines should have fading.

## 1.6. Character set
These are the only acceptable characters that can be used in an Aegisub script:
```abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789 -.,;:¨'"/!%&()#´`+```

# 2. Standards
## 2.1. Language
The primary language is U.S. English, mixed with occassional loaned words from Japanese depending on the situation.

## 2.2. Numbers
The number format to follow is `10,500,000.00`.
- Thousand separator: `,`
- Decimal separator: `.`

## 2.3. Others
- Measurement: Metric
- Time: 12-hour clock (AM/PM)
- Temperature: Celsius

# 3. Styling
## 3.1. Aegisub Styles
- Main: The default style.
- Secondary: When two characters are talking over each other, the less apparent dialog uses this style.
- Flashbacks:  For short flashbacks, when the voice has an echo or similar indicating that it's a flashback.
- Thoughts: For dialog where the character is thinking the line.
- Captions: For infoboxes, signs, etc.
- Note: For TL notes and other notes. Appears on top so it can be used in conjunction with other lines.
- Title: Title card text (HD only).
- Title2: Title card text (SD only).
- Credits: Opening credits.
- Narrator: For when the narrator is speaking.

## 3.2. Lines
- Lines may never be over two rows. Lines that exceed two rows should be rephrased or split into two.
- Each line may only contain one character's dialog. If multiple characters are speaking at the same time, use the Secondary style.

## 3.3. Credits
These are the official names of the different roles and credits for the openings:
- Editor
- QCer
- Translator
- Timer
- Visual Effects Artist
- Infobox maker
- Soundtracker
- Raw provider
