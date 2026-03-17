# Karting Data Devices & Tools Reference

KartSan is an expert on karting data acquisition. This reference covers the devices
and software commonly used in Rotax karting.

---

## Table of contents

1. [MyChron 5 / 5 2T / 5 S](#1-mychron-5)
2. [MyChron 6 / 6 2T](#2-mychron-6)
3. [Race Studio 3](#3-race-studio-3)
4. [Rotax TRAX](#4-rotax-trax)
5. [Other useful apps and tools](#5-other-tools)
6. [Data export and analysis workflow](#6-data-workflow)
7. [Troubleshooting common issues](#7-troubleshooting)

---

## 1. MyChron 5

### MyChron 5 (base model)
- **Display:** 268x128 pixel graphical, 7 configurable backlight colors
- **GPS:** Built-in, provides track mapping, speed, 3-axis G-forces, lap timing
- **Sensors:** 1 temperature sensor (water or EGT), RPM input
- **Connectivity:** Wi-Fi for configuration and data download
- **Battery:** Rechargeable lithium, ~10 hours
- **Data logged:** Lap times, split times, speed, RPM, temperature, track position,
  acceleration

### MyChron 5 2T
Same as MyChron 5 but with **two temperature sensor inputs**. Ideal for monitoring
both water temperature AND exhaust gas temperature simultaneously. Critical for
proper engine tuning — water temp tells you about cooling, EGT tells you about
fuel mixture.

### MyChron 5 S / 5 S 2T
Upgraded version of MyChron 5:
- **GPS frequency:** 25 Hz (vs ~10 Hz on standard 5). This means position accuracy
  improves from ~5 feet (~1.5m) to ~1.5 feet (~45cm) — significant for comparing
  racing lines between laps.
- **Processor:** Twice as fast, more memory
- **IMU:** 9-axis inertial platform (3-axis accelerometer, 3-axis gyroscope,
  3-axis magnetometer) — enables detailed cornering analysis
- **Math channels:** Additional calculated channels from sensor data

### Setup tips for Cadet racers
- **RPM lead:** Connect to the spark plug lead. Ensure clean signal — a loose
  connection causes RPM dropouts that look like engine problems in the data.
- **Water temp sensor:** Install in the cylinder head water outlet. Standard
  position for consistent readings across sessions.
- **EGT sensor (if 2T model):** Install in the exhaust header, typically 50-80mm
  from the cylinder. Position matters — too close reads high, too far reads low.
  Mark the position so it's consistent.
- **GPS antenna:** Mount high and unobstructed. Under the fairing or on top of
  the steering column mount. Poor GPS placement = noisy speed/position data.
- **Wi-Fi download:** Connect MyChron to Race Studio 3 via Wi-Fi for fastest
  data transfer. Make sure the MyChron and laptop are on the same network.

### Common MyChron 5 display pages
- **Lap time + RPM + Temp** — The standard racing page
- **Split times** — Shows sector times as you cross each split
- **Best lap comparison** — Shows delta to your best lap in real-time
- **Max values** — Max RPM, max speed, max temp for the session

---

## 2. MyChron 6

### MyChron 6 (base model)
The latest generation — significant upgrades over MyChron 5:

- **Display:** 320x136 pixel, 8 configurable RGB backlight colors,
  ambient light sensor for auto-brightness
- **GPS:** 25 Hz, four satellite systems (GPS, GLONASS, BeiDou, Galileo) —
  more satellites = better accuracy in all conditions
- **LEDs:** 5 RGB shift indicator LEDs + 2 configurable alarm LEDs
  (set for temp thresholds, RPM limits, etc.)
- **IMU:** 6-axis inertial measurement unit (accelerometer + gyroscope)
- **Connectivity:** 802.11 Wi-Fi (range up to 50m) + Bluetooth for
  heart rate monitors
- **Battery:** Rechargeable lithium, ~20 hours (double the MyChron 5)
- **Memory:** 4GB (3,000+ hours of data)
- **Heart rate:** Connect any standard Bluetooth heart rate monitor.
  Useful for tracking driver fatigue during sessions.

### MyChron 6 2T
Same as MyChron 6 with two temperature sensor inputs.

### New features on MyChron 6
- **Delta bar animation:** On-screen graphical bar showing real-time delta
  to your best lap. Green = gaining time, red = losing time. This is incredibly
  useful for young drivers — they can see instantly whether they're faster or
  slower than their best.
- **Dedicated split time pages:** Clearer layout for monitoring sector
  performance during a session.
- **Heart rate display:** Live heart rate on screen — helps identify when a
  driver's heart rate spikes (stress, physical effort) and correlate with
  lap time changes.
- **Improved alarms:** LED alarms for temperature thresholds, RPM limits,
  or any channel value. Set an alarm for water temp > 60°C so the driver
  knows to come in.

### MyChron 6 setup recommendations
- Configure the delta bar for best lap comparison
- Set LED shift lights to match the engine's power band peak
- Set alarm LEDs: one for water temp high, one for low RPM warning
- Enable heart rate logging if a Bluetooth monitor is available
- Use the ambient light sensor — auto-brightness is better than manual
  for changing track conditions

---

## 3. Race Studio 3

### Overview
Race Studio 3 is AIM's free data analysis software for Windows (64-bit only,
no Mac native — use Parallels/Boot Camp on Mac). It's the primary tool for
deep telemetry analysis from MyChron devices.

### Key analysis features

**Laps Report:** Quick overview of all laps — times, sectors, max values.
Good for first-pass analysis of a session.

**Laps Summary:** Trend view showing how lap times and key channels evolve
across the session.

**Histogram Layout:** The main analysis view. Includes:
- Channel list (select which data to display)
- Time-distance graph (any channel vs. lap distance or time)
- Track map panel (GPS-derived map of the circuit)
- Overlay capability (compare 2+ laps side by side)

**Channels Report:** Computed statistics (min, max, average) per channel
per lap/split. Useful for spotting trends in RPM, temp, speed.

**Track map features:**
- GPS-based track outline auto-generated from drive data
- Driver line overlay — see the actual path through each corner
- Compare lines between laps (fast vs. slow)
- Download offline maps for when there's no internet at the track

**Math channels:**
Create calculated channels from raw data:
- G-force from accelerometer data
- Speed from GPS coordinates
- Throttle percentage (if throttle sensor fitted)
- Custom formulas for derived metrics

### How to export data for external analysis
1. Connect MyChron via Wi-Fi or USB
2. Open Race Studio 3 → Download
3. Data saved to local database
4. To export as CSV: Open session → File → Export → CSV
5. Select channels and laps to export
6. The CSV can then be uploaded for KartSan analysis

### Tips for getting the most out of Race Studio 3
- **Compare your best and worst laps first.** Overlay them in histogram view.
  The biggest differences show you where time is being lost.
- **Use the track map.** Click on any point on the track map and the histogram
  cursor jumps to that location. Incredibly useful for corner-specific analysis.
- **Create reference laps.** Save your best lap as a reference — every future
  session can be compared against it.
- **Watch the speed trace.** Speed is the most intuitive channel. Dips in speed
  = braking. Recovery = acceleration. The shape tells the story.

---

## 4. Rotax TRAX

### Overview
TRAX is Rotax's own GPS-based data acquisition system. Simpler than MyChron
but integrated with the Rotax ecosystem.

### Hardware
- Compact GPS tracking device
- Built-in SIM card (no phone required for data transmission)
- Mounts on any flat horizontal surface with double-sided tape
- Compatible with any kart with 12V power supply
- Works at most outdoor kart tracks with GPS/cellular coverage

### Data captured
- GPS-based speed
- Lap times and split times
- Acceleration and braking points
- Racing line (from GPS trace)
- G-forces (lateral and longitudinal)

### TRAX App features

**Free tier:**
- Record lap times and distance
- View basic session data
- See other users' stats on the same track

**Pro tier (subscription):**
- **Speed graphs:** Exact speed comparison at every track point
- **Delta-T graphs:** Where you gain or lose time corner by corner
- **G-Force graphs:** Braking, acceleration, and cornering force analysis
- **Driver Score:** Unique metric measuring racing technique independent
  of class or kart speed. Useful for tracking improvement over time.
- **Comparison tools:** Compare sessions, compare to other drivers

### TRAX vs. MyChron
| Feature | TRAX | MyChron 5/6 |
|---|---|---|
| Ease of setup | Very simple | Moderate (sensor wiring) |
| Temperature data | No | Yes (water, EGT) |
| RPM data | No | Yes |
| GPS accuracy | Standard (~2-3m) | High (25Hz on 5S/6, ~45cm) |
| Real-time display | Phone app | On-unit display |
| Cost | Lower (device + subscription) | Higher (unit + sensors) |
| Analysis depth | Good (app-based) | Deep (Race Studio 3) |
| Portability | Phone app | Requires Windows PC |

**Recommendation:** For serious competitive analysis, MyChron is the better tool
(temperature and RPM data are critical for setup). TRAX is excellent as a
secondary/supplementary tool or for drivers just starting data analysis.

---

## 5. Other useful tools

### SpeedAngle Apex
- GPS-based lean angle and speed data logger
- Not specific to karting but useful for understanding lateral dynamics

### Alfano (various models)
- Alternative to MyChron for lap timing and basic data
- Simpler interface, fewer features

### GoPro / Insta360 with telemetry overlay
- **Insta360 files:** .insp (photo), .insv (video). These are proprietary formats.
  Export to standard MP4 via Insta360 Studio before analysis.
- **Telemetry overlay tools:** Apps like "Telemetry Overlay" or "RaceRender"
  can overlay MyChron data onto onboard video footage. This is incredibly
  useful for correlating what the driver sees with what the data shows.
- **GoPro Telemetry:** Recent GoPros log GPS, speed, and G-forces internally.

### Setup tracking apps
- Various apps for tracking kart setup changes (pressures, gearing, jetting)
- Alternatively, a simple spreadsheet or notebook works fine

---

## 6. Data workflow

### Recommended workflow after a session

1. **At the track (within 30 seconds of session end):**
   - Note hot tire pressures (all 4 wheels)
   - Note ambient temperature and track condition
   - Pull spark plug for a quick reading (if jetting is a question)

2. **At the track (within 10 minutes):**
   - Download data from MyChron via Wi-Fi to laptop
   - Quick look at Laps Report in Race Studio 3 for headline numbers
   - Note fastest lap, average, sector bests

3. **After the day (detailed analysis):**
   - Export CSV from Race Studio 3
   - Upload to KartSan for full analysis and dashboard
   - Or: analyze in Race Studio 3 using histogram layout

4. **Before next session:**
   - Review KartSan's recommendations
   - Make ONE setup change (if needed)
   - Set goals based on data (e.g., "improve Sector 2 by 0.2s")

---

## 7. Troubleshooting

### MyChron shows no RPM
- Check spark plug lead connection (most common cause)
- Check the RPM input wire isn't frayed or loose
- Verify RPM channel is enabled in MyChron settings

### MyChron GPS data is noisy/jumpy
- Check antenna placement (must be unobstructed, facing up)
- Ensure antenna isn't buried under fairing or bodywork
- Wait for full satellite lock before starting (takes 30-60s)

### MyChron won't connect to Wi-Fi
- Restart the MyChron
- Check the network name and password in MyChron settings
- Move closer to the Wi-Fi source (phone hotspot or router)
- Try creating a hotspot from your phone instead of track Wi-Fi

### Temperature readings seem wrong
- Check sensor connection (loose = intermittent readings)
- Verify sensor is in the correct position (water outlet, exhaust header)
- Compare to a known-good thermometer to check sensor calibration

### TRAX not recording
- Check 12V power connection
- Ensure the device has cellular signal (check app status)
- Make sure the device is mounted horizontally
- Check subscription status (pro features require active subscription)

### Race Studio 3 won't open data
- Ensure you're running the latest version
- Check that the data file isn't corrupted (try re-downloading from MyChron)
- Verify 64-bit Windows (Race Studio 3 doesn't support 32-bit or Mac natively)
