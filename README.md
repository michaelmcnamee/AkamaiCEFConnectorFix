# AkamaiCEFConnectorFix
This is a replacement .sh file for Akamai CEF Connector 1.7.5 that fixes an issue preventing the stop command from working. 


The "kill" command does not work on the AkamaiConnector.sh due to an error on line 19 of the file, seen here -

          PID=`ps ax | grep -e"CEFCONNECTOR.KILL.MARK" | grep -v "grep" | awk '{printf(substr($0,1,6))}'`.

The 6 should be a 7, as limiting the output to 6 values removes the last value of the PID, so the PID is always incorrect. This prevents the command from working on anything other than ./AkamaiConnector.sh start.
