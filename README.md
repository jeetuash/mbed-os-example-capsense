# Introduction
This example demonstrates implementing CapSense® buttons and slider for PSoC® 6 MCU with Mbed OS using the [CapSense Middleware Library](https://github.com/cypresssemiconductorco/middleware-capsense). Additional PSoC 6-related code examples are available in other repos. See all examples at [Code Examples for Modus Toolbox](https://github.com/cypresssemiconductorco/Code-Examples-for-ModusToolbox-Software).

# Instructions to run the CapSense code example

1. Import the code example
 
        mbed import https://github.com/cypresssemiconductorco/mbed-os-example-capsense

2. Change working directory to the example folder
        
        cd mbed-os-example-capsense

3. Plug in the kit and ensure the kit is in DAPLink mode to allow programming from Mbed CLI. See *Switch Kit to DAPLink Mode* section in [ModusToolbox IDE User Guide](https://www.cypress.com/ModusToolboxUserGuide) for details. 

4. Compile the example and Program
    
        mbed compile --target CY8CPROTO_062_4343W --toolchain GCC_ARM --flash --sterm

        For other targets:
        mbed compile -m CY8CKIT_062_WIFI_BT -t GCC_ARM -f --sterm
        mbed compile -m CY8CKIT_062_BLE -t GCC_ARM -f --sterm

    **Note:** The *--sterm* option opens the serial terminal with 9600-8N1 setting on the command prompt itself after programming completes. Do not use this option if you wish to connect using another serial terminal application.

4. Following message is displayed on the serial terminal when the application starts running.

        Application has started. Touch any CapSense button or slider.

5. Touch the buttons or the slider to observe the red LED changing its state and the status printed on the serial terminal. 

6. You can also monitor the CapSense data using the CapSense Tuner application as explained below.

# How to monitor data using CapSense Tuner

1. Open *\<user_home>/ModusToolbox_\<version>/tools/capsense-configurator-\<version>/capsense-tuner* to run the CapSense Tuner application. 

2. Click File -> Open and open cycfg_capsense.h file which is available in this example directory. 

3. Switch from DAPLink mode to KitProg mode. 

- For single-button kits (CY8CPROTO_062_4343W) press button SW3 (MODE) for more than 2 seconds and release.
- For two-button kits (CY8CKIT_062_BLE and CY8CKIT_062_WIFI_BT) press and release button SW4 (CUSTOM APP).

4. In the Tuner application, click the settings icon or click Tools -> Tuner Communication Setup. In the window that appears, select I2C under KitProg and configure as follows. 

        I2C Address: 8
        Sub-address: 2-Bytes
        Speed (kHz): 400

5. Click the Connect button or Communiction -> Connect.

6. Click the Start button or Communication -> Start.

7. Under Widget View tab on the right side, you can see the corresponding widgets turning blue when you touch the button or slider. You can also view the sensor data in Graph View tab. e.g. To view sensor data for Button 0, you need to select Button0_Rx0 under Button0. 

See the ModusToolbox CapSense Tuner Guide (Help -> View Help) for more information. 

# How to modify the CapSense settings for this project

In this process, you cannot modify the pins or add/delete the CapSense widgets. You can only modify the CapSense settings such as IDAC, clock, threshold etc. 

1. Open *\<user_home>/ModusToolbox_\<version>/tools/capsense-configurator-\<version>/capsense-configurator* to run the CapSense Configurator application. 

2. Click File -> Open and open cycfg_capsense.h file which is available in this example directory.

3. When you save the changes, the tool updates cycfg_capsense.h and cfg_capsense.c files in this example project. 

# Reference

- CapSense Middleware API Reference - See *pdl_api_reference_manual.html* under ModusToolbox installation directory *\<user_home>/ModusToolbox_\<version>/libraries/psoc6sw-\<version>/docs*
- [CapSense Configurator Guide](https://www.cypress.com/ModusToolboxCapSenseConfig)
- [CapSense Tuner Guide](https://www.cypress.com/ModusToolboxCapSenseTuner)
- [ModusToolbox IDE User Guide](https://www.cypress.com/ModusToolboxUserGuide)
- [CY8CPROTO-062-4343W PSoC 6 Wi-Fi BT Prototyping kit](http://www.cypress.com/documentation/development-kitsboards/cy8cproto-063-4343w)
- [CY8CKIT-062-WiFi-BT PSoC 6 WiFi-BT Pioneer Kit](http://www.cypress.com/documentation/development-kitsboards/psoc-6-wifi-bt-pioneer-kit)
- [CY8CKIT-062-BLE PSoC 6 BLE Pioneer Kit](http://www.cypress.com/documentation/development-kitsboards/psoc-6-ble-pioneer-kit)
