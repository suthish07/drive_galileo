# drive_galileo
## Functions Used
### Callback Functions 
* messageCb
  This function is called whenever it recieves a message from the topic ' motor_pwm ' . This functions is used to send the ' PWM ' signals to the motors ' (4 drivers and 4 steering) '. It gets the input from the reference variable ' drive_inp ' and stores the ' PWM ' values in the temporary variable ' drive_buf ' ' (inside the for loop) '
### Interrupt Functions

  * These type of functions are subclass of callback functions. These functions are called when the value of assigned variable changes. For example, In this code ' attachInterrupt(digitalPinToInterrupt(encA[0]),callback_0,RISING); ' whenever the encA[0] risess from 0 to 1, the attached interrupt function ' callback_0 ' is called.
  * The digitalPinToInterrupt() function  returns the pin number if it can be used as an interrupt.
  * The ' attachInterrupt ' can take 3 inputs : pin to be setted
                                           ' Interrupt Service Routine ' : These functions won't take any input and does not return anything, but runs whenever there is change in value .
                                           ' Mode ' : RISING,FALLING or CHANGE , this tells when the ISR functions to be called
  * In total there are '7 callback functions for each encoder, Named from ' callback_0 ' to ' callback_6 '
 
