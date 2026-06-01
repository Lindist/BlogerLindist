---
title: Guide How to use Cathoa IOT Dashboard (Demo) ENG
description: The Cathoa IOT Dashboard is a web application that allows you to monitor and control your IoT devices.
date: 2026-05-30 00:02:00 +0700
author: Cathoa
categories: [Blogging, Demo]
tags: [IOT,dashboard]
pin: true
math: true
mermaid: true
---

# How to use Cathoa IOT Dashboard

## 1. Login

### If you already have an account or want to try logging in with GitHub

1. Open your web browser and navigate to [Cathoa IOT Dashboard](https://cathoaiot.com/login)
2. Enter your username [EMAIL_ADDRESS] and password [PASSWORD]
3. Click "Login"

![Cathoa IOT Dashboard Login](/assets/img/cathoaIOTDashboard/LoginDashboardIOT.png){: .shadow .rounded }
_Cathoa IOT Dashboard Login_

### If you are not a member and want to register

1. Open your web browser and navigate to [Cathoa IOT Dashboard](https://cathoaiot.com/register) or click on "Request Provisioning"
2. Fill in your information in each field. Fields with red stars are required. Optional fields can be left blank.
3. Don't forget to check the PDPA checkbox.
4. Click on "Request Provisioning" to register.

   ![Cathoa IOT Dashboard Request Provisioning](/assets/img/cathoaIOTDashboard/RequestProvisioningDashboardIOT.png){: .shadow .rounded }
   _Cathoa IOT Dashboard Request Provisioning_

5. You will be redirected to the Back to Login page, and an email will be sent for confirmation.
6. Check your email and click on Verify Email Address.

![Cathoa IOT Dashboard Confirm](/assets/img/cathoaIOTDashboard/ConfirmEmailDashboardIOT.png){: .shadow .rounded }
_Cathoa IOT Dashboard Confirm_

## 2. When entering the Dashboard

1. After logging in, you will see a blank page. You can click on the profile picture in the top right corner to edit your name and picture.

   ![Cathoa IOT Dashboard Profile](/assets/img/cathoaIOTDashboard/ProfileDashboardIOT.png){: .shadow .rounded }
   _Cathoa IOT Dashboard Profile_

2. Next, download the library at [Cathoa IOT Library](https://github.com/Lindist/CathoaIOT-Library/releases/tag/v2.0.4.4)

   ![Cathoa IOT Library](/assets/img/cathoaIOTDashboard/CathoaIOT-Library.png){: .shadow .rounded }
   _Cathoa IOT Library_

3. Once downloaded, open the Arduino IDE to use the library. Go to Sketch > Include Library > Add .ZIP Library... > Select the CathoaIOT-Library.zip file > Click Open.

   ![Cathoa IOT Library](/assets/img/cathoaIOTDashboard/AddZipLibrary.png){: .shadow .rounded }
   _Cathoa IOT Library_

4. Don't forget to install these required libraries:

   ![Cathoa IOT ArduinoJson](/assets/img/cathoaIOTDashboard/ArduinoJson.png){: .shadow .rounded }
    _ArduinoJson_
   ![Cathoa IOT PubSubClient](/assets/img/cathoaIOTDashboard/PubSubClient.png){: .shadow .rounded }
    _PubSubClient_

## 3. Configuring data in Arduino IDE

### 1. Data display Widgets
1. Open the example file from the downloaded Cathoa IOT Library by going to File > Examples > CathoaIOT > BasicTelemetry_For_ESP8266andESP32. The example file window will open.
   ![Cathoa IOT Arduino BasicTelemetry_For_ESP8266andESP32](/assets/img/cathoaIOTDashboard/BasicTelemetry_For_ESP8266andESP32.png){: .shadow .rounded }
   _Cathoa IOT Arduino BasicTelemetry_For_ESP8266andESP32_
2. Complete the WiFi setup by entering your ssid and password.
3. Enter the DEVICE_ID obtained from the dashboard. Go to Edit Mode by clicking Edit layout on the left, then click Manage Dashboard on the right, and then click Create Device. Give the device a name, such as ESP32, then copy the ID and paste it into `DEVICE_ID`. If you are using an existing device, you can skip creating it and just copy the existing device ID.

    ![Cathoa IOT Create Device](/assets/img/cathoaIOTDashboard/CreateDevice.png){: .shadow .rounded }
    _Cathoa IOT Create Device_

4. Complete the MQTT setup by entering the MQTT_HOST, MQTT_PORT, MQTT_USER, MQTT_PASS. You can find these by clicking the gear icon in the top right corner. Copy the Broker hostname to `MQTT_HOST`, copy the Broker port to `MQTT_PORT`, copy the MQTT Username to `MQTT_USER`, and copy the MQTT Password to `MQTT_PASS`.
    ![Cathoa IOT MQTT](/assets/img/cathoaIOTDashboard/MQTT.png){: .shadow .rounded }
    _Cathoa IOT MQTT_
5. Upload the code to the board by clicking the Upload button. Make sure to select the correct board and port. In our examples, we recommend ESP32 and ESP8266.

#### DigitalValue Widget

1. Return to the Dashboard page, click the Manage Dashboard button, and go to create Widgets.
2. Select the Widget type DigitalValue.
3. Name the Widget and enter the subscribe key. In this example, we will use temperatureC and humidity for the subscribe key before clicking save.

    ![Cathoa IOT Set up Widget DigitalValue](/assets/img/cathoaIOTDashboard/setupWidgetDigitalValue.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget DigitalValue_

    > **Note**
    * Always match the subscribe key with the "your_key" value in `iot.sendTelemetry("your_key", "your_value");` in the code uploaded to the board in Arduino IDE to display data on the Dashboard.
    {: .prompt-warning }

4. This is a visual representation of data being displayed on the Dashboard online status.
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputDigitalValue.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

#### LED Indicator Widget

1. Return to the Dashboard page, click the Manage Dashboard button, and go to create Widgets.
2. Select the Widget type LED Indicator.
3. Name the Widget and enter the subscribe key. In this example, we will use status for the subscribe key with True Condition as ON. When the value matches the data sent from the board, the LED will display the configured color. You can select your preferred color for the LED display before clicking save.
    ![Cathoa IOT Set up Widget LED Indicator](/assets/img/cathoaIOTDashboard/setupWidgetLedIndicator.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget LED Indicator_

    > **Note**
    * Always match the subscribe key with the "your_key" value and True Condition with the "your_value" in `iot.sendTelemetry("your_key", "your_value");` in the code uploaded to the board in Arduino IDE to display data on the Dashboard.
    {: .prompt-warning }

4. This is a visual representation of data being displayed on the Dashboard online status.
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputLEDIndicator.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

#### Time series Widget

1. Return to the Dashboard page, click the Manage Dashboard button, and go to create Widgets.
2. Select the Widget type Time series.
3. Name the Widget and enter the subscribe keys. In this example, we will use temperatureC and humidity for the subscribe keys. You can choose graph colors, select graph units, and set the historical data time range.
    ![Cathoa IOT Set up Widget Time series](/assets/img/cathoaIOTDashboard/setupWidgetTimeSeries.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget Time series_

    > **Note**
    * Always match the subscribe keys with the "your_key" value in `iot.sendTelemetry("your_key", "your_value");` in the code uploaded to the board in Arduino IDE to display data on the Dashboard.
    {: .prompt-warning }

4. This is a visual representation of data displayed on the Dashboard.
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputTimeSeries.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

#### Data Table Widget

1. Return to the Dashboard page, click the Manage Dashboard button, and go to create Widgets.
2. Select the Widget type Data Table.
3. Name the Widget and enter the subscribe keys. In this example, we will use temperatureC and humidity for the subscribe keys. You can select units and limit the amount of historical data displayed.
    ![Cathoa IOT Set up Widget Data Table](/assets/img/cathoaIOTDashboard/setupWidgetDataTable.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget Data Table_

    > **Note**
    * Always match the subscribe keys with the "your_key" value in `iot.sendTelemetry("your_key", "your_value");` in the code uploaded to the board in Arduino IDE to display data on the Dashboard.
    {: .prompt-warning }

4. This is a visual representation of data displayed on the Dashboard.
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputDataTable.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

### 2. Control Widgets
1. Open the example file from the downloaded Cathoa IOT Library by going to File > Examples > CathoaIOT > AdvacedCommandHandling. The example file window will open.
   ![Cathoa IOT Arduino AdvacedCommandHandling](/assets/img/cathoaIOTDashboard/AdvacedCommandHanding.png){: .shadow .rounded }
   _Cathoa IOT Arduino AdvacedCommandHandling_

2. In the `WIFI_SSID` and `WIFI_PASSWORD` sections, enter the SSID name and password of the WiFi you want to use.
3. Enter the DEVICE_ID obtained from the dashboard. Go to Edit Mode by clicking Edit layout on the left, then click Manage Dashboard on the right, and then click Create Device. Give the device a name, such as ESP32, then copy the ID and paste it into `DEVICE_ID`. If you are using an existing device, you can skip creating it and just copy the existing device ID.

    ![Cathoa IOT Create Device](/assets/img/cathoaIOTDashboard/CreateDevice.png){: .shadow .rounded }
    _Cathoa IOT Create Device_

4. Complete the MQTT setup by entering the MQTT_HOST, MQTT_PORT, MQTT_USER, MQTT_PASS. You can find these by clicking the gear icon in the top right corner. Copy the Broker hostname to `MQTT_HOST`, copy the Broker port to `MQTT_PORT`, copy the MQTT Username to `MQTT_USER`, and copy the MQTT Password to `MQTT_PASS`.
    ![Cathoa IOT MQTT](/assets/img/cathoaIOTDashboard/MQTT.png){: .shadow .rounded }
    _Cathoa IOT MQTT_
5. Upload the code to the board by clicking the Upload button. Make sure to select the correct board and port. In our examples, we recommend ESP32 and ESP8266.


#### Toggle Widget
1. Return to the Dashboard page, click the Manage Dashboard button, and go to create Widgets.
2. Select the Widget type ToggleSwitch.
3. Name the Widget and enter the subscribe key. In this example, we will use toggle_Light before clicking save.
    ![Cathoa IOT Set up Widget ToggleSwitch](/assets/img/cathoaIOTDashboard/setupWidgetToggleSwitch.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget ToggleSwitch_
    
    > **Note**
    * Always match the subscribe key with the "command" value in `onCommandReceived(String command, String payload)` 
    in the code uploaded to the board in Arduino IDE. To display data on the Dashboard in real-time, remember that a Callback must always be sent. 
    `iot.sendTelemetry({ {"light_status", "ON"}, {command, payload} /* This line is a Callback */ });` 
    {: .prompt-warning }

4. This is a visual representation of data being displayed on the Dashboard online status.
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputToggleSwitch.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

#### Slider Widget
1. Return to the Dashboard page, click the Manage Dashboard button, and go to create Widgets.
2. Select the Widget type Slider.
3. <div>Name the Widget and enter the subscribe key. In this example, we will use set_speed. Set min, max, and Step as needed before saving.</div>
    ![Cathoa IOT Set up Widget Slider](/assets/img/cathoaIOTDashboard/setupWidgetSlider.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget Slider_
    
    > **Note**
    * Always match the subscribe key with the "command" value in `onCommandReceived(String command, String payload)` 
    in the code uploaded to the board in Arduino IDE. To display data on the Dashboard in real-time, remember that a Callback must always be sent. 
    `iot.sendTelemetry({ {"speed", "20"}, {command, payload} /* This line is a Callback */ });` 
    {: .prompt-warning }

4. This is a visual representation of data being displayed on the Dashboard online status.
    ![Cathoa IOT Dashboard Output Slider](/assets/img/cathoaIOTDashboard/OutputSlider.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Output Slider_

## More examples from Cathoa IOT Library
> You can find more examples at File > Examples > CathoaIOT > SimplifiedInstantiation for additional configuration details, which we recommend following.
{: .prompt-info }

## 4. Basic Dashboard IOT usage
1. Users can drag, resize, arrange, and adjust the layout of various Widgets on the Dashboard as desired.
    ![Cathoa IOT Dashboard Edit Mode](/assets/img/cathoaIOTDashboard/EditMode.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode_

2. <div>Users can edit or delete Widgets as needed by clicking the pencil or trash can icon at the top of the desired Widget.</div>

    ![Cathoa IOT Dashboard Edit Mode 2](/assets/img/cathoaIOTDashboard/EditMode2.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 2_

    ![Cathoa IOT Dashboard Edit Mode 3](/assets/img/cathoaIOTDashboard/EditMode3.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 3_
3. <div>Users can edit or delete Devices as needed by clicking the pencil or trash can icon on the right side of the desired Device.</div>

    ![Cathoa IOT Dashboard Edit Mode 4](/assets/img/cathoaIOTDashboard/EditMode4.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 4_

    ![Cathoa IOT Dashboard Edit Mode 5](/assets/img/cathoaIOTDashboard/EditMode5.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 5_
4. We can set Breakpoints for different screen layouts as needed in Edit Mode.
    ![Cathoa IOT Dashboard Breakpoint](/assets/img/cathoaIOTDashboard/Breakpoint.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Breakpoint_
5. We can add a Group to the Dashboard by clicking Manage Dashboard and then clicking Create Group.
    ![Cathoa IOT Dashboard Edit Mode 6](/assets/img/cathoaIOTDashboard/EditMode6.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 6_

    ![Cathoa IOT Dashboard Edit Mode 7](/assets/img/cathoaIOTDashboard/EditMode7.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 7_
6. We can use the Toggle Theme button to customize the Dashboard's theme.
    ![Cathoa IOT Dashboard Theme](/assets/img/cathoaIOTDashboard/Theme.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Theme_

## 5. Video Tutorial
{% include embed/youtube.html id='Z4ltfsBI3Qg' title='Video Tutorial for using Cathoa IOT Dashboard' %}