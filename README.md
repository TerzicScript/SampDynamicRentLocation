# SampDynamicRentLocation


English : This is include for dynamic rent locations. At each location you can rent a vehicles. It will not expire in time, and will only expire if player leaves them for 3 minutes or dissconnects from the server. It is using Y_INI saving

Serbian : Ovo je include za dinamicne rent lokacije. Na svakoj rent lokaciji mozete rentovati vozilo koje ne istice, vec se unistava ako igrac ne udje u njega na 3 minuta ili se diskonektuje sa servera. Za cuvanje koristi Y_INI

Includes needed : 
        - y_hooks
        - y_timers
        - y_ini
        - streamer
        
 Functions : 
        - RemoveRentLoc(playerid, rentid) - It is used to remove rent location by specifying RENT ID (playerid is used to send message to user removing rent location)
        - CreateRentLoc(playerid, rentid) - Creates rent location on the coordinates where player is currently standing
        - IniLoadRentLocations()          - This is called under GameModeInit to load existing rent locations and to show message in console 
        - RentVehicle(playerid)           - Function is used to check if player rented some vehicle, if he didn't it will show rent dialog if player is near Rent Location
        - UnRentVehicle(playerid)         - Checks if player rented vehicle, if he did it will destroy it for him
        
Usage Examples :

        CMD:deleterentloc(playerid, params[]) { //Used to remove rent location
          new id;
          if(sscanf(params, "d", id)) return SendClientMessage(playerid, -1, "/deleterentloc [ID]");
          RemoveRentLoc(playerid, id);
          return 1;
        }
        CMD:createrent(playerid, params[]) { //Used to create rent location
            new id;
            if(sscanf(params, "d", id)) return SendClientMessage(playerid, -1, "/createrent [ID]");
            CreateRentLoc(playerid, id);
            return 1;
        }
        CMD:rent(playerid, params[]) { //Used to rent vehicle 
            RentVehicle(playerid);
            return 1;
        }
        CMD:unrent(playerid, params[]) { //Used to unrent vehicle
            UnRentVehicle(playerid);
            return 1;
        }

