# WiFiJoystick
--------------
[MunichMakerLab - Project WiKi Page](https://wiki.munichmakerlab.de/wiki/WiFiJoystick)
<table>
  <tr>
    <th colspan="2">
This project shows a short description of how to create a WiFi enabled Gamepad / Joystick. The WiFiJoysticks can be used to play games on LED-Panels on events like makerfaires.
    </th>
  </tr>
  <tr style="vertical-align: top;">
    <td vAlign="top">
      <strong>Table of Contents</strong>
      <ul>
        <li><a href="#joystick--buttons">Joystick & Buttons</a>
          <ul>
            <li><a href="#pin-mapping">pin mapping</a></li>
            <li><a href="#mqtt-topics-receive">mqtt topics (receive)</a></li>
            <li><a href="#mqtt-messages-sending">mqtt messages (sending)</a></li>
          </ul>
        </li>
        <li><a href="#status-leds">status LEDs</a>
          <ul>
            <li><a href="#mqtt-topics-receive-2">mqtt topics (receive)</a></li>
          </ul>
        </li>
        <li><a href="#ic-io-expander">I²C IO expander</a></li>
      </ul>
    </td>
    <td>
      <img src="https://wiki.munichmakerlab.de/w/images/thumb/7/7c/WiFiJoystick_joystick.jpg/300px-WiFiJoystick_joystick.jpg" alt="Joystick" />
    </td>
  </tr>
</table>

## Joystick & Buttons
### pin mapping
<table>
  <tr>
    <th>function</th>
    <th>state 1</th>
    <th>state 2</th>
    <th>state 3</th>
    <th rowspan="6"><img alt="joystick" src="https://wiki.munichmakerlab.de/w/images/thumb/7/7a/WiFiJoystick_pins_color.jpg/300px-WiFiJoystick_pins_color.jpg"></td>
  </tr>
  <tr>
    <td><strong>push button</strong></td>
    <td><img alt="pushbutton state1" src="https://wiki.munichmakerlab.de/w/images/thumb/a/a8/WiFiJoystick_pushbutton.png/50px-WiFiJoystick_pushbutton.png"></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td><strong>left</strong></td>
    <td><img alt="left state1" src="https://wiki.munichmakerlab.de/w/images/thumb/6/60/WiFiJoystick_left1.png/50px-WiFiJoystick_left1.png"></td>
    <td><img alt="left state2" src="https://wiki.munichmakerlab.de/w/images/thumb/b/b1/WiFiJoystick_left2.png/100px-WiFiJoystick_left2.png"></td>
    <td><img alt="left state3" src="https://wiki.munichmakerlab.de/w/images/thumb/4/44/WiFiJoystick_left3.png/150px-WiFiJoystick_left3.png"></td>
  </tr>
  <tr>
    <td><strong>right</strong></td>
    <td><img alt="right state1" src="https://wiki.munichmakerlab.de/w/images/thumb/e/e7/WiFiJoystick_right1.png/50px-WiFiJoystick_right1.png"></td>
    <td><img alt="right state2" src="https://wiki.munichmakerlab.de/w/images/thumb/a/aa/WiFiJoystick_right2.png/100px-WiFiJoystick_right2.png"></td>
    <td><img alt="right state3" src="https://wiki.munichmakerlab.de/w/images/thumb/e/e6/WiFiJoystick_right3.png/150px-WiFiJoystick_right3.png"></td>
  </tr>
  <tr>
    <td><strong>up</strong></td>
    <td><img alt="up state1" src="https://wiki.munichmakerlab.de/w/images/thumb/1/11/WiFiJoystick_up1.png/50px-WiFiJoystick_up1.png"></td>
    <td><img alt="up state2" src="https://wiki.munichmakerlab.de/w/images/thumb/2/2a/WiFiJoystick_up2.png/100px-WiFiJoystick_up2.png"></td>
    <td><img alt="up state3" src="https://wiki.munichmakerlab.de/w/images/thumb/b/b8/WiFiJoystick_up3.png/150px-WiFiJoystick_up3.png"></td>
  </tr>
  <tr>
    <td><strong>down</strong></td>
    <td><img alt="down state1" src="https://wiki.munichmakerlab.de/w/images/thumb/6/63/WiFiJoystick_down1.png/50px-WiFiJoystick_down1.png"></td>
    <td><img alt="down state2" src="https://wiki.munichmakerlab.de/w/images/thumb/7/71/WiFiJoystick_down2.png/100px-WiFiJoystick_down2.png"></td>
    <td><img alt="down state3" src="https://wiki.munichmakerlab.de/w/images/thumb/d/d0/WiFiJoystick_down3.png/150px-WiFiJoystick_down3.png"></td>
  </tr>
</table>

### mqtt topics (receive)
topic | payload | example
--- | --- | ---
`WiFiJoystick/<CHIP-ID>/config` | *flags to configure* | **reboot**
`WiFiJoystick/<CHIP-ID>/brightness` | *brightness from 0 to 255* | **190**
`WiFiJoystick/<CHIP-ID>/debounce/push` | *debounce delay in ms* | **200**
`WiFiJoystick/<CHIP-ID>/debounce/button1` | *debounce delay in ms* | **200**
`WiFiJoystick/<CHIP-ID>/debounce/button2` | *debounce delay in ms* | **200**
`WiFiJoystick/<CHIP-ID>/debounce/left` | *state1,state2,state3 (debounce delay in ms)* | **150,100,200**
`WiFiJoystick/<CHIP-ID>/debounce/right` | *state1,state2,state3 (debounce delay in ms)* | **150,100,200**
`WiFiJoystick/<CHIP-ID>/debounce/up` | *state1,state2,state3 (debounce delay in ms)* | **150,100,200**
`WiFiJoystick/<CHIP-ID>/debounce/down` | *state1,state2,state3 (debounce delay in ms)* | **150,100,200**

### mqtt messages (sending)
topic | payload | example
--- | --- | ---
`WiFiJoystick/<CHIP-ID>/button/push` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/button1` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/button2` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/left1` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/left2` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/left3` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/right1` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/right2` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/right3` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/up1` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/up2` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/up3` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/down1` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/down2` | *press or release* | **press**
`WiFiJoystick/<CHIP-ID>/button/down3` | *press or release* | **press**

## status LEDs
### mqtt topics (receive)
topic | payload | example
--- | --- | ---
`WiFiJoystick/<CHIP-ID>/color/led1` | *solid / once / flash / fade ,red,green,blue (,interval,red2,green2,blue2)* | <p>**solid,255,0,0**<br/>(solid red)</p><p>**once,0,255,255,5000**<br/>(pink for 5s)</p>
`WiFiJoystick/<CHIP-ID>/color/led2` | *solid / once / flash / fade ,red,green,blue (,interval,red2,green2,blue2)* | <p>**fade,255,0,0,2000,0,255,0**<br/>(fade from red to green in 2s)</p><p>**flash,0,0,255,500**<br/>(flash from blue to black every 500ms)</p><p>**flash,255,0,0,1000,255,255,0**<br/>(flash from red to yellow every 1s)</p>

## I²C IO expander
The ESP8266 has too less IO pins - so we will use IO expander ICs with serial interface (I²C-Bus):

* [MCP 23017-E/SP (16-Bit I/O Expander with I²C-Bus Interface)](https://www.reichelt.de/index.html?ACTION=3;ARTICLE=140074;SEARCH=MCP%2023017-E/SP)
* [PCF 8574 T (8-Bit I/O Expander with I²C-Bus Interface)](https://www.reichelt.de/PCF-8574-T/3/index.html?&ACTION=3&LA=446&ARTICLE=39885&artnr=PCF+8574+T&SEARCH=PCF+8574+T)

