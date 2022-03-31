### TIG Stack on Raspberry Pi for Solar Dashboard

**TIG** is the Telegraf, Influxdb, Grafana set of tools.

  Telegraf collects data from various sources. In my case from a cheap $2 RS-485-USB adapter available from AliExpress or eBay. This interfaces to my Epever Tracer 3210AN solar charge controller. The Tracer is an MPPT controller that can accpet PV input up to 100V and "buck convert" it down to match a 12V / 24V battery system. It has a good set of measured voltage, current and power values that it can provide via an RS-485 Modebus interface. This data is collected by Telegraf and stored in the Influxdb.
  
  Influx is a database system - optimized for storing time series data and querying it in various time related ways.
  
  Grafana is a visual web panel developemtn tool. It can be used to easily create web dashboards with various gauges and graphs. 
  
This repo is a collection of various config and script files that tie my dashboard together and make it work. It assumes you have a basic install of the TIG stack. There are many tutorials around the web for getting that part done. Here are a couple I used when setting this up:

  https://nwmichl.net/2020/07/14/telegraf-influxdb-grafana-on-raspberrypi-from-scratch/
  
  https://simonhearne.com/2020/pi-influx-grafana/
  
  https://onlyoneaman.medium.com/how-to-install-tig-stack-telegraf-influx-and-grafana-on-ubuntu-405755901ac2
  
All were useful and I'm not sure which I followed in the end. It's all typical install-on-linux type stuff.

In addition to the TIG stack I found, modified and installed an Epever modbus telegraf plugin conf file (epever_modbus.conf). I altered it to have short names for the measurements and for my specific USB adapter. It is then placed in /etc/telegraf/telegraf.d/ where it is picked up by telegraf. There are also some changes to the default telegraf.conf so that system inputs aren't collected as much and some of my own logging choices etc.


  
