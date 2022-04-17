# erx_openvpn
OpenVPN on ER-X

Setting out to have the Ubiquiti Edgerouter-X talk to my openVPN server.
This is not a full Site-to-Site VPN but rather having the ER-X as a gateway for select clients that need to talk to another network.

# Get the ER-X ready
- Reset it by pushing the little reset button located at the back while connecting power, wait for the LED of eth4 to be lit and turn off.
- Plug in a cable to eth0.
- Plug in the cable to your PC.
- Set your PCs IP to be 192.168.1.2/24.
- Do basic setup ot the ER-X via the web interface. 
  - Set the LAN IP (of the internal switch) to your liking.
  - Will need to reboot.
  - Change the cable from eth0 into eth1 (or anything else but eth0).
  - Re-Set your PC's IP to whatever it was before.
- Re-Connect to the ER-X via the web interface on its new IP.
  - Change the time zone to your local one (so as not to run into issues with certificate validity).
  - Set the default gateway for the ER-X
  - Set the DNS to your liking.  

# Get the openvpn config file ready
- Embed certificates and private key in the config file
- Set option `route-nopull` in the config file. (we'll do that manually or via dynamic routing)
- The openvpn client on the er-x being ... retentive: set the cipher explicitly in the config file to the one used by the server (e.g. `cipher AES-256-CBC`). Caveat: That cipher will not work with older versions of edgeOS (think 1.10 or so).

# Activate it
https://ryanscullen.wordpress.com/2017/07/24/openvpn-client-setup-on-edgeos/

