# Performance Engineering Reference

This guide covers the mechanical and setup side of making a Rotax kart faster.
All recommendations must be cross-checked against `references/rotax-regulations.md`
before suggesting to the user.

**CRITICAL PATTERN:** Every setup recommendation must follow the Why-Observe-Report format:
- **Why:** Explain the reason for the change
- **What to observe:** What the driver/parent should look for after the change
- **Report back:** What data/feedback to bring back for next analysis

This teaches the driver and parent to think like engineers and builds a feedback loop
that makes each session more productive than the last.

---

## Table of contents

1. [Chassis tuning fundamentals](#1-chassis-tuning)
2. [Tire management](#2-tire-management)
3. [Gearing](#3-gearing)
4. [Engine and carburettor tuning](#4-engine-tuning)
5. [Data-driven diagnosis](#5-data-driven-diagnosis)
6. [Setup notebook methodology](#6-setup-notebook)
7. [Weather and conditions](#7-weather-adaptations)
8. [Kart-specific considerations](#8-kart-specific)

---

## 1. Chassis tuning

### How a kart turns
Karts have no differential. To turn, the inside rear wheel must lift off the ground
so the outside wheel can drive the kart through the corner. Everything about chassis
setup is about controlling when and how much the inside rear lifts.

### Key adjustments and their effects

#### Seat position
- **Forward:** More front grip, less rear grip. Kart turns in better but may slide
  on corner exit. Good for tight, technical tracks.
- **Backward:** More rear grip, less front grip. Kart is more stable on exit but
  may push (understeer) on entry. Good for high-speed flowing tracks.
- **Height:** Higher seat = higher center of gravity = more weight transfer = more
  inside-rear lift. Lower = more stable, less rotation.
- **Typical adjustment:** 5-10mm increments. Never move more than 10mm at a time.

#### Rear track width
- **Wider:** More rear grip, more mechanical lift of inside wheel. Good for
  low-grip conditions or when the kart won't rotate.
- **Narrower:** Less rear grip, kart rotates more freely. Good for high-grip
  conditions or when the kart is oversteering.
- **Typical range:** 5-10mm per side adjustments.

#### Front track width
- **Wider:** More initial turn-in response. Can make the kart nervous mid-corner.
- **Narrower:** Smoother, more progressive turn-in.

#### Axle stiffness
Cadet karts often have axle options (soft, medium, hard):
- **Soft axle:** More rear flex, less grip transfer, smoother. Good for high-grip,
  hot conditions where the kart has too much snap.
- **Hard axle:** More direct, more responsive, snappier. Good for low-grip or cold
  conditions where you need maximum mechanical grip.
- **In between:** Medium for normal conditions or as a safe starting baseline.

#### Ride height (front and rear)
- **Raise front:** More front weight, quicker turn-in, can cause instability.
- **Lower front:** More stable entry, slower turn-in.
- **Raise rear:** More weight transfer, more lift, can help rotation.
- **Lower rear:** More stability, less rotation.

#### Caster
- **More caster (more trail):** Increases jacking effect (inside-rear lift). More
  front grip on initial turn-in. Better for low-grip conditions.
- **Less caster:** Reduces jacking, more stable on high-grip tracks.

### Setup baseline

Always start from a known baseline for the driver's specific chassis. Record it:

| Parameter | Baseline value | Notes |
|---|---|---|
| Front track width | [record] | Measure center-to-center at spindle |
| Rear track width | [record] | Measure center-to-center at hub |
| Seat position fore/aft | [record] | Measure from rear axle center |
| Seat height | [record] | Measure from frame rail |
| Front ride height | [record] | |
| Rear ride height | [record] | |
| Caster setting | [record] | Pill position if applicable |
| Axle type | [record] | Soft/medium/hard |
| Front bar | [record] | Fitted/removed |

Ask the user for their chassis make/model if not specified — setup recommendations
vary significantly between OTK, CRG, Birel, etc.

---

## 2. Tire management

### Tire pressure fundamentals

Tire temperature builds pressure. Cold pressure is what you set in the pits.
Hot pressure is what matters on track. The relationship:

- Cold-to-hot gain: typically 0.10-0.20 bar depending on compound, track, and conditions
- Target hot pressure varies by compound — always ask what tires the driver is running

### Pressure targets by condition (general MG compound guidelines)

| Condition | Cold pressure (bar) | Target hot (bar) | Notes |
|---|---|---|---|
| **Dry, warm (25°C+)** | 0.80-0.85 | 0.95-1.05 | Lower cold, tires build heat fast |
| **Dry, mild (15-25°C)** | 0.85-0.90 | 1.00-1.10 | Standard starting point |
| **Dry, cold (<15°C)** | 0.90-0.95 | 1.05-1.15 | Higher cold to compensate for slow heat build |
| **Damp/drying** | 0.95-1.05 | 1.10-1.20 | More pressure = less contact patch = less aquaplaning |
| **Wet** | 1.00-1.10 | 1.15-1.25 | Reduced grip, need pressure for structure |

**Adjust based on:**
- the driver's weight relative to the minimum (lighter drivers generate less heat)
- Track surface roughness (rougher = more heat = lower cold pressure)
- Session length (longer sessions = tires get hotter = potentially lower starting pressure)

### Pressure adjustment during a race weekend
1. Set cold pressures before first session
2. Check hot pressures immediately when the driver comes in (within 30 seconds)
3. If hot pressure is too high: lower cold pressure by the overshoot amount
4. If hot pressure is too low: raise cold pressure
5. Record every data point — cold pressure set, hot pressure measured, ambient temp,
   track condition, lap times

### Tire scrubbing
New tires need 3-5 laps of progressive speed to scrub the surface treatment off.
Don't push hard on brand new tires — they're slippery for the first few laps.

### Chemical treatment
**Absolutely forbidden** under Rotax rules. Don't use tire softeners, treatments,
or conditioners. Disqualification and potential ban.

---

## 3. Gearing

### How to read gearing from telemetry

The key indicator is **max RPM on the longest straight**.

| Observation | Diagnosis | Action |
|---|---|---|
| Max RPM well above peak power (~500+ over) | Over-revving — wasting energy above power band | Go taller (fewer teeth on rear sprocket) |
| Max RPM right at or slightly above peak power | Optimal — engine reaches peak and holds | Keep current gearing |
| Max RPM below peak power | Kart can't reach full speed — gearing too tall | Go shorter (more teeth on rear sprocket) |

### Peak power RPM by class
- **Micro MAX:** ~7,000 RPM
- **Mini MAX:** ~7,500 RPM (verify with current engine spec)

### Sprocket changes
- One tooth on the rear sprocket makes a noticeable difference in a Cadet kart
- Going up one tooth (e.g., 80 to 81) = shorter gearing = more acceleration,
  lower top speed, RPM climbs faster
- Going down one tooth (e.g., 80 to 79) = taller gearing = less acceleration,
  higher top speed, RPM climbs slower

### Track-specific gearing
- **Tight, technical tracks:** Shorter gearing (more rear teeth). Acceleration
  matters more than top speed.
- **Fast, flowing tracks:** Taller gearing (fewer rear teeth). Top speed matters.
- **Mixed tracks:** Start with middle gearing and use RPM data to fine-tune.

### Gearing and conditions
- **Wet/damp:** Go 1 tooth taller than dry. Reduces wheel spin on exit.
  With less grip available, you don't need the acceleration of short gearing.
- **Cold track:** May need slightly shorter gearing as grip is lower and
  corner speeds are reduced.

---

## 4. Engine tuning

### Jetting (within regulations)

The carburettor main jet controls the fuel-air mixture at full throttle. This is
the primary tuning variable allowed in Rotax sealed-engine classes.

#### Reading the conditions
| Factor | Effect on mixture | Action |
|---|---|---|
| Higher altitude | Thinner air = mixture goes rich | Go leaner (smaller main jet) |
| Higher temperature | Less dense air = mixture goes rich | Go leaner |
| Higher humidity | Less oxygen in air = mixture goes rich | Go leaner |
| Lower altitude/temp/humidity | Opposite of above | Go richer |

#### EGT (Exhaust Gas Temperature) interpretation
- **EGT too low (below normal range):** Running too rich. Engine feels flat,
  may bog at full throttle. Go one main jet leaner.
- **EGT in normal range:** Good. Leave it.
- **EGT too high (above normal range):** Running too lean. Risk of engine damage.
  **Stop immediately** and go richer. A lean-running engine will seize.

**Normal EGT range for Micro/Mini MAX:** roughly 500-600°C depending on conditions.
If you see EGT consistently above 620°C, richen up immediately. Below 480°C, you're
leaving performance on the table from an overly rich mixture.

#### Needle clip position
The needle controls mixture in the mid-range (partial throttle):
- Clip toward pointed end = richer mid-range
- Clip toward flat end = leaner mid-range
- Start with the manufacturer's recommended position and adjust only if there's
  a specific mid-range issue (hesitation, bog, erratic idle)

#### Spark plug reading
After a session, pull the spark plug and read the insulator color:
- **Light tan/brown:** Optimal mixture
- **White/light grey:** Too lean — richen immediately
- **Dark brown/black/oily:** Too rich — lean out one step
- **Wet/fouled:** Significantly too rich, or ignition issue

### Water temperature monitoring
- **Normal operating range:** 45-65°C for Cadet engines
- **Below 45°C:** Engine isn't up to temperature. May feel flat.
  Check thermostat or add tape to radiator to restrict airflow.
- **Above 65°C:** Engine is running hot. Check coolant level, radiator
  blockage, or airflow. If climbing above 70°C, bring the driver in.
- **Rapid climb:** Could indicate coolant loss, water pump issue, or
  restricted airflow. Safety concern — investigate before running again.

---

## 5. Data-driven diagnosis

### Is it the driver or the kart?

| Pattern in data | Likely cause | Investigation |
|---|---|---|
| All sectors slow equally | Driver (fatigue, confidence) | Check lap-over-lap trend, RPM patterns |
| One sector slow, others fine | Corner-specific issue | Could be driver technique OR handling issue at that corner |
| Speed drops on straights | Engine/gearing | Check max RPM, EGT, water temp |
| Inconsistent sector times (high variance) | Driver inconsistency | Focus on braking points and reference markers |
| Sudden pace drop mid-session | Mechanical (flat tire, loose bodywork) or fatigue | Check temp data for anomalies |
| Slow in all slow corners | Understeer (push) | Chassis adjustment — more front grip or less rear |
| Slow in all fast corners | Oversteer (loose) or lack of confidence | Chassis adjustment — more rear grip or less front |
| Slow out of corners (low exit speed) | Poor throttle application or oversteer on exit | Check RPM trace for late throttle pick-up |
| Fast on entry, slow on exit | Over-braking or too much front grip | Adjust braking technique or chassis balance |

### Comparing fast vs. slow laps

When analyzing telemetry, always overlay the fastest lap against a representative
slow lap. Look for:

1. **Braking point:** Does the driver brake at the same point every lap? Or does he
   brake earlier on slow laps? (Look at speed or RPM drop point on the trace)
2. **Minimum corner speed:** Is it significantly different between fast and slow
   laps? If so, the driving line or entry speed is the issue.
3. **Throttle pick-up:** When does the driver get back on the gas? Earlier = faster.
   If the slow lap has a noticeably later throttle application, that's the gap.
4. **RPM recovery:** How quickly does RPM climb back to peak after a corner?
   Slower recovery = later throttle or different line.

---

## 6. Setup notebook methodology

Encourage the user to maintain a setup notebook. For every session:

```
Date: ___
Track: ___
Conditions: ambient temp ___, track temp ___, humidity ___%, dry/damp/wet
Tire compound: ___
Cold pressures: FL ___ FR ___ RL ___ RR ___
Hot pressures: FL ___ FR ___ RL ___ RR ___
Gearing: Front ___T, Rear ___T
Main jet: ___
Needle clip: position ___
Chassis setup: [any changes from baseline]
Fastest lap: ___
Average lap: ___
Notes: [what worked, what didn't, driver feedback]
Change made: [one thing changed for next session]
```

This creates a history that makes it much easier to make informed decisions.
"Last time it was 18°C and damp we used X and it worked" is far better than
guessing each weekend.

---

## 7. Weather adaptations

### Hot conditions (25°C+)
- Lower cold tire pressures (tires build heat faster)
- Potentially leaner jetting (less dense air)
- Watch water temps closely
- Tape off less of the radiator (or remove tape entirely)
- Hydration is critical for the driver — more water breaks

### Cold conditions (<10°C)
- Higher cold tire pressures (tires struggle to build heat)
- Potentially richer jetting (denser air)
- May need radiator tape to reach operating temperature
- Harder axle may be needed as grip is low
- Wider rear track for more mechanical grip

### Wet/rain
- Switch to wet tires if available (check series rules)
- If running slicks in damp: higher pressures, taller gearing
- Smooth inputs are critical — the driver should brake earlier and more gently
- Avoid painted lines, kerbs, and rubber build-up on the dry line
- The wet racing line is often different — explore off-line grip
- Chassis: soften if possible (soft axle, narrow rear track) for more feel

### Changing conditions (drying track)
- Start with damp setup
- As the track dries, progressively lower tire pressures toward dry settings
- Gearing can be shortened as grip increases
- The transition period is the hardest to get right — be ready to make
  multiple pressure adjustments across sessions
- Watch the times: if the driver's pace plateaus while others improve, the setup
  is behind the conditions

---

## 8. Kart-specific considerations

When the user specifies the driver's kart chassis, tailor advice accordingly.
Different chassis brands have different characteristics:

### Common Cadet chassis brands
- **OTK (Tony Kart, Kosmic, Exprit):** Generally high-grip, responsive. Known for
  being fast out of the box but sensitive to setup changes.
- **CRG:** Slightly more forgiving, good baseline. Popular in Rotax.
- **Birel ART:** Similar to CRG, good all-around.
- **Parolin:** Popular Cadet chassis, competitive at international level.
- **Energy:** Another strong Cadet option.

**Always ask** what chassis the driver runs if not specified — "what brand and model is
your kart?" The same setup change has different effects on different chassis.

### Component upgrades (within regulations)
- Seat: A well-fitted seat makes a huge difference. the driver should be snug but
  comfortable. As he grows, the seat needs to be updated.
- Steering column: Check for play or looseness. Worn bearings affect feedback.
- Wheel hubs: Front and rear hub lengths affect track width — make sure you're
  measuring consistently.
- Pedals: Should be positioned so the driver can reach them comfortably with
  full travel. As he grows, pedal position may need adjustment.
