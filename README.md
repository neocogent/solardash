### TIG Stack on Raspberry Pi for Solar Dashboard

**TIG** is the Telegraf, Influxdb, Grafana set of tools.

  Telegraf collects data from various sources. In my case from a cheap $2 RS-485-USB adapter available from AliExpress or eBay. This interfaces to my Epever Tracer 3210AN solar charge controller. The Tracer is an MPPT controller that can accpet PV input up to 100V and "buck convert" it down to match a 12V / 24V battery system. It has a good set of measured voltage, current and power values that it can provide via an RS-485 Modbus interface. This data is collected by Telegraf and stored in the Influxdb.
  
  Influx is a database system - optimized for storing time series data and querying it in various time related ways.
  
  Grafana is a visual web panel developemtn tool. It can be used to easily create web dashboards with various gauges and graphs. 
  
This repo is a collection of various config and script files that tie my dashboard together and make it work. It assumes you have a basic install of the TIG stack. There are many tutorials around the web for getting that part done. Here are a few I referred to when setting this up:

  https://nwmichl.net/2020/07/14/telegraf-influxdb-grafana-on-raspberrypi-from-scratch/
  
  https://simonhearne.com/2020/pi-influx-grafana/
  
  https://onlyoneaman.medium.com/how-to-install-tig-stack-telegraf-influx-and-grafana-on-ubuntu-405755901ac2
  
All were useful and I'm not sure which I followed most in the end. It's all typical install-on-linux type stuff.

In addition to the TIG stack I found, modified and installed an Epever modbus telegraf input plugin conf file (epever_modbus.conf). I altered it to have short names for the measurements and for my specific USB adapter. It is then placed in /etc/telegraf/telegraf.d/ where it is picked up by telegraf. There are also some changes to the default telegraf.conf so that system inputs aren't collected as much and some of my own logging choices etc.

## Steps to Install the Dashboard

1. Follow a tutorial above to get Telegraf, Influxdb and Grafana installed and running. I assume that part is done and each is running as it's own user with systemd services enabled so they start at boot.

2. TODO...


## Battery Energy Gauge - (Coulomb counter type battery level indicator)

In addition to some pretty typical Grafana gauges and charts I also put together an energy gauge that was a bit more involved. Due to some limits on getting timestamps from a subquery I figured out a workaround using a Grafana csv data source plugin, and a cronjob with simple script to pull and save the most recent time the batteyr was FULL. I'll add details on how this works here.

TODO...
  
## Bonus - Solar Tunnel for viewing dashboard on some remote server (totally optional)

TODO...
