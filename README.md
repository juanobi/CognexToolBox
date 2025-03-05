# CognexToolBox
A  UR Script file with a collection of functions for Native Mode communications to In-Sight cameras
In your before start, add a script and select file.
Load 2024_9_24 Cognex_native_comm_toolbox.script. 
Adjsut the settings for camera connection and connection attempts and timeouts.
Refer to the header for information about the functions:

** cog_telnet_login(): used to login to the Cognex camera. uses the camera settings defined below
 
** cog_setonline(state): used to set the camera online or offline. will not force the 
                       camera online if it boots offline and has not been set online by other means.
   state:
       0 = offline
       1 = online
 
** cog_loadfile(fileName): used to load a job file. Must take camera offline first, then put back online.
   example using assignment: load_file_result=cog_loadfile("samplejob")
 
** cog_cmd_send(nm_cmd): send a command to the camera and report the results. eaxmaple using assignment:
                       command_result=cmg_cmd_send("SIA00217") to set call A2 to 17. command result will
                       be 1 if successful.
   nm_cmd:
       Native mode SET command to be sent to camera. must be inside quotes.
 
** cog_get(nm_cmd): send a command to the camera to get a value back. example using assignment:
                    get_result=cog_get("GVC002"). get_result will be set to the value in the cell.
                    An array will be returned: [response,value]
                    response = command response from camera
                    value = value of the get command   

   nm_cmd:
       Native mode GET command to be sent to camera. must be inside quotes.
 
** cog_open_socket(): used to open the socked connection. called by cog_telnet_login()
 
** cog_close_socket(): close the socket
 
** send_str(str, socketname): used by other functions to add the CR and LF to the string sent to the camera.

** cog_trigger(): sends a SE8 to the camera to trigger an acquisition
