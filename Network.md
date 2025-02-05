# Network
## How does AerionCloud's networking work?
It depends on the type of device:
- Host Servers
- Client's Servers
- Admin Devices
  
They both handle networking a bit differently.

### Host Servers
Host Servers work depending on location.
If the server is in Spain (`ES`), in the city Puigcerdà (`PU`), and its the 2nd server (`02`) the hostname would be `es-pu-02` (follows this format: `COUNTRY-CITY-ID`)
To calculate the host server's IP we need to have in mind the city code and the server id, lets use `es-pu-02` server as an example,
if we convert "`pu`" to HEX we get 70 75, now we need to add up those two numbers, it gives 145, thats called the HSIP, now,
having the HSIP and the server ID we can easily have the server IP following this format: `100.100.HSIP.ID`,
in the case of `es-pu-02` the IP would be `100.100.145.2`.

### Client's Servers
Client's Servers work in a similar way as the Host Servers, but, easier.
You need to check your Server ID on the Admin Panel, lets use server ID 123 as an example,
after finding out your Server ID you need the Host Server's hostname, lets use `es-pu-02`
as an example, if we convert "`pu`" to HEX and add up those numbers we get "`145`",
that's the Host Server's HSIP, having those two numbers we can easily have the
client's Server IP following this format: `100.105.HSIP.ID` which in this case
would be `100.105.145.123`.

### Admin Devices
All Admin Devices are on a restricted admin-only network, you shouldn't ever
need to connect to an Admin Device, this is more of a reference for Administrators,
you first need to identify the device ID on this chart:

|Device |ID|
|-------|--|
|Windows|1 |
|macOS  |2 |
|Android|3 |
|iOS    |4 |
|Linux  |5 |
|Other  |6 |

Then just following the order of first connection you can use this format:
`100.110.ID.ORDER`. This means that the first mac that connect would get
`100.110.2.1`, the second one `100.110.2.2`, the third one `100.110.2.3`...


## Reserved IPs
You can also order a reserved IP which would use this format: `100.75.HSIP.x`
being x your choice (if its not claimed already), this places you on a
different network which would make crawler bots on `100.75.x.x`
configured only for that network hide your server. This also makes managing your
server easier as you get to choose the number in the IP.
