---
Title: "IR LED Board"
Author: "Brian Walczak"
Description: "A custom circuit to control an array of 16 high-current IR LEDs. This PCB is designed for integration with a Raspberry Pi and is used for Near-IR imaging projects!"
Created On: "8/9/2025"
---

# August 20th: Designing a protective case.

Final step of the process! Today I designed a simple 3D printable housing to keep the PCB and its components nice and safe. I tried to make the model as compact as possible to save space.

I created the case in Fusion 360 and added some pre-designated mounting holes where I can attach the PCB. It was specifically made to use four M3 screws, 8mm in length!

<img height="300" alt="image" src="https://github.com/user-attachments/assets/5dac2d5d-b5b4-4978-b274-93c94a39c024" /> <img height="300" alt="image" src="https://github.com/user-attachments/assets/e2bcc478-69ee-43c3-85f9-165e64d9afaa" />

**Total time spent: 1h**

# August 19th: Send to JLCPCB, ordering parts.

Hello! Today I finalized the design and exported the Gerber files to have them manufactured with JLCPCB. I was having trouble with the traces, so I used [Freerouting](https://github.com/freerouting/freerouting): an open-source auto-router for KiCad! This made the process much easier for me (and less stressful).

JLCPCB is estimating a total of $2.00 + $3.30 shipping, pretty solid for a quantity of 5 (in-case I mess up while soldering... heck I probably will).

<img height="300" alt="image" src="https://github.com/user-attachments/assets/892acb49-c153-4012-a20d-3f0a2753174f" /> <img height="300" alt="image" src="https://github.com/user-attachments/assets/11ea9755-d176-4a4d-8649-bab37f31686c" />

**Total time spent: 15m**

# August 18th: Minor changes on the PCB, almost ready.

Hey, it's been a while! I got busy from school the past few days, but I'm happy to say that I'm done with the PCB design!

I made a few extra modifications, and shifted the position of the IR LEDs so that I can include ~2mm screw holes on each corner. I decided to add these just in case I design a 3D-printed part in the future.

Overall, I'm pretty excited to see how the final board turns out. Next, I'll have to add the traces on the PCB and export the gerber!

Oh, and here's what it looks like:

<img height="300" alt="image" src="https://github.com/user-attachments/assets/1bc104b0-c4a9-45d7-b204-e6b6ab21bd8b" />

**Total time spent: 10m**

# August 14th: Finalizing the PCB design

Hi! Today, I've been working on the final step of the building process: designing the PCB. This time was pretty time consuming since KiCad positioning tools kind of suck, so I had to make sure each part was spaced evenly with the help of the Align/Distribute and Positioning Tools.

My goal is to make this PCB as compact as possible, which I was able to perfect after making some small modifications, then printing out a 1:1 sheet of the PCB. The print tool really helped me get an idea of what the final product will look like.

I'm thinking of adding some screw holes around the PCB in the event that I want to attach dividers between each LED group. These would be handy if I'm planning to use IR diffusers or polarizers in the future. As I probably mentioned earlier, the goal with this PCB is to explore how near-IR light interacts with surfaces and veins, and to learn a little more about optics and imaging. Oh, and so I can improve my soldering skills...

<img height="300" alt="image" src="https://github.com/user-attachments/assets/e668ee9b-f79f-46d3-81d5-c72b0b67b97e" />

**Total time spent: 2h**

# August 13th: Working on the schematic / symbols

I've been working on analyzing the datasheets of my selected components and creating symbols/footprints for them, since I wasn't able to find reliable ones online. The process of creating these took a good chunk of my time, since I wanted to make sure the measurements had millimeter accuracy according to the datasheets. I'd like to make this board as compact as possible, while still making it easy to solder on.

Also, I haven't used KiCad in a while, so I spent quite a lot of time getting used to it again. I've designed a simple schematic for the project using some net labels and I'm currently working on PCB design next!

<img height="400" alt="image" src="https://github.com/user-attachments/assets/6e260d4a-a332-4b13-92a8-1d981e03b3b7" />

**Total time spent: 2.5h**

# August 12th: Almost done choosing parts!

Good afternoon! Unfortunately, school has started for me today, so I didn't get much done. It might sound crazy, but I spent roughly 2 hours yesterday searching for parts. It turns out that finding affordable parts that **will actually work for your project** isn't easy. I've basically seen the entire DigiKey catalog for MOSFETs at this point lol.

I will say that Perplexity has been a lifesaver for most of this research. Being someone who's never worked with MOSFETs before, I just found out that there actually isn't an ideal MOSFET for 3.3V signals that's both affordable and available (most are obsolete on DigiKey). After looking for quite a while, I've basically concluded that the **IRLB8743PBF** N-Channel MOSFET will be the closest to what I'd need for this kind of project.

Even though it's not rated for 3.3V by the manufacturer, it's been used in many different projects and seems to be the most recommended by the community, even though it works better with 5V. It's definitely not a 100% ideal solution for most applications, but I think in this case it'll work just fine.

I'll also be getting some `100 Ω` resistors to prevent a big surge of current at the gate, and `100k Ω` pull-down resistors from the gate to GND so it doesn't randomly turn on when the Raspberry Pi is off.

The total comes out to about $45 before shipping, not bad! It's time to get to work in KiCad!

<img height="300" alt="image" src="https://github.com/user-attachments/assets/6f144711-37b7-4ce3-847f-636231505c4f" /> <img height="300" alt="image" src="https://github.com/user-attachments/assets/67b2ce47-c98c-419c-9fd1-01c60bbd8440" />
<img height="300" alt="image" src="https://github.com/user-attachments/assets/1920746d-1b79-4bcb-947d-dd836989dfe1" />

**Total time spent: 1h**

# August 11th: This may be more challenging than I assumed.

Hello again! I've been looking into a bunch of different ways to wire up all these IR LEDs efficiently. I've concluded that DigiKey will be the best place to get these parts, since they have a lot available in-stock and shipping times are usually the fastest.

My first problem is that I realized is it might be tricky to source the current for each LED. For this project, I'd like to be able to control these LEDs in groups of 4, essentially allowing me to turn groups on and off via the GPIO pins on the Raspberry Pi.

After doing some research, it looks like I may need to use MOSFETs to group these and ensure they can be switched reliably. There are some other alternative options (such as BJT's), but MOSFETs will be the best choice for my use case. That being said, I'll need to connect the PCB to the 5V pin on the Raspberry Pi to source enough power.

I've also decided that I'll be using `43 Ω` resistors for the LEDs, which will limit them to ~80mA of current. I've been eyeing [these](https://www.digikey.com/en/products/detail/ams-osram-usa-inc/SFH-4556-AW/7325582) IR LEDs on DigiKey for this project, since they offer 100mA in forward current and a 1.5V forward voltage.

```
Total Voltage = (5V - 1.5V) = 3.5V

Voltage / Current = Resistance
3.5V / 0.08A = 43.75 ohms
```
##### (here's how I got that number by the way)

I have already selected the camera I'll be using, and that's the **Raspberry Pi Camera 3 Module (NoIR Edition)**. I'm currently researching the other components needed to get this project done (including MOSFETs, other resistors, etc).

<img height="200" alt="2" src="https://github.com/user-attachments/assets/b77260c1-bbc6-4f55-97eb-66e6b36ab3b0" />

**Total time spent: 2h**

# August 10th: Time to research!

Welcome! This is a hardware project I'm looking to work on for the next few weeks. My goal is to design and build a PCB in KiCad that can simplify the control of 16 high-current (probably around ~50-100mA) IR LEDs for an imaging project.

For this project, I've decided to use my existing Raspberry Pi 5 to cut costs. It's already a perfect choice for this project, and I've been trying to figure out what I can do with it, so that's what we're doing here.

I've only ever created a PCB once (in KiCad as well). It was for a Flipper-Zero-style SubGHz device that captured, replayed, and analyzed SubGHz frequencies. It's called BKFZ SubGHz, you can check it out [here](https://github.com/brianwalczak/BKFZ-SubGHz). That being said, this was quite a simple PCB, and honestly wasn't entirely necessary for the project.

Before I get started with creating this PCB in KiCad, I'll need to spend the next few days researching my options and finding the parts I need to make this project. Ideally it should use 16 IR LEDs to make sure the surface is evenly illuminated. I'd like to be able to control the LEDs in groups of 4.

<img height="200" alt="1" src="https://github.com/user-attachments/assets/7eb27d12-d112-4b91-8c38-4b9663559246" />

**Total time spent: 30m**
