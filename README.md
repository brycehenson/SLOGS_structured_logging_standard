# SLOGS (structured logging standard)
Defining a standard for logging data to a json structure.
## design philosophy
- human and machine readable
- lagnuage agnostic
- verbose over compressed
- widely usable, from a single computer to 1000's

## Design Questions
- what should the file extension be? example_log_20190402T141013.txt or .json .slogs or something else
- for multi machine logging how to aviod name collisions of logs.
- am i missing important fields

## example log
example_log_20190402T141013.txt
here i show a line that is  (structured)[http://jsonviewer.stack.hu/] for human reading. // denotes comments
```json5
{
  "time_iso": "2019-04-02T14:10:13.110+11:00", // mandatory with local time zone, YYYY-MM-DDThh:mm:ss.sss±hh:mm
  "time_posix": 1.55417461311E+9,//mandatory UTC time
  "level": "log", //mandatory, 'log','ERROR','data','analysis' 
  "environment": { //optional for all but first line of each log file
    "tier": "development", //'development','testing,'model','production'
    "architecture": "win64",
    "computer_name": "brycelap",
    "network_interfaces": [
      {
        "FriendlyName": "Ethernet",
        "Description": "Realtek PCIe GBE Family Controller",
        "MAC_address": "xx-xx-xx-xx-xx-xx",
        "IPv4_address": "xxx.xxx.xxx.xxx",
        "IPv6_address": "xxxx::xxxx:xxxx:xxxx:xxxx"
      },
      {
        "FriendlyName": "Wi-Fi",
        "Description": "Intel(R) Dual Band Wireless-AC 7260",
        "MAC_address": "xx-xx-xx-xx-xx-xx",
        "IPv4_address": "xx.xx.xx.xx",
        "IPv6_address": "xxxx::xxxx:xxxx:xxxx:xxxx"
      }
    ]
  },
  "operation": "demonstrating how to use SLOGS", //mandatory string
  "parameters": { //optional, specify state/data parameters here
    "photodiode_power": 0.46658893504181043,
    "drive_voltage": 1.1508870929981723,
    "feedback_error": -0.53341106495818957,
    "feedback_loop_time": 0.080674726853994641
  }
}
```	

## Resources
- [structured logging](https://stackify.com/what-is-structured-logging-and-why-developers-need-it/)
