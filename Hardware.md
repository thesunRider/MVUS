# Hardware 

## Transducer

Target Frequency : 40khz
Bandwidth: 3khz

#### Low Power
Transducer Model: V40AN12T(R)

![[Pasted image 20220810203418.png| 400]]

Vrms: Vpp x 0.3535 = 7.07V
R(40khz) = 800ohms [From Datasheet](Ultrasonic_Sensor_Datasheet_REV1.1.pdf)
Prms = 7x7/800 = 61mW

#### Medium Power
Transducer Model: V40AW25B
![[Pasted image 20220810205248.png|400]]

Vrms : 42V
R(40khz) : 1000ohms [From Datasheet](Ultrasonic_Sensor_Datasheet_REV1.1.pdf)
Prms = 42 x 42/ 1000 = 1.764W


## Light Communication

For demodulating - a Transimpedance amplifier was used:
![[Pasted image 20220821025454.png]]

Demodulator Reference: [[Photodiode_detector.pdf]]

## Biasing TL072

> ![[Pasted image 20220821035351.png]]
> I have used the TL072 op-amp a lot because it is a quiet amplifier, good enough for at least 16 bit audio. But it is designed for +/- 12 volt to +/- 15 volt power supplies. The trick is to insert a 10 K resistor from the output pin to Vcc.
>
> This causes an offset current that stabilizes the op-amp. Replace your 1 Meg resistor with a 100 K resistor. Delete your 50 ohm resistor. Insert a 10 uF capacitor with the (+) pin connected to your IN- input. Do not use your IN+ input as this is not an instrument amplifier. Now you have a single ended input with a gain of 10, and a stable op-amp.
> 
> Because your output has a voltage equal to 1/2 Vcc on it, I would insert a 47uF capacitor at the output with the (+) pin going to the op-amp output.
> 
> The pin your pointing at with a red arrow is the Vee or V- pin, which normally goes to a -12 volt to -15 volt rail. You can just ground it if you use the trick I mentioned in the first paragraph. Without that 10K pull-up resistor the op-amp may produce severe distortion. Adjust the 100K resistor if you need more gain. For stability and ripple filtering there should be a 47 uF capacitor from Vcc to the ground (Vee/V-) pin.

Reference: https://electronics.stackexchange.com/questions/348898/need-some-help-building-a-tl072-preamp-circuit

