# start the server (inside the CGI directory)
 python -u -m http.server --cgi

# run the appplication, after starting the server
http://localhost:8000/cgi-bin/hello_world.py


# The script has a few specific responsibilities as well. The script must:
- Be executable.
- Print any HTTP headers that are specific to the response it is generating.
- Print the blank line that separates the HTTP headers from the HTTP body.
- Generate and print the body of the HTTP response.
- Most web servers will only execute CGI scripts which are inside of a cgi-bin directory. This keeps malicious clients from getting your web server to execute scripts that may reside in other locations on your server.

# debugger for CGI scripts
import cgitb
cgitb.enable()

# passing arguments (http://localhost:8000/cgi-bin/field_storage.py?a=23&b-46&b-92)
import cgi

print("Content-Type: text/plain")
print()

form = cgi.FieldStorage()

stringval = form.getvalue('a', None)
listval = form.getlist('b')

print("a: {}, b: {}".format(str(stringval), str(listval)))

