# Packet Tracer – Navigate the IOS



## Part 1: Establish basic connections, access the CLI, and explore Help

**1. Console connection**
- Connect **PC1** to **S1** using the **Console** (light-blue) cable.
- On **PC1**: **Desktop → Terminal → OK** (leave defaults).

**2. First prompt**
- Press **Enter** at “Press RETURN to get started!”.
- **Answer:** Prompt is `S1>`.
- **Why:** `>` means user EXEC mode (basic mode).

**3. Using Help at user EXEC**
- Type `?`
  - **Answer:** Command beginning with **C** is **`connect`**.
- Type `t?`
  - **Answer:** **`telnet`, `traceroute`**.
- Type `te?`
  - **Answer:** **`telnet`**.
- **Why:** IOS help is context‑sensitive—the more letters you type, the narrower the list.

---

## Part 2: Explore EXEC modes

**1. Move to privileged EXEC**
- At `S1>`, type `en<Tab>` → **`enable`** (Tab auto‑completes).
- **What would `te<Tab>` do?** → **`telnet`**.
- Enter `enable`.
  - **Answer:** Prompt changes from **`S1>`** to **`S1#`**.
  - **Why:** `#` means privileged EXEC (more commands unlocked).
- At `S1#`, type `c?` (or `?` and scan):
  - **Answer (examples of new C-commands):** `clear`, `clock`, `configure`, `connect`, `copy` (there are many more here than in user EXEC).

**2. Enter global configuration**
- At `S1#`, type `configure` (or `conf`).
  - **Answer (message shown):** `Configuring from terminal, memory, or network [terminal]?`
- Press **Enter** to accept **[terminal]**.
  - **Answer (prompt):** `S1(config)#`.
- Type `exit` to return to `S1#` when done.

---

## Part 3: Set the clock

**1. Show and set time**
- At `S1#`, type `show clock`.
  - **Answer:** Shows current time; the **year is typically 1993** if the clock hasn’t been set.
- Type `clock` alone:
  - **Answer:** `% Incomplete command.` (needs more info.)
- Type `clock ?`:
  - **Answer:** `set  Set the time and date`.
- Type `clock set ?`:
  - **Answer:** Prompts for `hh:mm:ss` (24‑hour time).
- If you type only `clock set` and press Enter:
  - **Answer:** `% Incomplete command.`

**2. Example full setting**
- Enter the complete command:
  ```
  S1# clock set 15:00:00 31 Jan 2035
  ```
- Verify:
  ```
  S1# show clock
  ```
  - **Answer:** Time now reads around `15:00:xx UTC Tue Jan 31 2035` (seconds will vary).

**3. Practice common errors**
- `cl<Tab>` → **Answer:** auto‑completes to `clock`.
- `clock` → **Answer:** `% Incomplete command.`
- `clock set 25:00:00` → **Answer:** Error (hour out of range; valid is 00–23).
- `clock set 15:00:00 32` → **Answer:** Error (day out of range; must form a valid date).

---

## Quick recap 
- **Modes are like game menus:**
  - `S1>` look only; `S1#` you’re the boss; `S1(config)#` you change settings.
- **`?` = built‑in hint button.** Use it anywhere to see options.
- **Tab** finishes a unique command for you.
- The clock task teaches how to read errors and build commands step by step.

---

## Handy mini‑cheat sheet
```
User EXEC → Priv EXEC → Global Config
S1> enable        → S1#
S1# configure     → S1(config)#

Help & completion
?                 # list commands here
te?               # show commands starting with 'te'
<Tab>             # auto-complete unique command

Clock examples
show clock
clock set HH:MM:SS DAY MON YEAR
clock set 15:00:00 31 Jan 2035
```

