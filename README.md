# Program-the-robot-to-move-straight-for-5-seconds-in-full-speed-then-slow-downs-makes-u-turn-and-the
import RPi.GPIO as GPIO # Import Raspberry Pi GPIO library from time import sleep
#Import the sleep function from the time module
GPIO.setwarnings(False)# ignore warning for now
GPIO.setmode(GPIO.BOARD)# use physical pin numbering
GPIO.setup(10,GPIO.OUT,initial=GPIO.LOW)# set pin 12 to be an output pin and set initial
value to low (OFF)
GPIO.setup(12,GPIO.OUT,initial=GPIO.LOW)# set pin 12 to be an output pin and set initial
value to low (OFF)
GPIO.setup(22,GPIO.OUT,initial=GPIO.LOW)# set pin 12 to be an output pin and set initial
value to low (OFF)
GPIO.setup(16,GPIO.OUT,initial=GPIO.LOW)# set pin 12 to be an output pin and set initial
value to low (OFF)
GPIO.setup(32,GPIO.OUT,initial=GPIO.LOW)# set pin 12 to be an output pin and set initial
value to low (OFF)
GPIO.setup(33,GPIO.OUT,initial=GPIO.LOW)# set pin 12 to be an output pin and set initial
value to low (OFF)
El = GPIO.PWM(32, 100) # PWM
Er = GPIO.PWM(33, 100) # PWM
El.start(0)
Er.start(0)
#p.start(100) #Generate PWM signal with 0% duty cycle
while True:#Run forever
#Drive Farword for 5 seconds at full speed
El.ChangeDutyCycle(100)
Er.ChangeDutyCycle(100)
GPIO.output(10, GPIO.HIGH);
GPIO.output(12, GPIO.LOW);
GPIO.output(22, GPIO.HIGH);
GPIO.output(16, GPIO.LOW);
#slow Down
sleep(5)
for x in range (100, 25, -1):
El.ChangeDutyCycle(x)
Er.ChangeDutyCycle(x)
sleep(0.1)
#U-Turn
El.ChangeDutyCycle(25)
Er.ChangeDutyCycle(100)
GPIO.output(10, GPIO.HIGH);
GPIO.output(12, GPIO.LOW);
GPIO.output(22, GPIO.HIGH);
GPIO.output(16, GPIO.LOW);sleep(2)
