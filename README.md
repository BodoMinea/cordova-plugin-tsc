TSC Portable Thermal Printer Cordova Plugin with support for direct commands, plain text line printing
====================

Install:

`cordova plugin add git://github.com/BodoMinea/cordova-plugin-tsc`

Example for printing plain text (using escaped commands to enter and exit line mode - <ESC>Y and <ESC>Z as hex bytes):
```
TscPrinter.connectPrinter(localStorage.getItem('prmac'), function(){ // initiate connection to stored MAC address
    TscPrinter.sendCommand(String.fromCharCode(0x1B,0x59), function(){ // enter line mode
        TscPrinter.sendCommand("\r\nTEST\r\n", function(){ // send text
            setTimeout(function(){
                TscPrinter.sendCommand(String.fromCharCode(0x1B,0x5A), function(){ // exit line mode
                    TscPrinter.closeConnection(); // end connection
                });
            },3500);
        });
    });
});
```
  
TSPL manual: https://web.archive.org/web/20210308032715/http://www.kroyeuropedownload.com/English_User_Manuals/TSPL_TSPL2_Programming_Jan_2017.pdf
