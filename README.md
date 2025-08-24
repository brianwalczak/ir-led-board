# `ir-led-board`
A custom circuit connecting 16 high-current IR LEDs, designed for integration with Raspberry Pi and imaging projects.

Check out my [JOURNAL.md](JOURNAL.md) for updates and progress!

> [!NOTE]  
> All custom footprints in this project, as well as 3D print files, were created by me and are freely available under the MIT license. You are completely welcome to use, modify, and distribute them without any restrictions.

#### PCB Design
A custom-designed printed circuit board, designed in KiCad 9.0, allowing you to control 16 IR LEDs in groups of four. This PCB was designed as an easy way to connect the components and use them via GPIO pins on the Raspberry Pi.

<img src="https://github.com/user-attachments/assets/892acb49-c153-4012-a20d-3f0a2753174f" alt="PCB Design" width="600"/>

👉 [Read More](KiCad_PCB/README.md)

#### 3D Model (case)
A 3D printable case, designed in Fusion 360, made to securely hold the board and its components, as well as providing protection to prevent damage to the board.

<img src="https://github.com/user-attachments/assets/5dac2d5d-b5b4-4978-b274-93c94a39c024" alt="3D Design" width="600"/>
<br>
<img src="https://github.com/user-attachments/assets/e2bcc478-69ee-43c3-85f9-165e64d9afaa" alt="STL Model" width="600"/>

👉 [Read More](3D_Print/README.md)

#### Bill of Materials (BOM)

| Qty | Part Number                | Total Price |
|-----|------------------------------------------|-------------|
| 1   | Raspberry Pi Camera 3 NoIR               | $25.00      |
| 1   | Raspberry Pi 5 Camera Cable              | $1.10       |
| 16  | SFH 4556-AW (850nm IR LEDs)              | $9.47       |
| 16  | CFM12JT43R0 (43 Ohms resistor)           | $0.58       |
| 4   | IRLB8743PBF (MOSFETs)                    | $4.76       |
| 4   | DC0011 (thermal pads)                    | $2.20       |
| 4   | CF14JT100R (100 Ohms resistor)           | $0.24       |
| 4   | CF14JT100K (100K Ohms resistor)          | $0.24       |
| 1   | PPPC061LGBN-RC (90-degree connector)     | $0.57       |
|     | **Total**                                | **$44.16**  |
