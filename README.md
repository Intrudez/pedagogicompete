# Board Quiz: team quiz game for the smart board

## What is in this folder

```
sinif-yarismasi/
  index.html                  the game (open this)
  lib/xlsx.full.min.js        reads Excel files (keep it next to index.html)
  fonts/                      the game's fonts, so it looks the same offline (keep it next to index.html)
  assets/
    sounds/                   put your own sound files here (optional)
    celebration.mp4           optional "perfect team" video (you add it)
  sets/
    sets.json                 list of question folders (only needed online)
    grade7-theme1-set1/       Theme 1, set 1 (30 questions, 7 with pictures)
      questions.xlsx          the question list
      grandpa.jpg, lily.jpg … the pictures used in picture questions
      tall_short.png          a picture used as a clue
    grade7-theme1-set2/       Theme 1, set 2 (30 questions, 7 with pictures)
```

## Smart board (Pardus ETAP)

The game is made for the 1920×1080 working area that ETAP boards give the browser (Full HD boards at 100%, 4K boards at 200%). Every question fits on one screen without scrolling, with or without the browser toolbar, for 1 to 10 teams. Press F11 in Firefox for full screen.

## How to open the game

**From a USB stick, no internet:** double-click `index.html`. Press **Open a question folder…**, choose a folder like `sets/grade7-theme1-set1` (or the whole `sets` folder to see every list).

**From GitHub Pages, with internet:** open the game's web address. Every list in `sets/sets.json` appears automatically.

## How a game runs

1. Choose the question list. The game shows how many questions loaded and lists any rows it had to skip and why.
2. Choose the number of teams (1 to 10). The game uses the largest number of questions that divides equally between the teams.
3. Choose jokers per team (0 to 5), how many extra seconds a joker gives, and whether the 50:50 joker is on.
4. Choose seconds per question, turn order (Team 1, 2, 3 … again, or finish one team then the next), shuffle, and whether clues are on.
5. Type the team names. Enter jumps to the next name.

Each turn: the student comes to the board and presses **NEXT**. Only then the question appears and the timer starts.

| Event | Points |
|---|---|
| Teacher presses **Read aloud +50** (press again to undo) | +50 |
| Correct answer | +100 |
| Correct answer after buying the **CLUE** | +50 |
| Wrong answer or time is up | 0 (the wrong option turns red, the correct one green) |
| **Joker** | team may help out loud, timer gets extra seconds |
| **50:50** | the team pays 50 points, 2 wrong options disappear (once per question, needs at least 50 points) |

**Pause ■** turns the screen fully black and stops the timer. On the pause screen you can give or take 50 points from any team, turn clues or sounds on and off, or end the game early. The key **P** also pauses and resumes.

If a team answers all of its questions correctly, the celebration plays in the middle of the screen and fades away.

At the end: the final scores, then **Missed questions** shows every wrongly answered or timed-out question so you can solve them with the class (**Show answer** turns the correct option green).

## Adding and removing questions

Open `questions.xlsx` in Excel, LibreOffice or Google Sheets (download as .xlsx). One row is one question.

| Column | What to write |
|---|---|
| question | The question text. May be empty if `question_media` asks the question. |
| question_media | File name of a picture, GIF or video in the **same folder**, e.g. `girl1.jpg`, `dance.gif`, `clip.mp4`. |
| A, B, C, D, E, F | The options. Use 2 to 6, leave the rest empty. |
| answer | The letter of the correct option. |
| clue | Text shown when the student buys the clue. |
| clue_media | Picture, GIF or video file name in the same folder, shown as the clue. |

- Delete a row to remove a question. Add a row to add one.
- No clue and no clue_media: the CLUE button is hidden for that question.
- Keep the column names in row 1. Only the first sheet is read.
- CSV also works (comma or semicolon). Excel files are safer for Turkish characters.

## Making a new question list

1. Copy the `grade7-theme1-set1` folder and rename it, e.g. `grade8-theme1`.
2. Edit `questions.xlsx` and put the pictures and videos for this list in the same folder.
3. Online only: add a line to `sets/sets.json`:

```json
[
  { "name": "Grade 7 · Theme 1 · Set 1", "folder": "grade7-theme1-set1" },
  { "name": "Grade 8 · Theme 1 · Friendship", "folder": "grade8-theme1" }
]
```

On a USB stick you can skip step 3 and use **Open a question folder…**.

## Sounds and the celebration video

The game has built-in sounds. To use your own, put MP3 files with these exact names in `assets/sounds/`:

| File | When it plays |
|---|---|
| `question.mp3` | a question appears |
| `tick.mp3` | every second of the timer |
| `thinking.mp3` | optional background music that loops while the timer runs (ticks then play only in the last 5 seconds) |
| `correct.mp3` | correct answer |
| `wrong.mp3` | wrong answer |
| `timeup.mp3` | time is up |
| `joker.mp3` | joker used |
| `clue.mp3` | clue bought |
| `celebration.mp3` | perfect team and final scores |

Any file you don't add uses the built-in sound.

For the perfect-team celebration, put `celebration.mp4` (or `.webm` or `.gif`) in `assets/`. A list folder can have its own `celebration.mp4`, which wins over the one in `assets/`. Without a file, the game shows "PERFECT!" with confetti.

If a picture shows "File not found", check that the file name in Excel matches the file exactly, including .jpg or .png.
