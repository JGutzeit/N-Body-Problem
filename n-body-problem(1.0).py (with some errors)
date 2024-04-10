import math
import matplotlib.pyplot as plt
import time
from datetime import timedelta
from tqdm import tqdm



#!
# die beschleunigung neu korrekt Berechnen!
#!



Simulierte_Zeit_sekunden = 10**7
G=6.6730*10**-11
dt=1

d1= 12756
m1= 88
vx1= 0
vy1= 90
x1= 0
y1= 0

d2= 5
m2= 70
vx2= 0
vy2= 6000
x2= 300000 +(d1*0.5)
y2= 0

d3= 109
m3= 450000
vx3= 0
vy3= 7660 * 1.403
x3= 408000 +(d1*0.5)
y3= 0


X1_Achse=[]
X2_Achse=[]
X3_Achse=[]
Y1_Achse=[]
Y2_Achse=[]
Y3_Achse=[]
anzahl_intervalle=0
r12 = math.sqrt((abs(x1-x2)**2)+(abs(y1-y2)**2))
r13 = math.sqrt((abs(x1-x3)**2)+ (abs(y1-y2)**2))
r23 = math.sqrt((abs(x2-x3)**2)+(abs(y1-y2)**2))
range_argument=int(Simulierte_Zeit_sekunden/dt)

for i in tqdm(range(range_argument)):
    
    
    if r12<=(d1+d2)*0.5 or r13<=(d1+d3)*0.5 or r23<=(d2+d3)*0.5:
        print("Kollision bei anzahl intervalle =",anzahl_intervalle)
        break
    else:
        anzahl_intervalle+=dt
    
        r12 = math.sqrt((abs(x1-x2)**2)+(abs(y1-y2)**2))
        r13 = math.sqrt((abs(x1-x3)**2)+ (abs(y1-y2)**2))
        r23 = math.sqrt((abs(x2-x3)**2)+(abs(y1-y2)**2))
    
        Fmx1= ((G*m1*m2)/(r12**2)) + ((G*m1*m3)/(r13**2))
        Fmx2= ((G*m2*m1)/(r12**2)) + ((G*m2*m3)/(r23**2))
        Fmx3= ((G*m3*m1)/(r13**2)) + ((G*m3*m2)/(r23**2))
        
        Fmy1= ((G*m1*m2)/(r12**2)) + ((G*m1*m3)/(r13**2))
        Fmy2= ((G*m2*m1)/(r12**2)) + ((G*m1*m3)/(r23**2))
        Fmy3= ((G*m3*m1)/(r13**2)) + ((G*m1*m3)/(r23**2))
            
        amx1 =Fmx1/m1
        amx2 =Fmx2/m2
        amx3 =Fmx3/m3
        amy1 =Fmy1/m1
        amy2 =Fmy2/m2
        amy3 =Fmy3/m3
    
        vx1 =vx1+ amx1*dt
        vx2 =vx2+ amx2*dt
        vx3 =vx3+ amx3*dt
        vy1 =vy1+ amy1*dt
        vy2 =vy2+ amy2*dt
        vy3 =vy3+ amy3*dt
    
        x1=x1+ vx1*dt
        x2=x2+vx2*dt
        x3=x3+vx3*dt
        y1=y1+vy1*dt
        y2=y2+vy2*dt
        y3=y3+vy3*dt
    
        X1_Achse.append(x1)
        X2_Achse.append(x2)
        X3_Achse.append(x3)
        Y1_Achse.append(y1)
        Y2_Achse.append(y2)
        Y3_Achse.append(y3)
        
    
    
plt.plot(X1_Achse, Y1_Achse, label="erde", color="red")
plt.plot(X2_Achse, Y2_Achse, label="ich", color="grey")
plt.plot(X3_Achse, Y3_Achse, label="iss", color="blue")
plt.axhline(0, color="black", linewidth=0.5)
plt.axvline(0, color="black", linewidth=0.5)
plt.title("several-body-problem")
plt.xlabel("X (m)")
plt.ylabel("Y (m)")
plt.gca().axis("equal")
plt.grid()
plt.legend()
plt.show()


