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





![Skärmbild 2022-11-19 125727](https://user-images.githubusercontent.com/117173570/202849832-febdb551-3fe3-4de7-bd35-3fa573adf6a1.jpg)



- DS18B20 Temp sensor X2






![Skärmbild 2022-11-19 125908](https://user-images.githubusercontent.com/117173570/202849840-674dd9f1-7c41-4529-ae35-b5451fa125ba.jpg)






- 1" flow sensor YF-B10







![Skärmbild 2022-11-19 130101](https://user-images.githubusercontent.com/117173570/202849848-ce1eab49-aaac-456a-8e72-28d9e9baada8.jpg)






- Some wireing and a dev board to setup the project





Explain all material that is needed. All sensors, where you bought them and their specifications. Please also provide pictures of what you have bought and what you are using.

- [1] List of material
- [2] What the different things (sensors, wires, controllers) do - short specifications
- [3] Where you bought them and how much they cost


> Example:
>| IoT Thing | For this         |
>| --------- | ---------------- |
>| Perhaps   |                  |
>| is a      |                  |
>|-----------|------------------|
>
>In this project I have chosen to work with the Pycom LoPy4 device as seen in Fig. 1, it's a neat little device programmed by MicroPython and has several bands of connectivity. The device has many digital and analog input and outputs and is well suited for an IoT project.


>![LoPy!](https://pycom.io/wp-content/uploads/2018/08/lopySide-1.png)
>Fig. 1. LoPy4 with headers. Pycom.io


### Environment setup

How is the device programmed. Which IDE are you using. Describe all steps from flashing the firmware, installing plugins in your favorite editor. How flashing is done on MicroPython. The aim is that someone should be able to understand how to reproduce your project.

- [ ] Chosen IDE
- [ ] How the code is uploaded
- [ ] How is your project structured (important)
- [ ] Steps that you needed to do for your computer. Installation of Node.js, extra drivers, etc.

### Putting everything together

How is all the electronics connected? Describe all the wiring, good if you can show a circuit diagram. Be specific on how to connect everything, and what to think of in terms of resistors, current and voltage. Is this only for a development setup or could it be used in production?

- [ ] Circuit diagram (can be hand drawn) (Fritzing, Tinkercad, etc.)
- [ ] Electrical calculations
- [ ] Limitations of hardware depending on design choices.
- [ ] Discussion about a way forward - is it possible to scale?

### Platforms and infrastructure

Describe your choice of platform(s). You need to describe how the IoT-platform works, and also the reasoning and motivation about your choices. Have you developed your own platform, or used 

Is your platform based on a local installation or a cloud? Do you plan to use a paid subscription or a free? Describe the different alternatives on going forward if you want to scale your idea.

- [ ] Describe platform in terms of functionality
- [ ] Explain and elaborate what made you choose this platform
- [ ] Provide a pricing discussion. What are the prices for different platforms, and what are the pros and cons of using a low-code platform vs. developing yourself?

### The code

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
