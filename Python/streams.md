# find out what port a service uses #
import socket
socket.getservbyname('ssh')

# find out what service uses a given port #
socket.getservbyport(80)

# find out about the hostname and IP address of the machine you are currently using #
socket.gethostname()

# get IP of your compuer #
socket.gethostbyname(socket.gethostname())

# get IP of anowher computer #
socket.gethostbyname('google.com')

# provide more information about the machines we are exploring #
socket.gethostbyname_ex('google.com')

# to create a socket, you use the socket method of the socket library #
foo = socket.socket()

# provides information about available connections of a given host #
socket.getaddrinfo('google.com', 80)

# ask your own machine what possible connections are available for ‘http’ #
get_address_info(socket.gethostname(), 'http')

# get_address_info(host, port) #
def get_constants(prefix):
     """filtered mapping of socket module constants to their names"""
     return {
         getattr(socket, name): name
         for name in dir(socket) if name.startswith(prefix)
     }
	 
families = get_constants('AF')
types = get_constants('SOCK_')
protocols = get_constants('IPPROTO_')

def get_address_info(host, port):
    for response in socket.getaddrinfo(host, port):
        family, s_type, protocol, name, address = response
        print('family: {}'.format(families[family]))
        print('type: {}'.format(types[s_type]))
        print('protocol: {}'.format(protocols[protocol]))
        print('canonical name: {}'.format(name))
        print('socket address: {}'.format(address))
        print('')

# request and retrive a webpage #
import socket
socket.getaddrinfo('info.cern.ch', 'http')
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM, socket.IPPROTO_TCP)
client.connect(('188.184.100.182', 80))
msg = "GET / HTTP/1.1\r\n"
msg += "HOST: info.cern.ch\r\n\r\n"
msg = msg.encode('utf8')
client.sendall(msg)
client.recv(1024)
client.close()

# chat program
## server
import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM, socket.IPPROTO_TCP)
server_socket.bind(('127.0.0.1', 50000))
server_socket.listen(1)
connection, client_address = server_socket.accept()
connection.recv(64)
connection.sendall(b'Yes? Can you hear me?!')
connection.recv(64)
## client 
import socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM, socket.IPPROTO_TCP)
client_socket.connect(('127.0.0.1', 50000))
client_socket.sendall(b'Hello??')
client_socket.recv(64)
client_socket.sendall(b'Excellent!')

# read stream from a file - 100 bytes #
with open('frankenstein.txt', 'rb') as f:
	f.read(100)
	
# read stream from a file - whole file #
with open('frankenstein.txt', 'rb') as f:
	f.read()	
