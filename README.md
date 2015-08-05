# ovpn

Simple bash script wrapper for [kylemanna](https://github.com/kylemanna)'s [OpenVPN for Docker](https://github.com/kylemanna/docker-openvpn).

## Installation

Place the `ovpn` script somewhere in your PATH. Make sure it has execute permissions (`chmod +x ovpn`).

## Usage

```
ovpn install <hostname>             # Configure OpenVPN server container for the given hostname
ovpn client <clientname>            # Create certificates for given client and generate .ovpn file
ovpn getovpn <clientname>           # Regenerate the .ovpn file for the given client
ovpn start [<port>...]              # Start the OpenVPN server on the specified port(s)
ovpn stop                           # Stop the OpenVPN server
ovpn restart                        # Restart the OpenVPN server (on its original port(s))
ovpn shell                          # Start a bash session within the container
ovpn config                         # Edit the OpenVPN config files
ovpn logs                           # View container logs
ovpn reinstall <hostname>           # Reconfigure OpenVPN server for the given hostname
ovpn uninstall                      # Delete server and data containers (data will be lost!)
ovpn backup [<dir>] [<filename>]    # Backup server config to <dir>/<filename> on the host
ovpn restore <dir> <filename>       # Restore server config from <dir>/<filename> on the host
```

By default, the script runs OpenVPN on 1194/udp within the container. There should be no reason to change the port (as this will be mapped to from the host anyway), but there may be a need to use tcp instead. This can be achieved by setting the `OVPN_PROTOCOL` environment variable to `tcp`.

If there is a need to run multiple OpenVPN servers, the `OVPN_LABEL` environment variable can be overridden from its default value of `ovpn`. This will change the names used for the underlying Docker containers and allow multiple containers to run side-by-side.

## Known issues

There are a few known rough edges that need ironing out. Pull requests welcome :)

## License (MIT)

Copyright (c) 2015 Luke Bennett

Permission is hereby granted, free of charge, to any person obtaining 
a copy of this software and associated documentation files (the 
'Software'), to deal in the Software without restriction, including 
without limitation the rights to use, copy, modify, merge, publish, 
distribute, sublicense, and/or sell copies of the Software, and to 
permit persons to whom the Software is furnished to do so, subject to 
the following conditions:

The above copyright notice and this permission notice shall be 
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, 
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF 
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. 
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY 
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, 
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE 
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.