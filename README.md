# Arduino vs WebApp

How getting started with Arduino porjects match up with WebApps.

## Episodes

1. EP 00 - blinking light

   **Arduino**

   - on board LED
   - external LED

   **WebApp**

   - open chrome
   - about:blank
   - CMD ⌘ OPT ⌥ J
     Using javascript

   ```
   setInterval(
      () => document.bgColor = document.bgColor === "red" ? "" : "red" ,
      1000
   )

   # and with the ability to stop

   blink1000 = setInterval(() => document.bgColor = document.bgColor === "red" ? "" : "red" ,1000)
   clearInterval(blink1000)
   ```

1. EP XX - push button

   **WebApp**

   TODO: work on size, style and toggling

   ```
   # about:blank

   div = document.createElement("div")
   div.setAttribute("id", "output")
   document.body.appendChild(div)

   button = document.createElement("button")
   button.textContent = "click me"
   button.setAttribute("onClick", "document.getElementById('output').innerHTML = 'clicked'")
   document.body.appendChild(button)
   ```

1. EP XX - Pulsing light

   ```
   style = document.createElement("style");
   style.textContent = '@keyframes pulse {         ' +
     '   from {background-color: white; }          ' +
     '   to {background-color: red; }              ' +
     '}                                            ' +
     'body {                                       ' +
     '   background-color: white;                  ' +
     '   animation-name: pulse;                    ' +
     '   animation-duration: 1s;                   ' +
     '   animation-iteration-count: infinite;      ' +
     '   animation-direction: alternate;           ' +
     '   animation-timing-function: ease-in-out;   ' +
     '}';
   document.body.appendChild(style);
   ```

1. EP XX - Light Dependent Resistor LDR

   ```
   // from a https site like
   open https://failure-driven.com

   navigator.geolocation.getCurrentPosition(
      (position) => {
         console.log(position);
         fetch(`https://api.sunrise-sunset.org/json?lat=${position.coords.latitude}&lng=${position.coords.longitude}&formatted=0`)
            .then(result => result.json())
            .then(result => console.log(result))
      });

   // find where you are now?
   Object.entries(results)
   .filter(([key, value]) => typeof(value) !== "number")
   .map(([key, value]) => [key, (new Date(Date.parse(value)))])
   .filter(([key, value]) => now < value)
   .sort((a, b) => a[1] < b[1] ? 0 : 1)

   // ???
   ```

1. EP XX - temperature sensor LM35

   **WebApp**

   ```
   // sign up for https://www.weatherapi.com/my/ and get your key
   open http://api.weatherapi.com/v1/current.json?key=d15...008&q=melbourne

   // cut and paste the fetch from the network tab

   // clear all the children
   Array.from(document.body.children).forEach(child => document.body.removeChild(child))

   outputDiv = document.createElement("div")
   outputDiv.setAttribute('style', 'font-size: 50vh')
   fetch("http://api.weatherapi.com/v1/current.json?key=d15...008&q=melbourne")
   .then(result => result.json())
   .then(result => outputDiv.textContent = result.current.temp_c);
   document.body.appendChild(outputDiv)
   ```

1. EP XX - RGB LED

   ```
   // chrome about:blank

   button = document.createElement("button")
   button.textContent = "click me"
   button.setAttribute("style", "font-size: 100px")
   document.body.appendChild(button)

   colors = ["red", "green", "blue", ""]
   index = 0
   button.onclick = () => {document.bgColor = colors[index]; index = (index + 1) % colors.length}
   ```

1. EP XX - Potentiometer
1. EP XX - Buzzer
1. EP XX - Relay
1. EP XX - IR remote control
1. EP XX - Tilt switch
1. EP XX - Temperature and humidity sensor

   **WebApp**

   ```
   # sign up for https://www.weatherapi.com/my/ and get your key
   open http://api.weatherapi.com/v1/current.json?key=d15...008&q=melbourne

   # cut and paste the fetch from the network tab

   # clear all the children
   Array.from(document.body.children).forEach(child => document.body.removeChild(child))

   outputDiv = document.createElement("div")
   outputDiv.setAttribute("style", "font-size: 10vh")
   outputTempDiv = outputDiv
   outputHumidityDiv = outputDiv.cloneNode()
   fetch("http://api.weatherapi.com/v1/current.json?key=d15...008&q=melbourne")
     .then(result => result.json())
     .then(result => {
       outputTempDiv.textContent = `temperature: ${result.current.temp_c} ℃`;
       outputHumidityDiv.textContent = `humidity: ${result.current.humidity} %`;
     });
   document.body.appendChild(outputTempDiv)
   document.body.appendChild(outputHumidityDiv)
   ```

1. EP XX - Servo
1. EP XX - Soil Moisture Sensor
1. EP XX - Touch Switch
1. EP XX - Hall Effect Sensor
1. EP XX - Alcohol sensor
1. EP XX - Laser
1. EP XX - Sound module
1. EP XX - Ultrasonic Range Finder
1. EP XX - Reed Switch
1. EP XX - Infra Red (IR) transmitter
1. EP XX - Flame sensor
1. EP XX - Remote power from 9V battery
1. EP XX - accelerometer
1. EP XX - vibration sensor
1. EP XX - piezo disk vibration sensor
1. EP XX - analog Carbon Monoxide Sensor MQ7
1. EP XX - triple Axis Accelerometer MMA7361
1. EP XX - IR motion sensor
1. EP XX - joystick module

as inspired by

- https://www.littlebird.com.au/products/little-bird-arduino-advent-kit
- https://core-electronics.com.au/advance-sensor-set-for-arduino.html

also take a look at

- https://www.auselectronicsdirect.com.au/rfid-uno-starter-kit-for-arduino-projects
- https://au.banggood.com/Geekcreit-37-In-1-Sensor-Module-Board-Set-Starter-Kits-Geekcreit-products-that-work-with-official-Arduino-boards-p-1137051.html
- https://www.ebay.com.au/itm/162084166921
- https://www.littlebird.com.au/products/beginner-kit-for-arduino-uno

and in particular one that I can link to and get a percentage
```
