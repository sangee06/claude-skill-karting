# Track Knowledge Reference

KartSan has knowledge of karting tracks across Europe and can research tracks worldwide.
This reference covers how to use track information in coaching and dashboards.

---

## Table of contents

1. [Identifying a track](#1-identifying)
2. [Track visualization in dashboards](#2-visualization)
3. [Corner-by-corner coaching](#3-corner-coaching)
4. [Major European karting circuits](#4-european-tracks)
5. [Researching unknown tracks](#5-researching)

---

## 1. Identifying a track

When a user mentions a track, identify it from context:
- Track name (e.g., "Zuera", "Genk", "Lonato")
- City/country (e.g., "the track in Portimão")
- Series context (e.g., "the RMCGF venue this year")
- If unclear, ask: "Which track are you at?" / "Qual kartódromo?"

If the user provides GPS data from MyChron or TRAX, you can identify the track
from the GPS coordinates and track shape.

---

## 2. Track visualization in dashboards

### SVG track map generation

When building dashboards, include an SVG representation of the track. The track map
should be:

- **Drawn as a simplified top-down outline** of the circuit
- **Sector boundaries marked** with colored zones
- **Corners numbered** (matching the track's official numbering if available)
- **Interactive** — hover over a corner for a tooltip with:
  - Corner name/number
  - Type (hairpin, sweeper, chicane, etc.)
  - The driver's average speed through that corner
  - Comparison to their best lap
  - Coaching tip for that corner

### Performance overlay

Color-code the track map based on the driver's performance:

- **Green sections:** Within 0.1s of best sector/corner time (consistent, fast)
- **Yellow sections:** 0.1-0.3s off best (room for improvement)
- **Red sections:** >0.3s off best (priority area for coaching)
- **Gold star/icon:** Personal best sector was set here

This gives the driver an instant visual of where they're strong and where to focus.

### Implementation approach

For the SVG track, you have two options:

**Option A: Simple geometric track**
Draw from corner descriptions — hairpins as tight curves, sweepers as long arcs,
straights as lines. This is approximate but works for any track.

```svg
<svg viewBox="0 0 800 600">
  <!-- Track outline as path -->
  <path d="M100,300 L300,300 Q350,300 380,270 ..."
        stroke="#333" fill="none" stroke-width="20"/>
  <!-- Sector colors as overlay paths -->
  <!-- Corner markers as circles with labels -->
  <!-- Tooltips via title elements or JS hover -->
</svg>
```

**Option B: GPS-derived track**
If the user's telemetry includes GPS coordinates, plot the actual racing line
as the track outline. This is more accurate and shows the real track shape.

```javascript
// Convert GPS coordinates to SVG path
const points = gpsData.map(p => projectToSVG(p.lat, p.lng));
const path = `M ${points.map(p => `${p.x},${p.y}`).join(' L ')}`;
```

Prefer Option B when GPS data is available. Fall back to Option A otherwise.

### Corner annotation format

Each corner annotation should include:

```javascript
{
  number: 3,
  name: "Turn 3 / Curva 3",
  type: "Medium-speed right-hander",
  coachingTip: "Brake at the 3-board, turn in at the cone",
  driverAvgSpeed: 58.2,  // km/h
  bestLapSpeed: 61.5,    // km/h
  gap: -3.3,             // km/h slower than best
  priority: "yellow"     // green/yellow/red
}
```

---

## 3. Corner-by-corner coaching

When the track is known, provide corner-specific coaching tied to the data.
Structure for each corner:

### Corner analysis template
```
Corner [N]: [Name] — [Type: hairpin/sweeper/chicane/etc.]

Data says:
- Average speed: X km/h (best lap: Y km/h, gap: Z km/h)
- Time lost here: ~0.Xs per lap vs. best
- RPM at entry: X / exit: Y (best lap: A / B)

What to do:
- [Specific instruction: "Brake 1m later" / "Tighter apex" / etc.]

Why:
- [Explanation: "You're scrubbing speed by braking too early"]

What to feel:
- [Sensory cue: "The kart should feel lighter on the inside as you apex"]

Tell me after:
- [Feedback request: "Did you gain or lose confidence at this corner?"]
```

---

## 4. Major European karting circuits

Below are well-known European karting tracks that frequently host Rotax events.
For each, key characteristics that affect coaching:

### Southern Europe

**Kartódromo Internacional do Algarve — Portimão, Portugal**
- Length: ~1,530m. Technical with elevation changes.
- Notable: Long back straight, several tricky slow corners.
- Conditions: Hot in summer, wind can be a factor.

**Zuera International Circuit — Zuera, Spain**
- Length: ~1,700m. Fast and flowing.
- Notable: Long straights suit taller gearing. High-speed corners
  demand confidence and commitment.
- Hosted: Multiple RMCGF editions.

**Circuito Internazionale Napoli — Sarno, Italy**
- Length: ~1,699m. Technical with a mix of corner types.
- Notable: Tight hairpins and flowing sections. Good test of
  all-round driving skill.

**South Garda Karting — Lonato, Italy**
- Length: ~1,200m. Very popular for international events.
- Notable: Technical layout, heavy traffic in races.
- Hosted: Multiple FIA and Rotax events.

**Circuito Internazionale di Adria — Adria, Italy**
- Length: ~1,302m. Mix of fast and slow corners.
- Conditions: Can be dusty, grip evolves through the day.

### Northern/Central Europe

**Genk Karting Circuit — Genk, Belgium**
- Length: ~1,360m. Fast, flowing, demanding.
- Notable: High-speed corners require commitment and good chassis setup.
- Hosted: Multiple WSK and CIK-FIA events.

**PF International — Grantham, UK**
- Length: ~1,382m. Technical, cold weather challenge.
- Notable: Elevation changes, tricky mid-speed corners.

**Wackersdorf — Wackersdorf, Germany**
- Length: ~1,190m. Technical layout.
- Notable: Challenging in wet conditions.

**Kristianstad — Kristianstad, Sweden**
- Length: ~1,327m. European Championship venue.
- Notable: Long straights, heavy braking zones.

### Track-specific gearing notes
- Fast tracks (Zuera, Genk): Taller gearing, top-speed matters
- Technical tracks (Sarno, Lonato): Shorter gearing, acceleration matters
- Mixed tracks (Portimão, Kristianstad): Mid-range, tune based on RPM data

---

## 5. Researching unknown tracks

If the user mentions a track you don't have detailed information about:

1. **Ask for details:** "Can you describe the track? How many turns, any long
   straights, tight hairpins?"
2. **Check if they have GPS data:** "If you've done a session there, the MyChron
   GPS trace will tell me the layout."
3. **Search if needed:** Use web search to find the track layout, length, and
   characteristics.
4. **Build from GPS:** If they provide telemetry with GPS coordinates, you can
   reconstruct the track shape and create the visualization from data alone.

For tracks outside Europe:
- Many tracks worldwide host Rotax events — the RMCGF (Grand Finals) rotates
  locations globally
- Track characteristics (grip level, surface type, elevation) vary significantly
  by region
- Always ask about local conditions: surface type, ambient temperatures,
  altitude (affects jetting)

### Track data sources
- Official track websites
- Google Maps/Earth satellite view for layout confirmation
- Race results from previous events at the venue
- Karting community forums and track guides
- User's own GPS telemetry data (best source for actual layout)
