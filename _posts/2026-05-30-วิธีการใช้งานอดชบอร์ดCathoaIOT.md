---
title: วิธีการใช้งานแดชบอร์ดCathoaIOT (Demo) TH
description: Cathoa IOT Dashboard เป็นแอปพลิเคชันบนเว็บที่ช่วยให้คุณสามารถตรวจสอบและควบคุมอุปกรณ์ IoT ของคุณได้
date: 2026-05-30 00:02:00 +0700
author: Cathoa
categories: [Blogging, Demo]
tags: [IOT,dashboard]
pin: true
math: true
mermaid: true
---

# ขั้นตอนการใช้งาน Cathoa IOT Dashboard

## 1. เข้าสู่ระบบ

### กรณีสมัครสมาชิกแล้วหรืออยากลองLogin ด้วยgithub

1. เปิดเว็บเบราว์เซอร์และไปที่ [Cathoa IOT Dashboard](https://cathoaiot.com/login)
2. ป้อนชื่อผู้ใช้ [EMAIL_ADDRESS] รหัสผ่าน [PASSWORD]
3. คลิกที่ "เข้าสู่ระบบ"

![Cathoa IOT Dashboard Login](/assets/img/cathoaIOTDashboard/LoginDashboardIOT.png){: .shadow .rounded }
_Cathoa IOT Dashboard Login_

### กรณียังไม่ได้เป็นสมาชิกและอยากสมัคร

1. เปิดเว็บเบราว์เซอร์และไปที่ [Cathoa IOT Dashboard](https://cathoaiot.com/register) หรือ คลิกที่ "Request Provisioning"
2. ให้กรอกข้อมูลของคุณในแต่ละช่องได้เลย ส่วนที่เป็นดาวสีแดงให้กรอกข้อมูลด้วย ส่วน(Optional)จะกรอกหรือไม่กรอกก็ได้
3. อย่าลืมกด checkbox PDPA ด้วย
4. คลิกที่ "Request Provisioning" เพื่อสมัครสมาชิก

   ![Cathoa IOT Dashboard Request Provisioning](/assets/img/cathoaIOTDashboard/RequestProvisioningDashboardIOT.png){: .shadow .rounded }
   _Cathoa IOT Dashboard Request Provisioning_

5. จะมีหน้า Back to Login และมีการส่ง Email ไปให้ท่านยืนยัน
6. เข้า Email ของท่านแล้วกดที่ Verify Email Address

![Cathoa IOT Dashboard Confirm](/assets/img/cathoaIOTDashboard/ConfirmEmailDashboardIOT.png){: .shadow .rounded }
_Cathoa IOT Dashboard Confirm_

## 2. เมื่อเข้ายังหน้าDashboard

1. หลังจากเข้าสู่ระบบแล้ว จะมีหน้าว่างเปล่าอยู่ให้เราสามารถกดที่รูปโปรไฟล์ด้านมุมบนขวาเพื่อแก้ไขชื่อและรูปภาพ

   ![Cathoa IOT Dashboard Profile](/assets/img/cathoaIOTDashboard/ProfileDashboardIOT.png){: .shadow .rounded }
   _Cathoa IOT Dashboard Profile_

2. จากนั้นเข้ามาดาวน์โหลดไลบรารี่ที่ [Cathoa IOT Library](https://github.com/Lindist/CathoaIOT-Library/releases/tag/v2.0.4.4)

   ![Cathoa IOT Library](/assets/img/cathoaIOTDashboard/CathoaIOT-Library.png){: .shadow .rounded }
   _Cathoa IOT Library_

3. เมื่อดาวน์โหลดแล้ว ให้มาเปิดไฟล์ในโปรแกรม Arduino IDE เพื่อใช้งานไลบรารี่ ให้กดที่ Sketch > Include Library > Add .ZIP Library... > เลือกไฟล์ CathoaIOT-Library.zip > กด Open

   ![Cathoa IOT Library](/assets/img/cathoaIOTDashboard/AddZipLibrary.png){: .shadow .rounded }
   _Cathoa IOT Library_

4. อย่าลืมติดตั้งLibraryที่จำเป็นดังนี้

   ![Cathoa IOT ArduinoJson](/assets/img/cathoaIOTDashboard/ArduinoJson.png){: .shadow .rounded }
    _ArduinoJson_
   ![Cathoa IOT PubSubClient](/assets/img/cathoaIOTDashboard/PubSubClient.png){: .shadow .rounded }
    _PubSubClient_

## 3. ตั้งค่าข้อมูลในArduino IDE

### 1. Widgets ประแสดงผลข้อมูล
1. เปิดตัวอย่างไฟล์จาก Cathoa IOT Library ที่ดาวน์โหลดมาเข้าไปที่ File > Examples > CathoaIOT > BasicTelemetry_For_ESP8266andESP32 จากนั้นจะมีหน้าต่างตัวอย่างไฟล์เปิดขึ้นมา
   ![Cathoa IOT Arduino BasicTelemetry_For_ESP8266andESP32](/assets/img/cathoaIOTDashboard/BasicTelemetry_For_ESP8266andESP32.png){: .shadow .rounded }
   _Cathoa IOT Arduino BasicTelemetry_For_ESP8266andESP32_
2. ดำเนินการตั้งค่าWiFiให้เรียบร้อยใส่ชื่อ ssid รหัสผ่าน
3. ใส่ DEVICE_ID ที่ได้จากdashboard โดยเข้าไปที่Edit Modeโดยคลิกที่Edit layout ที่อยู่ด้านซ้ายจากนั้นกดปุ่มManage Dashboard ด้านขวา แล้วกดปุ่มCreate Device จากนั้นให้เราทำการตั้งชื่ออุปกรณ์ เช่น ESP32 จากนั้นให้เรากดปุ่มคัดลอกIDมา กรอกใน `DEVICE_ID` กรณีจะอุปกรณ์ตัวเดิมก็ข้ามขั้นตอนการสร้างและคัดลอกIDของอุปกรณ์ที่มีอยู่แล้วได้เลย

    ![Cathoa IOT Create Device](/assets/img/cathoaIOTDashboard/CreateDevice.png){: .shadow .rounded }
    _Cathoa IOT Create Device_

4. ดำเนินการตั้งค่า MQTT ให้เรียบร้อยใส่ชื่อ MQTT_HOST, MQTT_PORT, MQTT_USER, MQTT_PASS โดยสามารถเข้าไปที่รูปฟันเฟืองที่อยู่ด้านมุมขวาบนโดยการกดคลิกเข้าไป คัดลอกBroker hostname ใส่ที่ `MQTT_HOST` คัดลอกBroker port ใส่ที่ `MQTT_PORT` คัดลอกMQTT Username ใส่ที่ `MQTT_USER` คัดลอกMQTT Password ใส่ที่ `MQTT_PASS`
    ![Cathoa IOT MQTT](/assets/img/cathoaIOTDashboard/MQTT.png){: .shadow .rounded }
    _Cathoa IOT MQTT_
5. อัปโหลดโค้ดไปยังบอร์ด โดยกดที่ปุ่ม Upload อย่าลืมเช็ค บอร์ดและพอร์ตว่าถูกต้องหรือไม่ในตัวอย่างเราแนะนำเป็นESP32 และESP8266

#### DigitalValue Widget

1. ให้มาที่หน้าDashboardอีกครั้งให้ทำการกดปุ่มManage Dashboard กดที่ไปสร้างWidgets 
2. ทำการเลือกเป็นWidgetประเภท DigitalValue
3. ทำการตั้งชื่อ Widgets และกรอกsubscribekeyในตัวอย่างนี้เราจะใช้เป็น temperatureC และ humidityสำหรับsubscribekey ก่อนจะทำการกดsave

    ![Cathoa IOT Set up Widget DigitalValue](/assets/img/cathoaIOTDashboard/setupWidgetDigitalValue.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget DigitalValue_

    > **ข้อควรจำ**
    * กรอกsubscribe key ให้ตรงกับค่า "your_key" ใน `iot.sendTelemetry("your_key", "your_value");` ของโค้ดที่อัปโหลดไปยังบอร์ดในArduino IDEเสมอเพื่อให้สามารถแสดงผลข้อมูลบนDashboardได้
    {: .prompt-warning }

4. นี้คือภาพการแสดงผลของข้อมูลบนDashboardสถานะออนไลน์ 
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputDigitalValue.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

#### LED Indicator Widget

1. ให้มาที่หน้าDashboardอีกครั้งให้ทำการกดปุ่มManage Dashboard กดที่ไปสร้างWidgets 
2. ทำการเลือกเป็นWidgetประเภท LED Indicator
3. ทำการตั้งชื่อ Widgets และ กรอกsubscribe key ในตัวอย่างนี้เราจะใช้เป็น status สำหรับsubscribe key และมีTrue Condition เป็น ON เมื่อมีค่าตรงกับข้อมูลที่ส่งมาจากบอร์ดก็จะแสดงผลไฟสถานะเป็นสีที่เราได้ตั้งค่าไว้ ในการแสดงผลไฟสถานะเราสามารถเลือกสีไฟสถานะได้ตามต้องการก่อนจะทำการกดsave
    ![Cathoa IOT Set up Widget LED Indicator](/assets/img/cathoaIOTDashboard/setupWidgetLedIndicator.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget LED Indicator_

    > **ข้อควรจำ**
    * กรอกsubscribe key ให้ตรงกับค่า "your_key"และ True Condition ให้ตรงกับค่า "your_value" ใน `iot.sendTelemetry("your_key", "your_value");` ของโค้ดที่อัปโหลดไปยังบอร์ดในArduino IDEเสมอเพื่อให้สามารถแสดงผลข้อมูลบนDashboardได้
    {: .prompt-warning }

4. นี้คือภาพการแสดงผลของข้อมูลบนDashboardสถานะออนไลน์ 
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputLEDIndicator.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

#### Time series Widget

1. ให้มาที่หน้าDashboardอีกครั้งให้ทำการกดปุ่มManage Dashboard กดที่ไปสร้างWidgets 
2. ทำการเลือกเป็นWidgetประเภท Time series
3. ทำการตั้งชื่อ Widgets และ กรอกsubscribe keys ในตัวอย่างนี้เราจะใช้เป็น temperatureC และ humidity สำหรับsubscribe keys เราสามารถเลือกสีกราฟกันได้ และ สามารถเลือกหน่วยของกราฟได้อีกด้วย พร้อมช่องสำหรับกำหนดช่วงเวลาข้อมูลสำหรับแสดงผลย้อนหลัง
    ![Cathoa IOT Set up Widget Time series](/assets/img/cathoaIOTDashboard/setupWidgetTimeSeries.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget Time series_

    > **ข้อควรจำ**
    * กรอกsubscribe keys ให้ตรงกับค่า "your_key" ใน `iot.sendTelemetry("your_key", "your_value");` ของโค้ดที่อัปโหลดไปยังบอร์ดในArduino IDEเสมอเพื่อให้สามารถแสดงผลข้อมูลบนDashboardได้
    {: .prompt-warning }

4. นี้คือภาพการแสดงผลของข้อมูลบนDashboard
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputTimeSeries.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

#### Data Table Widget

1. ให้มาที่หน้าDashboardอีกครั้งให้ทำการกดปุ่มManage Dashboard กดที่ไปสร้างWidgets 
2. ทำการเลือกเป็นWidgetประเภท Data Table
3. ทำการตั้งชื่อ Widgets และ กรอกsubscribe keys ในตัวอย่างนี้เราจะใช้เป็น temperatureC และ humidity สำหรับsubscribe keys เราสามารถเลือกหน่วยและกำหนดจำนวนข้อมูลสำหรับแสดงผลย้อนหลัง
    ![Cathoa IOT Set up Widget Data Table](/assets/img/cathoaIOTDashboard/setupWidgetDataTable.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget Data Table_

    > **ข้อควรจำ**
    * กรอกsubscribe keys ให้ตรงกับค่า "your_key" ใน `iot.sendTelemetry("your_key", "your_value");` ของโค้ดที่อัปโหลดไปยังบอร์ดในArduino IDEเสมอเพื่อให้สามารถแสดงผลข้อมูลบนDashboardได้
    {: .prompt-warning }

4. นี้คือภาพการแสดงผลของข้อมูลบนDashboard
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputDataTable.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

### 2. Widgets ควบคุมข้อมูล
1. เปิดตัวอย่างไฟล์จาก Cathoa IOT Library ที่ดาวน์โหลดมาเข้าไปที่ File > Examples > CathoaIOT > AdvacedCommandHandling จากนั้นจะมีหน้าต่างตัวอย่างไฟล์เปิดขึ้นมา
   ![Cathoa IOT Arduino AdvacedCommandHandling](/assets/img/cathoaIOTDashboard/AdvacedCommandHanding.png){: .shadow .rounded }
   _Cathoa IOT Arduino AdvacedCommandHandling_

2. ในส่วนของ`WIFI_SSID`และ`WIFI_PASSWORD`ให้ทำการกรอกชื่อ SSID และรหัสผ่านของ WiFi ที่ต้องการใช้งาน
3. ใส่ DEVICE_ID ที่ได้จากdashboard โดยเข้าไปที่Edit Modeโดยคลิกที่Edit layout ที่อยู่ด้านซ้ายจากนั้นกดปุ่มManage Dashboard ด้านขวา แล้วกดปุ่มCreate Device จากนั้นให้เราทำการตั้งชื่ออุปกรณ์ เช่น ESP32 จากนั้นให้เรากดปุ่มคัดลอกIDมา กรอกใน `DEVICE_ID` กรณีจะอุปกรณ์ตัวเดิมก็ข้ามขั้นตอนการสร้างและคัดลอกIDของอุปกรณ์ที่มีอยู่แล้วได้เลย

    ![Cathoa IOT Create Device](/assets/img/cathoaIOTDashboard/CreateDevice.png){: .shadow .rounded }
    _Cathoa IOT Create Device_

4. ดำเนินการตั้งค่า MQTT ให้เรียบร้อยใส่ชื่อ MQTT_HOST, MQTT_PORT, MQTT_USER, MQTT_PASS โดยสามารถเข้าไปที่รูปฟันเฟืองที่อยู่ด้านมุมขวาบนโดยการกดคลิกเข้าไป คัดลอกBroker hostname ใส่ที่ `MQTT_HOST` คัดลอกBroker port ใส่ที่ `MQTT_PORT` คัดลอกMQTT Username ใส่ที่ `MQTT_USER` คัดลอกMQTT Password ใส่ที่ `MQTT_PASS`
    ![Cathoa IOT MQTT](/assets/img/cathoaIOTDashboard/MQTT.png){: .shadow .rounded }
    _Cathoa IOT MQTT_
5. อัปโหลดโค้ดไปยังบอร์ด โดยกดที่ปุ่ม Upload อย่าลืมเช็ค บอร์ดและพอร์ตว่าถูกต้องหรือไม่ในตัวอย่างเราแนะนำเป็นESP32 และESP8266


#### Toggle Widget
1. ให้มาที่หน้าDashboardอีกครั้งให้ทำการกดปุ่มManage Dashboard กดที่ไปสร้างWidgets 
2. ทำการเลือกเป็นWidgetประเภท ToggleSwitch
3. ทำการตั้งชื่อ Widgets และกรอกsubscribekeyในตัวอย่างนี้เราจะใช้เป็น toggle_Light ก่อนจะทำการกดsave
    ![Cathoa IOT Set up Widget ToggleSwitch](/assets/img/cathoaIOTDashboard/setupWidgetToggleSwitch.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget ToggleSwitch_
    
    > **ข้อควรจำ**
    * กรอกsubscribe key ให้ตรงกับค่า "command" ใน `onCommandReceived(String command, String payload)` 
    ของโค้ดที่อัปโหลดไปยังบอร์ดในArduino 
    IDEเสมอและเพื่อให้สามารถแสดงผลข้อมูลบนDashboardได้แบบRealtime โปรดจำไว้ว่าจะต้องส่งCallbackกลับมาเสมอ 
    `iot.sendTelemetry({ {"light_status", "ON"}, {command, payload} /*บรรทัดนี้เป็นCallbackน่ะ*/ });` 
    {: .prompt-warning }

4. นี้คือภาพการแสดงผลของข้อมูลบนDashboardสถานะออนไลน์ 
    ![Cathoa IOT Dashboard](/assets/img/cathoaIOTDashboard/OutputToggleSwitch.png){: .shadow .rounded }
    _Cathoa IOT Dashboard_

#### Slider Widget
1. ให้มาที่หน้าDashboardอีกครั้งให้ทำการกดปุ่มManage Dashboard กดที่ไปสร้างWidgets 
2. ทำการเลือกเป็นWidgetประเภท Slider
3. <div>ทำการตั้งชื่อWidgetsและกรอกsubscribekeyในตัวอย่างนี้เราจะใช้เป็น set_speedตั้งค่าmin,max,Stepตามต้องการก่อนsaveเพื่อบันทึก</div>
    ![Cathoa IOT Set up Widget Slider](/assets/img/cathoaIOTDashboard/setupWidgetSlider.png){: .shadow .rounded }
    _Cathoa IOT Set up Widget Slider_
    
    > **ข้อควรจำ**
    * กรอกsubscribe key ให้ตรงกับค่า "command" ใน `onCommandReceived(String command, String payload)` 
    ของโค้ดที่อัปโหลดไปยังบอร์ดในArduino 
    IDEเสมอและเพื่อให้สามารถแสดงผลข้อมูลบนDashboardได้แบบRealtime โปรดจำไว้ว่าจะต้องส่งCallbackกลับมาเสมอ 
    `iot.sendTelemetry({ {"speed", "20"}, {command, payload} /*บรรทัดนี้เป็นCallbackน่ะ*/ });` 
    {: .prompt-warning }

4. นี้คือภาพการแสดงผลของข้อมูลบนDashboardสถานะออนไลน์ 
    ![Cathoa IOT Dashboard Output Slider](/assets/img/cathoaIOTDashboard/OutputSlider.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Output Slider_

## ตัวอย่างเพิ่มเติมจาก Cathoa IOT Library
> เราสามารถดูตัวอย่างเพิมเติมได้ที่ File > Examples > CathoaIOT > SimplifiedInstantiation เพื่อดูการตั้งค่าเพิ่มเติม ซึ่งเราแนะนำให้ตั้งค่าตามเลย
{: .prompt-info }

## 4. การใช้งานDashboard IOTเบี้ยงต้น
1. ผู้ใช้สามารถลากย่อ ขยาย จัดวาง และปรับแต่งตำแหน่งของ Widgets ต่างๆ บนDashboardได้ตามต้องการ
    ![Cathoa IOT Dashboard Edit Mode](/assets/img/cathoaIOTDashboard/EditMode.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode_

2. <div>ผู้ใช้สามารถกดแก้ไขหรือลบWidgetได้ตามต้องการ โดยกดที่ไอคอนรูปดินสอหรือไอคอนรูปถังขยะ ที่อยู่ด้านบนของWidget ที่ต้องการ</div>

    ![Cathoa IOT Dashboard Edit Mode 2](/assets/img/cathoaIOTDashboard/EditMode2.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 2_

    ![Cathoa IOT Dashboard Edit Mode 3](/assets/img/cathoaIOTDashboard/EditMode3.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 3_
3. <div>ผู้ใช้สามารถกดแก้ไขหรือลบDeviceได้ตามต้องการ โดยกดที่ไอคอนรูปดินสอหรือไอคอนรูปถังขยะ ที่อยู่ด้านขวาของDevice ที่ต้องการ</div>

    ![Cathoa IOT Dashboard Edit Mode 4](/assets/img/cathoaIOTDashboard/EditMode4.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 4_

    ![Cathoa IOT Dashboard Edit Mode 5](/assets/img/cathoaIOTDashboard/EditMode5.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 5_
4. เราสามารถที่ตั้งBreakpointในหน้าจอต่างๆได้ตามต้องการในEditMode
    ![Cathoa IOT Dashboard Breakpoint](/assets/img/cathoaIOTDashboard/Breakpoint.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Breakpoint_
5. เราสามารถเพิ่มGroupในDashboardได้โดยกดไปที่Manage Dashboard แล้วกดที่Create Group
    ![Cathoa IOT Dashboard Edit Mode 6](/assets/img/cathoaIOTDashboard/EditMode6.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 6_

    ![Cathoa IOT Dashboard Edit Mode 7](/assets/img/cathoaIOTDashboard/EditMode7.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Edit Mode 7_
6. เราสามารถปุ่มToggle ธีม เพื่อปรับแต่งธีมของDashboard
    ![Cathoa IOT Dashboard Theme](/assets/img/cathoaIOTDashboard/Theme.png){: .shadow .rounded }
    _Cathoa IOT Dashboard Theme_

## 5. วิดีโอสอนใช้งาน
{% include embed/youtube.html id='eojVX6TuAGo' title='วิดีโอสอนการใช้งาน Dashboard Cathoa IOT' %}