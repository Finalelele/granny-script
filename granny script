local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "Granny",
   LoadingTitle = "Granny",
   LoadingSubtitle = "by Finalelele",
   ConfigurationSaving = {
      Enabled = false,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "Big Hub"
   },
   Discord = {
      Enabled = false,
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },
   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided",
      FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})

local Tab = Window:CreateTab("Player", 4483362458) -- Title, Image
local Section = Tab:CreateSection("Player Setting")
local Toggle = Tab:CreateToggle({
   Name = "Player Speed (if you been cliped you get easy ban)",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   if Value then
		local SpeedBox = workspace
		SpBox = Instance.new("BoxHandleAdornment")
		SpBox.Parent = SpeedBox
		SpBox.Name = "SpedBox"
		while wait(0.1) do
			local spb = workspace.SpedBox
			if spb.Parent == workspace then
				game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 20
			else
				break
			end
		end
	else
		local SpdBox = workspace.SpedBox
		SpdBox.Parent = nil
		game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 9
	end
end
})

local Tab = Window:CreateTab("Esp", 4483362458) -- Title, Image
local Section = Tab:CreateSection("Esp enemy")
local Toggle = Tab:CreateToggle({
   Name = "Esp Enemy",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   if Value then
		local granny = workspace.Map.Players.Enemy
		local enemyEsp = Instance.new("Highlight")
		enemyEsp.Parent = granny
		enemyEsp.FillColor = Color3.fromRGB(255, 0, 0)
		enemyEsp.FillTransparency = 0.5
		enemyEsp.OutlineColor = Color3.fromRGB(255, 255, 255)
		enemyEsp.OutlineTransparency = 0
		enemyEsp.DepthMode = "AlwaysOnTop"
		enemyEsp.Name = "EspEnemy"

		Toggle.WorkSpaceC = workspace.DescendantAdded:Connect(function(v)
			if v.Name == "Map" then
				wait(8)
				local granny = workspace.Map.Players.Enemy
				local enemyEsp = Instance.new("Highlight")
				enemyEsp.Parent = granny
				enemyEsp.FillColor = Color3.fromRGB(255, 0, 0)
				enemyEsp.FillTransparency = 0.5
				enemyEsp.OutlineColor = Color3.fromRGB(255, 255, 255)
				enemyEsp.OutlineTransparency = 0
				enemyEsp.DepthMode = "AlwaysOnTop"
				enemyEsp.Name = "EspEnemy"
			end
		end)
	else
		local enemyEspD = workspace.Map.Players.Enemy.EspEnemy
		enemyEspD:Destroy()

		if Toggle.WorkSpaceC then
			Toggle.WorkSpaceC:Disconnect()
			Toggle.WorkSpaceC = nil
		end
	end
end
})

local Toggle = Tab:CreateToggle({
    Name = "Esp Traps",
    CurrentValue = false,
    Flag = "Toggle1",
    Callback = function(Value)
    if Value then
		local function TrapCreateEsp(v)
			local espTrap = Instance.new("Highlight")
            espTrap.Parent = v
            espTrap.FillColor = Color3.fromRGB(255, 255, 0)
            espTrap.FillTransparency = 0.5
            espTrap.DepthMode = "AlwaysOnTop"
            espTrap.Name = "TrapEsp"
		end

        local mapTraps = workspace.Map.Traps
        for _, v in pairs(mapTraps:GetDescendants()) do
            if v.Name == "Trap" then
                TrapCreateEsp(v)
            end
        end

        Toggle.MapTrapC = mapTraps.DescendantAdded:Connect(function(v)
            if v.Name == "Trap" then
                TrapCreateEsp(v)
            end
        end)

		Toggle.MapTrapCRejoin = workspace.DescendantAdded:Connect(function(v)
			if v.Name == "Map" then
				local mapTraps = workspace.Map.Traps
				Toggle.MapTrapC2 = mapTraps.DescendantAdded:Connect(function(v)
           			if v.Name == "Trap" then
               			TrapCreateEsp(v)
            		end
        		end)
			end
		end)
    else
        local mapTraps = workspace.Map.Traps
        for _, v in pairs(mapTraps:GetDescendants()) do
            if v.Name == "TrapEsp" then
                v:Destroy()
            end
        end

        if Toggle.MapTrapC then
  			Toggle.MapTrapC:Disconnect()
    		Toggle.MapTrapC = nil
		end

		if Toggle.MapTrapCRejoin then
		    Toggle.MapTrapCRejoin:Disconnect()
		    Toggle.MapTrapCRejoin = nil
		end

		if Toggle.MapTrapC2 then
 			Toggle.MapTrapC2:Disconnect()
    		Toggle.MapTrapC2 = nil
		end
    end
end
})

local Toggle = Tab:CreateToggle({
    Name = "Esp Players",
    CurrentValue = false,
    Flag = "Toggle1",
    Callback = function(Value)
	if Value then
		local Fplayers = workspace.Map.Players
		for _,v in pairs (Fplayers:GetDescendants()) do
			if v.Name ~= "Enemy" and v:IsA("Model") then
				wait(0.1)
				local espPlayer = Instance.new("Highlight")
				espPlayer.Parent = v
    	    	espPlayer.FillColor = Color3.fromRGB(0, 255, 255)
    	    	espPlayer.FillTransparency = 0.5
   	    		espPlayer.DepthMode = "AlwaysOnTop"
				espPlayer.Name = "PlayerEsp"
			end
		end
		local avatar = workspace.Map.Players.Enemy.Avatar
		for _,v in pairs (avatar:GetDescendants()) do
			if v.Name == "PlayerEsp" then
				v:Destroy()
			end
		end
		
		Toggle.PlayerEspC = Fplayers.DescendantAdded:Connect(function(v)
			if v.Name ~= "Enemy" and v:IsA("Model") then
				wait(0.1)
				local espPlayer = Instance.new("Highlight")
				espPlayer.Parent = v
    	    	espPlayer.FillColor = Color3.fromRGB(0, 255, 255)
    	   		espPlayer.FillTransparency = 0.5
   	    		espPlayer.DepthMode = "AlwaysOnTop"
				espPlayer.Name = "PlayerEsp"
			end

			local avatar = workspace.Map.Players.Enemy.Avatar
			for _,v in pairs (avatar:GetDescendants()) do
				if v.Name == "PlayerEsp" then
					v:Destroy()
				end
			end
		end)
    else
        local Fplayers = workspace.Map.Players
		for _,v in pairs (Fplayers:GetDescendants()) do
			if v.Name == "PlayerEsp" then
				v:Destroy()
			end
		end

		if Toggle.PlayerEspC then
			Toggle.PlayerEspC:Disconnect()
			Toggle.PlayerEspC = nil
		end
    end
end
})

local Tab = Window:CreateTab("Esp tools", 4483362458) -- Title, Image
local Section = Tab:CreateSection("Esp")
local Toggle = Tab:CreateToggle({
   Name = "Esp House Tools",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   if Value then
		local function createHouseToolsEsp(v)
			local espToolsHouse = Instance.new("Highlight")
            espToolsHouse.Parent = v
            espToolsHouse.FillColor = Color3.fromRGB(0, 255, 0)
            espToolsHouse.FillTransparency = 0.5
            espToolsHouse.DepthMode = "AlwaysOnTop"
			espToolsHouse.Name = "HouseToolsEsp"
		end

		local houseTools = workspace.Map.House.Tools
		for _, v in pairs(houseTools:GetDescendants()) do
		 	if v:IsA("Model") then
				createHouseToolsEsp(v)
			end
		end

		Toggle.HouseToolsC = houseTools.DescendantAdded:Connect(function(v)
			if v:IsA("Model") then
				local houseTools = workspace.Map.House.Tools
    			for _, v in pairs(houseTools:GetDescendants()) do
        			if v.Name == "HouseToolsEsp" then
           				v:Destroy()
					end
        		end
				wait(0.01)
				local houseTools = workspace.Map.House.Tools
				for _, v in pairs(houseTools:GetDescendants()) do
		 			if v:IsA("Model") then
						createHouseToolsEsp(v)
					end
				end
			end

			if v.Name == "PlayerEsp" then
				v:Destroy()
			end
		end)

		Toggle.HouseToolsCRejoin = workspace.DescendantAdded:Connect(function(v)
			if v.Name == "Map" then
				local houseTools = workspace.Map.House.Tools
				Toggle.HouseToolsC2 = houseTools.DescendantAdded:Connect(function(v)
					if v:IsA("Model") then
						local houseTools = workspace.Map.House.Tools
    					for _, v in pairs(houseTools:GetDescendants()) do
        					if v.Name == "HouseToolsEsp" then
           						v:Destroy()
							end
        				end
						wait(0.01)
						local houseTools = workspace.Map.House.Tools
						for _, v in pairs(houseTools:GetDescendants()) do
		 					if v:IsA("Model") then
								createHouseToolsEsp(v)
							end
						end
					end

					if v.Name == "PlayerEsp" then
						v:Destroy()
					end
				end)
			end
		end)
	else
		local houseTools = workspace.Map.House.Tools
    	for _, v in pairs(houseTools:GetDescendants()) do
        	if v.Name == "HouseToolsEsp" then
           		v:Destroy()
			end
        end

		if Toggle.HouseToolsC then
			Toggle.HouseToolsC:Disconnect()
			Toggle.HouseToolsC = nil
		end

		if Toggle.HouseToolsCRejoin then
			Toggle.HouseToolsCRejoin:Disconnect()
			Toggle.HouseToolsCRejoin = nil
		end

		if Toggle.HouseToolsC2 then
			Toggle.HouseToolsC2:Disconnect()
			Toggle.HouseToolsC2 = nil
		end
    end
end
})

local Toggle = Tab:CreateToggle({
   Name = "Esp House II Tools",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   if Value then
		local function createHouse2ToolsEsp(v)
			local espToolsHouse2 = Instance.new("Highlight")
            espToolsHouse2.Parent = v
            espToolsHouse2.FillColor = Color3.fromRGB(0, 255, 0)
            espToolsHouse2.FillTransparency = 0.5
            espToolsHouse2.DepthMode = "AlwaysOnTop"
			espToolsHouse2.Name = "House2ToolsEsp"
		end

		local house2Tools = workspace.Map["House II"].Tools
		for _, v in pairs(house2Tools:GetDescendants()) do
		 	if v:IsA("Model") then
				createHouse2ToolsEsp(v)
			end
		end

		Toggle.House2ToolsC = house2Tools.DescendantAdded:Connect(function(v)
			if v:IsA("Model") then
				local house2Tools = workspace.Map["House II"].Tools
    			for _, v in pairs(house2Tools:GetDescendants()) do
        			if v.Name == "House2ToolsEsp" then
           				v:Destroy()
					end
        		end
				wait(0.01)
				local house2Tools = workspace.Map["House II"].Tools
				for _, v in pairs(house2Tools:GetDescendants()) do
		 			if v:IsA("Model") then
						createHouse2ToolsEsp(v)
					end
				end
			end

			if v.Name == "PlayerEsp" then
				v:Destroy()
			end
		end)

		Toggle.House2ToolsCRejoin = workspace.DescendantAdded:Connect(function(v)
			if v.Name == "Map" then
				local house2Tools = workspace.Map["House II"].Tools
				Toggle.House2ToolsC2 = house2Tools.DescendantAdded:Connect(function(v)
					if v:IsA("Model") then
						local house2Tools = workspace.Map["House II"].Tools
    					for _, v in pairs(house2Tools:GetDescendants()) do
        					if v.Name == "House2ToolsEsp" then
           						v:Destroy()
							end
        				end
						wait(0.01)
						local house2Tools = workspace.Map["House II"].Tools
						for _, v in pairs(house2Tools:GetDescendants()) do
		 					if v:IsA("Model") then
								createHouse2ToolsEsp(v)
							end
						end
					end

					if v.Name == "PlayerEsp" then
						v:Destroy()
					end
				end)
			end
		end)
	else
		local house2Tools = workspace.Map["House II"].Tools
    	for _, v in pairs(house2Tools:GetDescendants()) do
        	if v.Name == "House2ToolsEsp" then
           	 v:Destroy()
			end
        end

		if Toggle.House2ToolsC then
			Toggle.House2ToolsC:Disconnect()
			Toggle.House2ToolsC = nil
		end

		if Toggle.House2ToolsCRejoin then
			Toggle.House2ToolsCRejoin:Disconnect()
			Toggle.House2ToolsCRejoin = nil
		end

		if Toggle.House2ToolsC2 then
			Toggle.House2ToolsC2:Disconnect()
			Toggle.House2ToolsC2 = nil
		end
    end
end
})

local Toggle = Tab:CreateToggle({
   Name = "Esp Mansion Tools",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   if Value then
		local function createMansionToolsEsp(v)
			local espToolsMansion = Instance.new("Highlight")
            espToolsMansion.Parent = v
            espToolsMansion.FillColor = Color3.fromRGB(0, 255, 0)
            espToolsMansion.FillTransparency = 0.5
            espToolsMansion.DepthMode = "AlwaysOnTop"
			espToolsMansion.Name = "MansionToolsEsp"
		end

		local MansionTools = workspace.Map.Mansion.Tools
		for _, v in pairs(MansionTools:GetDescendants()) do
		 	if v:IsA("Model") then
				createMansionToolsEsp(v)
			end
		end

		Toggle.MansionToolsC = MansionTools.DescendantAdded:Connect(function(v)
			if v:IsA("Model") then
				local MansionTools = workspace.Map.Mansion.Tools
    			for _, v in pairs(MansionTools:GetDescendants()) do
        			if v.Name == "MansionToolsEsp" then
           				v:Destroy()
					end
        		end
				wait(0.01)
				local MansionTools = workspace.Map.Mansion.Tools
				for _, v in pairs(MansionTools:GetDescendants()) do
		 			if v:IsA("Model") then
						createMansionToolsEsp(v)
					end
				end
			end

			if v.Name == "PlayerEsp" then
				v:Destroy()
			end
		end)

		Toggle.MansionToolsCRejoin = workspace.DescendantAdded:Connect(function(v)
			if v.Name == "Map" then
				local MansionTools = workspace.Map.Mansion.Tools
				Toggle.MansionToolsC2 = MansionTools.DescendantAdded:Connect(function(v)
					if v:IsA("Model") then
						local MansionTools = workspace.Map.Mansion.Tools
    					for _, v in pairs(MansionTools:GetDescendants()) do
        					if v.Name == "MansionToolsEsp" then
           						v:Destroy()
							end
        				end
						wait(0.01)
						local MansionTools = workspace.Map.Mansion.Tools
						for _, v in pairs(MansionTools:GetDescendants()) do
		 					if v:IsA("Model") then
								createMansionToolsEsp(v)
							end
						end
					end

					if v.Name == "PlayerEsp" then
						v:Destroy()
					end
				end)
			end
		end)
	else
		local MansionTools = workspace.Map.Mansion.Tools
    	for _, v in pairs(MansionTools:GetDescendants()) do
        	if v.Name == "MansionToolsEsp" then
           	 v:Destroy()
			end
        end

		if Toggle.MansionToolsC then
			Toggle.MansionToolsC:Disconnect()
			Toggle.MansionToolsC = nil
		end

		if Toggle.MansionToolsCRejoin then
			Toggle.MansionToolsCRejoin:Disconnect()
			Toggle.MansionToolsCRejoin = nil
		end

		if Toggle.MansionToolsC2 then
			Toggle.MansionToolsC2:Disconnect()
			Toggle.MansionToolsC2 = nil
		end
    end
end
})

local Toggle = Tab:CreateToggle({
   Name = "Esp School Tools",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   if Value then
		local function createSchoolToolsEsp(v)
			local espToolsSchool = Instance.new("Highlight")
            espToolsSchool.Parent = v
            espToolsSchool.FillColor = Color3.fromRGB(0, 255, 0)
            espToolsSchool.FillTransparency = 0.5
            espToolsSchool.DepthMode = "AlwaysOnTop"
			espToolsSchool.Name = "SchoolToolsEsp"
		end

		local SchoolTools = workspace.Map.School.Tools
		for _, v in pairs(SchoolTools:GetDescendants()) do
		 	if v:IsA("Model") then
				createSchoolToolsEsp(v)
			end
		end

		Toggle.SchoolToolsC = SchoolTools.DescendantAdded:Connect(function(v)
			if v:IsA("Model") then
				local SchoolTools = workspace.Map.School.Tools
    			for _, v in pairs(SchoolTools:GetDescendants()) do
        			if v.Name == "SchoolToolsEsp" then
           				v:Destroy()
					end
        		end
				wait(0.01)
				local SchoolTools = workspace.Map.School.Tools
				for _, v in pairs(SchoolTools:GetDescendants()) do
		 			if v:IsA("Model") then
						createSchoolToolsEsp(v)
					end
				end
			end

			if v.Name == "PlayerEsp" then
				v:Destroy()
			end
		end)

		Toggle.SchoolToolsCRejoin = workspace.DescendantAdded:Connect(function(v)
			if v.Name == "Map" then
				local SchoolTools = workspace.Map.School.Tools
				Toggle.SchoolToolsC2 = SchoolTools.DescendantAdded:Connect(function(v)
					if v:IsA("Model") then
						local SchoolTools = workspace.Map.School.Tools
    					for _, v in pairs(SchoolTools:GetDescendants()) do
        					if v.Name == "SchoolToolsEsp" then
           						v:Destroy()
							end
        				end
						wait(0.01)
						local SchoolTools = workspace.Map.School.Tools
						for _, v in pairs(SchoolTools:GetDescendants()) do
		 					if v:IsA("Model") then
								createSchoolToolsEsp(v)
							end
						end
					end

					if v.Name == "PlayerEsp" then
						v:Destroy()
					end
				end)
			end
		end)
	else
		local SchoolTools = workspace.Map.School.Tools
    	for _, v in pairs(SchoolTools:GetDescendants()) do
        	if v.Name == "SchoolToolsEsp" then
           	 v:Destroy()
			end
        end

		if Toggle.SchoolToolsC then
			Toggle.SchoolToolsC:Disconnect()
			Toggle.SchoolToolsC = nil
		end

		if Toggle.SchoolToolsCRejoin then
			Toggle.SchoolToolsCRejoin:Disconnect()
			Toggle.SchoolToolsCRejoin = nil
		end

		if Toggle.SchoolToolsC2 then
			Toggle.SchoolToolsC2:Disconnect()
			Toggle.SchoolToolsC2 = nil
		end
    end
end
})

local Toggle = Tab:CreateToggle({
   Name = "Esp Ski resort Tools",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   if Value then
		local function createSkiResortEsp(v)
			local espToolsSkiResort = Instance.new("Highlight")
            espToolsSkiResort.Parent = v
            espToolsSkiResort.FillColor = Color3.fromRGB(0, 255, 0)
            espToolsSkiResort.FillTransparency = 0.5
            espToolsSkiResort.DepthMode = "AlwaysOnTop"
			espToolsSkiResort.Name = "SkiResortToolsEsp"
		end
		local SkiResortTools = workspace.Map["Ski resort"].Tools
		for _, v in pairs(SkiResortTools:GetDescendants()) do
		 	if v:IsA("Model") then
				createSkiResortEsp(v)
			end
		end

		Toggle.SkiResortToolsC = SkiResortTools.DescendantAdded:Connect(function(v)
			if v:IsA("Model") then
				local SkiResortTools = workspace.Map["Ski resort"].Tools
    			for _, v in pairs(SkiResortTools:GetDescendants()) do
        			if v.Name == "SkiResortToolsEsp" then
           				v:Destroy()
					end
        		end
				wait(0.01)
				local SkiResortTools = workspace.Map["Ski resort"].Tools
				for _, v in pairs(SkiResortTools:GetDescendants()) do
		 			if v:IsA("Model") then
						createSkiResortEsp(v)
					end
				end
			end

			if v.Name == "PlayerEsp" then
				v:Destroy()
			end
		end)

		Toggle.SkiResortToolsCRejoin = workspace.DescendantAdded:Connect(function(v)
			if v.Name == "Map" then
				local SkiResortTools = workspace.Map["Ski resort"].Tools
				Toggle.SkiResortToolsC2 = SkiResortTools.DescendantAdded:Connect(function(v)
					if v:IsA("Model") then
						local SkiResortTools = workspace.Map["Ski resort"].Tools
    					for _, v in pairs(SkiResortTools:GetDescendants()) do
        					if v.Name == "SkiResortToolsEsp" then
           						v:Destroy()
							end
        				end
						wait(0.01)
						local SkiResortTools = workspace.Map["Ski resort"].Tools
						for _, v in pairs(SkiResortTools:GetDescendants()) do
		 					if v:IsA("Model") then
								createSkiResortEsp(v)
							end
						end
					end

					if v.Name == "PlayerEsp" then
						v:Destroy()
					end
				end)
			end
		end)
	else
		local SkiResortTools = workspace.Map["Ski resort"].Tools
    	for _, v in pairs(SkiResortTools:GetDescendants()) do
        	if v.Name == "SkiResortToolsEsp" then
           	 v:Destroy()
			end
        end

		if Toggle.SkiResortToolsC then
			Toggle.SkiResortToolsC:Disconnect()
			Toggle.SkiResortToolsC = nil
		end

		if Toggle.SkiResortToolsCRejoin then
			Toggle.SkiResortToolsCRejoin:Disconnect()
			Toggle.SkiResortToolsCRejoin = nil
		end

		if Toggle.SkiResortToolsC2 then
			Toggle.SkiResortToolsC2:Disconnect()
			Toggle.SkiResortToolsC2 = nil
		end
    end
end
})

local Toggle = Tab:CreateToggle({
   Name = "Esp Cemetery Tools",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   if Value then
		local function createCemeteryEsp(v)
			local espToolsCemetery = Instance.new("Highlight")
            espToolsCemetery.Parent = v
            espToolsCemetery.FillColor = Color3.fromRGB(0, 255, 0)
            espToolsCemetery.FillTransparency = 0.5
            espToolsCemetery.DepthMode = "AlwaysOnTop"
			espToolsCemetery.Name = "CemeteryToolsEsp"
		end

		local CemeteryTools = workspace.Map.Cemetery.Tools
		for _, v in pairs(CemeteryTools:GetDescendants()) do
		 	if v:IsA("Model") then
				createCemeteryEsp(v)
			end
		end

		Toggle.CemeteryToolsC = CemeteryTools.DescendantAdded:Connect(function(v)
			if v:IsA("Model") then
				local CemeteryTools = workspace.Map.Cemetery.Tools
    			for _, v in pairs(CemeteryTools:GetDescendants()) do
        			if v.Name == "CemeteryToolsEsp" then
           				v:Destroy()
					end
        		end
				wait(0.01)
				local CemeteryTools = workspace.Map.Cemetery.Tools
				for _, v in pairs(CemeteryTools:GetDescendants()) do
		 			if v:IsA("Model") then
						createCemeteryEsp(v)
					end
				end
			end

			if v.Name == "PlayerEsp" then
				v:Destroy()
			end
		end)

		Toggle.CemeteryToolsCRejoin = workspace.DescendantAdded:Connect(function(v)
			if v.Name == "Map" then
				local CemeteryTools = workspace.Map.Cemetery.Tools
				Toggle.CemeteryToolsC2 = CemeteryTools.DescendantAdded:Connect(function(v)
					if v:IsA("Model") then
						local CemeteryTools = workspace.Map.Cemetery.Tools
    					for _, v in pairs(CemeteryTools:GetDescendants()) do
        					if v.Name == "CemeteryToolsEsp" then
           						v:Destroy()
							end
        				end
						wait(0.01)
						local CemeteryTools = workspace.Map.Cemetery.Tools
						for _, v in pairs(CemeteryTools:GetDescendants()) do
		 					if v:IsA("Model") then
								createCemeteryEsp(v)
							end
						end
					end

					if v.Name == "PlayerEsp" then
						v:Destroy()
					end
				end)
			end
		end)
	else
		local CemeteryTools = workspace.Map.Cemetery.Tools
    	for _, v in pairs(CemeteryTools:GetDescendants()) do
        	if v.Name == "CemeteryToolsEsp" then
           	 v:Destroy()
			end
        end

		if Toggle.CemeteryToolsC then
			Toggle.CemeteryToolsC:Disconnect()
			Toggle.CemeteryToolsC = nil
		end

		if Toggle.CemeteryToolsCRejoin then
			Toggle.CemeteryToolsCRejoin:Disconnect()
			Toggle.CemeteryToolsCRejoin = nil
		end

		if Toggle.CemeteryToolsC2 then
			Toggle.CemeteryToolsC2:Disconnect()
			Toggle.CemeteryToolsC2 = nil
		end
    end
end
})
