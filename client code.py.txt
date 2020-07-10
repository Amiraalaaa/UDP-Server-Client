import time
from socket import *
ourserverport = 7777
ourserverName = 'localhost'
ourclientSocket = socket(AF_INET, SOCK_DGRAM)
ping = 1
while ping < 11 :
 pingmessages = ' ping ' + str(ping) + ' time is ' + str(time.strftime(("%H:%M:%S")))
 theadress = (ourserverName,ourserverport)
 begin = time.time()
 ourclientSocket.sendto(pingmessages,theadress)
 ourclientSocket.settimeout(1.0)
 try :
     Newmessage,serveraddr = ourclientSocket.recvfrom(1024)
     print (Newmessage)
     last = time.time()
     totaltime = last - begin
     print ('RRT is equal to '+str(totaltime)+' sec')
 except timeout:
     print ('Request timed out')

 ping = ping+1







