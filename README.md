#mein KI-Projekt

<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# AIIS -artificial intelligence inspector scholae - for schools and perhaps public places

Final project for the Building AI course

## Summary

I thought about an intelligence microphone system in schools who check the noises around their environment in a case of danger or violence. 
An artificial intelligence shall interprete and check the noises. The voices of the kids will never been saved on its system. 
The only value which will be need is the decibel. If the decibel of a voice between the noises will be higher than it should be, 
the teachers will get a message on their phone, to check the place with the exactly data of the point of the floor or room. 

## Background

The Project is based on my own experiences with violence at school. 
As i was a victim and nobody could help, because teachers aren`t able to check every floor and room at any time - an AI System works immediately. 

Especially in cases of shooting, it can be helpfull, to reduce the danger, 
while the artifcial intelligence is closing the doors nearby the Gunman, while the system will help teachers and students to leave the school imeediately on its right way, when it is connected to the speakers.  


This is how you make a list, if you need one:
These are my questions at the beginning of my idea, which i have at all. Some more will coming up, as many programmer will work on it. 

* What is the acceptable normal surrounded decibel in schools? 
* What is a really high decibel during schools live?
* How many microphones need a school, for each floor and class room to run a system like that?

* What does it cost and is it possible to pay for that kind of system?
* How can learn the artificial intelligence to understand, that students scream, because they need help or having only a party or make loud noises, 
  because teenagers do it at all time without any reason for it? 

* How can teachers get the message of the AIIS?
* How many time do teachers have, to check the place, of the scream or noise?

* Do we need a neural network to valuate a special index value of noises? Yes, we need it to get a system which is trained and presents exactly reliable informations by any time. A part for professionels.
* How many different neurons do we need for the system to weight each characteristic and how we determine the characteristics, if a neural network will be work in the background as well? That will be a question for the real software architects.  
* etc... i think their will be a lot more questions, if prorgrammer code it. 

The following code is only a spark of it. Therefore i want to convince every programmer in the world to check it out, change, evaluate it and try to make it to a smart system, for the health of all of us, for the next nice educated society. 

The Future is now, sitting in their classrooms, waiting for your help, that AIIS can protect their lives and perhaps the lives of all of us in public places.    

## How is it used?

Is someone shooting, crying or loose someone his bag and cry for help, the system will send a message to all teachers, to check that place. 
If they checked it, they have an individual time to fix that problem otherwise the police will come to check the situation und have to ask the director, 
why the system was warning and nobody helped. It will be marked in a system to evaluate how serious schools do something against their problems of violence. 

<img src="ChatGPT Image 18. Juni 2026, 13_37_30.png">

This is how you create code examples:  

#please read at first: "do not use code, images, data etc. from others without permission" - "I was inspired by the exercise 20: Logistic Regression - of the Building AI Course of the University Helsinki. Picture is made by ChatGPT, created on the prompt of my summary!"
                                                                                
                                                                                
import math
import numpy as np
                                                                                
#Microphone 1 for Situation: "I heard a shot by a gun!" (Value: 135 decibel/ assesment value) 
#Microphone 2 for Situation: "Someone screams "Help!" (Value: 85 decibel/ assesment value)
#Microphone 3 for Situation: "Normal Voice Value during the day" (Value: 60 decibel/ assesment value)                                                                             
# all Values are average values                                                                              

M = np.array([135, 85, 60])

# the weights of three different situations like written above
#S1 reacts extremly on the volume of a shot
                                                                                
S1 = np.array([0.2, 0.5, 15])

#S2 reacts on the middle of a frequenz and reacts on someone who is crying for help
                                                                                
S2 = np.array([-.3, .7, .07])

#S3 reacts on a normal volume during the day in a school
S3 = np.array([-0.05, 1.0, .-8.0])
                                                                                
    
def sigmoid(z):
#to take care of an calculation error during big numbers, i limit the value of z                                                                           
    z = max(min(z, 50),-50)
    return 1 / (1+math.exp(-z))

#we need a threshold value for a normal standby modus during the day

bias = -35.0
                                                                                
    #print out the values
                                                                                
v1 = M @ S1 + bias
v2 = M @ S2 + bias
v3 = M @ S3 +10 #higher basis value for normal noise during the day
    
    #add the values in sigmoid function
Value_1 = sigmoid(v1)
Value_2 = sigmoid(v2)
Value_3 = sigmoid(v3)
    
    #show results
print(f"Result Coeff 1 (It is a gun): {Value_1:.4f}")
print(f"Result Coeff 2 (Someone needs help): {Value_2:.4f}")
print(f"Result Coeff 3: (normal noise value{Value_3:.4f}")
    
    #which is the highest value of which situation
highest = max(Value_1, Value_2, Value_3)
print(f"\nThe highest Sigmoid-Result is: {highest:.4f}")      

if highest == Value_1: 
   print:("Message to teacher: There is a danger of a gun in room x")
elif highest == Value_2: 
   print("Message to teacher: There is Aggression or someone needs help. Please check")
else: 
   print("Status: Everythin is fine(normal Pause-Noises).")


## Data sources and AI methods
Where does your data come from? Do you collect it yourself or do you use data collected by someone else?
                                                                                
I am not sure, but i think we have a lot of data on different databases, which can be used to train this kind of AI. 
Nevertheless it is important to measure the average decibel on a day for each place at school. 
So the AI knows for every place the average decibel value.  

Shots by a gun are already measured. I think we have already data, that AI can interprete the voice if someone needs really help or it is just a faked scream. 
I have asked google the diffrent assesment values of each situation. 
                                                                                
## Challenges

What does your project _not_ solve? Which limitations and ethical considerations should be taken into account when deploying a solution like this?

There are several problems - to take care that no personal data or words will be saved. At any time the AIIS is only allowed to react on special words like "Help" or the different gun shots for example or racism words which are already measured and saved on different plattforms i think. Everybody has the right to see how the AIIS is working in the background. Comments should explain how the programm works, for the directors at school and for any other person as well. Ideas are welcome at every time. Pupils are allowed to check the code if they want to and they are invited to solve different problems which the programm can have.  

The ethical consideration is to take care to handle it right and not influence the people in any negative way. It should be only trained to help for circumstances to save humans live. Any disregard of personal informations or incorrect use of the application have to be clarified by a democratic law, although my idea will be used in any kind of that way! 
                                                                                
It can not solve the problem why people react as they react. It is only a support. It will be an application like a fire alarm, to reduce the danger and violence at every time. 

## What next?

How could your project grow and become something even more? What kind of skills, what kind of assistance would you  need to move on? 

I think, i need programmers and scientists who are able to build it up the rest of the project, 
to make it happen and the people and goverments who understand that i only want to help, to keep us to live in safe places.
I believe next generations will grow up with less violence and can concentrate on their goals instead to see school as something wrong or an institution where they don`t feel save. 

If we have a laws in our countries, that parents are commited to bring their childrens to school, the goverment has the commitement to take care for the security of any child at every time, that it has the possibility to understand the tasks they need to. The price of a curious human beeing which is interested to learn and solve the problems of the future is too high to loose.    


## Acknowledgments

* list here the sources of inspiration: - My inspiration were the tasks of the AI Course. I used them, to build this kind of system. I thought about it and changed it to my circumstances. I hope everything is rightly done. 
* do not use code, images, data etc. from others without permission                                                                             
* when you have permission to use other people's materials, always mention the original creator and the open source / Creative Commons licence they've used
* etc
