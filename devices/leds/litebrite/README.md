---
layout: page
title: '"Lite-Brite" LED Simulation'
permalink: /devices/leds/litebrite/
machines:
  - id: lbDemo
    type: leds
    name: Lite-Brite Demo
    uncompiled: true
    config: |
      {
        "lbDemo": {
          "class": "Machine",
          "type": "leds",
          "name": "Lite-Brite Demo",
          "version": 1.10,
          "autoPower": false,
          "bindings": {
            "clear": "clearLB",
            "print": "printLB"
          },
          "overrides": ["autoPower"]
        },
        "lbChip": {
          "class": "Chip",
          "toggle": false,
          "rule": "C8",
          "bindings": {
            "colorPalette": "colorPaletteLB",
            "colorSelection": "colorSelectionLB",
            "colorSwatch1": "colorSwatchLB1",
            "colorSwatch2": "colorSwatchLB2",
            "colorSwatch3": "colorSwatchLB3",
            "colorSwatch4": "colorSwatchLB4",
            "colorSwatch5": "colorSwatchLB5",
            "colorSwatch6": "colorSwatchLB6",
            "colorSwatch7": "colorSwatchLB7",
            "colorSwatch8": "colorSwatchLB8",
            "countInit": "countInit",
            "countOn": "countOn",
            "countOff": "countOff",
            "countCycle": "countCycle",
            "backgroundImage": "backgroundImage",
            "saveToURL": "saveLB"
          },
          "colors": {
            "Original": {
              "Blue":   "#3067c1",
              "Green":  "#2f9a27",
              "Violet": "#9f3c92",
              "Red":    "#b71e1d",
              "Orange": "#fa7d14",
              "Pink":   "#ff7379",
              "Yellow": "#fadc4e",
              "White":  "#fffff9"
            }
          },
          "overrides": ["blue","green","violet","red","orange","pink","yellow","white","wrap","pattern"]
        },
        "lbClock": {
          "class": "Time",
          "cyclesPerSecond": 1,
          "cyclesMinimum": 1,
          "cyclesMaximum": 120,
          "bindings": {
            "run": "runLB",
            "speed": "speedLB",
            "step": "stepLB",
            "throttle": "throttleLB"
          },
          "overrides": ["cyclesPerSecond","yieldsPerSecond","yieldsPerUpdate","cyclesMinimum","cyclesMaximum","requestAnimationFrame"]
        },
        "lbDisplay": {
          "class": "LED",
          "type": 1,
          "cols": 45,
          "rows": 39,
          "backgroundColor": "black",
          "hexagonal": true,
          "highlight": false,
          "bindings": {
            "container": "displayLB"
          },
          "overrides": ["color","backgroundColor"]
        },
        "lbInput": {
          "class": "Input",
          "bindings": {
            "reset": "resetLB"
          }
        }
      }
styles:
  lbDemo:
    position: relative;
    display: inline-block;
    float: left;
    margin-right: 32px;
    margin-bottom: 16px;
  displayLB:
    position: relative;
    background-color: rgb(26,26,26);
    line-height: 0;
    margin-bottom: 8px;
    background-image: none;
    background-size: 100% 100%;
  .colorSwatchLB:
    display: none;
    width: 16px;
    height: 16px;
    border: 1px solid;
    border-radius: 50%;
    vertical-align: middle;
    background-color: green;
  diagsLB:
    float: left;
  printLB:
    font-family: Monaco,"Lucida Console",monospace;
---

"Lite-Brite" LED Simulation
---------------------------

The [Lite-Brite](https://en.wikipedia.org/wiki/Lite-Brite) concept was invented by Joseph M. Burck at
[Marvin Glass & Associates](https://en.wikipedia.org/wiki/Marvin_Glass_and_Associates) and first marketed as a toy
in 1967 by [Hasbro](https://en.wikipedia.org/wiki/Hasbro).

The original Lite-Brite design used a pair of matching black panels punctured with a series of evenly spaced holes
arranged in a grid of 39 rows, which alternated between 44 and 45 holes per row, resulting in a hexagonal ("honeycomb")
layout containing 1735 holes.  A piece of black paper containing a pre-printed pattern would be sandwiched between
the panels, and then your job was to insert any of the (blue, green, violet, red, orange, pink, yellow, or white)
colored pegs into the appropriately marked holes.

This demo takes the "Lite-Brite" concept a bit farther, allowing you to add counters to each of the colored LEDs, making
it possible to create a variety of "blinking" and "color-cycling" animations.

A small collection of original background images can also be turned on underneath the grid, to help you recreate them
with LEDs.  However, it's difficult to find decent high-quality images of the original 1967 patterns, so some
"artistic interpretation" is required.  Eventually, we'll also add some of the original black-and-white pattern images
that just displayed the original Lite-Brite color codes (B, G, V, R, O, P, Y, and W).

{% include machine.html id="lbDemo" config="json" %}

<div id="lbDemo">
  <div id="displayLB"></div>
  <select id="colorPaletteLB"></select>&nbsp;<select id="colorSelectionLB"></select>
  <div id="colorSwatchLB1" class="colorSwatchLB"></div>
  <div id="colorSwatchLB2" class="colorSwatchLB"></div>
  <div id="colorSwatchLB3" class="colorSwatchLB"></div>
  <div id="colorSwatchLB4" class="colorSwatchLB"></div>
  <div id="colorSwatchLB5" class="colorSwatchLB"></div>
  <div id="colorSwatchLB6" class="colorSwatchLB"></div>
  <div id="colorSwatchLB7" class="colorSwatchLB"></div>
  <div id="colorSwatchLB8" class="colorSwatchLB"></div>
  <select id="countInit">
    <option value="0" selected="selected">Start at 0</option>
    <option value="1">Start at 1</option>
    <option value="2">Start at 2</option>
    <option value="3">Start at 3</option>
    <option value="4">Start at 4</option>
    <option value="5">Start at 5</option>
    <option value="6">Start at 6</option>
    <option value="7">Start at 7</option>
  </select>
  <select id="countOn">
    <option value="0">On for 0</option>
    <option value="1" selected="selected">On for 1</option>
    <option value="2">On for 2</option>
    <option value="3">On for 3</option>
    <option value="4">On for 4</option>
    <option value="5">On for 5</option>
    <option value="6">On for 6</option>
    <option value="7">On for 7</option>
  </select>
  <select id="countOff">
    <option value="0" selected="selected">Off for 0</option>
    <option value="1">Off for 1</option>
    <option value="2">Off for 2</option>
    <option value="3">Off for 3</option>
    <option value="4">Off for 4</option>
    <option value="5">Off for 5</option>
    <option value="6">Off for 6</option>
    <option value="7">Off for 7</option>
  </select>
  <select id="countCycle">
    <option value="0" selected="selected">Cycle by 0</option>
    <option value="1">Cycle by 1</option>
    <option value="2">Cycle by 2</option>
    <option value="3">Cycle by 3</option>
    <option value="4">Cycle by 4</option>
    <option value="5">Cycle by 5</option>
    <option value="6">Cycle by 6</option>
    <option value="7">Cycle by 7</option>
  </select>
  <select id="backgroundImage">
    <option value="" selected="selected">No Image</option>
    <option value="images/Snow_Man.jpg">Snow Man</option>
    <option value="images/Bird_of_Paradise.jpg">Bird of Paradise</option>
  </select>
  <button id="saveLB">Save to URL</button>
</div>
<div id="diagsLB">
  <div>
    <textarea id="printLB" cols="78" rows="16"></textarea>
  </div>
  <button id="runLB">Run</button>
  <button id="stepLB">Step</button>
  <button id="resetLB">Reset</button>
  <button id="clearLB">Clear</button>
  <input type="range" min="1" max="120" value="15" class="slider" id="throttleLB"><span id="speedLB">Stopped</span>
</div>

{% comment %}

Test URL:

http://pcjs:8088/devices/leds/litebrite/?pattern=0/0/45/39/A45o$45o$21b47R154G39B1A256CoRGBACo$21o47R154G39B1A256C2oRGBACo$20o47R154G39B1A256CoRGBACb47R154G39B1A256CoRGBACo$20o47R154G39B1A256CoRGBAC2b47R154G39B1A256CoRGBACo$19o47R154G39B1A256CoRGBAC3b47R154G39B1A256CoRGBACo$19o47R154G39B1A256CoRGBAC4b47R154G39B1A256CoRGBACo$18o47R154G39B1A256CoRGBAC4b255R255G249B1A8976Co47R154G39B256CoRGBACo$18o47R154G39B1A256CoRGBAC3b255R255G249B1A784CobRGBACb47R154G39B1A256CoRGBACo$17o47R154G39B1A256CoRGBAC2b255R255G249B1A8976Co4880CoRGBAC3b47R154G39B1A256CoRGBACo$17o47R154G39B1A256CoRGBACb255R255G249B1A784CobRGBACo4b47R154G39B1A256CoRGBACo$16o47R154G39B1A256Co255R255G249B8976Co4880CoRGBACo6b47R154G39B1A256CoRGBACo$16o47R154G39B1A256CoRGBACo8b255R255G249B1A8976Co47R154G39B256CoRGBACo$15o47R154G39B1A256CoRGBACo7b255R255G249B1A784CobRGBACo47R154G39B1A256CoRGBACo$15o47R154G39B1A256CoRGBACo6b255R255G249B1A8976Co4880CoRGBAC3b47R154G39B1A256CoRGBACo$14o47R154G39B1A256CoRGBACo5b255R255G249B1A784CobRGBAC5b47R154G39B1A256CoRGBACo$14o47R154G39B1A256CoRGBAC5b255R255G249B1A8976Co4880CoRGBAC7b47R154G39B1A256CoRGBACo$13o47R154G39B1A256CoRGBAC4b255R255G249B1A784CobRGBAC8b255R255G249B1A8976Co47R154G39B256CoRGBACo$13o47R154G39B1A256CoRGBAC3b255R255G249B1A8976Co4880CoRGBAC8b255R255G249B1A784CobRGBACo47R154G39B1A256CoRGBACo$12o47R154G39B1A256CoRGBAC2b255R255G249B1A784CobRGBAC8b255R255G249B1A8976Co4880CoRGBAC3b47R154G39B1A256CoRGBACo$12o47R154G39B1A256CoRGBACb255R255G249B1A8976Co4880CoRGBACo7b255R255G249B1A784CobRGBAC5b47R154G39B1A256CoRGBACo$11o47R154G39B1A256Co255R255G249B784CobRGBAC8b255R255G249B1A8976Co4880CoRGBAC7b47R154G39B1A256CoRGBACo$11o47R154G39B1A256CoRGBAC9b255R255G249B1A784CobRGBAC8b255R255G249B1A8976Co47R154G39B256CoRGBACo$10o47R154G39B1A256CoRGBAC8b255R255G249B1A8976Co4880CoRGBAC8b255R255G249B1A784CobRGBACb47R154G39B1A256CoRGBACo$10o47R154G39B1A256CoRGBAC7b255R255G249B1A784CobRGBAC8b255R255G249B1A8976Co4880CoRGBAC3b47R154G39B1A256CoRGBACo$9o47R154G39B1A256CoRGBAC6b255R255G249B1A8976Co4880CoRGBAC8b255R255G249B1A784CobRGBAC5b47R154G39B1A256CoRGBACo$9o47R154G39B1A256CoRGBAC5b255R255G249B1A784CobRGBAC8b255R255G249B1A8976Co4880CoRGBAC7b47R154G39B1A256CoRGBACo$8o47R154G39B1A256CoRGBAC4b255R255G249B1A8976Co4880CoRGBAC8b255R255G249B1A784CobRGBAC8b255R255G249B1A8976Co47R154G39B256CoRGBACo$8o47R154G39B1A256CoRGBAC3b255R255G249B1A784CobRGBAC8b255R255G249B1A8976Co4880CoRGBAC8b255R255G249B1A784CobRGBACb47R154G39B1A256CoRGBACo$7o47R154G39B1A256CoRGBAC2b255R255G249B1A8976Co4880CoRGBAC8b255R255G249B1A784CobRGBAC8b255R255G249B1A8976Co4880CoRGBAC3b47R154G39B1A256CoRGBACo$7o47R154G39B1A256C30oRGBACo$21o250R125G20B1A256CoRGBACo$21o250R125G20B1A256C2oRGBACo$21o250R125G20B1A256CoRGBACo$21o250R125G20B1A256C2oRGBACo$21o250R125G20B1A256CoRGBACo$21o250R125G20B1A256C2oRGBACo$45o

{% endcomment %}