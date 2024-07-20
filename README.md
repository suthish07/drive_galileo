# drive_galileo
## Functions Used
### Callback Functions 
* messageCb
  This function is called whenever it recieves a message from the topic ` motor_pwm ` . This functions is used to send the ` PWM ` signals to the motors ` (4 drivers and 4 steering) `. It gets the input from the reference variable ` drive_inp ` and stores the ` PWM ` values in the temporary variable ` drive_buf ` ` (inside the for loop) `
### Interrupt Functions

  * These type of functions are subclass of callback functions. These functions are called when the value of assigned variable changes. For example, In this code ` attachInterrupt(digitalPinToInterrupt(encA[0]),callback_0,RISING); ` whenever the encA[0] risess from 0 to 1, the attached interrupt function ` callback_0 ` is called.
    
      1. The digitalPinToInterrupt() function  returns the pin number if it can be used as an interrupt.
      2. The ` attachInterrupt ` can take 3 inputs : pin to be setted
                                               ` Interrupt Service Routine ` : These functions won't take any input and does not return anything, but runs whenever there is change in value .
                                               ` Mode ` : RISING,FALLING or CHANGE , this tells when the ISR functions to be called
      3. In total there are '7 callback functions for each encoder, Named from ` callback_0 ` to ` callback_6 `
 
   * In each ` callback_x ` Functions it checks whether ` encA[x] ' and ` encb[x] ` are equal or not . If it is equal then the `enc_pos` is incremented by one, Otherwise it is decremented one.
   * The reason we are doing so because, we had used quadrature encoders ( these type of encoders have high accuracy and reliability ) . These give data in two channels and there is a constant 90 degree difference between both the channels.
     * If channel A leads then indicated that the motor is oving in anti_clockwise direection and vice-versa.
     * Our, seniors used a clever idea to find the direction of motion of encoders. They only considered at the time of ` Rising edge ` of one channel (here it is channel A) . At that time if we compare both the channels, then there can be two possibilities .
       *  If both the values are same then it is moving in ` anti_clockwise ` and we are incrementing the enc_pos .
       *  If both the values are not equal then it is moving in ` clockwise ` and we are derementing the enc_pos
![Diagram](main/Quadrature_encoders)
![Channels](main/Channels)

