# How to build a LoRaWAN temperature sensor in just 600 days

```
This joke is a collection of common mistakes that device manufacturers make during LoRaWAN project development. 
It can save you more than a year of development.
```


## Day 0

Got a simple, but helpful project for you.

I need to build a remote temperature sensor that would send measurements every hour over a LoRaWAN network.

It is a modern technology, inexpensive, and has low power consumption...


## Day 2

I got a microcontroller development board and a LoRa transceiver, and connected all the components.

I also downloaded an open-source LoRaWAN stack and put together a simple measure-transmit-sleep cycle. It all works! Fast and simple!

Now, let’s conduct some range tests...

It is amazing! Wow!

It is now time to design a custom board.


## Day 12

Got the first board prototypes. They look cool. My logo is on the PCB. I designed the PCB myself.

I kept all the connections the same as on the development board, so my code should work as is.

Some range tests again.

Well, not as good as the development board, because I have a smaller PCB antenna now.

It is not a big problem, because I would compensate for the antenna’s imperfection by a bit more TX power.

My software works perfectly now. The sensor is transmitting data every hour.

I would order some more PCBs and components, because it is time to run a proof of concept project.


## Day 24

Got the first 100 board prototypes.

It is amazing how quickly you could manufacture custom electronics these days!

Uploaded my firmware, but, unfortunately, I am using the same default device EUI on each device, completely forgot about it.

I need some more device EUIs and I also need to reprogram all the boards again :(

Painful, but not a big problem, as I can invent some random numbers for the EUIs.

Done. I can see some data flowing right now!

I am going to deploy these 100 boards in the field to evaluate how they perform in real life. It will take a couple of days to collect some statistics.


## Day 30

Something is wrong, half of the traffic is lost, even more, I would say.

Probably it is my antenna design that I was struggling with. I performed range tests again, but it looks good to me. Strange.

I didn’t sleep, but the issue is finally solved. All the devices were sending messages synchronously every hour: 13:00, 14:00, 15:00. It caused some messages to collide. I didn’t think about that before.

I randomized the transmission time and it all works well now. That’s a big win!

Unfortunately, I had to collect the devices from the field and reprogram them again. :(

Collected, updated and finally distributed them back across the field. Let’s wait for a week or so and evaluate the results.


## Day 37
The results are not bad at all, but I am still losing some messages.

I would probably include several past temperature measurements to the messages to create some data redundancy and avoid data loss. Poor man error correction code.

Fortunately, LoRaWAN is bi-directional, so I also decided to add a remote configuration of transmission period. A simple feature, but I am sure it will be popular.

I spent some time on it to make sure everything works and build some high quality code. Really proud of myself!

Final tests. Devices collected, reprogrammed and distributed back across the field...


## Day 47

Now it looks like there is a bug with the downlinks. Maybe it is a bad gateway, or timing, or the device stack is no good, or maybe there’s some error in my code. I swear it all worked before.

I collected the devices again, but all of them work fine. WTF?


## Day 54

Still can't reproduce this downlink bug.

Spent a week checking every potential issue: application, network server, gateways, RX windows, frequency channels, keys, device stack, device application. Still have no idea what this bug is about.

I decided to add the last downlink timestamp and RSSI values to my uplink message, so I can measure device radio performance in the downlink channel.


## Day 57

That was tough, but I finally cracked it. Looks like my antenna is not good enough. I compensated for the TX channel with extra power, but never measured device sensitivity. How shall I do this?

I spent a week exchanging e-mails with the chip manufacturer on how to do this, as it's not easy.

Now I need to find and hire a radio lab, because all the measurements are supposed to be done over air.


## Day 68

It took some time to get a window in a lab schedule, but the measurements are finally done and the antenna is fixed. It was quite an expensive exercise.

Time to deploy a bigger batch with a client. We agreed on 1 000 pcs. As a pilot. I can smell a rollout!


## Day 84

The devices have been manufactured, the firmware uploaded. It was a pain in the ass to upload, because all the device EUIs are different, but we’ve managed to do it together with my colleague.

Our customer has several offices, so we would use a professional public network operator for this pilot.

I hope that their coverage is good enough...


## Day 90

The pilot has been delayed, as the operator did not accept our devices.

We need to go through LoRaWAN and regulatory certification and operator interoperability tests.

We need to rush. Let the paperwork begin!


## Day 110

We didn’t pass LoRaWAN certification, because our EUI are not from an IEEE pool. How am I supposed to know that? What is an IEEE pool?

## Day 118

Fixed. Certification passed.

The LoRaWAN part was easy. I enabled an already implemented test mode of the open-source stack and it was done. Spent some money on EUIs and tests.

Regulatory thing was costly. Around $20k.


## Day 220

Omg! All the batteries are dead. But why?

I implemented power saving mode. I measured the power consumption with a multimeter hundreds of times and it always showed 0.

Fixed. I figured out that a special power-monitoring device is needed to measure super low sleep current. We shall also make sure our PCBA is good and clean.

I would enable a couple of devices to send messages every 10 seconds to see how many transmissions one battery can do.

Hopefully, it is the end of that story.


## Day 221

My test devices stopped sending messages in an hour. I am not surprised for some reason. That's probably some kind of a bug in the stack or memory exception. Let me add a watchdog.

Works for an hour. Stops. Watchdog reset. Works again. Why?


## Day 224

It was an embedded duty cycle limitation. Good to know. Management is pushing me to distribute devices into the field!


## Day 300

Pilot results are all good in general.

Some devices have periodic message loss, but it’s ok. I explained to the customer that it's a radio. He argued that he is not losing any WhatsApp messages over cellular.

My manager did some sales tricks and we agreed with the customer for a full scale rollout of 100k devices.

It is a lot of devices, so we performed some minor PCB changes for the manufacturing process. The circuit is the same, so it's all good.


## Day 384

Didn’t know that component lead time could be 12 weeks. I would implement some FUOTA functionality in the meantime to spare myself from any software bugs.


## Day 424

Just figured out that because of these minor PCB changes we have to re-run all the regulatory testing again. Lots of paperwork, but we already know how to do that.


## Day 430

We’re manufacturing 1000 devices per day. It is amazing!

Strange. It looks like some devices have higher message loss than others, but there is no difference between the devices.

Production has been halted. Unfortunately, the crystal we selected has a bigger frequency deviation than is required. The crystal supplier apologized and offered an express supply option. It would take just 8 weeks instead of 12 to get a new batch of crystals.


## Day 486

Eight weeks passed. Crystals stuck on customs now.


## Day 514

Finally received. Production is at full speed again.

All devices have been shipped and the customer is rolling them out.


## Day 531

At least 42% of devices are not communicating well after installation.

It looks like my manager is going to jump under the train, as his vocabulary of excuses is almost dry.


## Day 538

It took a week and several micro heart attacks to identify the reason!

The customer is using some devices to monitor the temperature of food boxes inside trucks and the ADR is not working properly inside a moving object. It's a new use case, but still.

Shall I use my FUOTA to fix it? I am a bit scared...


## Day 576

Phew. We agreed with the operator to use a static ADR setting for our devices: SF8 is fine with them.

They applied this solution today.


## Day 577

Another problem. Some devices are still not communicating well enough.

The customer is placing the devices on metal surfaces, which is affecting antenna performance. Unfortunately, we did not notice that during our pilot.

## Night 577

I have correct DevEUIs from the IEEE pool, but I have the same encryption keys everywhere. If one device is compromised - we are fucked.

Can’t sleep now, but I will probably calm down later.


## Day 600

The customer is using our system and is happy. It's a compliance use case, but there is a problem.

Some operators put two sensors in one place and noticed that the sensors are showing different temperatures.

Unfortunately, I forgot that we need to calibrate the thermometers during manufacturing, as I was too busy solving LoRaWAN issues.

