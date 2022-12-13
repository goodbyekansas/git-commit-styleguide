# Git Commit Styleguide ✨🎉

Styleguide for git commits @ GBK

In general, we follow [this](https://chris.beams.io/posts/git-commit/).

Take me to the [emojis!](#8-categorize-the-type-of-changes-with-one-or-two-of-the-following-emoji)

## Why are we doing this?
In short: "The best commit histories tell an understandable story".

## Summarized in steps:

### 1. Separate subject from body with a blank line

From the git commit manpage:

```
Though not required, it’s a good idea to begin the
commit message with a single short (less than 50 character)
line summarizing the change, followed by a blank line and
then a more thorough description. The text up to the first
blank line in a commit message is treated as the commit
title, and that title is used throughout Git.
For example, Git-format-patch(1) turns a commit into email,
and it uses the title on the Subject line and the rest of the 
commit in the body.
```

### 2. Limit the subject line to 50 characters

50 characters is not a hard limit, just a rule of thumb.
Keeping subject lines at this length ensures that they are
readable, and forces the author to think for a moment about
the most concise way to explain what’s going on.

### 3. Capitalize the subject line

This is as simple as it sounds. Begin all subject lines with a capital letter.

### 4. Do not end the subject line with a period

Trailing punctuation is unnecessary in subject lines.
Besides, space is precious when you’re trying to keep them to 50 chars or less.

### 5. Use the imperative mood in the subject line

Imperative mood just means “spoken or written as if giving a command or instruction”. A few examples:

    - Clean your room
    - Close the door
    - Take out the trash

Each of the eight rules you’re reading about right now are written 
in the imperative (“Wrap the body at 72 characters”, etc.).

The imperative can sound a little rude; 
that’s why we don’t often use it. 
But it’s perfect for Git commit subject lines. 
One reason for this is that Git itself uses the 
imperative whenever it creates a commit on your behalf.
For example, the default message created when using git merge reads:

```
Merge branch 'myfeature'
```

And when using git revert:

```
Revert "Add the thing with the stuff"

This reverts commit cc87791524aedd593cff5a74532befe7ab69ce9d.
```

Or when clicking the “Merge” button on a GitHub pull request:

```
Merge pull request #123 from someuser/somebranch
```

### 6. Wrap the body at 72 characters
Git never wraps text automatically. When you write the body of a commit message, you must mind its
right margin, and wrap text manually.

The recommendation is to do this at 72 characters, so that Git has plenty of room to indent text
while still keeping everything under 80 characters overall.

A good text editor can help here. It’s easy to configure Vim, for example, to wrap text at 72
characters when you’re writing a Git commit. Traditionally, however, IDEs have been terrible at
providing smart support for text wrapping in commit messages (although in recent versions, IntelliJ
IDEA has finally gotten better about this).

### 7. Use the body to explain what and why vs. how
This commit from Bitcoin Core is a great example of explaining what changed and why:

```
commit eb0b56b19017ab5c16c745e6da39c53126924ed6
Author: Pieter Wuille <pieter.wuille@gmail.com>
Date:   Fri Aug 1 22:57:55 2014 +0200

   Simplify serialize.h's exception handling

   Remove the 'state' and 'exceptmask' from serialize.h's stream
   implementations, as well as related methods.

   As exceptmask always included 'failbit', and setstate was always
   called with bits = failbit, all it did was immediately raise an
   exception. Get rid of those variables, and replace the setstate
   with direct exception throwing (which also removes some dead
   code).

   As a result, good() is never reached after a failure (there are
   only 2 calls, one of which is in tests), and can just be replaced
   by !eof().

   fail(), clear(n) and exceptions() are just never called. Delete
   them.
```

Take a look at the full diff and just think how much time the author is saving fellow and future
committers by taking the time to provide this context here and now. If he didn’t, it would probably
be lost forever.

In most cases, you can leave out details about how a change has been made. Code is generally
self-explanatory in this regard (and if the code is so complex that it needs to be explained in
prose, that’s what source comments are for). Just focus on making clear the reasons why you made the
change in the first place—the way things worked before the change (and what was wrong with that),
the way they work now, and why you decided to solve it the way you did.

The future maintainer that thanks you may be yourself!

### 8. Categorize the type of changes with one or two of the following emoji
These are placed at the start of the subject line as `emoji1 [emoji2] The actual subject`.

Use the real emoji character, not the shortcode (🕴not :business_man_in_suit_levitating:)
otherwise the readability of the log gets ruined

|   Commit type              | Emoji                                                                  |
|:---------------------------|:-----------------------------------------------------------------------|
| Initial commit             | 🎉 `:tada:`                                                            |
| Version tag                | 🔖 `:bookmark:`                                                        |
| New Release                | 💎 `:gem:`                                                             |
| New feature                | ✨ `:sparkles:`                                                        |
| Bugfix                     | 🐛 `:bug:`                                                             |
| Metadata                   | 📇 `:card_index:`                                                      |
| Documentation              | 📚 `:books:`                                                           |
| Documenting source code    | 💡 `:bulb:`                                                            |
| Performance                | 🐎 `:racehorse:`                                                       |
| Cosmetic                   | 💄 `:lipstick:`                                                        |
| Tests                      | 🚨 `:rotating_light:`                                                  |
| Adding a test              | ✅ `:white_check_mark:`                                                |
| Make a test pass           | ✔️ `:heavy_check_mark:`                                                 |
| Minor changes              | ⚡ `:zap:`                                                              |
| Improve format/structure   | 🎨 `:art:`                                                             |
| Refactor code              | 🔨 `:hammer:`                                                          |
| Removing code/files        | 🔥 `:fire:`                                                            |
| Continuous Integration     | 💚 `:green_heart:`                                                     |
| Security                   | 🔒 `:lock:`                                                            |
| Upgrading dependencies     | ⬆️ `:arrow_up:`                                                        |
| Downgrading dependencies   | ⬇️ `:arrow_down:`                                                      |
| Lint                       | 👕 `:shirt:`                                                           |
| Translation                | 👽 `:alien:`                                                           |
| Documentation              | 📚 `:pencil:`                                                          |
| Critical hotfix            | 🚑 `:ambulance:`                                                       |
| Deploying stuff            | 🚀 `:rocket:`                                                          |
| Fixing on MacOS            | 🍎 `:apple:`                                                           |
| Fixing on Linux            | 🐧 `:penguin:`                                                         |
| Fixing on Windows          | 🏁 `:checkered_flag:`                                                  |
| Work in progress           | 🚧  `:construction:`                                                   |
| Adding CI build system     | 👷 `:construction_worker:`                                             |
| Analytics or tracking code | 📈 `:chart_with_upwards_trend:`                                        |
| Removing a dependency      | ➖ `:heavy_minus_sign:`                                                |
| Adding a dependency        | ➕ `:heavy_plus_sign:`                                                 |
| Docker                     | 🐳 `:whale:`                                                           |
| Configuration files        | 🔧 `:wrench:`                                                          |
| Packaging files            | 📦 `:package:`                                                         |
| Breaking changes           | 💥 `:boom:`                                                            |
| Code review changes        | 👌 `:ok_hand:`                                                         |
| Accessibility              | ♿ `:wheelchair:`                                                       |
| Other                      | [Be creative](http://www.emoji-cheat-sheet.com/) and add to this list  |
