# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
CLIENT :
```
import socket
s = socket.socket()
s.bind(('localhost',8002))
s.listen(5)
c, addr = s.accept()
ListSize = int(input("Enter the number of frames to send : "))
List = list(range(ListSize))
WindowSize = int(input("Enter Window Size : "))
st, i = 0, 0
while True:
    while(i < ListSize):
        st += WindowSize
        c.send(str(List[i:st]).encode())
        Acknowledgment = c.recv(1024).decode()
        if Acknowledgment:
            print(Acknowledgment)
            i+=st
```

SERVER:

```
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
```
## OUPUT:

<img width="956" height="652" alt="Screenshot 2026-02-05 105928" src="https://github.com/user-attachments/assets/cea1456b-f634-4362-b4e9-f126e63ce2f0" />

<img width="1132" height="603" alt="Screenshot 2026-02-05 110035" src="https://github.com/user-attachments/assets/256548d8-27fb-4b94-874e-8447949c607a" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
