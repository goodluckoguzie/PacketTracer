# Packet Tracer – Navigate the IOS Using a Terminal Client for Console Connectivity (Physical Mode)



## Part 1: Access a Cisco Switch through the Serial Console Port

**Q (Step 1): Which IOS image and version is currently in use by the switch?**

**A:** `C2960-LANBASE-M, Version 12.2(25)FX`  
**Why:** That is the IOS image/version shown by the `show version` output in this activity.

---

## Part 2: Display and Configure Basic Device Settings

**Show the current time**
```
Switch> show clock
```
_Typically shows a default 1993 date if the clock hasn’t been set._

**Enter privileged EXEC**
```
Switch> enable
Switch#
```

**Use context help to set the clock**
```
Switch# clock set ?
  hh:mm:ss  Current Time
Switch# clock set 15:28:00 ?
  <1-31>  Day of the month
  MONTH   Month of the year
Switch# clock set 15:28:00 Nov 11 ?
  <1993-2035>  Year
Switch# clock set 15:28:00 Nov 11 2020
```

**Verify**
```
Switch# show clock
15:28:xx UTC Wed Nov 11 2020
```

**Notes for a 14‑year‑old learner**
- `?` = built‑in help; shows you what comes next.
- `enable` moves you to boss mode (`#`).
- Dates must be valid (e.g., hour 00–23, day 1–31).

---

## Part 3: Access a Cisco Router Using a Mini‑USB Console Cable

**After boot, exit setup dialog**
```
Would you like to enter the initial configuration dialog? [yes/no]: n
Press RETURN to get started!
Router>
```

---

## Reflection Questions

**1) How do you prevent unauthorized personnel from accessing the Cisco device through the console port?**
- Set a console password and require login:
  ```
  Switch# conf t
  Switch(config)# line console 0
  Switch(config-line)# password <STRONG-PASSWORD>
  Switch(config-line)# login
  ```
- Better: create a local user and use `login local`:
  ```
  Switch(config)# username admin secret <STRONG-SECRET>
  Switch(config)# line console 0
  Switch(config-line)# login local
  ```
- Add an inactivity timeout (auto‑logout):
  ```
  Switch(config-line)# exec-timeout 5 0   ! 5 minutes
  ```
- Physically secure the device (locked room/cabinet) so no one can plug into the console.

**2) Serial RS‑232 vs USB console – advantages & disadvantages**
- **Serial (RS‑232) rollover cable**
  - ✅ Very stable; no drivers; can work over longer distances.
  - ❌ Many modern laptops lack RS‑232; needs a USB‑to‑serial adapter; bulky connectors; slower.
- **USB console (mini‑USB/USB‑C)**
  - ✅ Ubiquitous on laptops; simple cable; fast.
  - ❌ Often needs the right driver; shorter reliable cable length; occasionally finicky with OS power/port settings.

---

## Mini‑Cheat Sheet
```
Enter privileged mode:    enable  → prompt ends with #
Enter global config:       configure terminal  → (config)#
Show version:              show version
Show/Set clock:            show clock
                           clock set HH:MM:SS DAY MON YEAR
Example:                   clock set 15:28:00 Nov 11 2020
Help:                      ?   (context‑sensitive)
Auto‑complete:             <Tab>
```

