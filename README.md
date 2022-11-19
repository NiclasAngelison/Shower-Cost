# Shower-Cost

# By Niclas Angelison 

#
- [ ] Project overview


# With an ongoing energy crisis and high heating costs throughout Europe, I thought I would find out how much a shower costs. So my project is to show how long do you shower and how much does it cost? With an ESP32 board, two Dallas DS18B20 temerature senors and a FLow sensor YF-B10 i manage to setup Blynk cloud and the data i presented in the Blynk App. The projekt toke about one week to total to finish.




### Objectives

I chose this project considering how much electricity costs have skyrocketed. Some days 1kwh costs up to 10 SEK, completely crazy.
Maybe you become more aware by practicing how much money you flush down the drain every time you take a long shower. You may not be alone at home, but you have a family that also showers every day. A ten-minute shower may not cost that much, but if you first multiply by 4 people and then 30 days, it adds up to a lot of money.
I think if you see how much your regular routine shower costs, you'll know what you can do to save money.


### Material

- DOIT ESP32 Devkit V1




![Skärmbild 2022-11-19 125727](https://user-images.githubusercontent.com/117173570/202850059-5dd53917-10b1-402a-92b8-18f4c1dbe2ef.jpg)




- DS18B20 Temp sensor X2






![Skärmbild 2022-11-19 125908](https://user-images.githubusercontent.com/117173570/202849840-674dd9f1-7c41-4529-ae35-b5451fa125ba.jpg)






- 1" flow sensor YF-B10







![Skärmbild 2022-11-19 130101](https://user-images.githubusercontent.com/117173570/202849848-ce1eab49-aaac-456a-8e72-28d9e9baada8.jpg)






- Some wireing and a dev board to setup the project






### What, how much and where?


>| Name      | Price | Link                                                                            | 
>| --------- | ------|---------------------------------------------------------------------------------|
>| ESP32     |  9€   | https://sizable.se/P.CE9S1/ESP32-30-pin                                         |
>|-----------|-------|---------------------------------------------------------------------------------|
>| DS20B18   |  3€   | https://sizable.se/P.29Z3D/DS18B20-Temperatursensor-vattentat-med-1-meter-kabel |
>|-----------|-------|---------------------------------------------------------------------------------|
>| YF-B10    |  20€  | https://digitalzakka.com/product/1-inch-water-flow-sensor-hall-sensor-switch-flow-meter-dn25-brass-water-meter-industrial-turbine-flowmeter-water-flow-sensor/?srsltid=AYJSbAd-aCvesRoM9pQvGGYC5gSx71MORl1fTLEDKyoSVcGTEDcChxkC-Xw |    








### Environment setup

I wouldn't call myself a coder, rather a newbie. But I had these steps presented to me and it worked. I have put the links below. I'm using a Windows PC but it's available for Mac OS as well.

I used Thonny for my IDE and hade to flash the board with new firmware (see steps in each link below)

### Project structure

![Skärmbild 2022-11-19 140542](https://user-images.githubusercontent.com/117173570/202852295-fccae283-3cb1-423a-bc16-944f7931b7bd.jpg)

Started with flashing the ESP32

- [Flash ESP32] https://nabucasa.github.io/esp-web-flasher/

- [Install Nodejs] https://nodejs.org/en/ Follow the instructions...
- [ ] install Node js (needed for the plugin)
- [ ] install the Atom IDE
- [ ] add the Pymakr plugin to your Atom


### Putting everything together

My test setup...







![IMG_1929](https://user-images.githubusercontent.com/117173570/202854273-d760f703-521a-4939-a5b8-75c5c88df3b7.jpg)


Wiring

![Skärmbild 2022-11-19 150440](https://user-images.githubusercontent.com/117173570/202854520-8ad32562-a8c8-458a-a682-8abe8c72525a.jpg)


When everyting was working i started to calibrate the flowsensor. The sensor spec was Q=7.5 ( Q = L/min ) but this was all wrong.
I start by putting the test to pour exactly 4 liters of water through the flow sensor. The result was Q = 8.25/min.
The next step will be to test it with continuous flow from my garden hose, by filling a 25Liter canister. The "Q" factor changes again to 8.95/min. Q = 8.95 is an important factor in all the calculations that you will see in the code.



![tratt](https://user-images.githubusercontent.com/117173570/202855811-7633379f-3a44-42d7-aa95-4153dc59a25a.jpeg)





![slang](https://user-images.githubusercontent.com/117173570/202855828-8330dd8d-d589-462c-8197-7199d8849af4.jpeg)



![Dunk](https://user-images.githubusercontent.com/117173570/202855835-8d9ae25a-5ca5-4238-9055-560336b2616a.jpeg)

![flowsensor install](https://user-images.githubusercontent.com/117173570/202855843-89bbb11d-2a8e-4d8c-a1a7-5e8bbb06195b.jpeg)
### In the picture above you can see my installation of the flow sensor and the two temperature sensors



### Platforms and infrastructure

I have used the Blynk cloud platform, and the Blynk app. I thought Blynk had a good and easy to understand get started tutorial, for someone like me who was completely new to IOT. Blynk has limited the features for those using the free version. But if you want to use Blynk's full potential, you can get access to all functions for $4.99. However, for my project they were not necessary.

https://blynk.io/ Just register and hit the QuickStart and you are on you way very easy even for me "MR Newbie"


![Skärmbild 2022-11-19 154856](https://user-images.githubusercontent.com/117173570/202856801-fc92117f-8440-4cac-8a34-ae403a408b6a.jpg)




### The code


import BlynkLib
from machine import Pin
import time, sys
from onewire import DS18X20
from onewire import OneWire
import random
from machine import WDT
import boot


### The Calculation

The code below is my calculation to convert two temperatures, Hot and coldwater and a fixed Electricity Price to kWhEnergy for A Liter warmwater.

def calculateCost(consumedWaterInLiter):
   print("received consumed water in liter: {}".format(consumedWaterInLiter))
   pricePerLiter = 2.21 # Electricity Price for kWh in SEK incl all
   hotWaterTemperature.start_conversion()
   coldWaterTemperature.start_conversion()
   time.sleep(1)
   hotWater = hotWaterTemperature.read_temp_async()
   coldWater = coldWaterTemperature.read_temp_async()
   print(hotWater)
   print(coldWater)
   if(hotWater is not None and coldWater is not None):
    tempDifference = hotWater - coldWater
   else:
    print("testing....")
    sys.exit("Temperature returned None!") 
   print("hot/cold water temp diff: {}".format(tempDifference))
   kWhEnergyForALiter = 4.18 * tempDifference / 3600
   print("kWh/liter: {}".format(kWhEnergyForALiter))
   consumptionPrice = kWhEnergyForALiter * pricePerLiter * consumedWaterInLiter
   return consumptionPrice
   
Second pice of code is total time and to multiply the flow/liter with the price kWh energy/liter and send that data to the Blybk cloud with WIFI from my local network to Vpin´s specified in the Blynk setup and the code. 
   
   while True:
    blynk.run()
    blynk.virtual_write(16, random.randint(0, 100))
    wdt.feed()
    try:
        start_pulseCount = 1
        time.sleep(1)
        start_pulseCount = 0
        totalFlow = 0
        flow = (pulseCount / 8.95 / 60) # Pulse frequency (Hz) = 7.5Q, Q is flow rate in L/sec.
        while flow != 0: # While water is running
            blynk.virtual_write(16, random.randint(0, 100))
            wdt.feed()
            if(time.time() - lastTrigger > sampleTimeInSec):
                print("Time passed: {}".format(time.time() - lastTrigger))
                lastTrigger = time.time()
                print("The flow is: {}".format(flow))
                totalFlow = totalFlow + flow # Adding current flow to the total
                print("Total water flow is: {}".format(totalFlow))
                showerTimeInSec()
                print("Shower time in sec is: {}".format(showerTime))
                pulseCount = 0
                start_pulseCount = 1
                time.sleep(1)
                start_pulseCount = 0
                flow = (pulseCount / 8.95 / 60) # Pulse frequency (Hz) = 7.5Q, Q is flow rate in L/sec.
                #flow = random.randint(0, 10) # substitute this with line above when connecting sensor
        print("shower done")
        if(totalFlow != 0 and showerTime != 0):
            averageWaterConsumptionInLiter = totalFlow / showerTime * 2 # sampling is every two seconds 
        consumedWaterInLiter = averageWaterConsumptionInLiter * showerTime
        showerCost = calculateCost(consumedWaterInLiter)
        if(showerCost != 0.0): 
            print("Sending Cost") # Send cost value to your tracking application
            blynk.virtual_write(1, showerTime)
            blynk.virtual_write(2, showerCost)
        print("Shower Cost is: %.2f SEK" % (showerCost))
        showerTime, lastTrigger, averageWaterConsumptionInLiter = 0, 0, 0 # Resetting variables for next shower session
        
 We also added a WDT (watchdogtimer) so if and when something crashes the board reboots.
        
        
        
        

Import core functions of your code here, and don't forget to explain what you have done. Do not put too much code here, focus on the core functionalities. Have you done a specific function that does a calculation, or are you using clever function for sending data on two networks? Or, are you checking if the value is reasonable etc. Explain what you have done, including the setup of the network, wireless, libraries and all that is needed to understand.


```python=
import this as that

def my_cool_function():
    print('not much here')

s.send(package)

# Explain your code!
```

### The physical network layer

How is the data transmitted to the internet or local server? Describe the package format. All the different steps that are needed in getting the data to your end-point. Explain both the code and choice of wireless protocols.

- [ ] How often is the data sent? 
- [ ] Which wireless protocols did you use (WiFi, LoRa, etc ...)?
- [ ] Which transport protocols were used (MQTT, webhook, etc ...)
- [ ] Elaborate on the design choices regarding data transmission and wireless protocols. That is how your choices affect the device range and battery consumption.
- [ ] What alternatives did you evaluate?
- [ ] What are the design limitations of your choices?

### Visualisation and user interface

Describe the presentation part. How is the dashboard built? How long is the data preserved in the database?

- [ ] Provide visual examples on how the visualisation/UI looks. Pictures are needed.
- [ ] How often is data saved in the database. What are the design choices?
- [ ] Explain your choice of database. What kind of database. Motivate.
- [ ] Automation/triggers of the data.
- [ ] Alerting services. Are any used, what are the options and how are they in that case included.

### Finalizing the design

Show the final results of your project. Give your final thoughts on how you think the project went. What could have been done in an other way, or even better? Pictures are nice!

- [ ] Show final results of the projec
- [ ] Pictures
- [ ] *Video presentation
