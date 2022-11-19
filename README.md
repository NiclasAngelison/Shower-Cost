# Shower-Cost

# By Niclas Angelison 

#
- [ ] Project overview


# With an ongoing energy crisis and high heating costs throughout Europe, I thought I would find out how much a shower costs. So my project is to show how long do you shower and how much does it cost? With an ESP32 board, two Dallas DS18B20 temerature senors and a FLow sensor YF-B10 i manage to setup Blynk cloud and the data i presented in the Blynk App. The projekt took about one week to total to finish.




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
>
>| ESP32     |  9€   | https://sizable.se/P.CE9S1/ESP32-30-pin                                         |
>
>| DS20B18   |  3€   | https://sizable.se/P.29Z3D/DS18B20-Temperatursensor-vattentat-med-1-meter-kabel |
>
>| YF-B10    |  20€  | https://digitalzakka.com/product/1-inch-water-flow-sensor-hall-sensor-switch-flow-meter-dn25-brass-water-meter-industrial-turbine-flowmeter-water-flow-sensor/?srsltid=AYJSbAd-aCvesRoM9pQvGGYC5gSx71MORl1fTLEDKyoSVcGTEDcChxkC-Xw |    








### Environment setup

I wouldn't call myself a coder, rather a newbie. But I had these steps presented to me and it worked. I have put the links below. I'm using a Windows PC but it's available for Mac OS as well.

I used Thonny for my IDE and hade to flash the board with new firmware (see steps in each link below)

### Project structure

![Skärmbild 2022-11-19 140542](https://user-images.githubusercontent.com/117173570/202852295-fccae283-3cb1-423a-bc16-944f7931b7bd.jpg)

Started with flashing the ESP32

- [Flash ESP32] https://nabucasa.github.io/esp-web-flasher/

- [ ] https://hackmd.io/@lnu-iot/SydH7MTcw#Windows-OS

- [ ] Follow the instructions...
- [ ] install Node js (needed for the plugin) https://nodejs.org/en/ 
- [ ] install the Atom IDE https://atom.io/
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

I have used the Blynk cloud platform, and the Blynk app. I thought Blynk had a good and easy to understand get started tutorial, for someone like me who was completely new to IOT. Blynk has limited the features for those using the free version. But if you want to use Blynk's full potential, you can get access to all functions for $4.99. However, for my project that was not necessary.

https://blynk.io/ Just register and hit the QuickStart and you are on you way, easy even for me "MR Newbie"


![Skärmbild 2022-11-19 154856](https://user-images.githubusercontent.com/117173570/202856801-fc92117f-8440-4cac-8a34-ae403a408b6a.jpg)




### The code


- [ ] Calculation

![Skärmbild 2022-11-19 165738](https://user-images.githubusercontent.com/117173570/202860056-0500b08a-4af7-43e0-96c9-1e1c1d061c6d.jpg)

   
Second pice of code is total time and to multiply the flow/liter with the price kWh energy/liter and send that data to the Blynk cloud with WIFI from my local network to Vpin´s specified in the Blynk setup and the code. 
   
![Skärmbild 2022-11-19 170624](https://user-images.githubusercontent.com/117173570/202860385-1ec50d50-d8f4-40a0-ada6-c212227a314d.jpg)

        
 We also added a WDT (watchdogtimer) so if and when something crashes the board reboots.
        
        
        
       


### The physical network layer

The data is sent when and if there are a reading from the flow sensor via my local wifi network to the blynk cloud using MQTT, then it projects to the Blynk app.

### Finalizing the design

https://user-images.githubusercontent.com/117173570/202861231-ec31e940-e48c-4169-aa47-ba6672c22482.mov



This type of project, "How long do you shower and how much does it cost" is not appreciated by my teenage children who spend the most time in the shower.
However, it gave an indication of what it costs and you can change your habits accordingly if you want to save on energy consumption. Now I have been lucky enough to lock in my electricity contract at a low level for three years. so this doesn't affect me that much, but those with variable electricity contracts will notice a big difference in the coming winter months.


The End!
