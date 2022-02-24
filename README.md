
# QbusToEsx Converting Qbus Scripts to ESX, Non-stop Update.
--------------------------------------------------------------------------------------------------
Qbus Foundation And ESX foundation.
 ```lua
QBCore = nil 

Citizen.CreateThread(function()
	while QBCore == nil do
		TriggerEvent('QBCore:GetObject', function(obj) QBCore = obj end)
		Citizen.Wait(30) -- Saniye Bekletme
	end
end)
```
Below is for the new ones -- above is for the old version, if it doesn't work try both...
```lua
local QBCore = exports['qb-core']:GetCoreObject()
```

# ABOVE QBUSCORE

# BELOW ESX
```lua
ESX = nil

Citizen.CreateThread(function()
  while ESX == nil do
    TriggerEvent('esx:getSharedObject', function(obj) ESX = obj end)
    Citizen.Wait(30)-- Saniye Bekletme
  end
end)
```

--------------------------------------------------------------------------------------------------

Gentlemen, this section was added.
Meaning:
The Player's Input Part is required when entering the game, that is, it is the server file.
This event is triggered when the player connects to the server
```lua
RegisterNetEvent('QBCore:Client:OnPlayerLoaded')
AddEventHandler('QBCore:Client:OnPlayerLoaded',
```
# ABOVE QBUSCORE

# BELOW ESX
```lua
RegisterNetEvent('esx:playerLoaded')
AddEventHandler('esx:playerLoaded',
```

--------------------------------------------------------------------------------------------------

Server File, Job Part is Occupation Part.
```lua
RegisterNetEvent('QBCore:Client:OnJobUptade')
AddEventHandler('QBCore:Client:OnJobUptade', 
```
# ABOVE QBUSCORE

# BELOW ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob',
```

--------------------------------------------------------------------------------------------------

You Can Check Here.
https://esx-framework.github.io/es_extended/common/events/onplayerdeath/#example-client-side-usage
```lua
RegisterNetEvent('QBCore:Client:OnPlayerUnload')
AddEventHandler('QBCore:Client:OnPlayerUnload',
```
# ABOVE QBUSCORE

# BELOW ESX
```lua
RegisterNetEvent('esx:onPlayerDeath')
AddEventHandler('esx:onPlayerDeath',
```

--------------------------------------------------------------------------------------------------

Gentlemen, this section was added.
Meaning:
This function gets the nearest player client id and distance to the player.
```lua
QBCore.Functions.GetClosestPlayer()
```
# ABOVE QBUSCORE

# BELOW ESX
```lua
ESX.Game.GetClosestPlayer()
```

--------------------------------------------------------------------------------------------------

Adding 3D Text, Cilent File. Sample :
https://media.discordapp.net/attachments/623207764314816562/812096508786507806/resim_1.png
```lua
QBCore.Functions.DrawText3D(1, 1, 1, 'Sample')
```
# ABOVE QBUSCORE

# BELOW ESX
```lua
DrawText3D(1, 1, 1, 'Example') -- (You need to open function below.)
ESX.Game.Utils.DrawText3D(1, 1, 1, 'Example') -- ESX doesn't need it, it already has the function.
```

------------------------------------------------ ------------------------------------------------

Menu Open Close Menus in ESX & QBCore Examples: https://prnt.sc/u4f7s5
``
QBCore.UI.Menu.Open
QBCore.UI.Menu.CloseAll() -- (you need to install menu default script.)
```
# ABOVE QBUSCORE

# ESX BELOW
``
ESX.UI.Menu.Open
ESX.UI.Menu.CloseAll()
```

------------------------------------------------ ------------------------------------------------
Notification Script Example: https://dosya.turkmmo.com/2020/09/36521_efa54848705a4069cbedfc2770e50cf1.png
``
QBCore.Functions.Notify("Tool locked.", "error")
```
# ABOVE QBUSCORE

# ESX BELOW
``
TriggerEvent('Notification',"Example.")
```

--------------------------------------------------------------------------------------------------

Inventory Item Section.
``
xPlayer.Functions.GetItemByName
```
# ABOVE QBUSCORE

# ESX BELOW
``
xPlayer.getInventoryItem
```
--------------------------------------------------------------------------------------------------

Inventory Item Section.
``
xPlayer.Functions.GetItemByName
```
# ABOVE QBUSCORE

# ESX BELOW
``
xPlayer.getInventoryItem
```

--------------------------------------------------------------------------------------------------

Job Initial code.
```lua
RegisterNetEvent('QBCore:Client:OnJobUpdate')
AddEventHandler('QBCore:Client:OnJobUpdate', function(job)
    PlayerData.job = job
end)
```
# ABOVE QBUSCORE

# BELOW ESX
```lua
RegisterNetEvent('esx:setJob')
AddEventHandler('esx:setJob', function(job)
    PlayerData.job = job
end)
```

--------------------------------------------------------------------------------------------------

Give Money Get Money Section
``
Player.Functions.AddMoney('bank', amount, "Bank deposit") -- bank
Player.Functions.RemoveMoney('cash', amount, "Bank deposit") -- money on it
```
# ABOVE QBUSCORE

# ESX BELOW
``
xPlayer.removeAccountMoney('bank', amount) --remove money
xPlayer.addMoney(amount) -- add money
```

--------------------------------------------------------------------------------------------------

Money Part Data.
``
Player.PlayerData.money["bank"]
```
# ABOVE QBUSCORE

# ESX BELOW
``
xPlayer.getAccount('bank').money
```

--------------------------------------------------------------------------------------------------

Inventory Item Deletion Section.
``
xPlayer.Functions.RemoveItem
```
# ABOVE QBUSCORE

# ESX BELOW
``
xPlayer.removeInventoryItem
```

--------------------------------------------------------------------------------------------------

Adding Inventory Items.
``
xPlayer.Functions.AddItem
```
# ABOVE QBUSCORE

# ESX BELOW
``
xPlayer.addInventoryItem
```

--------------------------------------------------------------------------------------------------

The Character Is Something Like The Id Of The Player.
``
QBCore.Functions.GetPlayer(src)
```
# ABOVE QBUSCORE

# ESX BELOW
``
ESX.GetPlayerFromId(src)
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetPlayerByCitizenId(src)
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.GetPlayerFromIdentifier(src)
```

--------------------------------------------------------------------------------------------------

This function crops a text, removing all trailing white spaces. Usually `GetVehicleNumberPlateText()` is used when sanitizing locals.
#sample
``
QBCore.Functions.MathTrim(GetVehicleNumberPlateText(vehicle))
````
#standard
``
QBCore.Functions.MathTrim
```
# ABOVE QBUSCORE

# ESX BELOW
``
ESX.Math.Trim(value)
```

--------------------------------------------------------------------------------------------------

Nill is unknown in this will be updated
# SAMPLE
``
QBCore.Functions.MathRound(GetVehicleBodyHealth(vehicle), 1),
```
#standard
``
QBCore.Functions.MathRound()
```
# ABOVE QBUSCORE

# ESX BELOW
# SAMPLE
``
local value - 5.444

print('value:' ..value) - returns 5,444 --
print ('value rounded:' .. ESX.Math.Round(value)) -- returns 5
print ('value rounded:' .. ESX.Math.Round(value, 1)) -- returns 5.4
```
#standard
``
ESX.Math.Round(value, numberDecimals)
```

--------------------------------------------------------------------------------------------------

Car Spawn Part Location Vsb Stuff.
``
QBCore.Functions.SpawnVehicle()
QBCore.Functions.DeleteVehicle()
QBCore.Functions.GetVehicleProperties()
QBCore.Functions.GetClosestVehicle()
```
# ABOVE QBUSCORE

# ESX BELOW
``
ESX.Game.SpawnVehicle()
ESX.Game.DeleteVehicle()
ESX.Game.GetVehicleProperties()
ESX.Game.GetClosestVehicle()
```
--(Almost everything that is ESX.Game is the same as QBCore.Functions.)

--------------------------------------------------------------------------------------------------

The Player is Your Own Character.
``
QBCore.Functions.GetPlayerData()
```
# ABOVE QBUSCORE

# ESX BELOW
``
ESX.GetPlayerData()
```
--------------------------------------------------------------------------------------------------

Item Creation.
``
QBCore.Functions.CreateUseableItem()
```
# ABOVE QBUSCORE

# ESX BELOW
``
ESX.RegisterUsableItem()
```

--------------------------------------------------------------------------------------------------

Bank Money Removal.
``
Player.Functions.RemoveMoney()
```
# ABOVE QBUSCORE

# ESX BELOW
``
xPlayer.removeMoney(money)
```

--------------------------------------------------------------------------------------------------

About Files.
``
QBCore.Functions.CreateCallback()
```
# ABOVE QBUSCORE

# ESX BELOW
``
ESX.RegisterServerCallback()
```

--------------------------------------------------------------------------------------------------

About Files.
``
QBCore.Functions.TriggerCallback()
```
# ABOVE QBUSCORE

# ESX BELOW
``
ESX.TriggerServerCallback()
```

--------------------------------------------------------------------------------------------------

identifier is used in cid esx in qb I left a small code block for you to solve the event.
```lua
QBCore.Functions.CreateCallback('system:fetchStatus', function(source, cb)
    local Player = QBCore.Functions.GetPlayer(source)

     if Player then
           exports['ghmattimysql']:execute('SELECT skills FROM players WHERE citizenid = @citizenid', {
               ['@citizenid'] = Player.PlayerData.citizenid
          }, function(status)
              if status ~= nil then
                   cb(json.decode(status))
              else
                   cb(nil)
              end
          end)
     else
          cb()
     end
end)
```
# ABOVE QBUSCORE

# ESX BELOW

```lua
ESX.RegisterServerCallback("system:fetchStatus", function(source, cb)
    local src = source
    local user = ESX.GetPlayerFromId(src)


    local fetch = [[
         SELECT
              skills
         FROM
              users
         WHERE
              identifier = @identifier
    ]]

    MySQL.Async.fetchScalar(fetch, {
         ["@identifier"] = user.identifier

    }, function(status)

         if status ~= nil then
              cb(json.decode(status))
         else
              cb(nil)
         end

    end)
end)
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Shared.Items
```
# ABOVE QBUSCORE

# ESX BELOW
```lua
ESX.GetItems()
```
--------------------------------------------------------------------------------------------------

SQL binding part
```lua
QBCore.Functions.ExecuteSql()
```
# ABOVE QBUSCORE

# ESX BELOW
```lua
ESX.ExecuteSql() --(ghmattimysql)
MySQL.Async.execute()
```

--------------------------------------------------------------------------------------------------


RegisterCommand - the chat command part.
``
QBCore.Commands.Add()
```
# ABOVE QBUSCORE

# ESX BELOW
``
RegisterCommand
```
-- (RegisterCommand also works in qbcore.)

--------------------------------------------------------------------------------------------------

Character Part Dir Data Test Binding.
``
local Player = QBCore.Functions.GetPlayer(source)
['@citizenid'] = Player.PlayerData.citizenid -- pull Player
```
# ABOVE QBUSCORE

# ESX BELOW
``
local user = ESX.GetPlayerFromId(src)
["@identifier"] = user.identifier -- pull user
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Shared.Trim()
QBCore.Shared.GroupDigits()
```
# ÜSTEKİ QBUSCORE

# ALTAKİ ESX
```lua
ESX.Math.Trim()
ESX.Math.GroupDigits()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetClosestObject()
```
# ABOVE QBUSCORE

# ESX BELOW
```lua
ESX.Game.GetClosestObject()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetVehicleInDirection()
```
# ABOVE QBUSCORE

# ESX BELOW
```lua
ESX.Game.GetVehicleInDirection()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetPeds()
```
# ABOVE QBUSCORE

# ESX BELOW
```lua
ESX.Game.GetPeds()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetObjects()
```
# ABOVE QBUSCORE

# ESX BELOW
```lua
ESX.Game.GetObjects()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.GetClosestPed()
```
# ABOVE QBUSCORE

# ESX BELOW
```lua
ESX.Game.GetClosestPed()
```

--------------------------------------------------------------------------------------------------

```lua
QBCore.Functions.SpawnObject()
```
# ABOVE QBUSCORE

# ESX BELOW
```lua
ESX.Game.SpawnObject()
```

--------------------------------------------------------------------------------------------------
