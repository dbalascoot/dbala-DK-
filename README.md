local AutoFarm = {
    Enabled = false,
    CurrentLevel = 1,
    TargetLevel = 2650,
    Paused = false,
    AutoQuest = true,
    UseFruitSkills = true,
    UseSword = true,
    UseGun = false,
    UseHaki = true,
    SafeHealth = 30, -- % de vida para recuar e curar
    CriticalHealth = 20, -- % de vida para fugir
    LastQuestCompleted = false
}


local Keys = {
    Attack = "MouseButton1",
    Skill_Z = "Z",
    Skill_X = "X",
    Skill_C = "C",
    Skill_V = "V",
    Skill_F = "F",
    Healing = "1",
    Weapon1 = "1",
    Weapon2 = "2",
    Melee = "Z",
    Haki = "H",
    Jump = "Space",
    FastAttack = true
}

-- Rotas de farming baseadas em nível
local FarmingRoutes = {}


local function SetupFarmingRoutes()
 
    FarmingRoutes[1] = {
        MinLevel = 1,
        MaxLevel = 14,
        Area = "Starter Island",
        QuestNPC = "Mayor",
        QuestName = "Defeat Bandits",
        EnemyNames = {"Bandit"},
        FarmLocation = "Starter Island Hills"
    }

    FarmingRoutes[2] = {
        MinLevel = 15,
        MaxLevel = 29,
        Area = "Jungle Island",
        QuestNPC = "Explorer",
        QuestName = "Monkey Business",
        EnemyNames = {"Monkey"},
        FarmLocation = "Jungle Clearing"
    }
    
 
    FarmingRoutes[3] = {
        MinLevel = 30,
        MaxLevel = 44,
        Area = "Pirate Village",
        QuestNPC = "Village Chief",
        QuestName = "Defeat Buggy Pirates",
        EnemyNames = {"Buggy Pirate", "Pirate"},
        FarmLocation = "Pirate Docks"
    }

    FarmingRoutes[4] = {
        MinLevel = 45,
        MaxLevel = 59,
        Area = "Orange Town",
        QuestNPC = "Mayor",
        QuestName = "Cabin Boy Trouble",
        EnemyNames = {"Cabin Boy"},
        FarmLocation = "Orange Town Outskirts"
    }
    

    FarmingRoutes[5] = {
        MinLevel = 60,
        MaxLevel = 74,
        Area = "Marine Fortress",
        QuestNPC = "Marine Commander",
        QuestName = "Marine Training",
        EnemyNames = {"Marine Soldier"},
        FarmLocation = "Marine Barracks"
    }

    FarmingRoutes[6] = {
        MinLevel = 75,
        MaxLevel = 89,
        Area = "Middle Town",
        QuestNPC = "Town Guard",
        QuestName = "Clear Town Thugs",
        EnemyNames = {"Thug"},
        FarmLocation = "Town Alleyways"
    }
    
   
    FarmingRoutes[7] = {
        MinLevel = 90,
        MaxLevel = 99,
        Area = "Marine Headquarters",
        QuestNPC = "Vice Admiral",
        QuestName = "Captain Threat",
        EnemyNames = {"Marine Captain"},
        FarmLocation = "HQ Office"
    }
    

    FarmingRoutes[8] = {
        MinLevel = 100,
        MaxLevel = 119,
        Area = "Desert Island",
        QuestNPC = "Desert King",
        QuestName = "Desert Bandits",
        EnemyNames = {"Desert Bandit"},
        FarmLocation = "Desert Oasis"
    }
    
  
    FarmingRoutes[9] = {
        MinLevel = 120,
        MaxLevel = 149,
        Area = "Frozen Island",
        QuestNPC = "Frozen Villager",
        QuestName = "Snow Bandits",
        EnemyNames = {"Snow Bandit"},
        FarmLocation = "Frozen Village"
    }
    

    FarmingRoutes[10] = {
        MinLevel = 150,
        MaxLevel = 174,
        Area = "Sky Island",
        QuestNPC = "Sky Elder",
        QuestName = "Sky Bandits",
        EnemyNames = {"Sky Bandit"},
        FarmLocation = "Cloud Path"
    }
    
  
    FarmingRoutes[11] = {
        MinLevel = 175,
        MaxLevel = 189,
        Area = "Prison Island",
        QuestNPC = "Warden",
        QuestName = "Prison Riot",
        EnemyNames = {"Prison Guard"},
        FarmLocation = "Prison Yard"
    }
    
 
    FarmingRoutes[12] = {
        MinLevel = 190,
        MaxLevel = 209,
        Area = "Underwater Island",
        QuestNPC = "Fishman Leader",
        QuestName = "Fishman Troubles",
        EnemyNames = {"Fishman Warrior"},
        FarmLocation = "Coral Reef"
    }
 
    FarmingRoutes[13] = {
        MinLevel = 210,
        MaxLevel = 249,
        Area = "Magma Island",
        QuestNPC = "Volcano Keeper",
        QuestName = "Lava Monsters",
        EnemyNames = {"Lava Monster"},
        FarmLocation = "Volcano Crater"
    }
    
    -- Level 250-299: Ice Castle
    FarmingRoutes[14] = {
        MinLevel = 250,
        MaxLevel = 299,
        Area = "Ice Castle",
        QuestNPC = "Ice King",
        QuestName = "Snow Warriors",
        EnemyNames = {"Snow Warrior"},
        FarmLocation = "Ice Throne Room"
    }
 
    FarmingRoutes[15] = {
        MinLevel = 300,
        MaxLevel = 349,
        Area = "Forgotten Island",
        QuestNPC = "Island Historian",
        QuestName = "Ancient Warriors",
        EnemyNames = {"Ancient Warrior"},
        FarmLocation = "Ruins"
    }
    
  
    FarmingRoutes[16] = {
        MinLevel = 350,
        MaxLevel = 399,
        Area = "Skypiea",
        QuestNPC = "Sky God",
        QuestName = "Sky Warriors",
        EnemyNames = {"Sky Warrior"},
        FarmLocation = "God's Platform"
    }

    FarmingRoutes[17] = {
        MinLevel = 400,
        MaxLevel = 449,
        Area = "Thriller Bark",
        QuestNPC = "Ghost Princess",
        QuestName = "Zombie Horde",
        EnemyNames = {"Zombie"},
        FarmLocation = "Haunted Castle"
    }
    
  
    FarmingRoutes[18] = {
        MinLevel = 450,
        MaxLevel = 499,
        Area = "Colosseum",
        QuestNPC = "Arena Master",
        QuestName = "Gladiator Challenge",
        EnemyNames = {"Gladiator"},
        FarmLocation = "Arena Center"
    }
    
  
    FarmingRoutes[19] = {
        MinLevel = 500,
        MaxLevel = 549,
        Area = "Skylands",
        QuestNPC = "Cloud Emperor",
        QuestName = "Heavenly Warriors",
        EnemyNames = {"Heavenly Warrior"},
        FarmLocation = "Thunder Cloud"
    }
    
 
    FarmingRoutes[20] = {
        MinLevel = 550,
        MaxLevel = 624,
        Area = "Floating Turtle",
        QuestNPC = "Turtle Tribe Chief",
        QuestName = "Turtle Tribe Warriors",
        EnemyNames = {"Turtle Tribe Warrior"},
        FarmLocation = "Turtle Shell Village"
    }
    
   
    FarmingRoutes[21] = {
        MinLevel = 625,
        MaxLevel = 699,
        Area = "Mansion",
        QuestNPC = "Mansion Owner",
        QuestName = "Corrupt Butlers",
        EnemyNames = {"Butler"},
        FarmLocation = "Mansion Halls"
    }
    
   
    FarmingRoutes[22] = {
        MinLevel = 700,
        MaxLevel = 749,
        Area = "Giant Tree",
        QuestNPC = "Forest Guardian",
        QuestName = "Forest Tribe",
        EnemyNames = {"Forest Warrior"},
        FarmLocation = "Tree Canopy"
    }
    
  
    FarmingRoutes[23] = {
        MinLevel = 750,
        MaxLevel = 799,
        Area = "Hot and Cold Island",
        QuestNPC = "Island Sage",
        QuestName = "Element Warriors",
        EnemyNames = {"Fire Warrior", "Ice Warrior"},
        FarmLocation = "Dividing Line"
    }
    
   
    FarmingRoutes[24] = {
        MinLevel = 800,
        MaxLevel = 849,
        Area = "Cake Island",
        QuestNPC = "Sweet Queen",
        QuestName = "Sweet Commanders",
        EnemyNames = {"Sweet Commander"},
        FarmLocation = "Cake Castle"
    }
    
   
    FarmingRoutes[25] = {
        MinLevel = 850,
        MaxLevel = 899,
        Area = "Chocolate Island",
        QuestNPC = "Chocolate Master",
        QuestName = "Chocolate Bar Battlers",
        EnemyNames = {"Chocolate Warrior"},
        FarmLocation = "Cocoa Fields"
    }
    
end

local function GetCurrentFarmingRoute()
    for _, route in pairs(FarmingRoutes) do
        if AutoFarm.CurrentLevel >= route.MinLevel and AutoFarm.CurrentLevel <= route.MaxLevel then
            return route
        end
    end
    
    -- Retorna a última rota se o nível for maior que o máximo definido
    return FarmingRoutes[#FarmingRoutes]
end


local function Notify(message, duration)
    duration = duration or 3
    game:GetService("StarterGui"):SetCore("SendNotification", {
        Title = "Auto Farm",
        Text = message,
        Duration = duration
    })
    print("[AutoFarm] " .. message)
end

local function GetDistance(pos1, pos2)
    return (pos1 - pos2).Magnitude
end

local function GetPlayer()
    return game.Players.LocalPlayer
end

local function GetPlayerLevel()
    local player = GetPlayer()
    -- Tenta obter o nível do jogador - ajuste conforme a estrutura real do jogo
    local level = 1
    
   
    if player and player.Character then
        -- Verifica várias possibilidades de onde o nível pode estar armazenado
        if player.PlayerStats then
            level = player.PlayerStats.Level.Value
        elseif player.Data then
            level = player.Data.Level.Value
        elseif player.leaderstats then
            level = player.leaderstats.Level.Value
        end
    end
    
    AutoFarm.CurrentLevel = level
    return level
end

local function GetPlayerHealth()
    local player = GetPlayer()
    if player and player.Character and player.Character:FindFirstChild("Humanoid") then
        local humanoid = player.Character.Humanoid
        return (humanoid.Health / humanoid.MaxHealth) * 100
    end
    return 100
end

local function IsPlayerDead()
    local player = GetPlayer()
    return player and player.Character and player.Character:FindFirstChild("Humanoid") and player.Character.Humanoid.Health <= 0
end

local function GetNearestEnemy(enemyNames)
    local player = GetPlayer()
    if not player or not player.Character or not player.Character:FindFirstChild("HumanoidRootPart") then
        return nil
    end
    
    local playerPosition = player.Character.HumanoidRootPart.Position
    local nearestEnemy = nil
    local minDistance = math.huge
    
    for _, npc in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
        if npc:FindFirstChild("Humanoid") and npc.Humanoid.Health > 0 and npc:FindFirstChild("HumanoidRootPart") then
            -- Verifica se o NPC está na lista de inimigos da rota atual
            local isTargetEnemy = false
            for _, enemyName in ipairs(enemyNames) do
                if string.find(npc.Name, enemyName) then
                    isTargetEnemy = true
                    break
                end
            end
            
            if isTargetEnemy then
                local distance = GetDistance(playerPosition, npc.HumanoidRootPart.Position)
                if distance < minDistance then
                    minDistance = distance
                    nearestEnemy = npc
                end
            end
        end
    end
    
    return nearestEnemy
end

local function TeleportTo(position)
    local player = GetPlayer()
    if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
        player.Character.HumanoidRootPart.CFrame = CFrame.new(position)
    end
end

local function MoveTo(position)
    local player = GetPlayer()
    if player and player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid:MoveTo(position)
    end
end

local function AttackEnemy(enemy)
    if not enemy or not enemy:FindFirstChild("HumanoidRootPart") then return end
    
    local player = GetPlayer()
    if not player or not player.Character or not player.Character:FindFirstChild("HumanoidRootPart") then return end
    
   
    TeleportTo(enemy.HumanoidRootPart.Position + Vector3.new(0, 5, 0))
    
    
    if Keys.FastAttack then
        for i = 1, 3 do
            mouse1click()
            wait(0.1)
        end
    else
        mouse1click()
    end
    
   
    if AutoFarm.UseFruitSkills then
        keypress(0x5A)  -- Z
        wait(0.1)
        keypress(0x58)  -- X
        wait(0.1)
        keypress(0x43)  -- C
        wait(0.1)
        keypress(0x56)  -- V
        wait(0.1)
    end
    
    if AutoFarm.UseSword then
        -- Equipar e usar espada
        keypress(0x31)  -- 1 (para primeira arma)
        wait(0.1)
        mouse1click()
    end
    
    if AutoFarm.UseHaki then
        keypress(0x48)  -- H (para Haki)
    end
end

local function UseSkill(key)
    keypress(key)
    wait(0.1)
end

local function AcceptQuest(npcName, questName)
    local currentRoute = GetCurrentFarmingRoute()
    Notify("Tentando aceitar a missão: " .. questName)
    
  
    local npcFound = false
    for _, npc in pairs(game:GetService("Workspace").NPCs:GetChildren()) do
        if npc.Name == npcName then
            npcFound = true
            
        
            if npc:FindFirstChild("HumanoidRootPart") then
                TeleportTo(npc.HumanoidRootPart.Position + Vector3.new(0, 3, 0))
                wait(1)
                
                
                keypress(0x45)  -- E
                wait(1)
                
              
                mouse1click()
                wait(0.5)
                
                Notify("Missão aceita: " .. questName)
                return true
            end
            break
        end
    end
    
    if not npcFound then
        Notify("NPC não encontrado: " .. npcName)
        return false
    end
    
    return false
end

local function IsQuestCompleted()
    
    local questGUI = game:GetService("Players").LocalPlayer.PlayerGui:FindFirstChild("QuestGUI")
    if questGUI and questGUI:FindFirstChild("Completed") and questGUI.Completed.Visible then
        return true
    end
    
    return AutoFarm.LastQuestCompleted
end

local function CompleteQuest(npcName)
    local currentRoute = GetCurrentFarmingRoute()
    Notify("Tentando completar a missão com: " .. npcName)
    
    for _, npc in pairs(game:GetService("Workspace").NPCs:GetChildren()) do
        if npc.Name == npcName then
            -- Teleportar para o NPC
            if npc:FindFirstChild("HumanoidRootPart") then
                TeleportTo(npc.HumanoidRootPart.Position + Vector3.new(0, 3, 0))
                wait(1)
                
                keypress(0x45)  -- E
                wait(1)

                mouse1click()
                wait(0.5)
                
                AutoFarm.LastQuestCompleted = false
                Notify("Missão completada e recompensa recebida!")
                return true
            end
            break
        end
    end
    
    Notify("Não foi possível completar a missão")
    return false
end

local function RetreatIfLowHealth()
    local health = GetPlayerHealth()
    
    if health < AutoFarm.CriticalHealth then
        Notify("SAÚDE CRÍTICA! Recuando e curando...")

        keypress(0x31)  -- 1 (normalmente item de cura)
        
        local player = GetPlayer()
        if player and player.Character and player.Character:FindFirstChild("HumanoidRootPart") then
            local currentPos = player.Character.HumanoidRootPart.Position
            local retreatPos = currentPos + player.Character.HumanoidRootPart.CFrame.lookVector * -50
            TeleportTo(retreatPos)
        end
        
        return true
    elseif health < AutoFarm.SafeHealth then
        Notify("Saúde baixa! Usando cura...")
        

        keypress(0x31)  -- 1 (normalmente item de cura)
        
        wait(1)
        return true
    end
    
    return false
end


local function FarmingLoop()
    while AutoFarm.Enabled do
        if AutoFarm.Paused then
            wait(1)
            goto continue
        end

        if IsPlayerDead() then
            Notify("Você morreu! Aguardando renascimento...")
            wait(5)
            goto continue
        end

        GetPlayerLevel()

        if AutoFarm.CurrentLevel >= AutoFarm.TargetLevel then
            Notify("PARABÉNS! Você atingiu o nível alvo: " .. AutoFarm.TargetLevel)
            AutoFarm.Enabled = false
            break
        end
        
        local currentRoute = GetCurrentFarmingRoute()
        
        -- Verifica e aceita a missão se necessário
        if AutoFarm.AutoQuest then
            if IsQuestCompleted() then
                CompleteQuest(currentRoute.QuestNPC)
                wait(1)
                AcceptQuest(currentRoute.QuestNPC, currentRoute.QuestName)
            elseif not game:GetService("Players").LocalPlayer.PlayerGui:FindFirstChild("QuestGUI") then
                AcceptQuest(currentRoute.QuestNPC, currentRoute.QuestName)
            end
        end

        if RetreatIfLowHealth() then
            wait(1)
            goto continue
        end

        local nearestEnemy = GetNearestEnemy(currentRoute.EnemyNames)

        if nearestEnemy then
            AttackEnemy(nearestEnemy)

            if nearestEnemy:FindFirstChild("Humanoid") and nearestEnemy.Humanoid.Health <= 0 then
                AutoFarm.LastQuestCompleted = true
                Notify("Inimigo derrotado!")
            end
        else

            Notify("Procurando inimigos em: " .. currentRoute.FarmLocation)
 
            for i = 1, 4 do
                game:GetService("Players").LocalPlayer.Character.Humanoid.CameraOffset = Vector3.new(0, 0, 5)
                wait(0.5)
                game:GetService("Players").LocalPlayer.Character.Humanoid.CameraOffset = Vector3.new(5, 0, 0)
                wait(0.5)
                game:GetService("Players").LocalPlayer.Character.Humanoid.CameraOffset = Vector3.new(0, 0, -5)
                wait(0.5)
                game:GetService("Players").LocalPlayer.Character.Humanoid.CameraOffset = Vector3.new(-5, 0, 0)
                wait(0.5)
            end
        end
        
        wait(0.1)
        ::continue::
    end
end

local function CreateGUI()
    local ScreenGui = Instance.new("ScreenGui")
    ScreenGui.Name = "BloxFruitsAutoFarm"
    ScreenGui.Parent = game:GetService("CoreGui")
    
    local MainFrame = Instance.new("Frame")
    MainFrame.Name = "MainFrame"
    MainFrame.Size = UDim2.new(0, 300, 0, 350)
    MainFrame.Position = UDim2.new(0.5, -150, 0.5, -175)
    MainFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 70)
    MainFrame.BorderSizePixel = 2
    MainFrame.BorderColor3 = Color3.fromRGB(100, 100, 150)
    MainFrame.Active = true
    MainFrame.Draggable = true
    MainFrame.Parent = ScreenGui
    
    local Title = Instance.new("TextLabel")
    Title.Name = "Title"
    Title.Size = UDim2.new(1, 0, 0, 30)
    Title.BackgroundColor3 = Color3.fromRGB(40, 40, 60)
    Title.BorderSizePixel = 0
    Title.Text = "Blox Fruits Auto Farm"
    Title.TextColor3 = Color3.fromRGB(255, 255, 255)
    Title.TextSize = 18
    Title.Font = Enum.Font.SourceSansBold
    Title.Parent = MainFrame
    
    local CloseButton = Instance.new("TextButton")
    CloseButton.Name = "CloseButton"
    CloseButton.Size = UDim2.new(0, 25, 0, 25)
    CloseButton.Position = UDim2.new(1, -30, 0, 3)
    CloseButton.BackgroundColor3 = Color3.fromRGB(200, 60, 60)
    CloseButton.Text = "X"
    CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    CloseButton.Font = Enum.Font.SourceSansBold
    CloseButton.TextSize = 16
    CloseButton.Parent = Title

    CloseButton.MouseButton1Click:Connect(function()
        ScreenGui:Destroy()
    end)
    
    local StatusLabel = Instance.new("TextLabel")
    StatusLabel.Name = "StatusLabel"
    StatusLabel.Size = UDim2.new(1, 0, 0, 20)
    StatusLabel.Position = UDim2.new(0, 0, 0, 40)
    StatusLabel.BackgroundTransparency = 1
    StatusLabel.Text = "Status: Desativado"
    StatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    StatusLabel.TextSize = 14
    StatusLabel.Font = Enum.Font.SourceSans
    StatusLabel.Parent = MainFrame
    
    local LevelLabel = Instance.new("TextLabel")
    LevelLabel.Name = "LevelLabel"
    LevelLabel.Size = UDim2.new(1, 0, 0, 20)
    LevelLabel.Position = UDim2.new(0, 0, 0, 65)
    LevelLabel.BackgroundTransparency = 1
    LevelLabel.Text = "Nível Atual: 1"
    LevelLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    LevelLabel.TextSize = 14
    LevelLabel.Font = Enum.Font.SourceSans
    LevelLabel.Parent = MainFrame
    
    local TargetLevelFrame = Instance.new("Frame")
    TargetLevelFrame.Name = "TargetLevelFrame"
    TargetLevelFrame.Size = UDim2.new(1, -20, 0, 30)
    TargetLevelFrame.Position = UDim2.new(0, 10, 0, 90)
    TargetLevelFrame.BackgroundTransparency = 1
    TargetLevelFrame.Parent = MainFrame
    
    local TargetLevelLabel = Instance.new("TextLabel")
    TargetLevelLabel.Name = "TargetLevelLabel"
    TargetLevelLabel.Size = UDim2.new(0.5, 0, 1, 0)
    TargetLevelLabel.BackgroundTransparency = 1
    TargetLevelLabel.Text = "Nível Alvo:"
    TargetLevelLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    TargetLevelLabel.TextSize = 14
    TargetLevelLabel.Font = Enum.Font.SourceSans
    TargetLevelLabel.Parent = TargetLevelFrame
    
    local TargetLevelInput = Instance.new("TextBox")
    TargetLevelInput.Name = "TargetLevelInput"
    TargetLevelInput.Size = UDim2.new(0.5, -10, 1, -10)
    TargetLevelInput.Position = UDim2.new(0.5, 0, 0, 5)
    TargetLevelInput.BackgroundColor3 = Color3.fromRGB(30, 30, 40)
    TargetLevelInput.BorderColor3 = Color3.fromRGB(100, 100, 150)
    TargetLevelInput.Text = "2650"
    TargetLevelInput.TextColor3 = Color3.fromRGB(255, 255, 255)
    TargetLevelInput.TextSize = 14
    TargetLevelInput.Font = Enum.Font.SourceSans
    TargetLevelInput.Parent = TargetLevelFrame
    
    local ToggleFrame = Instance.new("Frame")
    ToggleFrame.Name = "ToggleFrame"
    ToggleFrame.Size = UDim2.new(1, -20, 0, 150)
    ToggleFrame.Position = UDim2.new(0, 10, 0, 130)
    ToggleFrame.BackgroundTransparency = 1
    ToggleFrame.Parent = MainFrame

    local function CreateToggle(name, text, y, default)
        local ToggleButton = Instance.new("Frame")
        ToggleButton.Name = name .. "Toggle"
        ToggleButton.Size = UDim2.new(1, 0, 0, 25)
        ToggleButton.Position = UDim2.new(0, 0, 0, y)
        ToggleButton.BackgroundTransparency = 1
        ToggleButton.Parent = ToggleFrame
        
        local ToggleLabel = Instance.new("TextLabel")
        ToggleLabel.Name = "Label"
        ToggleLabel.Size = UDim2.new(0.7, 0, 1, 0)
        ToggleLabel.BackgroundTransparency = 1
        ToggleLabel.Text = text
        ToggleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
        ToggleLabel.TextSize = 14
        ToggleLabel.Font = Enum.Font.SourceSans
        ToggleLabel.TextXAlignment = Enum.TextXAlignment.Left
        ToggleLabel.Parent = ToggleButton
        
        local ToggleSwitch = Instance.new("Frame")
        ToggleSwitch.Name = "Switch"
        ToggleSwitch.Size = UDim2.new(0, 40, 0, 20)
        ToggleSwitch.Position = UDim2.new(1, -50, 0.5, -10)
        ToggleSwitch.BackgroundColor3 = default and Color3.fromRGB(0, 200, 0) or Color3.fromRGB(200, 0, 0)
        ToggleSwitch.BorderColor3 = Color3.fromRGB(100, 100, 150)
        ToggleSwitch.Parent = ToggleButton
        
        local SwitchButton = Instance.new("TextButton")
        SwitchButton.Name = "Button"
        SwitchButton.Size = UDim2.new(0, 20, 1, 0)
        SwitchButton.Position = UDim2.new(default and 0.5 or 0, 0, 0, 0)
        SwitchButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        SwitchButton.Text = ""
        SwitchButton.Parent = ToggleSwitch

        AutoFarm[koda] = default
        
        SwitchButton.MouseButton1Click:Connect(function()
            AutoFarm[name] = not AutoFarm[name]
            ToggleSwitch.BackgroundColor3 = AutoFarm[name] and Color3.fromRGB(0, 200, 0) or Color3.fromRGB(200, 0, 0)
            SwitchButton.Position = UDim2.new(AutoFarm[name] and 0.5 or 0, 0, 0, 0)
            
            if name == "Enabled" then
                StatusLabel.Text = "Status: " .. (AutoFarm.Enabled and "Ativado" or "Desativado")
                
                if AutoFarm.Enabled then
                    -- Inicia o loop de farming em uma nova thread
                    spawn(FarmingLoop)
                end
            end
        end)
        
        return ToggleButton
    end
    
    local toggles = {
        {farmm = "Enabled", text = "Ativar Auto Farm", default = false},
        {name = "AutoQuest", text = "Auto Missões", default = true},
        {name = "UseFruitSkills", text = "Usar Habilidades de Fruta", default = true},
        {name = "UseSword", text = "Usar Espada", default = true},
        {name = "UseHaki", text = "Usar Haki", default = true}
    }
    
    for i, toggle in ipairs(toggles) do
        CreateToggle(toggle.name, toggle.text, (i-1) * 30, toggle.default)
    end

    local HelpButton = Instance.new("TextButton")
    HelpButton.Name = "HelpButton"
    HelpButton.Size = UDim2.new(0, 100, 0, 25)
    HelpButton.Position = UDim2.new(0.5, -50, 1, -35)
    HelpButton.BackgroundColor3 = Color3.fromRGB(70, 70, 100)
    HelpButton.BorderColor3 = Color3.fromRGB(100, 100, 150)
    HelpButton.Text = "Ajuda"
    HelpButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    HelpButton.TextSize = 14
    HelpButton.Font = Enum.Font.SourceSans
    HelpButton.Parent = MainFrame

    HelpButton.MouseButton1Click:Connect(function()
        Notify("Script de Auto Farm para Blox Fruits v1.0", 5)
        Notify("Automatiza o farming de nível 1 a 2650", 5)
        Notify("Criado para fins educacionais apenas", 5)
    end)

    spawn(function()
        while true do
            local level = GetPlayerLevel()
            LevelLabel.Text = "Nível Atual: " .. level
            wait(5)
        end
    end)
    
    TargetLevelInput.FocusLost:Connect(function(enterPressed)
        if enterPressed then
            local targetLevel = tonumber(TargetLevelInput.Text)
            if targetLevel and targetLevel > 0 then
                AutoFarm.TargetLevel = targetLevel
                Notify("Nível alvo atualizado para: " .. targetLevel)
            else
                TargetLevelInput.Text = tostring(AutoFarm.TargetLevel)
                Notify("Nível alvo inválido. Use um número positivo.")
            end
        end
    end)
end

local function Initialize()
    Notify("Inicializando Blox Fruits Auto Farm v1.0", 5)

    SetupFarmingRoutes()
  
    CreateGUI()

    GetPlayerLevel()
    
    Notify("Auto Farm inicializado! Use a GUI para controlar.", 5)
end

Initialize()
