# CommandBox with CFconfig


### CommandBox Setup

1. Install CommandBox and CFconfig via commandline
2. Go to the app folder (i.e peoplesclues, testapp)
3. Make sure server-{app}.json and .CFconfig.json is available under the app folder
4. Run CommandBox as sudo 
5. Sudo su -> passoword and then box
6. Make sure your rewriterules are in place if you have it enabled
7. Change your hosts file with the domain if you wish to have it run on port 80, 443
      * 127.0.0.1       testapp.com
      * Have the same entries in the host node under your server.json file (example below)
      ```json
            {
              "app":{
                  "cfengine":"adobe@2018.0.10+320417"
              },
              "name":"xyz-app",
              "web":{
                  "host":"xyz.com",
                  "hostAlias":[
                      "mysite.xyz.com",
                      "myanothersite.xyz.com"
                  ],
                  "http":{
                      "port":"80"
                  },
                  "SSL":{
                      "enable":true,
                      "port":443
                  },
                  "rewrites":{
                      "config":"urlrewrite.xml",
                      "enable":true
                  }
              },
              "-debug":"true"
          }```
8. Sometimes you may run into the scripts not being loaded under CFadmin. Jquery.js is throwing 404. Following things can be checked.
      * CFFormScriptDirectory in .CFconfig.json if you are using it
      * You may have to set "/cfscripts/scripts/" or try keeping it blank. I still haven't figured out the actual fix but this setting seems to work depending on the CF and CB versions that you use.

### Frequently used CommandBox commands

1. server start xyz --debug
2. server stop xyz
3. server forget xyz
4. server forget xyz --force
5. server list
6. server start xyz --debug --console
7. system update

### CFconfig commands for settings done once configured

1.cfconfig datasource save name=test dbdriver=mysql host=asdasd.asdas.aws.com port=3306 database=dbname username=username password=pass
2.cfconfig set CFFormScriptDirectory="/cf_scripts/scripts/" to=xyz

