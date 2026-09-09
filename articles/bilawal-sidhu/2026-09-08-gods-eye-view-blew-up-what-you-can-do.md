---
title: God’s Eye View Blew Up. Here's What You Can Do With It.
author: Bilawal Sidhu
channel: Bilawal Sidhu
url: https://www.youtube.com/watch?v=o_FJ1NIH9yw
date: 2026-09-08 22:55
tags: ai, development
---

# God’s Eye View Blew Up. Here's What You Can Do With It.

God's Eye View is now open source. Within days, its launch video passed half a million views,
the repository reached number one on GitHub Trending, and it was still there a week later.
Chris Messina, the inventor of the hashtag, put it on Product Hunt, while Brendan Eich—the
creator of JavaScript, co-founder of Mozilla, and creator of Brave—joined the conversation.

The response produced two recurring questions: how can a non-coder run it, and what can the
tool actually do? This is a walkthrough of both.

## Two Ways to Install It

The simplest route on Windows, macOS, or Linux is Pinokio. Its catalog contains an officially
featured God's Eye View installer: download the tool and start the app with one button. An
earlier installation bug has been fixed, so users should install Pinokio 8.2 or newer.

Coders—and anyone who wants to modify the project—can instead give the GitHub repository and
the setup prompt from the video description to a local coding agent such as Codex, Claude
Code, Cursor, or Antigravity. This must be an agent running on the computer, not a chat
website. It can read the current instructions, install the dependencies, and launch the
keyless version. Contributors who build something useful are encouraged to submit a pull
request.

## First Launch and Map Providers

The default keyless experience uses Esri's 2D globe. All layers and interface controls still
work. Photorealistic 3D requires another provider. Google Maps is inexpensive and may remain
free for light use, though it can require a credit card. Cesium offers community access to
the same Google 3D tiles for personal, non-commercial projects.

The interface has data layers and a scene editor on the left, display settings and context
tools on the right, and presets and map sources along the bottom. The Power Up panel explains
which API keys unlock optional features and stores those keys locally. Available map styles
include labeled Bing maps, familiar OpenStreetMap views, and the 3D globe. Users can jump to
presets or search for any location, such as San Francisco International Airport.

## Tracking Aircraft and Listening to Radio

Turning on flight layers shows commercial aircraft in white and military aircraft in yellow.
The underlying data comes from tens of thousands of volunteers whose receivers collectively
maintain a digital twin of aircraft around the world.

Label density, the circular reticle, and the amount of information visible outside the
reticle are configurable. Celestial mode shows the positions of the sun and moon. The visual
styles range from a deliberately theatrical spy-satellite theme to a clean, minimal view,
with thermal, night-vision, and CRT-style options.

Contacts mode lists nearby commercial flights, military flights, vessels, and mapped
installations where data is available. Selecting a track reveals speed, altitude, and other
telemetry. Cockpit mode follows the aircraft from its perspective, shows nearby traffic, and
lets the user step between tracks. A context circle covers a 250-kilometer radius around the
selected object.

The radio layer exposes available police, weather, and ordinary broadcast stations. Sidhu
demonstrates listening to NOAA weather radio near San Francisco.

## Controlling the Globe by Voice

Voice control can remain on continuously or work as push-to-talk with the space bar. It
requires microphone permission and an OpenAI API key. Both models use GPT Realtime: the mini
model is cheaper, while the standard model offers higher quality at greater cost.

Sidhu enables vessels, flies to Rotterdam, marks the port, and starts a camera orbit entirely
by voice. The assistant can also draw a route between two places and animate the camera along
it. Routes default to walking directions. Because voice mode has general world knowledge, it
can explain places and infrastructure visible on the map, such as Laughlin Air Force Base and
its role in pilot training.

At Area 51, the app shows aircraft tracks and includes a playful UFO Easter egg: a selected
aircraft can be rendered as the rumored TR-3B craft. More importantly, the Easter egg
illustrates how easily users can ask a coding agent to add their own visual features.

## Traffic and Public Cameras

Traffic mode uses aggregate TomTom location data to color-code congestion. CCTV mode overlays
publicly available cameras, with previews on hover and larger images on selection. In Austin,
Sidhu compares a red traffic corridor with its camera image and confirms bumper-to-bumper
rush-hour traffic. London likewise has dense public-camera coverage.

These camera images represent current conditions, but they are not streaming video. Austin's
feeds refresh one frame every five to ten minutes. The city provides high-resolution images
at a deliberately low frame rate to reduce the risk of tracking individual vehicles. The
tool can therefore validate aggregate congestion without providing continuous surveillance.
Coverage is modular, and contributors are already adding more public-camera sources.

## Why the Strait of Hormuz Looks Empty

Aircraft receivers can detect planes high overhead, but terrestrial AIS receivers need to be
close to coastlines to track vessels. The free AISStream source provides strong vessel
coverage in Europe and the United States, so Rotterdam and the English Channel appear busy.
Its coverage around the Strait of Hormuz is weak, making the region look misleadingly empty.

Reliable coverage there requires satellites with radio-frequency sensors. Such data can cost
thousands or tens of thousands of dollars, and providers may apply surge pricing to regions
in high demand. Sidhu is exploring cheaper access. For now, users can replace the bundled
APIs with other providers, while military-aircraft data still offers useful regional clues.

## Riding Along With a Landing

When visiting a new region, users should wait briefly for terrain to load. Otherwise aircraft
near the ground may clip through the surface. At Atlanta's Hartsfield-Jackson airport, planes
gradually rise into the correct positions as terrain data initializes. Sidhu then enters
cockpit mode on Delta flight DAL 3146 and watches its landing from the aircraft's perspective.

## Recording Camera Tours

The scene editor turns selected views into a reusable camera sequence. A creator frames each
view, captures it as a shot, and can later update or reorder the shots. Pressing play runs the
whole camera tour, which can then be screen-recorded for a film or other project. Sidhu asks
creators who publish such footage to credit God's Eye View and link the repository.

## Fires, Earthquakes, and the Physical Internet

The app maps recent earthquakes and NASA FIRMS active-fire detections. FIRMS uses satellite
thermal imaging to identify fire hotspots. Comparing imagery providers can reveal different
details, such as the density of a smoke plume.

Sidhu is working to add free Sentinel imagery, but even public satellite imagery over war
zones can be delayed by roughly three days. Governments restrict timely access because
adversaries can exploit powerful open-source intelligence, which also delays the public's
understanding of events.

Other layers expose data centers and submarine cables. Voice mode can explain why Marseille
is a major undersea-cable landing hub and why data centers cluster near such connections:
shorter backhaul keeps latency and costs down, while France's nuclear-heavy grid supplies
comparatively low-carbon electricity. Together, these layers reveal the physical nervous
system behind online videos, social networks, and games.

## Reconstructing the Nepal Disaster

God's Eye View is intended as a foundation, not a fixed collection of layers. Users were
already applying it to reconstruct a disaster in Nepal. A coding agent can fetch open data
and official reports, then plot an earthquake, landslide, flood trajectory, and geolocated
social-media footage on the same map.

The resulting reconstruction shows both the flood's route and the scale of its destruction.
The same approach can support response, reporting, or understanding of environmental events,
geopolitical developments, and local infrastructure.

## Building the Collective Window

Natural-language coding agents make new layers accessible even before they reach the main
branch. Existing community work includes automatic license-plate readers, while another
proposal uses an inexpensive software-defined radio—costing tens of dollars—to monitor local
signals and radio traffic. Users can try experimental pull requests, submit their own, open
issues, and vote on feature ideas.

For personal, non-commercial use, the application can cost almost nothing, especially without
voice. Hosting is harder: even a free public service can count as commercial use under data
providers' terms. A hosted version would require replacing non-commercial APIs and might need
a paid tier for features such as voice. Historical data is another future possibility, but
it is considerably more expensive.

The open-source project will continue regardless. Sidhu's larger invitation is to treat it as
a shared window onto the real world—and to build whatever environmental, geopolitical, or
local tools the bundled version does not yet contain.
