# Yagi

The air around you is full of conversations you can't hear.

Your car's tires are reporting their pressure every few seconds. The weather station on the balcony is sending the temperature and humidity. Your doorbell, your smoke alarm, the thermometer in the oven, the remote for the garage door, the drone passing overhead. Billions of devices are talking all day long, over radio signals that almost nobody can read.

Yagi is a programming language that lets you read them, and talk back.

## Say what the signal is

Every one of those devices sends a signal with a simple shape. It switches its carrier on and off, or hops between two frequencies. It sends bits at a certain speed. It packs them into a message with a known layout: an ID, a temperature, a checksum. That shape is usually written down in a page or two of a datasheet.

Until now, turning that page into working software meant building a pile of signal processing by hand: filters, clock recovery, slicers, decoders, error checks. Weeks of work, by the small number of people who know how, and then the same work all over again for the next device.

With Yagi, you write down the shape and stop there.

```
signal WeatherSensor {
  modulation: ook
  coding:     pwm(short: 500 µs, long: 1000 µs)
  frame:      header { id: bits[8], temperature: bits[12], humidity: bits[8] }
}
```

That's the whole signal. Plug in a $30 USB radio, point Yagi at it, and readings from the sensor start to appear.

## One description, four programs

The description isn't a receiver. It's the signal itself, and Yagi builds everything else from it.

It builds the receiver that hears the signal and turns it into readings. It builds the transmitter that can send the same signal back out. It builds a simulator that produces the signal with realistic noise, so you can test your work on a laptop on a plane with no radio at all. And it builds a detector that tells you when that signal is on the air nearby.

Change the description and all four change with it. They can never drift apart, because there's only one thing to keep up to date.

## It checks your work

Radio has rules, and most mistakes break them. Yagi knows the units: frequencies, durations, sample rates, signal strengths. It won't let you add a frequency to a duration or listen to a signal with a radio too slow to capture it. It catches those problems before anything runs, and when something is wrong it tells you in plain English what happened and how to fix it.

That means you spend your time on the signal you care about, not on hunting down why nothing comes out.

## Any radio, any computer

A description doesn't care what hardware it runs on. The same few lines work with a cheap RTL-SDR dongle, a HackRF, or professional lab gear, on a Mac, a Linux box or a Windows laptop. Yagi works out the details for whatever you have plugged in.

## You already own the hardware it speaks to

Yagi comes with a growing library of real devices already described: weather stations, thermometers, tire pressure sensors, energy monitors, doorbells, remotes and more, each one tested against real recordings. Plug in a radio and Yagi can tell you what's transmitting around you right now. Pull your own sensors into a home dashboard. Find out what that box on the wall is actually sending.

And when the device you care about isn't in the library yet, you describe it yourself, in an afternoon instead of a month.

## Built for everybody

You shouldn't need a degree in radio engineering to find out what your weather station is saying. Yagi is designed so you don't. If you can follow a recipe, you can read a Yagi signal, and the tools walk you from your first scan to your first description of your own.

Students can learn how wireless really works by seeing it. Makers and tinkerers can build with the signals around them. Researchers can study devices without writing a decoder first. Teams who build radio products can go from a spec sheet to working, tested software in a fraction of the time, with the simulator and the real receiver coming from the same source.

## What SQL did for data

Before SQL, getting information out of a database meant writing code that walked through files and records by hand. SQL let people say what they wanted and let the system work out how. It opened databases up to millions of people who would never have written that code.

Radio is still in the before. Yagi is built to be its SQL.

## Coming in 2027

Yagi is in active development. The first public release is planned for 2027, with the language, the compiler, the tools and the core device library free for everyone.

Yagi is made by 291 Group in Canada.

https://291Group.com
