# Honk-Sense

**A car that understands Indian roads by ear.**
Directional alerts for the horns and sirens that matter. Silence for everything else.

Honk-Sense is a concept we submitted to the **HCoE Mobility Innovation Ideathon 2026** (Hyundai), under Topic 1: *India-Smart Interaction*, Track A.

- **Presentation:** [`slides/Honk-Sense.pdf`](slides/Honk-Sense.pdf)
- **Research brief:** [`research/Honk-Sense_research.pdf`](research/Honk-Sense_research.pdf)

---

## The problem: loud roads, deaf cabins

Indian roads are some of the loudest in the world, and the horn is used constantly. Two things happen as a result:

- **Alert fatigue.** Drivers hear so many honks that they tune all of them out, including the few that signal real danger.
- **The cabin paradox.** Better insulation, closed windows, AC and music make modern cabins quieter, so sirens and nearby horns are heard later.

Even when a driver does hear a siren, it is hard to tell where it is coming from in dense traffic. Drivers freeze or move the wrong way, and ambulances lose time.

| | |
|---|---|
| **>90 dB** | daily honking exposure for Mumbai commuters (IIT Bombay study) |
| **25–35 min** | for ambulances to reach accident scenes on core national highways |
| **4.8 lakh** | road accidents in India in 2023, with 1.72 lakh deaths |
| **36%** | of those were rear-end (21%) or side (15%) collisions |

Existing systems don't close this gap. Mirrors depend on attention, ultrasonic sensors only reach about 2 m, radar blind-spot monitoring is mostly on upper variants, and every one of them needs line of sight. Nothing sees around a bus, a truck or a hairpin bend.

**The gap:** turning outside sound into a short, directional, filtered cue inside the car.

## The idea

Small exterior microphones and an on-board AI **classify** every road sound, **locate** where it comes from, and **decide** whether the people inside need to know.

- **Ambulance behind?** The music dips and a rear chime plays: *"Ambulance behind, keep left."*
- **Bike honking in the blind spot?** A chime from that side, plus an arrow on the cluster.
- **Routine honking in a jam?** Nothing. The cabin stays calm.
- **Fleet relay:** cars that hear a siren warn Hyundai cars further ahead on the same road.

> Voice assistants understand what you say. Honk-Sense understands what the road is saying.

### The horn is a language

On Indian roads a honk means something specific: *"I'm here"* (a bike in your blind spot), *"I'm overtaking"* (trucks with "Horn OK Please" painted on the back), *"careful, blind turn"* (hill roads with "Blow Horn" signs), *"move"* in a jam, or a siren that says *give way now*. Honk-Sense is meant to understand this language the way an experienced Indian driver does, and translate only what matters.

## How it works

| 1. Listen | 2. Understand | 3. Locate | 4. Act |
|---|---|---|---|
| Small microphones outside the car hear the road, but not your own horn | AI in the car recognises the sound: siren, bike horn, truck horn or routine honk | Works out where it comes from and whether it is getting closer | Stays silent, gives a soft cue or an urgent alert, and warns other cars about sirens |

**Silence is a feature.** Deciding what *not* to announce is the core of the design.

### Three alert tiers

| Tier | Triggered by | Driver gets | Passengers get |
|---|---|---|---|
| **0. Silent** | Routine honks, distant horns, sounds ahead in a jam | Nothing (logged only) | Nothing |
| **1. Aware** | Horn very close at the side or rear; truck overtaking | Short chime from the matching speaker; arrow on the cluster | Nothing |
| **2. Urgent** | Siren approaching; horn plus fast approach during a lane change | Music ducked, spoken cue in the driver's language, arrow and suggested action | Rear-screen banner: "Ambulance approaching" |

The chime plays from the speaker nearest the sound source, so the driver's ears point the right way before they read anything. A hearing-impaired mode uses visual and seat-haptic alerts only.

### Fleet layer: clearing the way for ambulances

1. A Hyundai car hears a siren and estimates its direction of travel.
2. It shares only four facts with the connected-car cloud: a siren was heard, where, which way it is heading, and when.
3. The cloud confirms the event when several cars report it, which filters out false alarms.
4. Cars ahead on the same road get an early notice: *"Ambulance approaching from behind in about 1 minute. Prepare to keep left."*

## Use cases

| | Scenario | What Honk-Sense does |
|---|---|---|
| **U1** | **Hidden ambulance.** An ambulance is behind a bus; music on, windows up. | Shows "Ambulance, behind left, approaching", dips the music and suggests which way to move. |
| **U2** | **Which horn, and where?** Horns from every side; one is a bike at your rear-left as you turn left. | Shows only the horns that are close and directed at you, with an arrow, and ignores the rest. |
| **U3** | **Honk in the blind spot.** A bike or truck honks before you change lanes; most cars in India have no radar blind-spot monitor. | "Horn, right rear" as you signal. |
| **U4** | **Around the bend.** A bus honks at a hairpin bend before it is in view. | "Vehicle ahead, around the bend", seconds earlier. Cameras and radar cannot see around a corner; sound can. |
| **U5** | **A calmer cabin.** Peak-hour traffic with street noise above 90–100 dB. | Stays quiet for routine honks: less stress and less alarm fatigue. |

## What makes it possible

- **Only one new part:** four small exterior microphones. Automotive-grade versions already exist for other exterior-microphone features.
- **Everything else is already in the car:** the infotainment computer runs the AI, cabin speakers play the directional cue, the instrument cluster shows the arrow, and the connected-car modem shares sirens.
- **Runs offline inside the car:** about 1 second from sound to alert, no audio stored or sent anywhere, works in network dead zones, and improves through over-the-air updates.

## Comparison with existing technologies

| Situation | Mirrors | Dashcam | Ultrasonic | Radar BSM | Camera ADAS | **Honk-Sense** |
|---|:-:|:-:|:-:|:-:|:-:|:-:|
| Ambulance hidden in traffic | – | – | – | – | – | Yes |
| Horn behind a blind turn | – | – | – | – | – | Yes |
| Which side a horn came from | – | – | – | – | – | Yes |
| Honking bike in blind spot | Partly | – | – | Yes | – | Yes |
| Silent car in blind spot | Partly | – | – | Yes | – | – |
| Parking, low-speed obstacles | Partly | – | Yes | – | Partly | – |
| Lane departure, car ahead | – | – | – | – | Yes | – |

Honk-Sense is not a replacement for these systems. It covers what they can't: sound that arrives before line of sight.

## What is new

Siren detection and sound-direction patents exist (mostly for autonomous driving), and there is research on horn detection with microphones. Honk-Sense adds three things:

1. **India-trained sound understanding:** two-wheeler, auto-rickshaw and pressure horns, and Indian siren patterns.
2. **Alert-fatigue-first design:** deciding what not to announce is the core feature.
3. **Fleet siren relay:** cars that hear an ambulance warn the cars ahead of it.

## Roadmap

| Phase | Plan |
|---|---|
| **1** (Ideathon) | Concept, usage scenarios and experience design |
| **2** | Driver survey; proof of concept on a microphone array; Indian road recordings |
| **3** | Integration on an in-vehicle infotainment platform; automotive microphones; user study |
| **4** | Feature in production models; fleet siren relay; partnership with emergency services |

## Repository layout

```
slides/     The presentation (PDF)
research/   Research brief: problem validity, existing systems, literature, Indian conditions
```

## Team

**Piyush Anand** and **Ankith Deegoju**, IIT Hyderabad.

## Credits

Full references are at the end of the presentation and the research brief.

Use-case photos in the presentation are from Wikimedia Commons and keep their original licences:

- Ambulance, Kolkata: Biswarup Ganguly (CC BY 3.0)
- Two-wheeler traffic, Pune: Amityadav8 (public domain)
- "Blow Horn" truck: Justin Morgan (CC BY-SA 2.0)
- Hairpin bend, Western Ghats: Rohini (CC BY-SA 3.0)
- Traffic in Bangalore: Divya Chinnasamy (CC0)
