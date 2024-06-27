# STM32 USBX Composite Example based on the STM32H7

In this repository : 

* This application provides a C code example showing on how to use the Azure USBX Middleware to develop a USB Device Composite application.
* The application is designed to open a Virtual COM Port and control a Mouse through the CDC and HID Classes. The main purpose of the application is to provide a functional example for opening more than a class in a single USB Application.
* The application runs over the NUCLEO-H723ZG board, and can be tailored/used as example to any other STM32 Family. 
* The repository contains a project for STM32CubeIDE v1.14.1 for the STM32H723, using the STM32CubeH7 1.11.1 and the X-CUBE-AZRTOS-H7 3.1.0.

* This demo was created based on the article available in: https://community.st.com/t5/stm32-mcus/how-to-implement-the-usb-device-composite-class-in-stm32-using/ta-p/645017

### <b>Application</b>

  This example runs by using the Azure RTOS ThreadX to execute the Azure USBX. At the beginning of the application the ThreadX RTOS and the USBX application are initialized. 
  Within the USBX initialization code (app_usbx_device.c), the HID and CDC classes are registered and initialized. Once the proceess is completed, three Threads are created, two for transmitting and receiving data through CDC Class and the last one to send the Mouse Report through the HID class.
  Then, the thread entry task is executed to configure the Endpoints and start the USB OTG Peripheral. Done that, connect the board to a computer, open a virtual COM to see a message being transmitted on every second. Send the value 1 to turn ON the yellow LED and 0 to turn it OFF. Press the USER Button to see the mouse being moved due to an HID report being transmitted through the USB Communication.

### <b>Keywords</b>

USB, Composite Class, Azure USBX, STM32H7, HID, CDC, Azure RTOS, Azure ThreadX

### <b>Directory contents</b>

   Here are the list of the most relevant files for the application. The other files are Read Only or were not modified to build the application.

  - Core/Src/main.c                                            -> Commom peripheral initialization functions, Azure ThreadX and USBX initialization
  - Core/Inc/main.h                                            -> Exported function prototypes and includes
  - USBX/App/app_usbx_device.c                                 -> USBX Stack initialization, Threads creation and USB Peripheral initialization
  - USBX/App/ux_device_cdc_acm.h                               -> CDC ACM Threads Prototypes
  - USBX/App/ux_device_cdc_acm.c                               -> CDC ACM Thread functions code to manage the CDC Communication
  - USBX/App/ux_device_mouse.h                                 -> HID Threads Prototypes
  - USBX/App/ux_device_mouse.c                                 -> HID Thread function code to move the mouse when the user button is pressed


### <b>Hardware and Software environment</b>

  - This example runs on STM32H723ZGI devices.

  - This example has been tested with NUCLEO-H723ZG board and can be
    easily tailored to any other supported device and development board.

### <b>How to use it ?</b>

In order to make the program work, you must do the following :

 - Open and import the project into STM32CubeIDE v1.14.1 or newer
 - Rebuild all files and load your image into target memory
 - Run the example
