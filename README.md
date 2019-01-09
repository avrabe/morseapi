# MorseAPI

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/d4e13fe14b6b4f029ddb619c1fb3eebb)](https://www.codacy.com/app/avrabe/morseapi?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=avrabe/morseapi&amp;utm_campaign=Badge_Grade) 
[![Build Status](https://travis-ci.org/avrabe/morseapi.svg?branch=master)](https://travis-ci.org/avrabe/morseapi)

`MorseAPI` is an unofficial (and unsanctioned) python library for controlling
[Wonder Workshop's](https://www.makewonder.com/)
[Dash and Dot](https://www.makewonder.com/?gclid=CPOO8bC8k8oCFdaRHwodPeMIZg)
robots.


TODO: integrate into wonderpy

MorseAPI abstracts out this communication protocol and, through python methods
exposes control of lights, motion and sensor data.


## Motivation
There exist smartphone apps which allow remote-controlling Dash and Dot, and even "writing programs" for them.
However, the programming functionality is limited to drag-and-drop style and does not allow interaction with
any industry programming languages.

That doesn't need to be the case - young kids can get started with the simple
drag-and-drop interface to get some exposure and instill interest, then graduate to a programming API interface in order
to create more complicated and complete implementations of their creative ideas.

`MorseAPI` provides that programming interface, in a language that is easy to pick up even for non-engineers: Python.

## Installation
This is only tested on Debian, though it should work on other Linux flavors. OSX and Windows are NOT supported.

Steps:

 * clone this repo and `cd` into it
 * pip install -e . 

## Completeness
Dash and Dot have many different commands. Morse implements only fraction there of:

 * LED Lights:
  * Ears
  * Top of Head
  * Neck / Eye backlight
  * Individual iris LEDs
  * Iris brightness
  * ~~tail light~~
 * Motion (Dash only)
  * Head pitch and Yaw
  * Move back and forth
  * Turn left and right
 * Sound
  * Playback of built in sounds
  * ~~Uploading new sounds~~
 * Sensor feedback
  * Microphone volume
  * Proximity Sensing
  * Head pitch / yaw
  * wheel rotation
  * Dash sensing of Dot
  * Robot picked / bumped / toppled oved
  * Sound direction
  * Gyro pitch/yaw/roll
  * Vertical acceleration
  * Clap
  * ~~Battery state~~
 * ~~Robot discovery~~
   * feature discovery (Dash & Dot have different feature sets)


## Example
Run:

```
examples/clock.py C0:F0
```

where `C0:F0:84:3C:51:FA` should be the bluetooth address of your bot

```
$ python
>>> from morseapi import MorseRobot
>>> bot = MorseRobot("C0:F0:84:3C:51:FA")
>>> bot.reset()
>>> bot.connect()
>>> bot.say("hi")
>>> bot.move(100)
>>> bot.turn(45)
>>> bot.ear_color("red")
>>> bot.head_yaw(10)
>>> bot.eye(255)
>>> bot.eye(100)
```
