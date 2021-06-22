import RPi.GPIO as GPIO
from http.server import BaseHTTPRequestHandler, HTTPServer

GPIO.setmode(GPIO.BCM)
GPIO.setup(5, GPIO.OUT)
GPIO.setup(6, GPIO.OUT)
GPIO.setup(13, GPIO.OUT)
#GPIO.setup(19, GPIO.OUT)
Request = None

class RequestHandler_httpd(BaseHTTPRequestHandler):
  def do_GET(self):
    global Request
    messagetosend = bytes('Servidor Iniciado...',"utf")
    self.send_response(200)
    self.send_header('Content-Type', 'text/plain')
    self.send_header('Content-Length', len(messagetosend))
    self.end_headers()
    self.wfile.write(messagetosend)
    Request = self.requestline
    Request = Request[5 : int(len(Request)-9)]
    print(Request)
    if Request == 'on':
      GPIO.output(5,True)
    if Request == 'off':
      GPIO.output(5,False)
    if Request == '1':
      GPIO.output(6,True)
    if Request == '0':
      GPIO. output(6, False)
    if Request == '2':
      GPIO.output(13,True)
    if Request == '3':
      GPIO. output(13, False)
    return

server_address_httpd = ('192.168.100.168',8080)
httpd = HTTPServer(server_address_httpd, RequestHandler_httpd)
print('Iniciando Servidor')
httpd.serve_forever()
GPIO.cleanup()
