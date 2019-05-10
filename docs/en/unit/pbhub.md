# Unit PbHUB {docsify-ignore-all}

<img src="assets/img/product_pics/unit/pbhub/pbhub_p1.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/pbhub/pbhub_p2.png" width="30%" height="30%"><img src="assets/img/product_pics/unit/pbhub/pbhub_grove_a.png" width="30%" height="30%">

***

:memo:**[Description](#Description)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:electric_plug:**[Schematic](#Schematic)** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[Purchase](https://www.aliexpress.com/store/product/New-Arrival-M5Stack-Official-I-O-Hub-1-to-6-Expansion-Grove-I-O-Interface-for/3226069_33006652505.html?spm=2114.12010612.8148356.36.1e112c5cR01Vkh)**

<!-- :memo:**[Description](#Description)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:octocat:**[Example](#Example)**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; :electric_plug:**[Schematic](#Schematic)** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🛒**[Purchase](https://www.aliexpress.com/item/New-Arrival-M5Stack-Official-I2C-Hub-1-to-6-Expansion-Grove-I2C-Interface-for-Arduino-Blockly/32998974179.html?gps-id=pcStoreJustForYou&scm=1007.23125.122752.0&scm_id=1007.23125.122752.0&scm-url=1007.23125.122752.0&pvid=0cd77ea5-52b2-4aa7-856b-0dd4e43ee0d1&spm=a2g1y.12024536.smartJustForYou_39076158.12)** -->

## Description

**PbHUB**, is a expander for singel-bus GROVE PORTB(Black port on M5GO Base). 1-to-6. PortB can be used as GPIO and analog in two data lines connected to GPIO36 and GPIO26 on ESP32. Same as PaHUB, it provides a solution for mutiple device control by PORTB. With PbHUB each of the IO can be configurated to input, output and analog in as you like. Unfortunatly this Unit is unnested.
It is build with a MEGA328, with a simple driver firmware inside.

The I2C address of this unit is 0x40(Changable by resistors).

*Notice: Please pay attention to the channel order while programing*

<img src="assets/img/product_pics/unit/pbhub/pbhub_p3.png">

## Product Features

- Single-Bus GROVE PORTB Expander
- Two Lego-compatible holes
- Nested allowed
- 1-To-6

## Include

- 1x PbHUB Unit
- 1x Grove Cable

## Driver Protocol

- protovol type - I2C
- address - 0x61
- Set oneLED Color* : LED address(2bytes) + RGB value(3bytes)
- Set moreLED Color* : LED start address(2bytes) + LED end address(2bytes) + RGB value(3bytes)

<table>
    <tr>
        <td>state</td><td>IO0 Digital Write</td><td>IO1 Digital Write</td><td>IO0 Analog Write</td><td>IO1 Analog Write</td><td>IO0 Digital Read</td><td>IO1 Digital Read</td><td>IO0 Analog Read</td><td>reserve</td><td>Set Neopixle Num</td><td>Set oneLED Color*</td><td>Set moreLED Color*</td><td>Set Brightness</td>
    </tr>
    <tr>
        <td>r/w</td></td></td><td>w</td><td>w</td><td>w</td><td>w</td><td>r</td><td>r</td><td>r</td><td>r</td><td>w</td><td>w</td><td>w</td><td>w</td></tr>
    <tr>
        <td>data length (Byte)</td><td>1</td><td>1</td><td>1</td><td>1</td><td>1</td><td>1</td><td>2</td><td>/</td><td>2</td><td>5</td><td>7</td><td>1</td>
    </tr>
    <tr>
        <td>ch0 cmd</td></td><td>40</td><td>41</td><td>42</td><td>43</td><td>44</td><td>45</td><td>46</td><td>47</td><td>48</td><td>49</td><td>4A</td><td>4B</td>
    </tr>
    <tr>
        <td>ch1 cmd</td></td><td>50</td><td>51</td><td>52</td><td>53</td><td>54</td><td>55</td><td>56</td><td>57</td><td>58</td><td>59</td><td>5A</td><td>5B</td>
    </tr>
    <tr>
        <td>ch2 cmd</td></td><td>60</td><td>61</td><td>62</td><td>63</td><td>64</td><td>65</td><td>46</td><td>67</td><td>68</td><td>69</td><td>6A</td><td>6B</td>
    </tr>
    <tr>
       <td>ch3 cmd</td></td><td>70</td><td>71</td><td>72</td><td>73</td><td>74</td><td>75</td><td>76</td><td>77</td><td>78</td><td>79</td><td>7A</td><td>7B</td>
    </tr>
    <tr>
        <td>ch4 cmd</td></td><td>80</td><td>81</td><td>82</td><td>83</td><td>84</td><td>85</td><td>86</td><td>87</td><td>88</td><td>89</td><td>8A</td><td>8B</td>
    </tr>
    <tr>
       <td>ch5 cmd</td></td><td>A0</td><td>A1</td><td>A2</td><td>A3</td><td>A4</td><td>A5</td><td>A6</td><td>A7</td><td>A8</td><td>A9</td><td>AA</td><td>AB</td>
    </tr>
</table>

## Related Link

- **[Offical Video](https://www.youtube.com/channel/UCozgFVglWYQXbvTmGyS739w)**

- **[Forum](http://forum.m5stack.com/)**

- Driver firmware - **[PbHUB](https://github.com/m5stack/PbHUB/tree/master/PortB_HUB/Firmware)**

- Test code - **[PbHUB](https://github.com/m5stack/PbHUB/tree/master/PortB_HUB)**

<!-- ## Example

### 1. Arduino IDE

*The code below is incomplete. To get complete code, please click [here](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/Makey_NewVersion/Arduino/Makey_new_version).*

```arduino
#include <M5Stack.h>
#include <Wire.h>

// initialization
M5.begin();
pinMode(21, INPUT); pinMode(22, INPUT);
Wire.begin();// Init I2C

// read data
Wire.requestFrom(MAKEY_ADDR, 2);
while (Wire.available()) {
  Key1 = Wire.read();//read data from MAKEY
  Key2 = Wire.read();//read data from MAKEY
  tone_key = (Key2<<8) | Key1;// the following picture will explain "tone_key"
}
```

<img src="assets/img/product_pics/unit/unit_example/MAKEY/tone_key_pitch_zh_CN.png">

<img src="assets/img/product_pics/unit/M5GO_Unit_makey_04.png" width="30%" height="30%">

### 2. UIFlow

*To get complete code, please click [here](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/Makey_NewVersion/UIFlow).*

<img src="assets/img/product_pics/unit/unit_example/MAKEY/example_unit_makey_02.png"> -->

## Schematic

<img src="assets/img/product_pics/unit/pbhub/pbhub_sch.png">

### PinMap

<table>
 <tr><td>M5Core(GROVE A)</td><td>GPIO22</td><td>GPIO21</td><td>5V</td><td>GND</td></tr>
 <tr><td>PbHUB Unit</td><td>SCL</td><td>SDA</td><td>5V</td><td>GND</td></tr>
</table>

<!--
<img src="assets/img/product_pics/unit/M5GO_Unit_makey_03.png" width="30%" height="30%"> -->