# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS:
#### NAME:N.KANNAN
#### REGISTER NO:212223230097
#### DEPARTMENT:AI&DS
## AIM:
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
## CLIENT:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect(('localhost', port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
   while True:
      print('receiving data...')
      data = s.recv(1024)
      print('data=%s', (data))
      if not data:
        break
      f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
## SERVER:
```
import socket 
port = 60000 
s = socket.socket() 
host = socket.gethostname() 
s.bind(('localhost', port)) 
s.listen(5) 
while True:
  conn, addr = s.accept() 
  data = conn.recv(1024)
  print('Server received', repr(data))
  filename='mytext.txt'
  f = open(filename,'rb')
  l = f.read(1024)
  while (l):
     conn.send(l)
  print('Sent ',repr(l))
  l = f.read(1024)
  f.close()
  print('Done sending')
  conn.send('Thank you for connecting'.encode())
  conn.close()
```
## OUTPUT:
## CLIENT WINDOW:
![Screenshot 2024-04-28 192941](https://github.com/kannan-nagaraju/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/145742755/9d3bcf33-c6ce-4c67-ad4e-0047e3fdc9a7)
## SERVER WINDOW:
![image](https://github.com/kannan-nagaraju/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/145742755/a2dea9a5-e872-48e6-b7c8-8700ba502163)

## RESULT:
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
