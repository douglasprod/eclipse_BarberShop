## [ESX]Eclipse BarberShop

## Requirements
- [plume-esx](https://youtu.be/iGfwUCO0RZQ) (you can use different version esx)
- [esx-skin](https://github.com/esx-framework/esx_skin)
- [skinchanger](https://github.com/ESX-Org/skinchanger)


Put eclipse_BarberShop in your resource directory

Setting config `resources\eclipse_BarberShop\config.json`

	Change language, add new shops and etc.
  ![image](https://cdn.discordapp.com/attachments/759479979435098152/943156160901566524/unknown.png)
  
## Installation:

skinchanger:
1. Go to skinchanger/client/main.lua
2. add the following code to the end 
```lua
local CharacterData = {}

RegisterNetEvent('skinchanger:buyEyebrows')
AddEventHandler('skinchanger:buyEyebrows', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['eyebrows_1'] = shopData.eyebrows_1
		characterData['eyebrows_2'] = shopData.eyebrows_2
		characterData['eyebrows_3'] = shopData.eyebrows_3
		characterData['eyebrows_4'] = shopData.eyebrows_4
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

RegisterNetEvent('skinchanger:buyBeard')
AddEventHandler('skinchanger:buyBeard', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['beard_1'] = shopData.beard_1
		characterData['beard_2'] = shopData.beard_2
		characterData['beard_3'] = shopData.beard_3
		characterData['beard_4'] = shopData.beard_4
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

RegisterNetEvent('skinchanger:buyChest')
AddEventHandler('skinchanger:buyChest', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['chest_1'] = shopData.chest_1
		characterData['chest_2'] = shopData.chest_2
		characterData['chest_3'] = shopData.chest_3
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)


RegisterNetEvent('skinchanger:buyHair')
AddEventHandler('skinchanger:buyHair', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['hair_color_1'] = shopData.hair_color_1
		characterData['hair_color_2'] = shopData.hair_color_2
		characterData['hair_1'] = shopData.hair_1
		characterData['hair_2'] = shopData.hair_2
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

RegisterNetEvent('skinchanger:buySunDamage')
AddEventHandler('skinchanger:buySunDamage', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['sun_1'] = shopData.sun_1
		characterData['sun_2'] = shopData.sun_2
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

AddEventHandler('skinchanger:updateSunDamage', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 7,		CharacterData['sun_1'],				(CharacterData['sun_2'] / 10) + 0.0)			-- Sun Damage + opacity
end)

RegisterNetEvent('skinchanger:buyMolesFreckes')
AddEventHandler('skinchanger:buyMolesFreckes', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['moles_1'] = shopData.moles_1
		characterData['moles_2'] = shopData.moles_2
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

AddEventHandler('skinchanger:updateLipstick', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 8,		CharacterData['lipstick_1'],		(CharacterData['lipstick_2'] / 10) + 0.0)		-- Lipstick + opacity
	SetPedHeadOverlayColor		(playerPed, 8, 1,	CharacterData['lipstick_3'],		CharacterData['lipstick_4'])					-- Lipstick Color
end)

RegisterNetEvent('skinchanger:buyLipstick')
AddEventHandler('skinchanger:buyLipstick', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['lipstick_1'] = shopData.lipstick_1
		characterData['lipstick_2'] = shopData.lipstick_2
		characterData['lipstick_3'] = shopData.lipstick_3
		characterData['lipstick_4'] = shopData.lipstick_4
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

AddEventHandler('skinchanger:updateBlush', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 5,		CharacterData['blush_1'],			(CharacterData['blush_2'] / 10) + 0.0)			-- Blush + opacity
	SetPedHeadOverlayColor		(playerPed, 5, 2,	CharacterData['blush_3'])			
end)

RegisterNetEvent('skinchanger:buyBlush')
AddEventHandler('skinchanger:buyBlush', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['blush_1'] = shopData.blush_1
		characterData['blush_2'] = shopData.blush_2
		characterData['blush_3'] = shopData.blush_3
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

AddEventHandler('skinchanger:updateMakeup', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	print(CharacterData['makeup_1'])
	SetPedHeadOverlay			(playerPed, 4,		CharacterData['makeup_1'],			(CharacterData['makeup_2'] / 10) + 0.0)			-- Makeup + opacity
	SetPedHeadOverlayColor		(playerPed, 4, 2,	CharacterData['makeup_3'],			32)						-- Makeup Color
end)

RegisterNetEvent('skinchanger:buyMakeup')
AddEventHandler('skinchanger:buyMakeup', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['makeup_1'] = shopData.makeup_1
		characterData['makeup_2'] = shopData.makeup_2
		characterData['makeup_3'] = shopData.makeup_3
		characterData['makeup_4'] = shopData.makeup_4
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

AddEventHandler('skinchanger:updateMolesFreckes', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 9,		CharacterData['moles_1'],			(CharacterData['moles_2'] / 10) + 0.0)			-- Moles/Freckles + opacity
end)

RegisterNetEvent('skinchanger:buyComplexion')
AddEventHandler('skinchanger:buyComplexion', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['complexion_1'] = shopData.complexion_1
		characterData['complexion_2'] = shopData.complexion_2
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

AddEventHandler('skinchanger:updateComplexion', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 6,		CharacterData['complexion_1'],		(CharacterData['complexion_2'] / 10) + 0.0)		-- Complexion + opacity
end)

RegisterNetEvent('skinchanger:buyBlemishess')
AddEventHandler('skinchanger:buyBlemishess', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['blemishes_1'] = shopData.blemishes_1
		characterData['blemishes_2'] = shopData.blemishes_2
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

AddEventHandler('skinchanger:updateBlemishess', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 0,		CharacterData['blemishes_1'],		(CharacterData['blemishes_2'] / 10) + 0.0)		-- Blemishes + opacity
end)

AddEventHandler('skinchanger:updateBodyBlemishess', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	print(data)
	SetPedHeadOverlay			(playerPed, 11,		CharacterData['bodyb_1'],		(CharacterData['bodyb_2'] / 10) + 0.0)		-- Complexion + opacity
end)


RegisterNetEvent('skinchanger:buyBodyBlemishess')
AddEventHandler('skinchanger:buyBodyBlemishess', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['bodyb_1'] = shopData.bodyb_1
		characterData['bodyb_2'] = shopData.bodyb_2
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

RegisterNetEvent('skinchanger:buyAgeing')
AddEventHandler('skinchanger:buyAgeing', function(data) 
	local shopData = json.decode(data)
	TriggerEvent('skinchanger:getSkin', function(skin)
		local characterData = skin
		characterData['age_1'] = shopData.age_1
		characterData['age_2'] = shopData.age_2
		ApplySkin(characterData)
		TriggerServerEvent('ECLIPSE:SaveData', json.encode(characterData))
	end)
end)

AddEventHandler('skinchanger:updateAgeing', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 3,		CharacterData['age_1'],				(CharacterData['age_2'] / 10) + 0.0)			-- Age + opacity
end)

AddEventHandler('skinchanger:updateHair', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHairColor				(playerPed,			CharacterData['hair_color_1'],		CharacterData['hair_color_2'])					-- Hair Color
	SetPedComponentVariation	(playerPed, 2,		CharacterData['hair_1'],			CharacterData['hair_2'], 2)						-- Hair
end)

AddEventHandler('skinchanger:updateEyebrows', function(data) 
	print('updateEyebrows')
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 2,		CharacterData['eyebrows_1'],		(CharacterData['eyebrows_2'] / 10) + 0.0)		-- Eyebrows + opacity
	SetPedHeadOverlayColor		(playerPed, 2, 1,	CharacterData['eyebrows_3'],		CharacterData['eyebrows_4'])					-- Eyebrows Color
end)

AddEventHandler('skinchanger:updateBeard', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 1,		CharacterData['beard_1'],			(CharacterData['beard_2'] / 10) + 0.0)			-- Beard + opacity
	SetPedHeadOverlayColor		(playerPed, 1, 1,	CharacterData['beard_3'],			CharacterData['beard_4'])						-- Beard Color
end)

AddEventHandler('skinchanger:updateChest', function(data) 
	CharacterData = json.decode(data)
	local playerPed = PlayerPedId()
	SetPedHeadOverlay			(playerPed, 10,		CharacterData['chest_1'],			(CharacterData['chest_2'] / 10) + 0.0)			-- Chest Hair + opacity
	SetPedHeadOverlayColor		(playerPed, 10, 1,	CharacterData['chest_3'])		

end)



--
```


Start your server.

For more questions https://discord.gg/8nXR6rfB2C




