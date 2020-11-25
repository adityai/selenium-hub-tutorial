# Setup selenium hub and node

## Hub
### Basic startup of hub 
`java -jar selenium-server-standalone.jar -role hub`

### Start hub with json config file
`java -jar selenium-server-standalone.jar -role hub -hubConfig hubConfig.json -debug`

### Sample hubConfig.json
`{
  "_comment" : "Configuration for Hub - hubConfig.json",
  "host": ip,
  "maxSession": 5,
  "port": 4444,
  "cleanupCycle": 5000,
  "timeout": 300000,
  "newSessionWaitTimeout": -1,
  "servlets": [],
  "prioritizer": null,
  "capabilityMatcher": "org.openqa.grid.internal.utils.DefaultCapabilityMatcher",
  "throwOnCapabilityNotPresent": true,
  "nodePolling": 180000,
  "platform": "WINDOWS"}
`

### Start hub with logging
`java -jar selenium-server-standalone.jar -role hub -log log.txt`

### Start hub in debug mode
`java -jar selenium-server-standalone.jar -role hub -debug`


## Node
### Basic startup of node
`java -jar selenium-server-standalone.jar -role node -hub http://localhost:4444`

### Start node with json config file
`java -Dwebdriver.chrome.driver=chromedriver.exe -jar selenium-server-standalone.jar -role node -nodeConfig node1Config.json`

### Sample node1Config.json
`
{
  "capabilities": [
    {
      "browserName": "firefox",
      "acceptSslCerts": true,
      "javascriptEnabled": true,
      "takesScreenshot": false,
      "firefox_profile": "",
      "browser-version": "27",
      "platform": "WINDOWS",
      "maxInstances": 5,
      "firefox_binary": "",
      "cleanSession": true
    },
    {
      "browserName": "chrome",
      "maxInstances": 5,
      "platform": "WINDOWS",
      "webdriver.chrome.driver": "C:/Program Files (x86)/Google/Chrome/Application/chrome.exe"
    },
    {
      "browserName": "internet explorer",
      "maxInstances": 1,
      "platform": "WINDOWS",
      "webdriver.ie.driver": "C:/Program Files (x86)/Internet Explorer/iexplore.exe"
    }
  ],
  "configuration": {
    "_comment" : "Configuration for Node",
    "cleanUpCycle": 2000,
    "timeout": 30000,
    "proxy": "org.openqa.grid.selenium.proxy.WebDriverRemoteProxy",
    "port": 5555,
    "host": ip,
    "register": true,
    "hubPort": 4444,
    "maxSession": 5
  }
}
`

