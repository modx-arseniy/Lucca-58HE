# Lucca 58HE
The Lucca 58HE is a 58 key hall effect split keyboard!

This keyboard is still very much a work in progress!! Kicad files for PCBs and switch plate, 3d files for case all available. Currently working under KMK!  
[**Здорово, что она OpenSource OpenHardware!]

![IMG_6700](https://github.com/user-attachments/assets/aa22d8b3-7bef-4428-90fe-1be624bb01be)

## Features

- Fully addressable per-key RGB
//** imho, плохой выбор, хотя он кругом и всюду применяется в 90+% механических клавиатур сегодня. Но очень трудно избавиться от засветов вокруг; на Double-Shot полупрозрачных и прозрачных "ледяных не матовых" и тп кейкапах очень сильные засветы и одновременно нифига не видно надписи. Часто бьёт LED сквозь щели свитча напрямую в глаза под некоторыми углами, весьма неприятно... Бывают свитчи с диффузорами-световодами, матовыми и тп линзами, но они относительно редкие и дорогие отдельно (AKKO/MonsGeek и тп, у них видел! Но даже это не спасает от засветов в дефолтном варианте, осталась надежда на выводные 2*3*4 square/круглые 3mm как в старых свитчах полноразмерных от MX - но это не  ARGB! ARGB выводные видел только 5mm диаметром, не влезают(но, говорят, они спокойно обтачиваются до нужной формы! Круглую шляпку точно спилить надо, т.к. круглая, якобы, дает сконцентрированный пучок, плоские наоборот дают рассеяние на большое пятно)
- 10-point RGB Underglow on each half
- Full USB-C support
- Hardware support for both SPI and UART communication between halves
- OLED screens
- Rapid Trigger
- 3D Printed Case
- Compatible with standard HE Switches, I reccomend Gateron Jades

![IMG_6701](https://github.com/user-attachments/assets/d41b9f8e-27c2-444f-80f4-b9e1a3898853)

## Bill of Materials

- Multiplexer - ADG732BSUZ [datasheet url](https://www.analog.com/media/en/technical-documentation/data-sheets/adg726_732.pdf)
//**Дорогущий аналоговый Multiplexer Switch ICs  1x32:1 с неудобным корпусом TQFP-48(7x7), в 20! раз дороже применяемых в фабричных и других проектах OpenSource HE/TMR, например [CD74HC4067](https://www.ti.com/lit/ds/symlink/cd74hc4067.pdf) 16-Channel Analog Digital Multiplexer. Если уж для сплит(половинки от кол-ва клавиш!) клавиатуры магнитной на +-современных ARM/RISC-V, то портов должно хватить; скорость отклика не будет лучше, если не на 1 порт все сенсоры-свитчи?
Скорости 99+% юзеров хватит даже 1kHz и меньше(наоборот предусмотреть бы для энергопотребления уменьшение до минимальных офисных значений!), поэтому может быть выбор был обусловлен удобством трассировки платы?
Но в варианте [riskable/void_switch_65](https://github.com/riskable/void_switch_65_pct?tab=readme-ov-file) смогли почти однослойную плату развести с такими мультиплексорами, в тут в Lucca-58HE же чуть не BGA! Интересно, как с наводками?)
- MCU - Waveshare RP2040 Zero 
- OLED - SSD1306 128x32 
- HE Sensor - DRV5053VAQDBZR
//**(High voltage (up to 38V) Bipolar linear hall effect sensor 3-pin [SOT-23](https://kazus.ru/nuke/guid/packs/SOT-23/SOT-23.gif) (размер: 2.9 x 1.6 x 1.45мм)
//**High voltage (up to 38V) [Зачем высоковольтные при питании от USB/Li-Ion?]
//**Bipolar(А униполярные и тп подойдут? А для TMR если их сдвинуть каките нужны?)
linear hall effect sensor in a SOT-23 Датчик Холла (магнитный датчик) для монтажа на плате 2.5-38V Ana Bipolar Hall Effect Sensor
//**Редкие и дорогие сенсоры, находил в ритейле в 20+! раз дешевле варианты(
- LPF Resistor 1.5k Ohm 0805 package
- I2C / SPI pull-up resistor 4.7k Ohm 0805 package
- 0 Ohm Resistors for UART mode 0805 package
- Filter caps 100nF 0805 package
- SK6803 MINI-E (you can use SK6812 instead but dont use both under glow and per key as current draw is too high)\
//**хочу найти недорогие ARGBWW подобные адрессные светодиоды, но находил только крупные 5050*
//**если захочишь выводные ARGB LEDs - находил только 5мм круглые 2812 (но говорят, что их можно сточить!)
//**находил rgb выводные leds не адрессные и даже будто бы для свитчей клавиатур MX, но дорогущие х10+ ценой( +вопрос как этим всем управлять! Хотя мне бы хватило пары цветов для разных раскладок национальных алфавитов/слоев.
//**!В магнитных свитчах внутри освободилось полно места, сравнивая с обычными механическими свитчами! Теперь там и сбоку, и сверху, и снизу место свободное - ВЛЕЗЕТ ПАРА-ТРОЙКА светодиодов разных цветов! В этом есть жирный плюс, т.к. они лучше будет подсвечивать свои области с разными символами в полупрозрачных кейкапах. Основной сверху и дополнительный сбоку снизу, можно попробовать убрать засветы вокруг кейкапов-свитчей!  
- M2.5, 3mm brass stand offs 
- M2.5, 12mm screws with flat tops
- M2.5 x 6 x 0.4mm washers 
- M2.5 nuts 1.8mm thick
- My 3d Printed case!
//**pcb -> hotswappable 3d printed Amoeba like mini boards for handwiring! There nothing like this for now( So needed HE/TMR to-92s, not sot23 HE. Also ARGB/ARGBWW?? (I do not lose hope of finding them in a suitable case and cheap)

## How To Install

- ...

## To do

- OLED code implementation
- implement auto calibration
- QMK port
- New HE sensor? (**TMR sensors??)
- (** testing compatibility swap to TMR sensors without changing ? Which of them to choose? What sensor Ics used in [fun60-ultra](https://www.monsgeek.com/product/fun60-ultra/)? They are placed little not in the center of the switchsбд so possible 3pin and 5pin hotswap with simple mech switches))
- (**Redesigning pcb to +-=analog of AKKO "MagMech" = Hot-swappable with 5-Pin Mechanical Switches. ([MagMech](https://www.monsgeek.com/blog/magmech-switch-between-magnetic-switches-and-mechanical-switches-freely/) Compatible TMR Version only)
- (** Void switch in low profile transparent version of keycaps-switchs? As in [FLUX keyboard](https://fluxkeyboard.com/) )


[GitHub Pages](https://pages.github.com/).


NEW STATUS UPDATE:

Am currently typing this update from the Lucca58HE! So its fully up and running now! There is definitely a slight latency with UART on the slave half of the keyboard. The PCB supports SPI which could potentialy have latency reductions. It might also be possible to get UART latency down too, especially once im using QMK.


OLD STATUS UPDATES:

Left half of the keyboard is now perfectly functioning under KMK! changing the actuation from from 0 to 3.5mm is possible, but some weirdness means theres a deadzone towards the end of the keystroke, it can be fixed by increasing the distance between the switch plate and PCB so not a big deal. Could probably be avoided with different HE sensors?

Working with QMK has proved a lot more difficult than i thought, so im going to get it working with KMK and circuitpython first, and then worry about QMK support after!

Hall effect sensors are currently resulting in a resolution of 0.00706mm, so things are looking very promising. My choice of HE sensor results in a voltage range of ~0 to ~0.4v, so using a different HE sensor with a greater sensitivity (not to be confused with resolution) could result in even greater resolution of distance traveled, as the 12bit ADC on the RP2040 references the internal 3.3v. Am going on family holiday soon so progress will slow down a lot, may not be able to finish the project until the new year... 
(** Интересно, а кто-нибудь использовал 16-битные и большего разрешения АЦП? Смысл какой-то в этом есть? 
Интересно бы посмотреть с комментариями инженеров, гиков и разработчиков, как добились 128kHz и тп, и что это даёт на практике? 
(в некоторых недорогих HE клавиатурах, в AULA/Mchoose/MOD...  и тп видел в рекламе-спецификациях, в варианте с дороже-приятнее комплектом: свитчи без люфта/корпус алюминиевый(но один фиг толстенный, что им мешает низкопрофильные делать!?)/металлическим плейтом(были и пластиковые аля толстый гнущийся ПЭТ и тп - тоже понравились, меньше говняются пылью и отпечатками, легкие, полупрозрачные!)/с листом силикона в бутерброде и тп)



![IMG_6613](https://github.com/Maka8295/Lucca-58HE/assets/108311420/4b1c28fb-dfae-451a-887c-c89deb428f4d)


![IMG_6614](https://github.com/Maka8295/Lucca-58HE/assets/108311420/ee2d040d-f45c-473e-afe9-ba04d163128f)



