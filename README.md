# mdp-link

The [MDP-XP](http://www.miniware.com.cn/product/mdp-xp-digital-power-supply-set/) is a Digital Power supply composed of two modules, the M01 screen and the P905 power module.

My goal is to be able to communicate with the power modules from a laptop using USB, without requiring the M01 screen, and be able to record different parameters (V, I, W) over time to build power profiles, or even to graph them on the bigger screen.

The MDP modules use the `nrf24L01+` device for the 2.4GHz wireless communications, in ESB mode. More information about the chipset and the protocol can be found [here](https://infocenter.nordicsemi.com/pdf/nRF24L01P_PS_v1.0.pdf).

For more information about the MDP you can have a look [here](https://www.eevblog.com/forum/testgear/miniware-mdp-xp-digital-power-supply-set/).

I'm using an [nrf52840-mdk](https://wiki.makerdiary.com/nrf52840-mdk/) development kit, it includes a `nrf52840` microcontroller which has a radio that supports ESB.

To be able to compile this code you need to follow [the Apache Mynewt Quick Start](https://mynewt.apache.org/quick-start/). I recommend to setup both, the native tools, plus the docker container, because the support for 32 bits was deprecated in xcode 10 and you will avoid many troubles compiling for debugging.

Then run the following commands to build and flash the device:

```sh
newt build nrf52_boot
newt build nrf52_mdp_link
newt create-image nrf52_mdp_link 1.0.0
newt load nrf52_mdp_link
```

## Possible protocols for USB

- Adhoc binary protocol: to be designed ...
- [SCPI](http://sdphca.ucsd.edu/Lab_Equip_Manuals/SCPI-99.pdf)
- [LXI](http://www.lxistandard.org/members/Adopted%20Specifications/Latest%20Version%20of%20Standards_/LXI%20Standard%201.5%20Specifications/LXI%20Device%20Specification%20v1_5_01.pdf)
