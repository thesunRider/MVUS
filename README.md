# MVUS (Messaging and voice for Underwater Systems MVUS)

<img src="documentation/images/diver_front.jpg?raw=true" width="80%">

## Docs
Problem Statement: [Problem Statement](Problem_Statement.md)

Questionaire: [Questionare](Questionare.md)


### Requested Specifications:

| S.No | Parameters                 | Specifications                                                                                                                                            |
| ---- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1    | Mode of Communication      | Wireless, Full Duplex                                                                                                                                     |
| 2    | Operating modes            | Telephony mode; Emergency mode for transmitting SOS signal; Heart beat monitoring mode                                                                    |
| 3    | Modulation schemes         | Single sideband Suppressed carrier Amplitude modulation in STANAG 1475(NATO)/ EKM standard (Telephony mode); Emergency Pinger & Morse code of SOS signal  |
| 4    | Power                      | 5Watts                                                                                                                                                    |
| 5    | Maximum depth of operation | 80m                                                                                                                                                       |
| 6    | Working Distance           | 500m to 1000m                                                                                                                                             |
| 7    | Battery life               | About 6 hours                                                                                                                                             |
| 8    | Accessories                | Diver Headset; Push-to-talk (PTT) Buttons; Sensitive vibration detecting microphone laryngophone (Throat Mic) with finger PTT/ bone-conduction microphone |
| 9    | size                       | Compact and portable unit for fitment on diver’s suit- both combat and normal suits.                                                                      |


## Maximum Specifications

Transducer Spec: [[Hardware#Transducer]]
Transducer Frequency: 40Khz
Transducer Max Power : 5W

Battery Voltage: 12V
Battery Capacity: 5200mAh = 5.2Ah
Efficiency : 80%
Battery Life (FULL USE):   **Discharging Time = Battery Capacity x Battery Volt / Device Watt.**
5.2Ah x 12V * efficiency / 10W(usage-max) = 5.5Hr  

Modulation Scheme: AM Requested, FSK would be better
Data Encoding: Audio Interpolation Requested , but digital Scheme would be better as AI approach would help in better audio quality and better data security, REMEMBER we need to send additional details too.

### Design Thoughts
- AM would be preffered to conserve power as there would be no powerloss when there is no data transmission happening,whereas for FSK there is powerloss even when there is no data for trnsmission.
- FM would be preffered as there would be less distortion happening to FM based signals and Signal strength will be a constant independent of the medium losses, Furthermore an AGC wont be required for FM broadcasts
- FM (LESS COMPLEXITY) , AM (MORE COMPLEXITY)
- ASK using digital technique might be used too.

## Approaches Available
1. Generating Carrier: (AM)
	-  The asked approach is an AM based, using MC1496 we can generate the am dsb signal
	-  We can digitally sample the the signal and multiply it using a 40khz sine wave array to yield another signal,this can be easily ssb'd
	
	For FM
	- We can use a PLL to generate the requested frequency.
	
	For ASK
	- By using a full wave bridge driver and turning it on and off ASK is achieved.

2. Amplifying the signal would be done with a push pull amplifier.
3. Impedance Matching using a transformer and senting out the signal.
5. Decoding can be done: (AM & ASK)
	- MC1496 as a Profuct detector
	
	For FM
	- A PLL can be used to regenerate the signal.

6. Recover back the Digital/Analog Signal,Play it back.

## Approach Taken
Since we have a limited amount of time going ith ASK is the best option available.
Encoding and Decoding are done using simple Serial Chips like CH340G a a baud rate of 3600bps.

### Problems Facing
- Digital or Analog Modulation
- No Tranducer in hand, in hand 40khz transducer
- In hand Transducer very low power
- AGC is needed for low powered audio signal reception


## TODO's
- [ ] Create A PCB Layout
- [ ] Create CAD Files
- [x] Breif Test Acoustic Transmitter and Reciever in Air
- [ ] Create Underwater Channel simulations

## Acoustic Communications
Recieved signal is demodulated by passing it through a BPF then through a Full wave rectifier followed by an LPF.

Driver: https://www.edn.com/increase-piezoelectric-transducer-acoustic-output-with-a-simple-circuit/

ASK Demodlator: https://www.youspice.com/spiceprojects/spice-simulation-projects/radio-circuits-spice-projects/demodulators-spice-simulation-projects/ask-demodulator/

## Light Communications

Light communication would be held using blue light sources/green light sources, 460nm blue lasers will establish communication with long targets or for surface uplinks.

![[Pasted image 20220816051546.png|500]]

![[Pasted image 20220816171746.png|300]]
Referals: https://ocean-innovations.net/companies/deepsea/knowledgebase/understanding-basics-underwater-lighting/


## Channel Simulations
https://codeocean.com/capsule/2136333/tree/v2


#### Similar Products
- https://subsea-import.com/scubaphone-2000d

> Open on Obsidian for best results
