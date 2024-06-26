# Traffic Lights 

This university project aims to put into practice the knowledge of sequential circuits, flip-flops, latches, and state tables through the construction of a set of traffic lights, with red and green LED lights

The circuit aims to handle the control of the lights of a traffic light, through a clock. 

## Activation

To activate the circuit, we make sure that the simulation is activated and we click on the clock. 
 
The traffic light will start with the green light on, and thanks to the 7-segment LEDS, it allows to display the decimal numbers in the countdown. The green traffic light is represented by the two green LEDs (decimal and unit) and descends from the number 12 to 0. For the flank to last 1 seconds, set the tick to a frequency of 2Hz, since there are 2 ticks for the clock,so, 5 seconds plus 0.5 second (2Hz=0.5 second)

Likewise for the red traffic light, the LEDS are red, and they descend from 24 to 0. While a traffic light is on, the other color display the numbers “00” indicating that they are not activated.  
 
Below is an image of the LEDS in operation. The green light of traffic light is on, and its LED is number seven. When it reaches zero, the Red traffic light LED will turn on for 24 seconds, and we will see its countdown in the display.

![](/images/image2.jpg)

## Building the circuit

To build the circuit, I created these circuit folders:
* main
* counter 12SEGUNDOS
* flip flop 4 bit TIPO D
* COMB12
* counter 24SEGUNDOS
* flip flop 5 bit TIPO D
* COMB24
* DECODIFICADOR_unidades
* DECODIFICADORES_decenas

The two counters (counter 12SEGUNDOS and counter 24SEGUNDOS) are both counters, one for each state of the traffic light, and therefore different durations.

## Counter 12SEGUNDOS

![](/images/image3.jpg)

As we can see, its circuit has 2 circuit boxes: 4-bit flipflop TIPO D (4 bits, since it will be used for the green of the traffic light, duration of 12 seconds, and therefore, no more than 4 bits for binary number representation.
A circuit called COMB12 has also been created to pass to the decoder the number to be displayed  (if it is 0, it will show 12 - if 9, it'll be 8 - if 3, it'll be 2)

## Flip-Flop 4 bits  formed by 4 Flip-Flops type D: 

![](/images/image4.jpg)

## COMB12 circuit table inside 12 second counter:

![](/images/image5.jpg)

With a type D flip-flop we can store a bit of information. Since we need 4 bits for the green traffic light counter, I simply put 4 of them together, with the same clock input for all of them, and an individual “D” for each bit. The exits will be their respective “Q”s. 
The correct functioning of COMB12 will depend on the correct preparation of the table. I want to program the circuit so that its outputs give us the correct previous numbers of the entries. If the Qs entries form the number “0000” (zero in 4-bit binary), its FUTURE outputs of “Qa” will form “1100” (number 12), and thus forms its countdown loop.

The same will happen for the 24 second counter, with the difference that this time, 5 bits will be needed to carry out its process:

## Counter 24SEGUNDOS (left) and its 5-bit TYPE D Flip-flop (right):

![](images/image6.jpg)

## main

The counter will be connected to the clock (same clock for the entire circuit).

![](/images/image7.jpg)

Left image: before starting. Right image: first “tick”

![](/images/image8.jpg)

Both counters are connected to their respective decoders to that can shape the numbers on the 7-segment display. 
The image above is the circuit system that makes the ignition an exclusive LED (so red and green cannot light up at the same time). Its bottom element (a flip-flop D) is responsible for giving the starting point (image “left” above) of the mechanism, and therefore, the system starts with the green light:               
when all inputs to the logical NOR port are zero, the output is 1. 1 will be the                input of the flip-flop type D which will have an output Q of value o (zero).                  
Thus Q' will be 1 and will activate the OR gate of the green traffic light.

![](/images/image9.jpg)

(type D flip-flop responsible for activating the OR gate of the green LED).

The circuit is efficient and functional, operating in a loop once activated.