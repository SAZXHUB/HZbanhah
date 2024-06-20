if game.PlaceId == 2753915549 then
	World1 = true
elseif game.PlaceId == 4442272183 then
	World2 = true
elseif game.PlaceId == 7449423635 then
	World3 = true
end

local DINOHUB = Instance.new("ScreenGui")
local OPENCLOSE = Instance.new("TextButton")

DINOHUB.Name = "close"
DINOHUB.Parent = game.CoreGui
DINOHUB.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

OPENCLOSE.Name = "OPENCLOSE"
OPENCLOSE.Parent = DINOHUB
OPENCLOSE.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
OPENCLOSE.BorderSizePixel = 3
OPENCLOSE.Position = UDim2.new(0.120833337, 0, 0.0952890813, 0)
OPENCLOSE.Size = UDim2.new(0.0447916649, 0, 0.0845824406, 0)
OPENCLOSE.Font = Enum.Font.DenkOne
OPENCLOSE.Text = "close"
OPENCLOSE.TextColor3 = Color3.fromRGB(255, 50, 100)
OPENCLOSE.TextScaled = true
OPENCLOSE.TextSize = 14.000
OPENCLOSE.TextWrapped = true
OPENCLOSE.MouseButton1Click:Connect(function()
    game.CoreGui:FindFirstChild("Discord").Enabled = not game.CoreGui:FindFirstChild("Discord").Enabled
end)

getgenv().ToTarget = function(Pos)
    Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
        if game.Players.LocalPlayer.Character.Humanoid.Sit == true then game.Players.LocalPlayer.Character.Humanoid.Sit = false end
        pcall(function() tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/3599999, Enum.EasingStyle.Linear),{CFrame = Pos}) end)
        tween:Play()
        if Distance <= 99999 then
            tween:Cancel()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Pos
        end
        if _G.StopTween == true then
            tween:Cancel()
            _G.Clip = false
        end
end

function topos(Pos)
	Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	if game.Players.LocalPlayer.Character.Humanoid.Sit == true then game.Players.LocalPlayer.Character.Humanoid.Sit = false end
	pcall(function() tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/210, Enum.EasingStyle.Linear),{CFrame = Pos}) end)
	tween:Play()
	if Distance <= 250 then
		tween:Cancel()
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Pos
	end
	if _G.StopTween == true then
		tween:Cancel()
		_G.Clip = false
	end
end

	function topos(Pos)
			if not _G.StopTween then
				local Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
				Speed = 100
				if Distance < 250 then
					Speed = 5000
				elseif Distance < 500 then
					Speed = 650
				elseif Distance < 1000 then
					Speed = 350
				elseif Distance >= 1000 then
					Speed = 250
				end
				Tween = game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart,TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),{CFrame = P1})
				if _G.StopTween or Auto_Raid then
					Tween:Cancel()
				elseif game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
					Tween:Play()
				end
			end
		end
		
function topos(Pos)
	local Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	if Distance < 250 then
		Speed = 10000
	elseif Distance < 500 then
		Speed = 500
	elseif Distance < 1000 then
		Speed = 250
	elseif Distance >= 1000 then
		Speed = 250
	end
	game:GetService("TweenService"):Create(
		game.Players.LocalPlayer.Character.HumanoidRootPart,
		TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
		{CFrame = Pos}
	):Play()
	if _G.StopTween then
		game:GetService("TweenService"):Create(
		game.Players.LocalPlayer.Character.HumanoidRootPart,
		TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
			{CFrame = Pos}
		):Cancel()
	end
end

function topos(Pos)
	local Distance = (Pos.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	if Distance < 150 then
		Speed = 5000
	elseif Distance < 200 then
		Speed = 1500
	elseif Distance < 300 then
		Speed = 800
	elseif Distance < 500 then
		Speed = 500
	elseif Distance < 1000 then
		Speed = 250
	elseif Distance >= 1000 then
		Speed = 250
	end
	game:GetService("TweenService"):Create(
		game.Players.LocalPlayer.Character.HumanoidRootPart,
		TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
		{CFrame = Pos}
	):Play()
	if _G.StopTween then
		game:GetService("TweenService"):Create(
		game.Players.LocalPlayer.Character.HumanoidRootPart,
		TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
			{CFrame = Pos}
		):Cancel()
	end
	_G.Clip = true
	wait(Distance/Speed)
	_G.Clip = false
end

function StopTween(target)
	if not target then
		_G.StopTween = true
		wait()
		topos(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
		wait()
		if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
			game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
		end
		_G.StopTween = false
		_G.Clip = false
	end
end


function GetDistance(target)
	return math.floor((target.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude)
end

function UseCode(Text)
	game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(Text)
end

function hop()
	local PlaceID = game.PlaceId
	local AllIDs = {}
	local foundAnything = ""
	local actualHour = os.date("!*t").hour
	local Deleted = false
	function TPReturner()
		local Site;
		if foundAnything == "" then
			Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
		else
			Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
		end
		local ID = ""
		if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
			foundAnything = Site.nextPageCursor
		end
		local num = 0;
		for i,v in pairs(Site.data) do
			local Possible = true
			ID = tostring(v.id)
			if tonumber(v.maxPlayers) > tonumber(v.playing) then
				for _,Existing in pairs(AllIDs) do
					if num ~= 0 then
						if ID == tostring(Existing) then
							Possible = false
						end
					else
						if tonumber(actualHour) ~= tonumber(Existing) then
							local delFile = pcall(function()
								-- delfile("NotSameServers.json")
								AllIDs = {}
								table.insert(AllIDs, actualHour)
							end)
						end
					end
					num = num + 1
				end
				if Possible == true then
					table.insert(AllIDs, ID)
					wait()
					pcall(function()
						-- writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(AllIDs))
						wait()
						game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
					end)
					wait(4)
				end
			end
		end
	end
	function Teleport()
		while wait() do
			pcall(function()
				TPReturner()
				if foundAnything ~= "" then
					TPReturner()
				end
			end)
		end
	end
	Teleport()
end

spawn(function()
	pcall(function()
		game:GetService("RunService").Stepped:Connect(function()
			if _G.Auto_Farm_Level or _G.Auto_New_World or _G.TeleportIsland or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.Auto_Farm_Boss or _G.GunMastery or _G.Mastery or _G.AutoFarmFruitMastery or _G.AutoFarmGunMastery or _G.Auto_Elite_Hunter or _G.AutoFarmKenHaki or _G.AutoFactory or _G.AutoFarmSelectMonster or _G.Auto_Cake_Prince or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.d or _G.Auto_Rengoku or _G.Autotushita or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Mirage or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.AutoFarmMaterial or _G.autoraid or _G.Auto_Twin_Hook or AutoNextIsland or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.AutoObservationHakiV2 or _G.d or _G.Auto_Next_Island or _G.Auto_Farm_Sword or _G.MeleeFarm or _G.Auto_Kill_Law or _G.Auto_Raid then
				for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
					if v:IsA("BasePart") then
						v.CanCollide = false    
					end
				end
			end
		end)
	end)
end)
    
local DiscordLib = loadstring(game:HttpGet"https://raw.githubusercontent.com/kickTh/New-Ui/main/discord%20lib%20(1).txt")()

local win = DiscordLib:Window("discord library")

local serv = win:Server("BY Cat dev", "")

local btns = serv:Channel("ของแมพ Blox fruit")

local Teleport = serv:Channel("วาป")

local btna = serv:Channel("troll script all map")

btns:Button(" infinite yield ", function()
loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
end)

local lp = game:GetService('Players').LocalPlayer
local mouse = lp:GetMouse()

spawn(function()
    while wait() do
        if _G.Aimbot_Skill then
            pcall(function()
                local MaxDist, Closest = math.huge
                for i, v in pairs(game:GetService("Players"):GetChildren()) do
                    local Head = v.Character:FindFirstChild("HumanoidRootPart")
                    local Dist = (Head.Position - lp.Character.HumanoidRootPart.Position).Magnitude
                    if Dist < MaxDist and v.Name ~= lp.Name then
                        MaxDist = Dist
                        _G.Aim_Players = v
                    end
                end
            end)
        end
    end
end)

checkspeed = .0*.0*.0
btns:Toggle("Aim Bot Skill และ Gun (ของดี)",false, function(value)
		_G.Aimbot_Skill = value
		_G.Aimbot_Gun = value
	end)
	
	spawn(function()
        local gg = getrawmetatable(game)
        local old = gg.__namecall
        setreadonly(gg,false)
        gg.__namecall = newcclosure(function(...)
            local method = getnamecallmethod()
            local args = {...}
            if tostring(method) == "FireServer" then
                if tostring(args[1]) == "RemoteEvent" then
                    if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
                        if _G.Aimbot_Skill then
                            args[2] = _G.Aim_Players.Character.HumanoidRootPart.Position
                            return old(unpack(args))
                        end
                    end
                end
            end
            return old(...)
        end)
    end)
spawn(function()
	while wait() do
		if _G.Aimbot_Skill then
			if game.Players:FindFirstChild(SelectPlayer) and game.Players:FindFirstChild(SelectPlayer).Character:FindFirstChild("HumanoidRootPart") and game.Players:FindFirstChild(SelectPlayer).Character:FindFirstChild("Humanoid") and game.Players:FindFirstChild(SelectPlayer).Character.Humanoid.Health > 0 then
				AimBotSkillPosition = game.Players:FindFirstChild(SelectPlayer).Character:FindFirstChild("HumanoidRootPart").Position
			end
		end
	end
end)

spawn(function()
	while wait() do
		for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
			if v:IsA("Tool") then
				if v:FindFirstChild("RemoteFunctionShoot") then 
					SelectToolWeaponGun = v.Name
				end
			end
		end
		for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do  
			if v:IsA("Tool") then
				if v:FindFirstChild("RemoteFunctionShoot") then 
					SelectToolWeaponGun = v.Name
				end
			end
		end
	end
end)

local lp = game:GetService('Players').LocalPlayer
local mouse = lp:GetMouse()
mouse.Button1Down:Connect(function()
	if _G.Aimbot_Gun and game.Players.LocalPlayer.Character:FindFirstChild(SelectToolWeaponGun) and game:GetService("Players"):FindFirstChild(SelectPlayer) then
		tool = game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun]
		v17 = workspace:FindPartOnRayWithIgnoreList(Ray.new(tool.Handle.CFrame.p, (game:GetService("Players"):FindFirstChild(SelectPlayer).Character.HumanoidRootPart.Position - tool.Handle.CFrame.p).unit * 100), { game.Players.LocalPlayer.Character, workspace._WorldOrigin });
		game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun].RemoteFunctionShoot:InvokeServer(game:GetService("Players"):FindFirstChild(SelectPlayer).Character.HumanoidRootPart.Position, (require(game.ReplicatedStorage.Util).Other.hrpFromPart(v17)));
	end 
end) 

btns:Toggle("บินขึ้นฟ้า เพื่อ หนี",false, function(vu)
tw = vu
getgenv().ToTarget = function(p)
	spawn(function()
		pcall(function()
			if game:GetService("Players").LocalPlayer:DistanceFromCharacter(p.Position) <= 250 then 
				game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = p
			elseif not game.Players.LocalPlayer.Character:FindFirstChild("Root")then 
				local K = Instance.new("Part",game.Players.LocalPlayer.Character)
				K.Size = Vector3.new(1,0.5,1)
				K.Name = "Root"
				K.Anchored = true
				K.Transparency = 1
				K.CanCollide = false
				K.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0,20,0)
			end
			local U = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude
			local z = game:service("TweenService")
			local B = TweenInfo.new((p.Position-game.Players.LocalPlayer.Character.Root.Position).Magnitude/300,Enum.EasingStyle.Linear)
			local S,g = pcall(function()
				local q = z:Create(game.Players.LocalPlayer.Character.Root,B,{CFrame = p})
				q:Play()
			end)
			if not S then 
				return g
			end
			game.Players.LocalPlayer.Character.Root.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
			if S and game.Players.LocalPlayer.Character:FindFirstChild("Root") then 
				pcall(function()
					if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude >= 20 then 
						spawn(function()
							pcall(function()
								if (game.Players.LocalPlayer.Character.Root.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 150 then 
									game.Players.LocalPlayer.Character.Root.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame
								else 
									game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame=game.Players.LocalPlayer.Character.Root.CFrame
								end
							end)
						end)
					elseif (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude >= 10 and(game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude < 20 then 
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = p
					elseif (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-p.Position).Magnitude < 10 then 
						game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = p
					end
				end)
			end
		end)
	end)
end

while tw do
local targetPosition = Vector3.new(-117, 83808, 238)
getgenv().ToTarget(CFrame.new(targetPosition))
wait(.0)
end
end)

btns:Button("เพิ่มขนาดhitbox", function()
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local RunService = game:GetService("RunService")
local StarterGui = game:GetService("StarterGui")

local function extendHitboxes(deltaTime)
    local Character = LocalPlayer.Character
    if not Character then
        return
    end

    local HumanoidRootPart = Character:FindFirstChild("HumanoidRootPart")
    if not HumanoidRootPart then
        return
    end

    for _, Player in pairs(Players:GetPlayers()) do
        if Player == LocalPlayer then
            continue
        end

        local PlayerCharacter = Player.Character

        if not PlayerCharacter then
            continue
        end

        local PlayerHumanoidRootPart = PlayerCharacter:FindFirstChild("HumanoidRootPart")

        if not PlayerHumanoidRootPart then
            continue
        end

        local areTouching = false

        for _, Part in pairs(workspace:GetPartsInPart(PlayerHumanoidRootPart)) do
            if Part:IsDescendantOf(Character) then
                areTouching = true
                break
            end
        end

        if Player.Team == LocalPlayer.Team or areTouching then
            PlayerHumanoidRootPart.Size = Vector3.new(45, 45, 45)
            PlayerHumanoidRootPart.Transparency = 0.95
            PlayerHumanoidRootPart.BrickColor = Player.Team.TeamColor
            PlayerHumanoidRootPart.Shape = Enum.PartType.Ball
            PlayerHumanoidRootPart.CanCollide = false
            continue
        end

        PlayerHumanoidRootPart.Size = Vector3.new(45, 45, 45)
        PlayerHumanoidRootPart.Transparency = 0.7
        PlayerHumanoidRootPart.BrickColor = Player.Team.TeamColor
        PlayerHumanoidRootPart.Shape = Enum.PartType.Ball
        PlayerHumanoidRootPart.CanCollide = true
    end
end

RunService.Stepped:Connect(extendHitboxes)

StarterGui:SetCore("SendNotification", {
    Title = "Loaded",
    Text = "Yes, you did execute it",
    Icon = "rbxassetid://10248739826"
})
end)

btns:Button("ย้ายเชิฟ", function()
local module = loadstring(game:HttpGet"https://raw.githubusercontent.com/LeoKholYt/roblox/main/lk_serverhop.lua")()

module:Teleport(game.PlaceId)
end)
	
btns:Button("ดึงเรือที่ไกล้ที่สุดทุกชนิด", function()
local player = game.Players.LocalPlayer
local boatsFolder = game:GetService("Workspace").Boats

local function findNearestBoat()
    local playerPos = player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.HumanoidRootPart.Position
    if not playerPos then return end

    local nearestBoat, nearestDist
    for _, boat in pairs(boatsFolder:GetChildren()) do
        if boat:IsA("Model") and boat:FindFirstChild("VehicleSeat") then
            local dist = (playerPos - boat.VehicleSeat.Position).Magnitude
            if not nearestDist or dist < nearestDist then
                nearestBoat, nearestDist = boat, dist
            end
        end
    end

    return nearestBoat
end

local nearestBoat = findNearestBoat()
if nearestBoat then
    nearestBoat:SetPrimaryPartCFrame(player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.HumanoidRootPart.CFrame)
end
end)

btns:Toggle("fast attack konen",false, function(t)
_G.FastAttack = t

local Char = game.Players.LocalPlayer.Character
local Root = Char.HumanoidRootPart
local Players = game.Players
local LocalPlayer = Players.LocalPlayer

local CollectionService = game:GetService("CollectionService")
repeat 
    LocalPlayer = Players.LocalPlayer
    wait()
until LocalPlayer
local kkii = require(game.ReplicatedStorage.Util.CameraShaker)
kkii:Stop()
local ItsTrue = true or false
local CurrentAllMob,
      recentlySpawn,
      StoredSuccessFully,
      canHits, RecentCollected,
      FruitInServer,
      RecentlyLocationSet,
      lastequip = {}, 0, 0, {}, 0, {}, 0, tick()
local PC,
      RL,
      DMG, 
      RigC,
      Combat = require(LocalPlayer.PlayerScripts.CombatFramework.Particle), require(game:GetService("ReplicatedStorage").CombatFramework.RigLib), require(LocalPlayer.PlayerScripts.CombatFramework.Particle.Damage), getupvalue(require(LocalPlayer.PlayerScripts.CombatFramework.RigController),2), getupvalue(require(LocalPlayer.PlayerScripts.CombatFramework),2)

local UserInputService, RunService, vim, CollectionService, CoreGui = game:GetService("UserInputService")
    ,game:GetService("RunService")
    ,game:GetService('VirtualInputManager')
    ,game:GetService("CollectionService")
    ,game:GetService("CoreGui")
local dist = function(a,b,noHeight)
    if not b then
        b = Root.Position
    end
    return (Vector3.new(a.X,not noHeight and a.Y,a.Z) - Vector3.new(b.X,not noHeight and b.Y,b.Z)).magnitude
end
do -- Starter Thread
    task.spawn(function()
        local stacking = .0
        local printCooldown = .0
        while _G.FastAttack do
             task.wait(.0)
            pcall(function()
                local nearbymon = false
                table.clear(CurrentAllMob)
                table.clear(canHits)
                local mobs = CollectionService:GetTagged("ActiveRig")
                for i=1,#mobs do local v = mobs[i]
                    local Human = v:FindFirstChildOfClass("Humanoid")
                    if Human and Human.Health > 0 and Human.RootPart and v ~= Char then
                        local IsPlayer = game.Players:GetPlayerFromCharacter(v)
                        local IsAlly = IsPlayer and CollectionService:HasTag(IsPlayer,"Ally"..LocalPlayer.Name)
                        if not IsAlly then
                            CurrentAllMob[#CurrentAllMob + 1] = v
                            if not nearbymon and dist(Human.RootPart.Position) < 65 then
                                nearbymon = true
                            end
                        end
                    end
                end
                if nearbymon then
                    local Enemies = workspace.Enemies:GetChildren()
                    local Players = Players:GetPlayers()
                    for i=1,#Enemies do local v = Enemies[i]
                        local Human = v:FindFirstChildOfClass("Humanoid")
                        if Human and Human.RootPart and Human.Health > 0 and dist(Human.RootPart.Position) < 65 then
                            canHits[#canHits+1] = Human.RootPart
                        end
                    end
                    for i=1,#Players do local v = Players[i].Character
                        if not Players[i]:GetAttribute("PvpDisabled") and v and v ~= LocalPlayer.Character then
                            local Human = v:FindFirstChildOfClass("Humanoid")
                            if Human and Human.RootPart and Human.Health > 0 and dist(Human.RootPart.Position) < 65 then
                                canHits[#canHits+1] = Human.RootPart
                            end
                        end
                    end
                end
            end)
        end
    end)
end
-- Initialize Fast Attack .
task.spawn(function()
    local Data = Combat
    local Blank = function() end
    local RigEvent = game:GetService("ReplicatedStorage").RigControllerEvent
    local Animation = Instance.new("Animation")
    local RecentlyFired = 0
    local AttackCD = 0
    local Controller
    local lastFireValid = 0
    local MaxLag = 350
    fucker = 0.0
    TryLag = 0
    local resetCD = function()
        local WeaponName = Controller.currentWeaponModel.Name
        local Cooldown = {
            combat = 0.0
        }
        AttackCD = tick() + (fucker and Cooldown[WeaponName:lower()] or fucker or 0.285) + ((TryLag/MaxLag)*0.3)
        RigEvent.FireServer(RigEvent,"weaponChange",WeaponName)
        TryLag += 1
        task.delay((fucker or .0) + (TryLag+0.5/MaxLag)*0.3,function()
            TryLag -= 1
        end)
    end
    if not shared.orl then shared.orl = RL.wrapAttackAnimationAsync end
    if not shared.cpc then shared.cpc = PC.play end
    if not shared.dnew then shared.dnew = DMG.new end
    if not shared.attack then shared.attack = RigC.attack end
    RL.wrapAttackAnimationAsync = function(a,b,c,d,func)
        if _G.FastAttack then
            PC.play = shared.cpc
            return shared.orl(a,b,c,65,func)
        end
        local Radius = _G.FastAttack or 65
        if _G.FastAttack and canHits and #canHits > 0 then
            PC.play = function() end
            a:Play(0.00075,0.01,0.01)
            func(canHits)
            wait(a.length * .0)
          --  a:Stop()
        end
    end
    
    while _G.FastAttack do
    task.wait(.0)
        pcall(function()
            if #canHits > 0 then
                Controller = Data.activeController
                if NormalClick then
                    pcall(spawn,Controller.attack,Controller)
                end
                if Controller and Controller.equipped and (not Char.Busy.Value or not LocalPlayer.PlayerGui.Main.Dialogue.Visible) and Char.Stun.Value == 0 and Controller.currentWeaponModel then
                    if _G.FastAttack then
                        if _G.FastAttack and tick() > AttackCD then
                            resetCD()
                        end 
                        if tick() - lastFireValid > .0 then
                            Controller.timeToNextAttack = 0
                            Controller.increment = 1
                            Controller.hitboxMagnitude = 65
                            pcall(task.spawn,Controller.attack,Controller)
                            lastFireValid = tick()
                        end
                        local AID3 = Controller.anims.basic[3]
                        local AID2 = Controller.anims.basic[2]
                        local ID = AID3 or AID2
                        Animation.AnimationId = ID
                        local Playing = Controller.humanoid:LoadAnimation(Animation)
                        Playing:Play(0.00075,0.01,0.01)
                        RigEvent.FireServer(RigEvent,"hit",canHits,AID3 and 1 or 3 or 2,"") -- 3 or 2
                        pcall(Controller.attack)
                        AttackSignal:Fire()
                        delay(.0,function()
                            Playing:Stop()
                        end)
                    end
                end
            end
        end)
    end
end)
_G.Fast_Delay = 0.0
spawn(function()
	while task.wait(.0) do
		pcall(function()
			if _G.FastAttack then
				repeat wait(_G.Fast_Delay)
					AttackNoCD()
				until not _G.FastAttack
			end
		end)
	end
end)
end)

btns:Button("fly player v2", function()
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")

local gui = Instance.new("ScreenGui")
gui.Parent = game.CoreGui

local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0, 200, 0, 200)
Frame.Position = UDim2.new(0.5, -100, 0.5, -100)
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.BorderSizePixel = 0
Frame.Active = true
Frame.Draggable = true
Frame.ClipsDescendants = true
Frame.Parent = gui

local Title = Instance.new("TextLabel")
Title.Size = UDim2.new(1, 0, 0.1, 0)
Title.Position = UDim2.new(0, 0, 0, 0)
Title.Text = "Fly Command"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextScaled = true
Title.Parent = Frame

local SpeedTextBox = Instance.new("TextBox")
SpeedTextBox.Size = UDim2.new(1, -20, 0.1, 0)
SpeedTextBox.Position = UDim2.new(0, 10, 0.15, 0)
SpeedTextBox.PlaceholderText = "Fly Speed"
SpeedTextBox.Parent = Frame

local Button = Instance.new("TextButton")
Button.Size = UDim2.new(1, -20, 0.1, 0)
Button.Position = UDim2.new(0, 10, 0.3, 0)
Button.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
Button.Text = "Start Flying"
Button.TextColor3 = Color3.fromRGB(255, 255, 255)
Button.TextScaled = true
Button.Parent = Frame

local Status = Instance.new("TextLabel")
Status.Size = UDim2.new(1, 0, 0.1, 0)
Status.Position = UDim2.new(0, 0, 0.45, 0)
Status.Text = ""
Status.TextColor3 = Color3.fromRGB(255, 255, 255)
Status.TextScaled = true
Status.Parent = Frame

local Description = Instance.new("TextLabel")
Description.Size = UDim2.new(1, 0, 0.1, 0)
Description.Position = UDim2.new(0, 0, 0.7, 0)
Description.Text = "Enter the speed to control your flying speed."
Description.TextColor3 = Color3.fromRGB(255, 255, 255)
Description.TextScaled = true
Description.Parent = Frame

local flying = false
local speed = 100

local function startFlying(flySpeed)
    flying = true
    local humanoidRootPart = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart")

    if not humanoidRootPart then
        Status.Text = "Cannot find HumanoidRootPart"
        return
    end

    local bodyVelocity = Instance.new("BodyVelocity")
    bodyVelocity.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
    bodyVelocity.Velocity = Workspace.CurrentCamera.CFrame.LookVector * flySpeed
    bodyVelocity.Parent = humanoidRootPart

    -- Update camera to follow the humanoid root part
    Workspace.CurrentCamera.CameraSubject = humanoidRootPart
    Workspace.CurrentCamera.CameraType = Enum.CameraType.Custom

    local function onHeartbeat()
        if flying then
            bodyVelocity.Velocity = Workspace.CurrentCamera.CFrame.LookVector * flySpeed
        else
            bodyVelocity:Destroy()
        end
    end

    local connection
    connection = RunService.Heartbeat:Connect(function()
        if not flying then
            connection:Disconnect()
        end
        onHeartbeat()
    end)
end

local function stopFlying()
    flying = false
    -- Restore the camera to its default state
    Workspace.CurrentCamera.CameraSubject = LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid")
    Workspace.CurrentCamera.CameraType = Enum.CameraType.Custom
end

Button.MouseButton1Click:Connect(function()
    if flying then
        stopFlying()
        Button.Text = "Start Flying"
        Status.Text = "Stopped Flying"
    else
        speed = tonumber(SpeedTextBox.Text) or 100 -- ความเร็วเริ่มต้น 100
        startFlying(speed)
        Button.Text = "Stop Flying"
        Status.Text = "Flying at speed " .. speed
    end
end)
end)

btns:Toggle("ตีเร็ว v9 (เหมือน v8 แต่แค่เร็วกว่า",false, function(vu)
_G.FastAttack = true;
local plr = game.Players.LocalPlayer

local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
      local p13 = CbFw2.activeController
      local ret = p13.blades[1]
      if not ret then return end
      while ret.Parent ~= game.Players.LocalPlayer.Character do ret=ret.Parent end
      return ret
end

local SeraphFrame = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework")))[2]
local VirtualUser = game:GetService('VirtualUser')
local RigControllerR = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.RigController))[2]
local Client = game:GetService("Players").LocalPlayer
local DMG = require(Client.PlayerScripts.CombatFramework.Particle.Damage)
local pingThreshold1 = 150
local pingThreshold2 = 200
function SeraphFuckWeapon() 
	local p13 = SeraphFrame.activeController
	local wea = p13.blades[1]
	if not wea then return end
	while wea.Parent~=game.Players.LocalPlayer.Character do wea=wea.Parent end
	return wea
end
function getHits(Size)
	local Hits = {}
	local Enemies = workspace.Enemies:GetChildren()
	local Characters = workspace.Characters:GetChildren()
	for i=1,#Enemies do local v = Enemies[i]
		local Human = v:FindFirstChildOfClass("Humanoid")
		if Human and Human.RootPart and Human.Health > 0 and game.Players.LocalPlayer:DistanceFromCharacter(Human.RootPart.Position) < Size+5 then
			table.insert(Hits,Human.RootPart)
		end
	end
	for i=1,#Characters do local v = Characters[i]
		if v ~= game.Players.LocalPlayer.Character then
			local Human = v:FindFirstChildOfClass("Humanoid")
			if Human and Human.RootPart and Human.Health > 0 and game.Players.LocalPlayer:DistanceFromCharacter(Human.RootPart.Position) < Size+5 then
				table.insert(Hits,Human.RootPart)
			end
		end
	end
	return Hits
end
function GetPing()
    local HttpService = game:GetService("HttpService")
    local url = "http://www.google.com"
    local startTime = tick()
    local success, result = pcall(function()
        HttpService:GetAsync(url)
    end)
    local endTime = tick()
    
    if success then
        return math.floor((endTime - startTime) * 1000)
    else
        return 9999 -- Return a large value if ping test fails
    end
end
spawn(function()
    local CombatFrameworkOld = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
    local CombatFrameworkR = getupvalues(CombatFrameworkOld)[2]
    function maxincrement()
        return #CombatFrameworkR.activeController.anims.basic
    end
task.spawn(
	function()
		while wait(.0) do
			if  _G.FastAttack9 then
				if SeraphFrame.activeController then
					--if v.Humanoid.Health > 0 then
					SeraphFrame.activeController.timeToNextAttack = 0
					SeraphFrame.activeController.focusStart = 0
					SeraphFrame.activeController.hitboxMagnitude = 40/9999
					SeraphFrame.activeController.humanoid.AutoRotate = true
					SeraphFrame.activeController.increment = 1 + 1 / 2
					
				--   end
               end
			end
		end
	end)
function Boost()
	spawn(function()
		game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(SeraphFuckWeapon()))
	end)
end
function Unboost()
	spawn(function()
		game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("unequipWeapon",tostring(SeraphFuckWeapon()))
	end)
end
local cdnormal = .0
_G.Dalt = .0
local Animation = Instance.new("Animation")
local CooldownFastAttack = .0
Attack = function()
	local ac = SeraphFrame.activeController
	if ac and ac.equipped then
		task.spawn(
			function()
				if tick() - cdnormal > .0 then
					ac:attack()
					cdnormal = tick()
					if _G.Dalt >= 10 then
						wait(.0)
						_G.Dalt = 0
					else
						ac:attack()
						cdnormal = tick()
						_G.Dalt = _G.Dalt + 1
					end
				else
					if _G.Dalt >= 10 then
						wait(.0)
						_G.Dalt = 0
					else
						Animation.AnimationId = ac.anims.basic[2]
						ac.humanoid:LoadAnimation(Animation):Play(1, 1)
						game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", getHits(60), 2, "")
						_G.Dalt = _G.Dalt + 2/2
					end
				end
			end)
	end
end
b = tick()
spawn(function()
	while wait(.0) do
		if  _G.FastAttack9 then
			if b - tick() > .0 then
				wait(.0)
				b = tick()
			end
			pcall(function()
				for i, v in pairs(game.Workspace.Enemies:GetChildren()) do
					if v.Humanoid.Health > 0 then
						if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40 then
							Attack()
							Boost()
							if _G.Dalt2 >= 30 then
								wait(.0)
								_G.Dalt2 = 0
							else
								Attack()
								_G.Dalt2 = _G.Dalt2 + 2/2
							end
						end
					end
				end
			end)
		end
	end
end)
k = tick()
spawn(function()
	while wait(.0) do
		if  _G.FastAttack9 then
			if k - tick() > .1 then
				wait()
				k = tick()
			end
			pcall(function()
				for i, v in pairs(game.Workspace.Enemies:GetChildren()) do
					if v.Humanoid.Health > 0 then
						if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40 then
							Unboost()
						end
					end
				end
			end)
		end
	end
end)
tjw1 = true
task.spawn(
	function()
		local a = game.Players.LocalPlayer
		local b = require(a.PlayerScripts.CombatFramework.Particle)
		local c = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib)
		if not shared.orl then
			shared.orl = c.wrapAttackAnimationAsync
		end
		if not shared.cpc then
			shared.cpc = b.play
		end
		if tjw1 then
			pcall(
				function()
					c.wrapAttackAnimationAsync = function(d, e, f, g, h)
						local i = c.getBladeHits(e, f, g)
						if i then
							b.play = function()
							end
							d:Play(0, 0, 0)
							h(i)
							b.play = shared.cpc
							wait(.1)
							d:Stop()
						end
					end
				end
			)
		end
	end
)
require(game.ReplicatedStorage.Util.CameraShaker):Stop();
CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework);
y = debug.getupvalues(CombatFrameworkR)[2];
spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
		if _G.FastAttack9 then
			if (typeof(y) == "table") then
				pcall(function()
					y.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
					y.activeController.hitboxMagnitude = 60;
					y.activeController.active = false;
					y.activeController.timeToNextBlock = 0;
					y.activeController.focusStart = 1655503339.0980349;
					y.activeController.increment = 0;
					y.activeController.blocking = false;
					y.activeController.attacking = false;
					y.activeController.humanoid.AutoRotate = true;
				end);
			end
		end
	end);
end);
spawn(function ()
	local v0 = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework")))[2];
	local v1 = game:GetService("VirtualUser");
	local v2 = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.RigController))[2];
	local v3 = game:GetService("Players").LocalPlayer;
	local v4 = require(v3.PlayerScripts.CombatFramework.Particle.Damage);
	function SeraphFuckWeapon()
		local v11 = v0.activeController;
		local v12 = v11.blades[1];
		if not v12 then
			return;
		end
		while v12.Parent ~= game.Players.LocalPlayer.Character do
			v12 = v12.Parent;
		end
		return v12;
	end
	task.spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			if _G.FastAttack9 then
				if v0.activeController then
					v0.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
					v0.activeController.focusStart = 0;
					v0.activeController.hitboxMagnitude = 60;
					v0.activeController.humanoid.AutoRotate = true;
					v0.activeController.increment = 1 + (1 / 1);
				end
			end
		end)
	end);
	function Boost()
		spawn(function()
			game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange", tostring(SeraphFuckWeapon()));
		end);
	end
	local v3 = game.Players.LocalPlayer;
	local v5 = require(v3.PlayerScripts.CombatFramework.Particle);
	local v6 = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib);
	task.spawn(function()
		pcall(function()
			if not shared.orl then
				shared.orl = v6.wrapAttackAnimationAsync;
			end
			if not shared.cpc then
				shared.cpc = v5.play;
			end
			spawn(function()
				require(game.ReplicatedStorage.Util.CameraShaker):Stop();
				game:GetService("RunService").Heartbeat:Connect(function()
					v6.wrapAttackAnimationAsync = function(v38, v39, v40, v41, v42)
						local v43 = v6.getBladeHits(v39, v40, v41);
						if v43 then
							if _G.FastAttack9 then
								v5.play = function()
								end;
								v38:Play(10.1, 9.1, 8.1);
								v42(v43);
								v5.play = shared.cpc;
								wait(v38.length * 10.5);
								v38:Stop();
							else
								v42(v43);
								v5.play = shared.cpc;
								wait(v38.length * 10.5);
								v38:Stop();
							end
						end
					end;
				end);
			end);
		end);
	end);
	function Unboost()
		spawn(function()
			game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("unequipWeapon", tostring(SeraphFuckWeapon()));
		end);
	end
	local v7 = 0;
	local v8 = Instance.new("Animation");
	local v9 = 0;
	function Attack()
		local v13 = v0.activeController;
		if (v13 and v13.equipped) then
			task.spawn(function()
				if ((tick() - v7) > .0) then
					v13:attack();
					v7 = tick();
				else
					v8.AnimationId = v13.anims.basic[2];
					v13.humanoid:LoadAnimation(v8):Play(2, 2);
					game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", getHits(120), 2, "");
				end
			end);
		end
	end
	b = tick();
	spawn(function()
		while wait(0) do
			if _G.FastAttack9 then
				if ((b - tick()) > 0.75) then
					wait(.0);
					b = tick();
				end
				pcall(function()
					for v57, v58 in pairs(game.Workspace.Enemies:GetChildren()) do
						if (v58.Humanoid.Health > 0) then
							if ((v58.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40) then
								Attack();
								wait(.0);
								Boost();
							end
						end
					end
				end);
			end
		end
	end);
	k = tick();
	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			if _G.FastAttack9 then
				if ((k - tick()) > 0.75) then
					wait(0);
					k = tick();
				end
				pcall(function()
					for v59, v60 in pairs(game.Workspace.Enemies:GetChildren()) do
						if (v60.Humanoid.Health > 0) then
							if ((v60.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40) then
								wait(0);
								Unboost();
							end
						end
					end
				end);
			end
		end)
	end);
	function getHits(v14)
		local v15 = {};
		local v16 = workspace.Enemies:GetChildren();
		local v17 = workspace.Characters:GetChildren();
		for v22 = 1, #v16 do
			local v23 = v16[v22];
			local v24 = v23:FindFirstChildOfClass("Humanoid");
			if (v24 and v24.RootPart and (v24.Health > 0) and (game.Players.LocalPlayer:DistanceFromCharacter(v24.RootPart.Position) < (v14 + 5))) then
				table.insert(v15, v24.RootPart);
			end
		end
		for v25 = 1, #v17 do
			local v26 = v17[v25];
			if (v26 ~= game.Players.LocalPlayer.Character) then
				local v36 = v26:FindFirstChildOfClass("Humanoid");
				if (v36 and v36.RootPart and (v36.Health > 0) and (game.Players.LocalPlayer:DistanceFromCharacter(v36.RootPart.Position) < (v14 + 5))) then
					table.insert(v15, v36.RootPart);
				end
			end
		end
		return v15;
	end
	require(game.ReplicatedStorage.Util.CameraShaker):Stop();
	CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework);
	y = debug.getupvalues(CombatFrameworkR)[2];
	spawn(function()
		game:GetService("RunService").RenderStepped:Connect(function()
			if _G.FastAttack9 then
				if (typeof(y) == "table") then
					pcall(function()
						y.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
						y.activeController.hitboxMagnitude = 60;
						y.activeController.active = false;
						y.activeController.timeToNextBlock = 0;
						y.activeController.focusStart = 1655503339.0980349;
						y.activeController.increment = 0;
						y.activeController.blocking = false;
						y.activeController.attacking = false;
						y.activeController.humanoid.AutoRotate = true;
					end);
				end
			end
		end);
	end);
	tjw1 = true;
	task.spawn(function()
		local v18 = game.Players.LocalPlayer;
		local v19 = require(v18.PlayerScripts.CombatFramework.Particle);
		local v20 = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib);
		if not shared.orl then
			shared.orl = v20.wrapAttackAnimationAsync;
		end
		if not shared.cpc then
			shared.cpc = v19.play;
		end
		if tjw1 then
			pcall(function()
				v20.wrapAttackAnimationAsync = function(v44, v45, v46, v47, v48)
					local v49 = v20.getBladeHits(v45, v46, v47);
					if v49 then
						v19.play = function()
						end;
						v44:Play(15.25, 15.25, 15.25);
						v48(v49);
						v19.play = shared.cpc;
						wait(0);
						v44:Stop();
					end
				end;
			end);
		end
	end);
	end)
end) 
end)

btns:Toggle("ตีเร็ว v8 (ใช้ฆ่ามอนสเตอร์แบบทันที)",false, function(v)
_G.FastAttack = v;
local plr = game.Players.LocalPlayer

local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
      local p13 = CbFw2.activeController
      local ret = p13.blades[1]
      if not ret then return end
      while ret.Parent ~= game.Players.LocalPlayer.Character do ret=ret.Parent end
      return ret
end

local SeraphFrame = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework")))[2]
local VirtualUser = game:GetService('VirtualUser')
local RigControllerR = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.RigController))[2]
local Client = game:GetService("Players").LocalPlayer
local DMG = require(Client.PlayerScripts.CombatFramework.Particle.Damage)

function SeraphFuckWeapon() 
	local p13 = SeraphFrame.activeController
	local wea = p13.blades[1]
	if not wea then return end
	while wea.Parent~=game.Players.LocalPlayer.Character do wea=wea.Parent end
	return wea
end

function getHits(Size)
	local Hits = {}
	local Enemies = workspace.Enemies:GetChildren()
	local Characters = workspace.Characters:GetChildren()
	for i=1,#Enemies do local v = Enemies[i]
		local Human = v:FindFirstChildOfClass("Humanoid")
		if Human and Human.RootPart and Human.Health > 0 and game.Players.LocalPlayer:DistanceFromCharacter(Human.RootPart.Position) < Size+5 then
			table.insert(Hits,Human.RootPart)
		end
	end
	for i=1,#Characters do local v = Characters[i]
		if v ~= game.Players.LocalPlayer.Character then
			local Human = v:FindFirstChildOfClass("Humanoid")
			if Human and Human.RootPart and Human.Health > 0 and game.Players.LocalPlayer:DistanceFromCharacter(Human.RootPart.Position) < Size+5 then
				table.insert(Hits,Human.RootPart)
			end
		end
	end
	return Hits
end

task.spawn(
	function()
		while wait(.0/.0) do
			if  _G.FastAttack then
				if SeraphFrame.activeController then
					--if v.Humanoid.Health > 0 then
					SeraphFrame.activeController.timeToNextAttack = 0
					SeraphFrame.activeController.focusStart = 0
					SeraphFrame.activeController.hitboxMagnitude = 40
					SeraphFrame.activeController.humanoid.AutoRotate = true
					SeraphFrame.activeController.increment = 4 + 4 / 5
					game:GetService'VirtualUser':CaptureController()
			        game:GetService'VirtualUser':Button1Down(Vector2.new(0,1,0,1))
				--   end
               end
			end
		end
	end)

function Boost()
	spawn(function()
		game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(SeraphFuckWeapon()))
	end)
end

function Unboost()
	spawn(function()
		game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("unequipWeapon",tostring(SeraphFuckWeapon()))
	end)
end

local cdnormal = .0
_G.Dalt = .0
local Animation = Instance.new("Animation")
local CooldownFastAttack = .0
Attack = function()
	local ac = SeraphFrame.activeController
	if ac and ac.equipped then
		task.spawn(
			function()
				if tick() - cdnormal > .0 then
					ac:attack()
					cdnormal = tick()
					if _G.Dalt >= .0/980 then
						wait(.0/980)
						_G.Dalt = 0
					else
						ac:attack()
						cdnormal = tick()
						_G.Dalt = _G.Dalt + 1
					end
				else
					if _G.Dalt >= .0/980 then
						wait(.0/980)
						_G.Dalt = 0
					else
						Animation.AnimationId = ac.anims.basic[2]
						ac.humanoid:LoadAnimation(Animation):Play(1, 1)
						game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", getHits(60), 2, "")
						_G.Dalt = _G.Dalt + 5
					end
				end
			end)
	end
end

b = tick()
spawn(function()
	while wait(.0/.0) do
		if  _G.FastAttack then
			if b - tick() > .0/999 then
				wait(.0/.0)
				b = tick()
			end
			pcall(function()
				for i, v in pairs(game.Workspace.Enemies:GetChildren()) do
					if v.Humanoid.Health > 0 then
						if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40 then
							Attack()
							Boost()
							if _G.Dalt2 >= .0/99e99 then
								wait(.0/999)
								_G.Dalt2 = 0
							else
								Attack()
								_G.Dalt2 = _G.Dalt2 + 5
							end
						end
					end
				end
			end)
		end
	end
end)

k = tick()
spawn(function()
	while wait(.0/.0) do
		if  _G.FastAttack then
			if k - tick() > .0/.0 then
				wait()
				k = tick()
			end
			pcall(function()
				for i, v in pairs(game.Workspace.Enemies:GetChildren()) do
					if v.Humanoid.Health > 0 then
						if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40 then
							Unboost()
						end
					end
				end
			end)
		end
	end
end)

tjw1 = true
task.spawn(
	function()
		local a = game.Players.LocalPlayer
		local b = require(a.PlayerScripts.CombatFramework.Particle)
		local c = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib)
		if not shared.orl then
			shared.orl = c.wrapAttackAnimationAsync
		end
		if not shared.cpc then
			shared.cpc = b.play
		end
		if tjw1 then
			pcall(
				function()
					c.wrapAttackAnimationAsync = function(d, e, f, g, h)
						local i = c.getBladeHits(e, f, g)
						if i then
							b.play = function()
							end
							d:Play(0, 0, 0)
							h(i)
							b.play = shared.cpc
							wait(.0)
							d:Stop()
						end
					end
				end
			)
		end
	end
)

require(game.ReplicatedStorage.Util.CameraShaker):Stop();
CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework);
y = debug.getupvalues(CombatFrameworkR)[2];
spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
		if _G.FastAttack then
			if (typeof(y) == "table") then
				pcall(function()
					y.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
					y.activeController.hitboxMagnitude = 60;
					y.activeController.active = false;
					y.activeController.timeToNextBlock = 0;
					y.activeController.focusStart = 1655503339.0980349;
					y.activeController.increment = 0;
					y.activeController.blocking = false;
					y.activeController.attacking = false;
					y.activeController.humanoid.AutoRotate = true;
				end);
			end
		end
	end);
end);
spawn(function ()
	local v0 = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework")))[2];
	local v1 = game:GetService("VirtualUser");
	local v2 = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.RigController))[2];
	local v3 = game:GetService("Players").LocalPlayer;
	local v4 = require(v3.PlayerScripts.CombatFramework.Particle.Damage);
	function SeraphFuckWeapon()
		local v11 = v0.activeController;
		local v12 = v11.blades[1];
		if not v12 then
			return;
		end
		while v12.Parent ~= game.Players.LocalPlayer.Character do
			v12 = v12.Parent;
		end
		return v12;
	end
	task.spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			if _G.FastAttack then
				if v0.activeController then
					v0.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
					v0.activeController.focusStart = 0;
					v0.activeController.hitboxMagnitude = 60;
					v0.activeController.humanoid.AutoRotate = true;
					v0.activeController.increment = 5 + (5 / 10);
				end
			end
		end)
	end);
	function Boost()
		spawn(function()
			game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange", tostring(SeraphFuckWeapon()));
		end);
	end
	local v3 = game.Players.LocalPlayer;
	local v5 = require(v3.PlayerScripts.CombatFramework.Particle);
	local v6 = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib);
	task.spawn(function()
		pcall(function()
			if not shared.orl then
				shared.orl = v6.wrapAttackAnimationAsync;
			end
			if not shared.cpc then
				shared.cpc = v5.play;
			end
			spawn(function()
				require(game.ReplicatedStorage.Util.CameraShaker):Stop();
				game:GetService("RunService").Heartbeat:Connect(function()
					v6.wrapAttackAnimationAsync = function(v38, v39, v40, v41, v42)
						local v43 = v6.getBladeHits(v39, v40, v41);
						if v43 then
							if _G.FastAttack then
								v5.play = function()
								end;
								v38:Play(10.1, 9.1, 8.1);
								v42(v43);
								v5.play = shared.cpc;
								wait(v38.length * 10.5);
								v38:Stop();
							else
								v42(v43);
								v5.play = shared.cpc;
								wait(v38.length * 10.5);
								v38:Stop();
							end
						end
					end;
				end);
			end);
		end);
	end);
	function Unboost()
		spawn(function()
			game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("unequipWeapon", tostring(SeraphFuckWeapon()));
		end);
	end
	local v7 = 0;
	local v8 = Instance.new("Animation");
	local v9 = 0;
	function Attack()
		local v13 = v0.activeController;
		if (v13 and v13.equipped) then
			task.spawn(function()
				if ((tick() - v7) > .0/.0) then
					v13:attack();
					v7 = tick();
				else
					v8.AnimationId = v13.anims.basic[2];
					v13.humanoid:LoadAnimation(v8):Play(2, 2);
					game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", getHits(120), 2, "");
				end
			end);
		end
	end
	b = tick();
	spawn(function()
		while wait(0) do
			if _G.FastAttack then
				if ((b - tick()) > .0/.0) then
					wait(.0);
					b = tick();
				end
				pcall(function()
					for v57, v58 in pairs(game.Workspace.Enemies:GetChildren()) do
						if (v58.Humanoid.Health > 0) then
							if ((v58.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40) then
								Attack();
								wait(.0);
								Boost();
							end
						end
					end
				end);
			end
		end
	end);
	k = tick();
	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			if _G.FastAttack then
				if ((k - tick()) > .0/.0) then
					wait(.0);
					k = tick();
				end
				pcall(function()
					for v59, v60 in pairs(game.Workspace.Enemies:GetChildren()) do
						if (v60.Humanoid.Health > 0) then
							if ((v60.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40) then
								wait(.0/.0);
								Unboost();
							end
						end
					end
				end);
			end
		end)
	end);
	function getHits(v14)
		local v15 = {};
		local v16 = workspace.Enemies:GetChildren();
		local v17 = workspace.Characters:GetChildren();
		for v22 = 1, #v16 do
			local v23 = v16[v22];
			local v24 = v23:FindFirstChildOfClass("Humanoid");
			if (v24 and v24.RootPart and (v24.Health > 0) and (game.Players.LocalPlayer:DistanceFromCharacter(v24.RootPart.Position) < (v14 + 5))) then
				table.insert(v15, v24.RootPart);
			end
		end
		for v25 = 1, #v17 do
			local v26 = v17[v25];
			if (v26 ~= game.Players.LocalPlayer.Character) then
				local v36 = v26:FindFirstChildOfClass("Humanoid");
				if (v36 and v36.RootPart and (v36.Health > 0) and (game.Players.LocalPlayer:DistanceFromCharacter(v36.RootPart.Position) < (v14 + 5))) then
					table.insert(v15, v36.RootPart);
				end
			end
		end
		return v15;
	end
	require(game.ReplicatedStorage.Util.CameraShaker):Stop();
	CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework);
	y = debug.getupvalues(CombatFrameworkR)[2];
	spawn(function()
		game:GetService("RunService").RenderStepped:Connect(function()
			if _G.FastAttack then
				if (typeof(y) == "table") then
					pcall(function()
						y.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
						y.activeController.hitboxMagnitude = 60;
						y.activeController.active = false;
						y.activeController.timeToNextBlock = 0;
						y.activeController.focusStart = 1655503339.0980349;
						y.activeController.increment = 0;
						y.activeController.blocking = false;
						y.activeController.attacking = false;
						y.activeController.humanoid.AutoRotate = true;
					end);
				end
			end
		end);
	end);
	tjw1 = true;
	task.spawn(function()
		local v18 = game.Players.LocalPlayer;
		local v19 = require(v18.PlayerScripts.CombatFramework.Particle);
		local v20 = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib);
		if not shared.orl then
			shared.orl = v20.wrapAttackAnimationAsync;
		end
		if not shared.cpc then
			shared.cpc = v19.play;
		end
		if tjw1 then
			pcall(function()
				v20.wrapAttackAnimationAsync = function(v44, v45, v46, v47, v48)
					local v49 = v20.getBladeHits(v45, v46, v47);
					if v49 then
						v19.play = function()
						end;
						v44:Play(15.25, 15.25, 15.25);
						v48(v49);
						v19.play = shared.cpc;
						wait(.0/.0);
						v44:Stop();
					end
				end;
			end);
		end
	end);

end)
end)

btns:Toggle("ตีเร็ว v7 (เร็วแต่โอกาสโดนเตะน้อย)",false, function(vu)
local ASA = true
local plr = game.Players.LocalPlayer
local CbFw = getupvalues(require(game.Players.LocalPlayer.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]
local pingThreshold1 = 150
local pingThreshold2 = 200

function GetCurrentBlade() 
    local p13 = CbFw2.activeController
    local ret = p13.blades[1]
    if not ret then return end
    while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
    return ret
end

function GetPing()
    local HttpService = game:GetService("HttpService")
    local url = "http://www.google.com"
    local startTime = tick()
    local success, result = pcall(function()
        HttpService:GetAsync(url)
    end)
    local endTime = tick()
    
    if success then
        return math.floor((endTime - startTime) * 1000)
    else
        return 9999 -- Return a large value if ping test fails
    end
end

spawn(function()
    local CombatFrameworkOld = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
    local CombatFrameworkR = getupvalues(CombatFrameworkOld)[2]

    function maxincrement()
        return #CombatFrameworkR.activeController.anims.basic
    end

    spawn(function()
        local old
        old = hookmetamethod(game, "__namecall", function(self,...)
            local method = getnamecallmethod() local args = {...}
            if method:lower() == "fireserver" then
                if args[1] == "hit" then
                    args[3] = maxincrement()
                    return old(self,unpack(args))
                end 
            end
            return old(self,...)
        end) 
    end)
end)

spawn(function()
    while wait(.0/9999e9999) do
        pcall(function()
            if ASA then
                repeat wait(.0/9999e9999)
                    local AC = CbFw2.activeController
                    local ping = GetPing()
                    
                    if ping <= pingThreshold1 then
                        AC.attackCooldown = 0.4 -- Set your desired attack cooldown
                    elseif ping <= pingThreshold2 then
                        AC.attackCooldown = 0.2 -- Set a different attack cooldown
                    else
                        -- Use Megumint if ping exceeds the thresholds
                        -- Implement Megumint logic here
                    end
                    
                    for i = 1, 1 do 
                        local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
                            plr.Character,
                            {plr.Character.HumanoidRootPart},
                            60
                        )
                        local cac = {}
                        local hash = {}
                        for k, v in pairs(bladehit) do
                            if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
                                table.insert(cac, v.Parent.HumanoidRootPart)
                                hash[v.Parent] = true
                            end
                        end
                        bladehit = cac
                        if #bladehit > 0 then
                            local u8 = debug.getupvalue(AC.attack, 5)
                            local u9 = debug.getupvalue(AC.attack, 6)
                            local u7 = debug.getupvalue(AC.attack, 4)
                            local u10 = debug.getupvalue(AC.attack, 7)
                            local u12 = (u8 * 798405 + u7 * 727595) % u9
                            local u13 = u7 * 798405
                            (function()
                                u12 = (u12 * u9 + u13) % 1099511627776
                                u8 = math.floor(u12 / u9)
                                u7 = u12 - u8 * u9
                            end)()
                            u10 = u10 + 1
                            debug.setupvalue(AC.attack, 5, u8)
                            debug.setupvalue(AC.attack, 6, u9)
                            debug.setupvalue(AC.attack, 4, u7)
                            debug.setupvalue(AC.attack, 7, u10)
                            pcall(function()
                                if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then
                                    AC.animator.anims.basic[1]:Play(0.0001, 0.0000001, 0.00000001)
                                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
                                    game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "")
                                end
                            end)
                        end
                    end
                until not ASA
            end
        end)
    end
end)

local cac

if ASA then 
    AttackNoCD()
    cac = wait
else
    AttackNoCD()
    cac = wait
end
end)

btns:Toggle("ตีเร็ว v6",false, function(vu)
getgenv().Fastattack = vu

spawn(
    function()
        game:GetService("RunService").RenderStepped:Connect(
            function()
                if getgenv().Fastattack == true then
                    game.Players.LocalPlayer.Character.Stun.Value = 0
                    game.Players.LocalPlayer.Character.Humanoid.Sit = false
                    game.Players.LocalPlayer.Character.Busy.Value = false
                end
            end
        )
    end
)
spawn(function()
	if game.Players.LocalPlayer.Character:FindFirstChild("Stun") then
		game.Players.LocalPlayer.Character.Stun.Changed:connect(function()
			pcall(function()
				if game.Players.LocalPlayer.Character:FindFirstChild("Stun") then
					game.Players.LocalPlayer.Character.Stun.Value = 0
				end
			end)
		end)
	end
end)

local CombatFramework = require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework"))
local CombatFrameworkR = getupvalues(CombatFramework)[2]
local RigController = require(game:GetService("Players")["LocalPlayer"].PlayerScripts.CombatFramework.RigController)
local RigControllerR = getupvalues(RigController)[2]
local realbhit = require(game.ReplicatedStorage.CombatFramework.RigLib)
local cooldownfastattack = tick()

function CurrentWeapon()
	local ac = CombatFrameworkR.activeController
	local ret = ac.blades[1]
	if not ret then return game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name end
	pcall(function()
		while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
	end)
	if not ret then return game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name end
	return ret
end

function getAllBladeHitsPlayers(Sizes)
	local Hits = {}
	local Client = game.Players.LocalPlayer
	local Characters = game:GetService("Workspace").Characters:GetChildren()
	for i=1,#Characters do local v = Characters[i]
		local Human = v:FindFirstChildOfClass("Humanoid")
		if v.Name ~= game.Players.LocalPlayer.Name and Human and Human.RootPart and Human.Health > 0 and Client:DistanceFromCharacter(Human.RootPart.Position) < Sizes+5 then
			table.insert(Hits,Human.RootPart)
		end
	end
	return Hits
end

function getAllBladeHits(Sizes)
	local Hits = {}
	local Client = game.Players.LocalPlayer
	local Enemies = game:GetService("Workspace").Enemies:GetChildren()
	for i=1,#Enemies do local v = Enemies[i]
		local Human = v:FindFirstChildOfClass("Humanoid")
		if Human and Human.RootPart and Human.Health > 0 and Client:DistanceFromCharacter(Human.RootPart.Position) < Sizes+5 then
			table.insert(Hits,Human.RootPart)
		end
	end
	return Hits
end

function AttackFunction()
	local ac = CombatFrameworkR.activeController
	if ac and ac.equipped then
		for indexincrement = 1, 1 do
			local bladehit = getAllBladeHits(60)
			if #bladehit > 0 then
				local AcAttack8 = debug.getupvalue(ac.attack, 5)
				local AcAttack9 = debug.getupvalue(ac.attack, 6)
				local AcAttack7 = debug.getupvalue(ac.attack, 4)
				local AcAttack10 = debug.getupvalue(ac.attack, 7)
				local NumberAc12 = (AcAttack8 * 798405 + AcAttack7 * 727595) % AcAttack9
				local NumberAc13 = AcAttack7 * 798405
				(function()
					NumberAc12 = (NumberAc12 * AcAttack9 + NumberAc13) % 1099511627776
					AcAttack8 = math.floor(NumberAc12 / AcAttack9)
					AcAttack7 = NumberAc12 - AcAttack8 * AcAttack9
				end)()
				AcAttack10 = AcAttack10 + 1
				debug.setupvalue(ac.attack, 5, AcAttack8)
				debug.setupvalue(ac.attack, 6, AcAttack9)
				debug.setupvalue(ac.attack, 4, AcAttack7)
				debug.setupvalue(ac.attack, 7, AcAttack10)
				for k, v in pairs(ac.animator.anims.basic) do
					v:Play(0.01,0.01,0.01)
				end                 
				if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") and ac.blades and ac.blades[1] then 
					game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(CurrentWeapon()))
					game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(NumberAc12 / 1099511627776 * 16777215), AcAttack10)
					game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, 2, "") 
				end
			end
		end
	end
end
spawn(function()
	while wait() do
		for i,v in pairs(game:GetService("Workspace")["_WorldOrigin"]:GetChildren()) do
			pcall(function()
				if v.Name == ("CurvedRing") or v.Name == ("SlashHit") or v.Name == ("SwordSlash") or v.Name == ("SlashTail") or v.Name == ("Sounds") then
					v:Destroy()
				end
			end)
		end
	end
end)

		coroutine.wrap(function()
			while wait(.0/999999) do
				local ac = CombatFrameworkR.activeController
				if ac and ac.equipped then
					if getgenv().Fastattack then
						AttackFunction()
						if getgenv().Fastattack then
							if tick() - cooldownfastattack > .00000 then wait(.0000) cooldownfastattack = tick() end
						end
					elseif getgenv().FastAttack == true then
						if ac.hitboxMagnitude ~= 55 then
							ac.hitboxMagnitude = 55
						end
					if getgenv().Fastattack == false then
						require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework).activeController.hitboxMagnitude = 50
						end
						ac:attack()
					end
				end
			end
		end)()

spawn(function()
	if game.Players.LocalPlayer.Character:FindFirstChild("Stun") then
		game.Players.LocalPlayer.Character.Stun.Changed:connect(function()
			pcall(function()
				if game.Players.LocalPlayer.Character:FindFirstChild("Stun") then
					game.Players.LocalPlayer.Character.Stun.Value = 0
				end
			end)
		end)
	end
end)
		local Client = game.Players.LocalPlayer
		local STOP = require(Client.PlayerScripts.CombatFramework.Particle)
		local STOPRL = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib)
		spawn(function()
			while wait(.0/9999999) do
				pcall(function()
					if not shared.orl then shared.orl = STOPRL.wrapAttackAnimationAsync end
					if not shared.cpc then shared.cpc = STOP.play end
						STOPRL.wrapAttackAnimationAsync = function(a,b,c,d,func)
						local Hits = STOPRL.getBladeHits(b,c,d)
						if Hits then
            								if getgenv().Fastatack then
								STOP.play = function() end
								a:Play(0.01,0.01,0.01)
								func(Hits)
								STOP.play = shared.cpc
								wait(a.length * 0.5)
								a:Stop()
							else
								a:Play()
							end
						end
					end
				end)
			end
		end)
		end)

btns:Toggle("ตีเร็ว v5",false, function(vu)
local FastAttack = vu
--ขายห้ามแจก
require(game.ReplicatedStorage.Util.CameraShaker):Stop()
    local plr = game.Players.LocalPlayer
	local CbFw = getupvalues(require(game.Players.LocalPlayer.PlayerScripts.CombatFramework))
	local CbFw2 = CbFw[2]

	function GetCurrentBlade() 
		local p13 = CbFw2.activeController
		local ret = p13.blades[1]
		if not ret then return end
		while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
		return ret
	end
	local CombatFramework = require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework"))
	local CombatFrameworkR = getupvalues(CombatFramework)[2]
	local RigController = require(game:GetService("Players")["LocalPlayer"].PlayerScripts.CombatFramework.RigController)
	local RigControllerR = getupvalues(RigController)[2]
	local realbhit = require(game.ReplicatedStorage.CombatFramework.RigLib)
	local cooldownfastattack = tick()
		
	spawn(function()
		local CombatFrameworkOld = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
		local CombatFrameworkR = getupvalues(CombatFrameworkOld)[2]
		local CameraShakerR = require(game.ReplicatedStorage.Util.CameraShaker)
			
		function maxincrement()
			return #CombatFrameworkR.activeController.anims.basic
		end
			
		spawn(function()
			local old
			old = hookmetamethod(game, "__namecall",function(self,...)
				local method = getnamecallmethod() local args = {...}
				if method:lower() == "fireserver" then
					if args[1] == "hit" then
						args[3] = maxincrement()
						return old(self,unpack(args))
					end 
				end
			return old(self,...)
			end) 
		end)
	end)
	
	spawn(function()
		while wait(.0/9999e9999) do
			pcall(function()
				if FastAttack then
					repeat wait(.0/9999e9999)
						local AC = CbFw2.activeController
						for i = 1, 1 do 
							local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
								plr.Character,
								{plr.Character.HumanoidRootPart},
								60
							)
							local cac = {}
							local hash = {}
							for k, v in pairs(bladehit) do
								if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
									table.insert(cac, v.Parent.HumanoidRootPart)
									hash[v.Parent] = true
								end
							end
							bladehit = cac
							if #bladehit > 0 then
								local u8 = debug.getupvalue(AC.attack, 5)
								local u9 = debug.getupvalue(AC.attack, 6)
								local u7 = debug.getupvalue(AC.attack, 4)
								local u10 = debug.getupvalue(AC.attack, 7)
								local u12 = (u8 * 798405 + u7 * 727595) % u9
								local u13 = u7 * 798405
								(function()
									u12 = (u12 * u9 + u13) % 1099511627776
									u8 = math.floor(u12 / u9)
									u7 = u12 - u8 * u9
								end)()
								u10 = u10 + 1
								debug.setupvalue(AC.attack, 5, u8)
								debug.setupvalue(AC.attack, 6, u9)
								debug.setupvalue(AC.attack, 4, u7)
								debug.setupvalue(AC.attack, 7, u10)
								pcall(function()
									if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then
										AC.animator.anims.basic[1]:Play(0.0000001,0.0000001,0.00000001)
										game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
										game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
										game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "")
									end
								end)
							end
						end
					until not FastAttack
				end
			end)
		end
	end)
	
	local cac
if FastAttack then 
AttackNoCD()
	cac=wait
else
AttackNoCD()
	cac=wait
end
end)

btns:Toggle("ตีเร็ว v4",false, function(vu)
_G.FastAttack = vu;
local plr = game.Players.LocalPlayer

local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
	local p13 = CbFw2.activeController
	local ret = p13.blades[1]
	if not ret then return end
	while ret.Parent ~= game.Players.LocalPlayer.Character do ret=ret.Parent end
	return ret
end

local SeraphFrame = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework")))[2]
local VirtualUser = game:GetService('VirtualUser')
local RigControllerR = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.RigController))[2]
local Client = game:GetService("Players").LocalPlayer
local DMG = require(Client.PlayerScripts.CombatFramework.Particle.Damage)

function SeraphFuckWeapon() 
	local p13 = SeraphFrame.activeController
	local wea = p13.blades[1]
	if not wea then return end
	while wea.Parent~=game.Players.LocalPlayer.Character do wea=wea.Parent end
	return wea
end

function getHits(Size)
	local Hits = {}
	local Enemies = workspace.Enemies:GetChildren()
	local Characters = workspace.Characters:GetChildren()
	for i=1,#Enemies do local v = Enemies[i]
		local Human = v:FindFirstChildOfClass("Humanoid")
		if Human and Human.RootPart and Human.Health > 0 and game.Players.LocalPlayer:DistanceFromCharacter(Human.RootPart.Position) < Size+5 then
			table.insert(Hits,Human.RootPart)
		end
	end
	for i=1,#Characters do local v = Characters[i]
		if v ~= game.Players.LocalPlayer.Character then
			local Human = v:FindFirstChildOfClass("Humanoid")
			if Human and Human.RootPart and Human.Health > 0 and game.Players.LocalPlayer:DistanceFromCharacter(Human.RootPart.Position) < Size+5 then
				table.insert(Hits,Human.RootPart)
			end
		end
	end
	return Hits
end

spawn(
	function()
		while wait(0/99999999999) do
			if  _G.FastAttack then
				if SeraphFrame.activeController then
					--if v.Humanoid.Health > 0 then
					SeraphFrame.activeController.timeToNextAttack = 0
					SeraphFrame.activeController.focusStart = 0
					SeraphFrame.activeController.hitboxMagnitude = 40
					SeraphFrame.activeController.humanoid.AutoRotate = true
					SeraphFrame.activeController.increment = 1 + 1 / 1
					game:GetService("ReplicatedStorage").Effect.Container.Death:Destroy()
				--   end
               end
			end
		end
	end)

function Boost()
	spawn(function()
		game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(SeraphFuckWeapon()))
	end)
end

function Unboost()
	spawn(function()
		game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("unequipWeapon",tostring(SeraphFuckWeapon()))
	end)
end

local cdnormal = .0/988888888
_G.Dalt = .0/988888888
local Animation = Instance.new("Animation")
local CooldownFastAttack = .0/999999
Attack = function()
	local ac = SeraphFrame.activeController
	if ac and ac.equipped then
		spawn(
			function()
				if tick() - cdnormal > .0/988888888 then
					ac:attack()
					cdnormal = tick()
					if _G.Dalt >= .0 then
						wait(.0/988888888)
						_G.Dalt = .0/988888888
					else
						ac:attack()
						cdnormal = tick()
						_G.Dalt = _G.Dalt + 1/1
					end
				else
					if _G.Dalt >= .0/9888888889 then
						wait(.0/988888888)
						_G.Dalt = .0/9888888889
					else
						Animation.AnimationId = ac.anims.basic[2]
						ac.humanoid:LoadAnimation(Animation):Play(1, 1)
						game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", getHits(60), 2, "")
						_G.Dalt = _G.Dalt + 1/1
					end
				end
			end)
	end
end

b = tick()
spawn(function()
	while wait() do
		if  _G.FastAttack then
			if b - tick() > .0/988888888 then
				wait()
				b = tick()
			end
			pcall(function()
				for i, v in pairs(game.Workspace.Enemies:GetChildren()) do
					if v.Humanoid.Health > 0 then
						if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40 then
							Attack()
							Boost()
							if _G.Dalt2 >= .0/988888888 then
								wait()
								_G.Dalt2 = .0/988888888
							else
								Attack()
								_G.Dalt2 = _G.Dalt2 + 1/1
							end
						end
					end
				end
			end)
		end
	end
end)

k = tick()
spawn(function()
	while wait() do
		if  _G.FastAttack then
			if k - tick() > .0/988888888 then
				wait()
				k = tick()
			end
			pcall(function()
				for i, v in pairs(game.Workspace.Enemies:GetChildren()) do
					if v.Humanoid.Health > 0 then
						if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40 then
							Unboost()
						end
					end
				end
			end)
		end
	end
end)

tjw1 = true
spawn(
	function()
		local a = game.Players.LocalPlayer
		local b = require(a.PlayerScripts.CombatFramework.Particle)
		local c = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib)
		if not shared.orl then
			shared.orl = c.wrapAttackAnimationAsync
		end
		if not shared.cpc then
			shared.cpc = b.play
		end
		if tjw1 then
			pcall(
				function()
					c.wrapAttackAnimationAsync = function(d, e, f, g, h)
						local i = c.getBladeHits(e, f, g)
						if i then
							b.play = function()
							end
							d:Play(0, 0, 0)
							h(i)
							b.play = shared.cpc
							wait(.0/988888888)
							d:Stop()
						end
					end
				end
			)
		end
	end
)

require(game.ReplicatedStorage.Util.CameraShaker):Stop();
CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework);
y = debug.getupvalues(CombatFrameworkR)[2];
spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
		if _G.FastAttack then
			if (typeof(y) == "table") then
				pcall(function()
					y.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
					y.activeController.hitboxMagnitude = 60;
					y.activeController.active = false;
					y.activeController.timeToNextBlock = 0;
					y.activeController.focusStart = 1655503339.0980349;
					y.activeController.increment = 0;
					y.activeController.blocking = false;
					y.activeController.attacking = false;
					y.activeController.humanoid.AutoRotate = true;
				end);
			end
		end
	end);
end);
spawn(function ()
	local v0 = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework")))[2];
	local v1 = game:GetService("VirtualUser");
	local v2 = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework.RigController))[2];
	local v3 = game:GetService("Players").LocalPlayer;
	local v4 = require(v3.PlayerScripts.CombatFramework.Particle.Damage);
	function SeraphFuckWeapon()
		local v11 = v0.activeController;
		local v12 = v11.blades[1];
		if not v12 then
			return;
		end
		while v12.Parent ~= game.Players.LocalPlayer.Character do
			v12 = v12.Parent;
		end
		return v12;
	end
	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			if _G.FastAttack then
				if v0.activeController then
					v0.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
					v0.activeController.focusStart = 0;
					v0.activeController.hitboxMagnitude = 60;
					v0.activeController.humanoid.AutoRotate = true;
					v0.activeController.increment = 1 + (1 / 1);
				end
			end
		end)
	end);
	function Boost()
		spawn(function()
			game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange", tostring(SeraphFuckWeapon()));
		end);
	end
	local v3 = game.Players.LocalPlayer;
	local v5 = require(v3.PlayerScripts.CombatFramework.Particle);
	local v6 = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib);
	spawn(function()
		pcall(function()
			if not shared.orl then
				shared.orl = v6.wrapAttackAnimationAsync;
			end
			if not shared.cpc then
				shared.cpc = v5.play;
			end
			spawn(function()
				require(game.ReplicatedStorage.Util.CameraShaker):Stop();
				game:GetService("RunService").Heartbeat:Connect(function()
					v6.wrapAttackAnimationAsync = function(v38, v39, v40, v41, v42)
						local v43 = v6.getBladeHits(v39, v40, v41);
						if v43 then
							if _G.FastAttack then
								v5.play = function()
								end;
								v38:Play(10.1, 9.1, 8.1);
								v42(v43);
								v5.play = shared.cpc;
								wait(v38.length * 10.5);
								v38:Stop();
							else
								v42(v43);
								v5.play = shared.cpc;
								wait(v38.length * 10.5);
								v38:Stop();
							end
						end
					end;
				end);
			end);
		end);
	end);
	function Unboost()
		spawn(function()
			game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("unequipWeapon", tostring(SeraphFuckWeapon()));
		end);
	end
	local v7 = 0;
	local v8 = Instance.new("Animation");
	local v9 = 0;
	function Attack()
		local v13 = v0.activeController;
		if (v13 and v13.equipped) then
			spawn(function()
				if ((tick() - v7) > .0/9999) then
					v13:attack();
					v7 = tick();
				else
					v8.AnimationId = v13.anims.basic[2];
					v13.humanoid:LoadAnimation(v8):Play(2, 2);
					game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", getHits(120), 2, "");
				end
			end);
		end
	end
	b = tick();
	spawn(function()
		while wait(.0/988888888) do
			if _G.FastAttack then
				if ((b - tick()) > .0/9999) then
					wait(.0/999999);
					b = tick();
				end
				pcall(function()
					for v57, v58 in pairs(game.Workspace.Enemies:GetChildren()) do
						if (v58.Humanoid.Health > 0) then
							if ((v58.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40) then
								Attack();
								wait(.0/999999999999);
								Boost();
							end
						end
					end
				end);
			end
		end
	end);
	k = tick();
	spawn(function()
		game:GetService("RunService").Heartbeat:Connect(function()
			if _G.FastAttack then
				if ((k - tick()) > .0/9999) then
					wait(.0/999998);
					k = tick();
				end
				pcall(function()
					for v59, v60 in pairs(game.Workspace.Enemies:GetChildren()) do
						if (v60.Humanoid.Health > 0) then
							if ((v60.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 40) then
								wait(.0/99999998889);
								Unboost();
							end
						end
					end
				end);
			end
		end)
	end);
	function getHits(v14)
		local v15 = {};
		local v16 = workspace.Enemies:GetChildren();
		local v17 = workspace.Characters:GetChildren();
		for v22 = 1, #v16 do
			local v23 = v16[v22];
			local v24 = v23:FindFirstChildOfClass("Humanoid");
			if (v24 and v24.RootPart and (v24.Health > 0) and (game.Players.LocalPlayer:DistanceFromCharacter(v24.RootPart.Position) < (v14 + 5))) then
				table.insert(v15, v24.RootPart);
			end
		end
		for v25 = 1, #v17 do
			local v26 = v17[v25];
			if (v26 ~= game.Players.LocalPlayer.Character) then
				local v36 = v26:FindFirstChildOfClass("Humanoid");
				if (v36 and v36.RootPart and (v36.Health > 0) and (game.Players.LocalPlayer:DistanceFromCharacter(v36.RootPart.Position) < (v14 + 5))) then
					table.insert(v15, v36.RootPart);
				end
			end
		end
		return v15;
	end
	require(game.ReplicatedStorage.Util.CameraShaker):Stop();
	CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework);
	y = debug.getupvalues(CombatFrameworkR)[2];
	spawn(function()
		game:GetService("RunService").RenderStepped:Connect(function()
			if _G.FastAttack then
				if (typeof(y) == "table") then
					pcall(function()
						y.activeController.timeToNextAttack = -(math.huge ^ (math.huge ^ math.huge));
						y.activeController.hitboxMagnitude = 60;
						y.activeController.active = false;
						y.activeController.timeToNextBlock = 0;
						y.activeController.focusStart = 1655503339.0980349;
						y.activeController.increment = 0;
						y.activeController.blocking = false;
						y.activeController.attacking = false;
						y.activeController.humanoid.AutoRotate = true;
					end);
				end
			end
		end);
	end);
	tjw1 = true;
	spawn(function()
		local v18 = game.Players.LocalPlayer;
		local v19 = require(v18.PlayerScripts.CombatFramework.Particle);
		local v20 = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib);
		if not shared.orl then
			shared.orl = v20.wrapAttackAnimationAsync;
		end
		if not shared.cpc then
			shared.cpc = v19.play;
		end
		if tjw1 then
			pcall(function()
				v20.wrapAttackAnimationAsync = function(v44, v45, v46, v47, v48)
					local v49 = v20.getBladeHits(v45, v46, v47);
					if v49 then
						v19.play = function()
						end;
						v44:Play(15.25, 15.25, 15.25);
						v48(v49);
						v19.play = shared.cpc;
						wait(.0/988888888);
						v44:Stop();
					end
				end;
			end);
		end
	end);
	
	end)
	
	end)

btns:Toggle("ตีเร็ว v3",false, function(vu)
astAttack = vu

local plr = game.Players.LocalPlayer

local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
    local p13 = CbFw2.activeController
    local ret = p13.blades[1]
    if not ret then return end
    while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
    return ret
end

function AttackNoCD() 
    local AC = CbFw2.activeController
    for i = 1, 1 do 
        local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
            plr.Character,
            {plr.Character.HumanoidRootPart},
            45
        )
        local cac = {}
        local hash = {}
        for k, v in pairs(bladehit) do
            if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
                table.insert(cac, v.Parent.HumanoidRootPart)
                hash[v.Parent] = true
            end
        end
        bladehit = cac
        if #bladehit > 0 then
            local u8 = debug.getupvalue(AC.attack, 5)
            local u9 = debug.getupvalue(AC.attack, 6)
            local u7 = debug.getupvalue(AC.attack, 4)
            local u10 = debug.getupvalue(AC.attack, 7)
            local u12 = (u8 * 798405 + u7 * 727595) % u9
            local u13 = u7 * 798405
            (function()
                u12 = (u12 * u9 + u13) % 1099511627776
                u8 = math.floor(u12 / u9)
                u7 = u12 - u8 * u9
            end)()
            u10 = u10 + 1
            debug.setupvalue(AC.attack, 5, u8)
            debug.setupvalue(AC.attack, 6, u9)
            debug.setupvalue(AC.attack, 4, u7)
            debug.setupvalue(AC.attack, 7, u10)
            pcall(function()
                for k, v in pairs(AC.animator.anims.basic) do
                    v:Play()
                end                  
            end)
            if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
                game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
            end
        end
    end
end

spawn(function()
    while astAttack do
        pcall(function()
            AttackNoCD() 
        end)
        wait(.0/10e10) -- ปรับตามความเหมาะสม
    end
end)

require(game.ReplicatedStorage.Util.CameraShaker):Stop()

spawn(function()
    while wait(0.0) do
        pcall(function()
            if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
            end
        end)
    end
end)
end)

btns:Toggle("ตีเร็ว v2",false, function(vu)
AW = vu

local plr = game.Players.LocalPlayer

local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
    local p13 = CbFw2.activeController
    local ret = p13.blades[1]
    if not ret then return end
    while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
    return ret
end

function AttackNoCD() 
    local AC = CbFw2.activeController
    for i = 1, 1 do 
        local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
            plr.Character,
            {plr.Character.HumanoidRootPart},
            45
        )
        local cac = {}
        local hash = {}
        for k, v in pairs(bladehit) do
            if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
                table.insert(cac, v.Parent.HumanoidRootPart)
                hash[v.Parent] = true
            end
        end
        bladehit = cac
        if #bladehit > 0 then
            local u8 = debug.getupvalue(AC.attack, 5)
            local u9 = debug.getupvalue(AC.attack, 6)
            local u7 = debug.getupvalue(AC.attack, 4)
            local u10 = debug.getupvalue(AC.attack, 7)
            local u12 = (u8 * 798405 + u7 * 727595) % u9
            local u13 = u7 * 798405
            (function()
                u12 = (u12 * u9 + u13) % 1099511627776
                u8 = math.floor(u12 / u9)
                u7 = u12 - u8 * u9
            end)()
            u10 = u10 + 1
            debug.setupvalue(AC.attack, 5, u8)
            debug.setupvalue(AC.attack, 6, u9)
            debug.setupvalue(AC.attack, 4, u7)
            debug.setupvalue(AC.attack, 7, u10)
            pcall(function()
                for k, v in pairs(AC.animator.anims.basic) do
                    v:Play()
                end                  
            end)
            if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
                game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
            end
        end
    end
end

local fastAttackLoop
fastAttackLoop = game:GetService("RunService").RenderStepped:Connect(function()
    if AW then
        pcall(function()
            AttackNoCD() 
        end)
    else
        fastAttackLoop:Disconnect()
    end
end)

require(game.ReplicatedStorage.Util.CameraShaker):Stop()
spawn(function()
    while wait(.0*.0*0*.0*0*.0*0*.0*0*.0*0*.0*0*.0*0*.0*0*.0*0*.0/math.huge) do
        pcall(function()
        AttackNoCD() 
            if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
            end
        end)
    end
end) 
end)

fast10 = .0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0
btns:Toggle("ตีเร็ว(เลือกระดับก่อน)",false, function(fam)
_G.FastAttack = fam
end)

local AttackList = {"ช้า", "ปรานกลาง", "ตีเร็ว", "ตีเร็วมาก (หลุดได้)", "ตีเร็วพระเจ้า (หลุดง่าย)", "ตีเร็วระดับไอหนึ่งเก", "เอาดีแค่อันหลังๆแม่งก็เร็วล่ะน่ะยังไม่พออีกหรือ"}
_G.FastAttackDelay = "ช้า"
btns:Dropdown("เลือกระดับความเร็ว", AttackList, function(adl)
    _G.FastAttackDelay = adl
end)
spawn(function()
    while wait(fastsetting) do
        if _G.FastAttackDelay then
            pcall(function()
                if _G.FastAttackDelay == "ช้า" then
                    _G.FastAttackDelay = 0.9
                elseif _G.FastAttackDelay == "ปรานกลาง" then
                    _G.FastAttackDelay = 0.5
                elseif _G.FastAttackDelay == "ตีเร็ว" then
                    _G.FastAttackDelay = 0.3
                elseif _G.FastAttackDelay == "ตีเร็วมาก (หลุดได้)" then
                    _G.FastAttackDelay = 0.1
                elseif _G.FastAttackDelay == "ตีเร็วพระเจ้า (หลุดง่าย)" then
                    _G.FastAttackDelay = .0*.0*.0*.0*.0*.0
                elseif _G.FastAttackDelay == "ตีเร็วระดับไอหนึ่งเก" then
                    _G.FastAttackDelay = .0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0*.0
                    elseif _G.FastAttackDelay == "เอาดีแค่อันหลังๆแม่งก็เร็วล่ะน่ะยังไม่พออีกหรือ" then
                    _G.FastAttackDelay = -(math.huge ^ (math.huge ^ math.huge (math.huge ^ math.huge (math.huge ^ math.huge))));
                end
            end)
        end
    end
end)
btns:Toggle("เรือบินใช้ได้แต่ เรือ โดฟา",false, function(bool)
  _G.FigPos = 150
  Gay = bool
  
  while Gay do
  wait()
        pcall(function ()
            if game:GetService("Workspace").Boats:FindFirstChild("Guardian") then
                game:GetService("Workspace").Boats:FindFirstChild("Guardian").VehicleSeat.BodyPosition.Position = Vector3.new(0,_G.FigPos,0)
            elseif game:GetService("Workspace").Boats:FindFirstChild("Beast Hunter") then
                game:GetService("Workspace").Boats:FindFirstChild("Beast Hunter").VehicleSeat.BodyPosition.Position = Vector3.new(0,_G.FigPos,0)
            end
        end) 
     end
        end)

btns:Toggle("ฮาราชันย์ Bike (อย่าเปิดตอนบอสฉลามมาเพราะมันจะบัค)",false, function(boo)
_G.FreezeMob = boo
Cooldown = .0*.0*.0*.0*.0*.0*.0*.0*.0

while _G.FreezeMob do
    pcall(function()
    wait(Cooldown)
        local player = game.Players.LocalPlayer
        local playerPos = player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.HumanoidRootPart.Position

        if playerPos then
            for _, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                local mobPos = v:FindFirstChild("HumanoidRootPart") and v.HumanoidRootPart.Position

                if mobPos and (playerPos - mobPos).Magnitude <= 50 then
                    v.HumanoidRootPart.Size = Vector3.new(2, 2, 2) 
                    v.HumanoidRootPart.Transparency = 2
                    v.HumanoidRootPart.CanCollide = false
                    v.Humanoid.WalkSpeed = 0
                    v.Humanoid.JumpPower = 0
                    v.humanoid.Gravity = 0

                    if sethiddenproperty then
                        sethiddenproperty(player, "SimulationRadius", math.huge)
                    end
                end
            end
        end
    end)
end
end)

local speedwair = .0*.0*.0*.0*.0
btns:Toggle("เรือเร็ว ใช้ได้ทุกชนิด",false, function(boo)
sp = boo

while sp do
    wait(speedwair)
    
    for _, boat in pairs(game:GetService("Workspace").Boats:GetChildren()) do
        if boat:IsA("Model") and boat:FindFirstChild("VehicleSeat") then
            boat.VehicleSeat.MaxSpeed = 365
        end
    end
end
end)

btns:Toggle("เดินบนน้ำ",true, function(vu)
_G.WalkWater = vu
		end)
		
		spawn(function()
			while task.wait() do
				pcall(function()
					if _G.WalkWater then
						game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,112,1000)
					else
						game:GetService("Workspace").Map["WaterBase-Plane"].Size = Vector3.new(1000,80,1000)
					end
				end)
			end
		end)

btns:Toggle("ออโต้คลิกแลค",false, function(bool)
Ast = bool
click = bool

coroutine.wrap(function()
local StopCamera = require(game.ReplicatedStorage.Util.CameraShaker)StopCamera:Stop()
    for v,v in pairs(getreg()) do
        if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework then
             for v,v in pairs(debug.getupvalues(v)) do
                if typeof(v) == "table" then
                    spawn(function()
                        game:GetService("RunService").RenderStepped:Connect(function()
                            if Ast then
                                 pcall(function()
                                     v.activeController.timeToNextAttack = -(math.huge^math.huge^math.huge)
                                     v.activeController.attacking = false
                                     v.activeController.increment = 4*4*4
                                     v.activeController.blocking = false   
                                     v.activeController.hitboxMagnitude = 150
    		                         v.activeController.humanoid.AutoRotate = true
    	                      	     v.activeController.focusStart = 0
    	                      	     v.activeController.currentAttackTrack = 0
                                     sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRaxNerous", math.huge)
                                 end)
                             end
                         end)
                    end)
                end
            end
        end
    end
end)();

spawn(function()
    game:GetService("RunService").RenderStepped:Connect(function()
        if click then
             pcall(function()
                game:GetService'VirtualUser':CaptureController()
			    game:GetService'VirtualUser':Button1Down(Vector2.new(0,1,0,1))
            end)
        end
    end)
end)
end)

Teleport:Button("Teleport To Old World", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelMain")
end)

Teleport:Button("Teleport To Second Sea", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
end)

Teleport:Button("Teleport To Third Sea", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
end)


if World1 then
	Teleport:Dropdown("Select Island",{
		"WindMill",
		"Marine",
		"Middle Town",
		"Jungle",
		"Pirate Village",
		"Desert",
		"Snow Island",
		"MarineFord",
		"Colosseum",
		"Sky Island 1",
		"Sky Island 2",
		"Sky Island 3",
		"Prison",
		"Magma Village",
		"Under Water Island",
		"Fountain City",
		"Shank Room",
		"Mob Island"
	},function (value)
		_G.SelectIsland = value
	end)
end

if World2 then
	Teleport:Dropdown("Select Island",{
		"The Cafe",
		"Frist Spot",
		"Dark Area",
		"Flamingo Mansion",
		"Flamingo Room",
		"Green Zone",
		"Factory",
		"Colossuim",
		"Zombie Island",
		"Two Snow Mountain",
		"Punk Hazard",
		"Cursed Ship",
		"Ice Castle",
		"Forgotten Island",
		"Ussop Island",
		"Mini Sky Island"
	},function (value)
		_G.SelectIsland = value
	end)
end

if World3 then
	Teleport:Dropdown("Select Island",{
		"Mansion",
		"Port Town",
		"Great Tree",
		"Castle On The Sea",
		"MiniSky", 
		"Hydra Island",
		"Floating Turtle",
		"Haunted Castle",
		"Ice Cream Island",
		"Peanut Island",
		"Cake Island",
		"Sea to Treats New"
	},function (value)
		_G.SelectIsland = value
	end)
end

Teleport:Toggle("Teleport",false, function(value)
	_G.TeleportIsland = value
	if _G.TeleportIsland == true then
		repeat wait()
			if _G.SelectIsland == "WindMill" then
				topos(CFrame.new(979.79895019531, 16.516613006592, 1429.0466308594))
			elseif _G.SelectIsland == "Marine" then
				topos(CFrame.new(-2566.4296875, 6.8556680679321, 2045.2561035156))
			elseif _G.SelectIsland == "Middle Town" then
				topos(CFrame.new(-690.33081054688, 15.09425163269, 1582.2380371094))
			elseif _G.SelectIsland == "Jungle" then
				topos(CFrame.new(-1612.7957763672, 36.852081298828, 149.12843322754))
			elseif _G.SelectIsland == "Pirate Village" then
				topos(CFrame.new(-1181.3093261719, 4.7514905929565, 3803.5456542969))
			elseif _G.SelectIsland == "Desert" then
				topos(CFrame.new(944.15789794922, 20.919729232788, 4373.3002929688))
			elseif _G.SelectIsland == "Snow Island" then
				topos(CFrame.new(1347.8067626953, 104.66806030273, -1319.7370605469))
			elseif _G.SelectIsland == "MarineFord" then
				topos(CFrame.new(-4914.8212890625, 50.963626861572, 4281.0278320313))
			elseif _G.SelectIsland == "Colosseum" then
				topos( CFrame.new(-1427.6203613281, 7.2881078720093, -2792.7722167969))
			elseif _G.SelectIsland == "Sky Island 1" then
				topos(CFrame.new(-4869.1025390625, 733.46051025391, -2667.0180664063))
			elseif _G.SelectIsland == "Sky Island 2" then  
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
			elseif _G.SelectIsland == "Sky Island 3" then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
			elseif _G.SelectIsland == "Prison" then
				topos( CFrame.new(4875.330078125, 5.6519818305969, 734.85021972656))
			elseif _G.SelectIsland == "Magma Village" then
				topos(CFrame.new(-5247.7163085938, 12.883934020996, 8504.96875))
			elseif _G.SelectIsland == "Under Water Island" then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
			elseif _G.SelectIsland == "Fountain City" then
				topos(CFrame.new(5127.1284179688, 59.501365661621, 4105.4458007813))
			elseif _G.SelectIsland == "Shank Room" then
				topos(CFrame.new(-1442.16553, 29.8788261, -28.3547478))
			elseif _G.SelectIsland == "Mob Island" then
				topos(CFrame.new(-2850.20068, 7.39224768, 5354.99268))
			elseif _G.SelectIsland == "The Cafe" then
				topos(CFrame.new(-380.47927856445, 77.220390319824, 255.82550048828))
			elseif _G.SelectIsland == "Frist Spot" then
				topos(CFrame.new(-11.311455726624, 29.276733398438, 2771.5224609375))
			elseif _G.SelectIsland == "Dark Area" then
				topos(CFrame.new(3780.0302734375, 22.652164459229, -3498.5859375))
			elseif _G.SelectIsland == "Flamingo Mansion" then
				topos(CFrame.new(-483.73370361328, 332.0383605957, 595.32708740234))
			elseif _G.SelectIsland == "Flamingo Room" then
				topos(CFrame.new(2284.4140625, 15.152037620544, 875.72534179688))
			elseif _G.SelectIsland == "Green Zone" then
				topos( CFrame.new(-2448.5300292969, 73.016105651855, -3210.6306152344))
			elseif _G.SelectIsland == "Factory" then
				topos(CFrame.new(424.12698364258, 211.16171264648, -427.54049682617))
			elseif _G.SelectIsland == "Colossuim" then
				topos( CFrame.new(-1503.6224365234, 219.7956237793, 1369.3101806641))
			elseif _G.SelectIsland == "Zombie Island" then
				topos(CFrame.new(-5622.033203125, 492.19604492188, -781.78552246094))
			elseif _G.SelectIsland == "Two Snow Mountain" then
				topos(CFrame.new(753.14288330078, 408.23559570313, -5274.6147460938))
			elseif _G.SelectIsland == "Punk Hazard" then
				topos(CFrame.new(-6127.654296875, 15.951762199402, -5040.2861328125))
			elseif _G.SelectIsland == "Cursed Ship" then
				topos(CFrame.new(923.40197753906, 125.05712890625, 32885.875))
			elseif _G.SelectIsland == "Ice Castle" then
				topos(CFrame.new(6148.4116210938, 294.38687133789, -6741.1166992188))
			elseif _G.SelectIsland == "Forgotten Island" then
				topos(CFrame.new(-3032.7641601563, 317.89672851563, -10075.373046875))
			elseif _G.SelectIsland == "Ussop Island" then
				topos(CFrame.new(4816.8618164063, 8.4599885940552, 2863.8195800781))
			elseif _G.SelectIsland == "Mini Sky Island" then
				topos(CFrame.new(-288.74060058594, 49326.31640625, -35248.59375))
			elseif _G.SelectIsland == "Great Tree" then
				topos(CFrame.new(2681.2736816406, 1682.8092041016, -7190.9853515625))
			elseif _G.SelectIsland == "Castle On The Sea" then
				topos(CFrame.new(-5074.45556640625, 314.5155334472656, -2991.054443359375))
			elseif _G.SelectIsland == "MiniSky" then
				topos(CFrame.new(-260.65557861328, 49325.8046875, -35253.5703125))
			elseif _G.SelectIsland == "Port Town" then
				topos(CFrame.new(-290.7376708984375, 6.729952812194824, 5343.5537109375))
			elseif _G.SelectIsland == "Hydra Island" then
				topos(CFrame.new(5228.8842773438, 604.23400878906, 345.0400390625))
			elseif _G.SelectIsland == "Floating Turtle" then
				topos(CFrame.new(-13274.528320313, 531.82073974609, -7579.22265625))
			elseif _G.SelectIsland == "Mansion" then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-12471.169921875, 374.94024658203, -7551.677734375))
			elseif _G.SelectIsland == "Haunted Castle" then
				topos(CFrame.new(-9515.3720703125, 164.00624084473, 5786.0610351562))
			elseif _G.SelectIsland == "Ice Cream Island" then
				topos(CFrame.new(-902.56817626953, 79.93204498291, -10988.84765625))
			elseif _G.SelectIsland == "Peanut Island" then
				topos(CFrame.new(-2062.7475585938, 50.473892211914, -10232.568359375))
			elseif _G.SelectIsland == "Cake Island" then
				topos(CFrame.new(-1884.7747802734375, 19.327526092529297, -11666.8974609375))
			elseif _G.SelectIsland == "Sea to Treats New" then
				topos(CFrame.new(-1141.0223388671875, 47.25519561767578, -14204.609375))	
			end
		until not _G.TeleportIsland
	end
	StopTween(_G.TeleportIsland)
end)

btna:Button("ความเร็วรถสูง(ใช้ได้ทุกแมพ)", function()
local UserInputService = game:GetService("UserInputService")
     local GuiService = game:GetService("GuiService")
     local LocalPlayer = game:GetService("Players").LocalPlayer
     
     local intens = 500 --set speed boost
     
     vehicleloopspeed = game:GetService("RunService").Stepped:Connect(function()
            local Humanoid = workspace.CurrentCamera.CameraSubject;
            if Humanoid:IsA("Humanoid") then
                Humanoid.SeatPart:ApplyImpulse(Humanoid.SeatPart.CFrame.LookVector * Vector3.new(intens, intens, intens))
            elseif Humanoid:IsA("BasePart") then
                Humanoid:ApplyImpulse(Humanoid.CFrame.LookVector * Vector3.new(intens, intens, intens))
            end
     end)
end)

btna:Button("สตริปไรไม่รุ้", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/zephyr10101/MultiToolsV1/main/script"))()
end)

btna:Button("สคริปควบคุมมอน (กดไปที่มอนและขะควบคุมทันที", function()
loadstring(game:HttpGet(('https://pastefy.app/x8nWWq0M/raw'),true))()
end)

btna:Button("ชิปล็อค", function()
----[[subscribe to ghacks script 


loadstring(game:HttpGet("https://raw.githubusercontent.com/MiniNoobie/ShiftLockx/main/Shiftlock-MiniNoobie",true))()  
end)

btna:Button("Script troll gui ", function()
loadstring(game:HttpGet("https://pastebin.com/raw/hiUAhj8w"))()
end)

btna:Button("ดึงของที่ผู้เล่นคนอื่นทิ้ง", function(speaker)
local humanoid = speaker.Character:FindFirstChildWhichIsA("Humanoid")
	for _, child in ipairs(workspace:GetChildren()) do
		if speaker.Character and child:IsA("BackpackItem") and child:FindFirstChild("Handle") then
			humanoid:EquipTool(child)
		end
	end

	if grabtoolsFunc then 
		grabtoolsFunc:Disconnect() 
	end

	grabtoolsFunc = workspace.ChildAdded:Connect(function(child)
		if speaker.Character and child:IsA("BackpackItem") and child:FindFirstChild("Handle") then
			humanoid:EquipTool(child)
		end
	end)
end)

btna:Button("ยกเลิกดึงของ", function()
if grabtoolsFunc then 
    grabtoolsFunc:Disconnect() 
end
end)

btna:Button("ประชิดตัวใครคนนั้น กระเด็น ", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/0Ben1/fe./main/Fling%20GUI"))()
end)

btna:Button("บิน", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/XNEOFF/FlyGuiV3/main/FlyGuiV3.txt"))()
end)

btna:Button("ไอเท็มต่อยหมดไม่สนลูกใคร", function()
loadstring(game:HttpGet("https://raw.githubusercontent.com/fedoratums/Base-Script/Base-Script/fedoratum punch fling",true))()
end)

btna:Button("ไอเท็มโกง ใช้กับมอนได้ทุกชนิด ควบคุม พลังจิต", function()
-- Press a block to pick it (ignores anchored blocks) (there is a thing called network ownership so you cannot pick it but works on games sometimes like da hood)
-- Long Press - Flings a block (power is customizable at line 19)
-- Unequip  - Releases a block

-- Create a ScreenGui to hold the GUI elements


Range = "Min" -- "Min" (idk), "Max" (lag), "Default" (fastest)

local BP = Instance.new("BodyPosition")
BP.maxForce = Vector3.new(math.huge * math.huge, math.huge * math.huge, math.huge * math.huge)
BP.P = BP.P * 1.1

local BP = Instance.new("BodyPosition")
BP.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
BP.Position = BP.Position + Vector3.new(0, 0.1, 0)

task.spawn(function()
game:GetService("RunService").RenderStepped:Connect(function()
if Range == "Max" then
sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", 0)
elseif Range == "Min" then
sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", 500)
end
end)
end)

local function a(b, c)
    local d = getfenv(c)
    local e =
        setmetatable(
        {},
        {__index = function(self, f)
                if f == "script" then
                    return b
                else
                    return d[f]
                end
            end}
    )
    setfenv(c, e)
    return c
end
local power = 1000*2000*3000*4000*5000*6000*7000*8000*9000*10000*100000*100000000*999926477847573859723*99999999999999999999999999999999999999999
local usrinput = game:GetService("UserInputService")
local g = {}
local h = Instance.new("Model", game:GetService("Lighting"))
local i = Instance.new("Tool")
local j = Instance.new("Part")
local k = Instance.new("Script")
local l = Instance.new("LocalScript")
local m = sethiddenproperty or set_hidden_property
i.Name = "Telekinesis"
i.Parent = h
i.Grip = CFrame.new(0, 0, 0, 0, 1, 0, 0, 0, 1, 1, 0, 0)
i.GripForward = Vector3.new(-0, -1, -0)
i.GripRight = Vector3.new(0, 0, 1)
i.GripUp = Vector3.new(1, 0, 0)
j.Name = "Handle"
j.Parent = i
j.CFrame = CFrame.new(-17.2635937, 15.4915619, 46, 0, 1, 0, 1, 0, 0, 0, 0, -1)
j.Orientation = Vector3.new(0, 180, 90)
j.Position = Vector3.new(-17.2635937, 15.4915619, 46)
j.Rotation = Vector3.new(-180, 0, -90)
j.Color = Color3.new(0.0666667, 0.0666667, 0.0666667)
j.Transparency = 1
j.Size = Vector3.new(1, 1.20000005, 1)
j.BottomSurface = Enum.SurfaceType.Weld
j.BrickColor = BrickColor.new("Really black")
j.Material = Enum.Material.Metal
j.TopSurface = Enum.SurfaceType.Smooth
j.brickColor = BrickColor.new("Really black")
k.Name = "LineConnect"
k.Parent = i
table.insert(
    g,
    a(
        k,
        function()
            wait()
            local n = script.Part2
            local o = script.Part1.Value
            local p = script.Part2.Value
            local q = script.Par.Value
            local color = script.Color
            local r = Instance.new("Part")
            r.TopSurface = 0
            r.BottomSurface = 0
            r.Reflectance = .5
            r.Name = "Laser"
            r.Locked = true
            r.CanCollide = false
            r.Anchored = true
            r.formFactor = 0
            r.Size = Vector3.new(1, 1, 1)
            local s = Instance.new("BlockMesh")
            s.Parent = r
            while true do
                if n.Value == nil then
                    break
                end
                if o == nil or p == nil or q == nil then
                    break
                end
                if o.Parent == nil or p.Parent == nil then
                    break
                end
                if q.Parent == nil then
                    break
                end
                local t = CFrame.new(o.Position, p.Position)
                local dist = (o.Position - p.Position).magnitude
                r.Parent = q
                r.BrickColor = color.Value.BrickColor
                r.Reflectance = color.Value.Reflectance
                r.Transparency = color.Value.Transparency
                r.CFrame = CFrame.new(o.Position + t.lookVector * dist / 2)
                r.CFrame = CFrame.new(r.Position, p.Position)
                s.Scale = Vector3.new(.25, .25, dist)
                wait()
            end
            r:remove()
            script:remove()
        end
    )
)
k.Disabled = true
l.Name = "MainScript"
l.Parent = i
table.insert(
    g,
    a(
        l,
        function()
            wait()
            tool = script.Parent
            lineconnect = tool.LineConnect
            object = nil
            mousedown = false
            found = false
            BP = Instance.new("BodyPosition")
            BP.maxForce = Vector3.new(math.huge * math.huge, math.huge * math.huge, math.huge * math.huge)
            BP.P = BP.P * 2
            dist = nil
            point = Instance.new("Part")
            point.Locked = true
            point.Anchored = true
            point.formFactor = 0
            point.Shape = 0
            point.BrickColor = BrickColor.Black()
            point.Size = Vector3.new(1, 1, 1)
            point.CanCollide = false
            local s = Instance.new("SpecialMesh")
            s.MeshType = "Sphere"
            s.Scale = Vector3.new(.7, .7, .7)
            s.Parent = point
            handle = tool.Handle
            front = tool.Handle
            color = tool.Handle
            objval = nil
            local u = false
            local v = BP:clone()
            v.maxForce = Vector3.new(30000, 30000, 30000)
            function LineConnect(o, p, q)
                local w = Instance.new("ObjectValue")
                w.Value = o
                w.Name = "Part1"
                local x = Instance.new("ObjectValue")
                x.Value = p
                x.Name = "Part2"
                local y = Instance.new("ObjectValue")
                y.Value = q
                y.Name = "Par"
                local z = Instance.new("ObjectValue")
                z.Value = color
                z.Name = "Color"
                local A = lineconnect:clone()
                A.Disabled = false
                w.Parent = A
                x.Parent = A
                y.Parent = A
                z.Parent = A
                A.Parent = workspace
                if p == object then
                    objval = x
                end
            end
            function onButton1Down(B)
                if mousedown == true then
                    return
                end
                mousedown = true
                coroutine.resume(
                    coroutine.create(
                        function()
                            local C = point:clone()
                            C.Parent = tool
                            LineConnect(front, C, workspace)
                            while mousedown == true do
                                C.Parent = tool
                                if object == nil then
                                    if B.Target == nil then
                                        local t = CFrame.new(front.Position, B.Hit.p)
                                        C.CFrame = CFrame.new(front.Position + t.lookVector * 1000)
                                    else
                                        C.CFrame = CFrame.new(B.Hit.p)
                                    end
                                else
                                    LineConnect(front, object, workspace)
                                    break
                                end
                                wait()
                            end
                            C:remove()
                        end
                    )
                )
                while mousedown == true do
                    if B.Target ~= nil then
                        local D = B.Target
                        if D.Anchored == false then
                            object = D
                            dist = (object.Position - front.Position).magnitude
                            break
                        end
                    end
                    wait()
                end
                while mousedown == true do
                    if object.Parent == nil then
                        break
                    end
                    local t = CFrame.new(front.Position, B.Hit.p)
                    BP.Parent = object
                    BP.position = front.Position + t.lookVector * dist
                    wait()
                end
                BP:remove()
                object = nil
                objval.Value = nil
            end
            function onKeyDown(E, B)
                local E = E:lower()
                local F = false
                if E == "q" then
                    if dist >= 5 then
                        dist = dist - 10
                    end
                end
                if E == "r" then
                    if object == nil then
                        return
                    end
                    for G, H in pairs(object:children()) do
                        if H.className == "BodyGyro" then
                            return nil
                        end
                    end
                    BG = Instance.new("BodyGyro")
                    BG.maxTorque = Vector3.new(math.huge, math.huge, math.huge)
                    BG.cframe = CFrame.new(object.CFrame.p)
                    BG.Parent = object
                    repeat
                        wait()
                    until object.CFrame == CFrame.new(object.CFrame.p)
                    BG.Parent = nil
                    if object == nil then
                        return
                    end
                    for G, H in pairs(object:children()) do
                        if H.className == "BodyGyro" then
                            H.Parent = nil
                        end
                    end
                    object.Velocity = Vector3.new(0, 0, 0)
                    object.RotVelocity = Vector3.new(0, 0, 0)
                    object.Orientation = Vector3.new(0, 0, 0)
                end
                if E == "e" then
                    dist = dist + 10
                end
                if E == "t" then
                    if dist ~= 10 then
                        dist = 10
                    end
                end
                if E == "y" then
                    if dist ~= 200 then
                        dist = 200
                    end
                end
                if E == "=" then
                    BP.P = BP.P * 1.5
                end
                if E == "-" then
                    BP.P = BP.P * 0.5
                end
            end
            function onEquipped(B)
                touched = false
                uneq = false
                keymouse = B
                local I = tool.Parent
                human = I.Humanoid
                human.Changed:connect(
                    function()
                        if human.Health == 0 then
                            mousedown = false
                            uneq = true
                            touched = false
                            BP:remove()
                            point:remove()
                            tool:remove()
                        end
                    end
                )
                usrinput.TouchTapInWorld:connect(
                    function()
                        if uneq == false then
                        if touched == false then
                        onButton1Down(B)
                        touched = true
                        elseif touched == true then
                        touched = false
                        end
                        end
                    end
                )
                usrinput.TouchLongPress:connect(function()
                    if uneq == false then
                        if dist ~= power then
                            dist = power
                        end
                    end
                end)
                B.KeyDown:connect(
                    function(E)
                        onKeyDown(E, B)
                    end
                )
                B.Icon = "rbxasset://textures\\GunCursor.png"
            end
            tool.Equipped:connect(onEquipped)
            tool.Unequipped:connect(function() uneq = true touched = false mousedown = false end)
        end
    )
)
for J, H in pairs(h:GetChildren()) do
    H.Parent = game:GetService("Players").LocalPlayer.Backpack
    pcall(
        function()
            H:MakeJoints()
        end
    )
end
h:Destroy()
for J, H in pairs(g) do
    spawn(
        function()
            pcall(H)
        end
    )
end
end)

btna:Button("ทำให้มอนหยุดเดิน ใน ระยะ 35 ก้าว GUI", function()
local Workspace = game:GetService("Workspace")
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local Noclip = Instance.new("ScreenGui")
local BG = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Toggle = Instance.new("TextButton")
local StatusPF = Instance.new("TextLabel")
local Status = Instance.new("TextLabel")
local Credit = Instance.new("TextLabel")
local Plr = Players.LocalPlayer
local Clipon1 = false
Cooldown1 = .0*.0*.0*.0

Noclip.Name = "stop monter Script"
Noclip.Parent = game.CoreGui

BG.Name = "BG"
BG.Parent = Noclip
BG.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
BG.BorderColor3 = Color3.new(0.0588235, 0.0588235, 0.0588235)
BG.BorderSizePixel = 2
BG.Position = UDim2.new(0.149479166, 0, 0.82087779, 0)
BG.Size = UDim2.new(0, 210, 0, 127)
BG.Active = true
BG.Draggable = true

Title.Name = "Title"
Title.Parent = BG
Title.BackgroundColor3 = Color3.new(13, 105, 172)
Title.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Title.BorderSizePixel = 2
Title.Size = UDim2.new(0, 210, 0, 33)
Title.Font = Enum.Font.Highway
Title.Text = "stop monster walk and stop jump op"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.FontSize = Enum.FontSize.Size32
Title.TextSize = 30
Title.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Title.TextStrokeTransparency = 0

Toggle.Parent = BG
Toggle.BackgroundColor3 = Color3.new(123, 182, 232)
Toggle.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.BorderSizePixel = 2
Toggle.Position = UDim2.new(0.152380958, 0, 0.374192119, 0)
Toggle.Size = UDim2.new(0, 146, 0, 36)
Toggle.Font = Enum.Font.Highway
Toggle.FontSize = Enum.FontSize.Size28
Toggle.Text = "stop toggle"
Toggle.TextColor3 = Color3.new(1, 1, 1)
Toggle.TextSize = 25
Toggle.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.TextStrokeTransparency = 0

StatusPF.Name = "StatusPF"
StatusPF.Parent = BG
StatusPF.BackgroundColor3 = Color3.new(1, 1, 1)
StatusPF.BackgroundTransparency = 1
StatusPF.Position = UDim2.new(0.314285725, 0, 0.708661377, 0)
StatusPF.Size = UDim2.new(0, 56, 0, 20)
StatusPF.Font = Enum.Font.Highway
StatusPF.FontSize = Enum.FontSize.Size24
StatusPF.Text = "Status:"
StatusPF.TextColor3 = Color3.new(1, 1, 1)
StatusPF.TextSize = 20
StatusPF.TextStrokeColor3 = Color3.new(0.333333, 0.333333, 0.333333)
StatusPF.TextStrokeTransparency = 0
StatusPF.TextWrapped = true

Status.Name = "Status"
Status.Parent = BG
Status.BackgroundColor3 = Color3.new(1, 1, 1)
Status.BackgroundTransparency = 1
Status.Position = UDim2.new(0.580952346, 0, 0.708661377, 0)
Status.Size = UDim2.new(0, 56, 0, 20)
Status.Font = Enum.Font.Highway
Status.FontSize = Enum.FontSize.Size14
Status.Text = "off"
Status.TextColor3 = Color3.new(0.666667, 0, 0)
Status.TextScaled = true
Status.TextSize = 14
Status.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Status.TextWrapped = true
Status.TextXAlignment = Enum.TextXAlignment.Left

Credit.Name = "Credit"
Credit.Parent = BG
Credit.BackgroundColor3 = Color3.new(1, 1, 1)
Credit.BackgroundTransparency = 1
Credit.Position = UDim2.new(0.195238099, 0, 0.866141737, 0)
Credit.Size = UDim2.new(0, 128, 0, 17)
Credit.Font = Enum.Font.SourceSans
Credit.FontSize = Enum.FontSize.Size18
Credit.Text = "by sazx hub"
Credit.TextColor3 = Color3.new(1, 1, 1)
Credit.TextSize = 16
Credit.TextStrokeColor3 = Color3.new(0.196078, 0.196078, 0.196078)
Credit.TextStrokeTransparency = 0
Credit.TextWrapped = true
Toggle.MouseButton1Click:connect(function()
    if Status.Text == "off" then
        Clipon1 = true
        Status.Text = "on"
        Status.TextColor3 = Color3.new(0, 185, 0)
        
        -- เพิ่มลูป while นี้
local Cooldown = 0.2 -- ปรับเวลาให้เหมาะสม

while Clipon1 do
    ypcall(function()
        wait(Cooldown1)
        local player = game.Players.LocalPlayer
        local playerPos = player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.HumanoidRootPart.Position

        if playerPos then
            local allPlayers = game.Players:GetPlayers()

            for _, v in pairs(game:GetService("Workspace"):GetDescendants()) do
                if v:IsA("Model") and v:FindFirstChild("HumanoidRootPart") and not v:IsA("Player") then
                    local humanoidRootPart = v:FindFirstChild("HumanoidRootPart")
                    local mobPos = humanoidRootPart.Position

                    local isScriptRunner = v == player.Character
                    local isOtherPlayer = false

                    for _, otherPlayer in ipairs(allPlayers) do
                        if v == otherPlayer.Character then
                            isOtherPlayer = true
                            break
                        end
                    end

                    -- ตรวจสอบว่า v ไม่ใช่ตัวเอง และไม่ใช่ผู้เล่นคนอื่น
                    if mobPos and (playerPos - mobPos).Magnitude <= 35 and not isScriptRunner and not isOtherPlayer then
                        humanoidRootPart.Size = Vector3.new(0, 0, 0)
                        humanoidRootPart.Transparency = 0.5
                        humanoidRootPart.CanCollide = false

                        local humanoid = v:FindFirstChildOfClass("Humanoid")
                        if humanoid then
                            humanoid.WalkSpeed = 0
                            humanoid.JumpPower = 0
                        end

                        if sethiddenproperty then
                            sethiddenproperty(player, "SimulationRadius", math.huge)
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        end
                    end
                end
            end
        end
    end)
end
    else
        Clipon1 = false
        Status.Text = "off"
        Status.TextColor3 = Color3.new(170, 0, 0)
    end
end)
end)

btna:Button("พลังจิตทำให้มอนอยู่กับทีี. v2", function()
local Workspace = game:GetService("Workspace")
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local Noclip = Instance.new("ScreenGui")
local BG = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Toggle = Instance.new("TextButton")
local StatusPF = Instance.new("TextLabel")
local Status = Instance.new("TextLabel")
local Credit = Instance.new("TextLabel")
local Plr = Players.LocalPlayer
local Clipon2 = false

Noclip.Name = "stop monter Script"
Noclip.Parent = game.CoreGui

BG.Name = "BG"
BG.Parent = Noclip
BG.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
BG.BorderColor3 = Color3.new(0.0588235, 0.0588235, 0.0588235)
BG.BorderSizePixel = 2
BG.Position = UDim2.new(0.149479166, 0, 0.82087779, 0)
BG.Size = UDim2.new(0, 210, 0, 127)
BG.Active = true
BG.Draggable = true

Title.Name = "Title"
Title.Parent = BG
Title.BackgroundColor3 = Color3.new(13, 105, 172)
Title.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Title.BorderSizePixel = 2
Title.Size = UDim2.new(0, 210, 0, 33)
Title.Font = Enum.Font.Highway
Title.Text = "stop monster walk and stop jump op v2"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.FontSize = Enum.FontSize.Size32
Title.TextSize = 30
Title.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Title.TextStrokeTransparency = 0

Toggle.Parent = BG
Toggle.BackgroundColor3 = Color3.new(123, 182, 232)
Toggle.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.BorderSizePixel = 2
Toggle.Position = UDim2.new(0.152380958, 0, 0.374192119, 0)
Toggle.Size = UDim2.new(0, 146, 0, 36)
Toggle.Font = Enum.Font.Highway
Toggle.FontSize = Enum.FontSize.Size28
Toggle.Text = "stop toggle"
Toggle.TextColor3 = Color3.new(1, 1, 1)
Toggle.TextSize = 25
Toggle.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.TextStrokeTransparency = 0

StatusPF.Name = "StatusPF"
StatusPF.Parent = BG
StatusPF.BackgroundColor3 = Color3.new(1, 1, 1)
StatusPF.BackgroundTransparency = 1
StatusPF.Position = UDim2.new(0.314285725, 0, 0.708661377, 0)
StatusPF.Size = UDim2.new(0, 56, 0, 20)
StatusPF.Font = Enum.Font.Highway
StatusPF.FontSize = Enum.FontSize.Size24
StatusPF.Text = "Status:"
StatusPF.TextColor3 = Color3.new(1, 1, 1)
StatusPF.TextSize = 20
StatusPF.TextStrokeColor3 = Color3.new(0.333333, 0.333333, 0.333333)
StatusPF.TextStrokeTransparency = 0
StatusPF.TextWrapped = true

Status.Name = "Status"
Status.Parent = BG
Status.BackgroundColor3 = Color3.new(1, 1, 1)
Status.BackgroundTransparency = 1
Status.Position = UDim2.new(0.580952346, 0, 0.708661377, 0)
Status.Size = UDim2.new(0, 56, 0, 20)
Status.Font = Enum.Font.Highway
Status.FontSize = Enum.FontSize.Size14
Status.Text = "off"
Status.TextColor3 = Color3.new(0.666667, 0, 0)
Status.TextScaled = true
Status.TextSize = 14
Status.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Status.TextWrapped = true
Status.TextXAlignment = Enum.TextXAlignment.Left

Credit.Name = "Credit"
Credit.Parent = BG
Credit.BackgroundColor3 = Color3.new(1, 1, 1)
Credit.BackgroundTransparency = 1
Credit.Position = UDim2.new(0.195238099, 0, 0.866141737, 0)
Credit.Size = UDim2.new(0, 128, 0, 17)
Credit.Font = Enum.Font.SourceSans
Credit.FontSize = Enum.FontSize.Size18
Credit.Text = "by sazx hub"
Credit.TextColor3 = Color3.new(1, 1, 1)
Credit.TextSize = 16
Credit.TextStrokeColor3 = Color3.new(0.196078, 0.196078, 0.196078)
Credit.TextStrokeTransparency = 0
Credit.TextWrapped = true
Toggle.MouseButton1Click:connect(function()
    if Status.Text == "off" then
        Clipon2 = true
        Status.Text = "on"
        Status.TextColor3 = Color3.new(0, 185, 0)
        
        -- เพิ่มลูป while นี้
local Cooldown2 = .0*.0*.0 -- ปรับเวลาให้เหมาะสม

while Clipon2 do
    pcall(function()
        wait(Cooldown2)
        local player = game.Players.LocalPlayer
        local playerPos = player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.HumanoidRootPart.Position

        if playerPos then
            local allPlayers = game.Players:GetPlayers()

            for _, v in pairs(game:GetService("Workspace"):GetDescendants()) do
                if v:IsA("Model") and v:FindFirstChild("HumanoidRootPart") and not v:IsA("Player") then
                    local humanoidRootPart = v:FindFirstChild("HumanoidRootPart")
                    local mobPos = humanoidRootPart.Position

                    local isScriptRunner = v == player.Character
                    local isOtherPlayer = false

                    for _, otherPlayer in ipairs(allPlayers) do
                        if v == otherPlayer.Character then
                            isOtherPlayer = true
                            break
                        end
                    end

                    -- ตรวจสอบว่า v ไม่ใช่ตัวเอง และไม่ใช่ผู้เล่นคนอื่น
                    if mobPos and (playerPos - mobPos).Magnitude <= 35 and not isScriptRunner and not isOtherPlayer then
                        humanoidRootPart.Size = Vector3.new(4, 4, 4)
                        humanoidRootPart.Transparency = 0.5
                        humanoidRootPart.CanCollide = false
                        
                        humanoidRootPart.CFrame = CFrame.new(humanoidRootPart.Position)

                        local humanoid = v:FindFirstChildOfClass("Humanoid")
                        if humanoid then
                            humanoidRootPart.CFrame = CFrame.new(humanoidRootPart.Position)
                        end

                        if sethiddenproperty then
                            sethiddenproperty(player, "SimulationRadius", math.huge)
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        end
                    end
                end
            end
        end
    end)
end
    else
        Clipon2 = false
        Status.Text = "off"
        Status.TextColor3 = Color3.new(170, 0, 0)
    end
end)
end)

btna:Button("สคริปไอเท็ม ควบคุม part", function()
loadstring(game:HttpGet(('https://pastefy.app/Vcuyg09O/raw'),true))()
end)

btna:Button("พามอนสเตอร์ไปโลกความตาย", function()
local Workspace = game:GetService("Workspace")
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local Noclip = Instance.new("ScreenGui")
local BG = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Toggle = Instance.new("TextButton")
local StatusPF = Instance.new("TextLabel")
local Status = Instance.new("TextLabel")
local Credit = Instance.new("TextLabel")
local Plr = Players.LocalPlayer
local Clipon3 = false

Noclip.Name = "stop monter Script"
Noclip.Parent = game.CoreGui

BG.Name = "BG"
BG.Parent = Noclip
BG.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
BG.BorderColor3 = Color3.new(0.0588235, 0.0588235, 0.0588235)
BG.BorderSizePixel = 2
BG.Position = UDim2.new(0.149479166, 0, 0.82087779, 0)
BG.Size = UDim2.new(0, 210, 0, 127)
BG.Active = true
BG.Draggable = true

Title.Name = "Title"
Title.Parent = BG
Title.BackgroundColor3 = Color3.new(13, 105, 172)
Title.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Title.BorderSizePixel = 2
Title.Size = UDim2.new(0, 210, 0, 33)
Title.Font = Enum.Font.Highway
Title.Text = "monster goto void (bypass 69%)"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.FontSize = Enum.FontSize.Size32
Title.TextSize = 30
Title.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Title.TextStrokeTransparency = 0

Toggle.Parent = BG
Toggle.BackgroundColor3 = Color3.new(123, 182, 232)
Toggle.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.BorderSizePixel = 2
Toggle.Position = UDim2.new(0.152380958, 0, 0.374192119, 0)
Toggle.Size = UDim2.new(0, 146, 0, 36)
Toggle.Font = Enum.Font.Highway
Toggle.FontSize = Enum.FontSize.Size28
Toggle.Text = " toggle"
Toggle.TextColor3 = Color3.new(1, 1, 1)
Toggle.TextSize = 25
Toggle.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.TextStrokeTransparency = 0

StatusPF.Name = "StatusPF"
StatusPF.Parent = BG
StatusPF.BackgroundColor3 = Color3.new(1, 1, 1)
StatusPF.BackgroundTransparency = 1
StatusPF.Position = UDim2.new(0.314285725, 0, 0.708661377, 0)
StatusPF.Size = UDim2.new(0, 56, 0, 20)
StatusPF.Font = Enum.Font.Highway
StatusPF.FontSize = Enum.FontSize.Size24
StatusPF.Text = "Status:"
StatusPF.TextColor3 = Color3.new(1, 1, 1)
StatusPF.TextSize = 20
StatusPF.TextStrokeColor3 = Color3.new(0.333333, 0.333333, 0.333333)
StatusPF.TextStrokeTransparency = 0
StatusPF.TextWrapped = true

Status.Name = "Status"
Status.Parent = BG
Status.BackgroundColor3 = Color3.new(1, 1, 1)
Status.BackgroundTransparency = 1
Status.Position = UDim2.new(0.580952346, 0, 0.708661377, 0)
Status.Size = UDim2.new(0, 56, 0, 20)
Status.Font = Enum.Font.Highway
Status.FontSize = Enum.FontSize.Size14
Status.Text = "off"
Status.TextColor3 = Color3.new(0.666667, 0, 0)
Status.TextScaled = true
Status.TextSize = 14
Status.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Status.TextWrapped = true
Status.TextXAlignment = Enum.TextXAlignment.Left

Credit.Name = "Credit"
Credit.Parent = BG
Credit.BackgroundColor3 = Color3.new(1, 1, 1)
Credit.BackgroundTransparency = 1
Credit.Position = UDim2.new(0.195238099, 0, 0.866141737, 0)
Credit.Size = UDim2.new(0, 128, 0, 17)
Credit.Font = Enum.Font.SourceSans
Credit.FontSize = Enum.FontSize.Size18
Credit.Text = "by sazx hub"
Credit.TextColor3 = Color3.new(1, 1, 1)
Credit.TextSize = 16
Credit.TextStrokeColor3 = Color3.new(0.196078, 0.196078, 0.196078)
Credit.TextStrokeTransparency = 0
Credit.TextWrapped = true
Toggle.MouseButton1Click:connect(function()
    if Status.Text == "off" then
        Clipon3 = true
        Status.Text = "on"
        Status.TextColor3 = Color3.new(0, 185, 0)
        
        -- เพิ่มลูป while นี้
local Cooldown3 = .0*.0*.0 -- ปรับเวลาให้เหมาะสม

while Clipon3 do
    pcall(function()
        wait(Cooldown3)
        local player = game.Players.LocalPlayer
        local playerPos = player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.HumanoidRootPart.Position

        if playerPos then
            local allPlayers = game.Players:GetPlayers()

            for _, v in pairs(game:GetService("Workspace"):GetDescendants()) do
                if v:IsA("Model") and v:FindFirstChild("HumanoidRootPart") and not v:IsA("Player") then
                    local humanoidRootPart = v:FindFirstChild("HumanoidRootPart")
                    local mobPos = humanoidRootPart.Position

                    local isScriptRunner = v == player.Character
                    local isOtherPlayer = false

                    for _, otherPlayer in ipairs(allPlayers) do
                        if v == otherPlayer.Character then
                            isOtherPlayer = true
                            break
                        end
                    end

                    -- ตรวจสอบว่า v ไม่ใช่ตัวเอง และไม่ใช่ผู้เล่นคนอื่น
                    if mobPos and (playerPos - mobPos).Magnitude <= 20 and not isScriptRunner and not isOtherPlayer then
                        humanoidRootPart.Size = Vector3.new(0, 0, 0)
                        humanoidRootPart.Transparency = 0.5
                        humanoidRootPart.CanCollide = false

                        local humanoid = v:FindFirstChildOfClass("Humanoid")
                        if humanoid then
                            humanoid.WalkSpeed = 0
                            humanoid.JumpPower = 0
                        end

                        -- เพิ่มส่วนนี้เพื่อทำให้มอนสเตอร์วาปไปยัง CFrame ที่ระบุ
                        local teleportCFrame = CFrame.new(-999, -50, -50)
                        v:SetPrimaryPartCFrame(teleportCFrame)

                        if sethiddenproperty then
                            sethiddenproperty(player, "SimulationRadius", math.huge)
                            sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        end
                    end
                end
            end
        end
    end)
end
    else
        Clipon3 = false
        Status.Text = "off"
        Status.TextColor3 = Color3.new(170, 0, 0)
    end
end)
end)

btna:Button("สคริปฆ่าแบบอาณาเขตมอนสเตอร์ตายทุกตัว", function()
local Workspace = game:GetService("Workspace")
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local Noclip = Instance.new("ScreenGui")
local BG = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Toggle = Instance.new("TextButton")
local StatusPF = Instance.new("TextLabel")
local Status = Instance.new("TextLabel")
local Credit = Instance.new("TextLabel")
local Plr = Players.LocalPlayer
local player = game.Players.LocalPlayer
local Clipon5 = false

Noclip.Name = "stop monter Script"
Noclip.Parent = game.CoreGui

BG.Name = "BG"
BG.Parent = Noclip
BG.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
BG.BorderColor3 = Color3.new(0.0588235, 0.0588235, 0.0588235)
BG.BorderSizePixel = 2
BG.Position = UDim2.new(0.149479166, 0, 0.82087779, 0)
BG.Size = UDim2.new(0, 210, 0, 127)
BG.Active = true
BG.Draggable = true

Title.Name = "Title"
Title.Parent = BG
Title.BackgroundColor3 = Color3.new(13, 105, 172)
Title.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Title.BorderSizePixel = 2
Title.Size = UDim2.new(0, 210, 0, 33)
Title.Font = Enum.Font.Highway
Title.Text = "kill arua monster"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.FontSize = Enum.FontSize.Size32
Title.TextSize = 30
Title.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Title.TextStrokeTransparency = 0

Toggle.Parent = BG
Toggle.BackgroundColor3 = Color3.new(123, 182, 232)
Toggle.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.BorderSizePixel = 2
Toggle.Position = UDim2.new(0.152380958, 0, 0.374192119, 0)
Toggle.Size = UDim2.new(0, 146, 0, 36)
Toggle.Font = Enum.Font.Highway
Toggle.FontSize = Enum.FontSize.Size28
Toggle.Text = "stop toggle"
Toggle.TextColor3 = Color3.new(1, 1, 1)
Toggle.TextSize = 25
Toggle.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.TextStrokeTransparency = 0

StatusPF.Name = "StatusPF"
StatusPF.Parent = BG
StatusPF.BackgroundColor3 = Color3.new(1, 1, 1)
StatusPF.BackgroundTransparency = 1
StatusPF.Position = UDim2.new(0.314285725, 0, 0.708661377, 0)
StatusPF.Size = UDim2.new(0, 56, 0, 20)
StatusPF.Font = Enum.Font.Highway
StatusPF.FontSize = Enum.FontSize.Size24
StatusPF.Text = "Status:"
StatusPF.TextColor3 = Color3.new(1, 1, 1)
StatusPF.TextSize = 20
StatusPF.TextStrokeColor3 = Color3.new(0.333333, 0.333333, 0.333333)
StatusPF.TextStrokeTransparency = 0
StatusPF.TextWrapped = true

Status.Name = "Status"
Status.Parent = BG
Status.BackgroundColor3 = Color3.new(1, 1, 1)
Status.BackgroundTransparency = 1
Status.Position = UDim2.new(0.580952346, 0, 0.708661377, 0)
Status.Size = UDim2.new(0, 56, 0, 20)
Status.Font = Enum.Font.Highway
Status.FontSize = Enum.FontSize.Size14
Status.Text = "off"
Status.TextColor3 = Color3.new(0.666667, 0, 0)
Status.TextScaled = true
Status.TextSize = 14
Status.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Status.TextWrapped = true
Status.TextXAlignment = Enum.TextXAlignment.Left

Credit.Name = "Credit"
Credit.Parent = BG
Credit.BackgroundColor3 = Color3.new(1, 1, 1)
Credit.BackgroundTransparency = 1
Credit.Position = UDim2.new(0.195238099, 0, 0.866141737, 0)
Credit.Size = UDim2.new(0, 128, 0, 17)
Credit.Font = Enum.Font.SourceSans
Credit.FontSize = Enum.FontSize.Size18
Credit.Text = "by sazx hub"
Credit.TextColor3 = Color3.new(1, 1, 1)
Credit.TextSize = 16
Credit.TextStrokeColor3 = Color3.new(0.196078, 0.196078, 0.196078)
Credit.TextStrokeTransparency = 0
Credit.TextWrapped = true
Toggle.MouseButton1Click:connect(function()
    if Status.Text == "off" then
        Clipon5 = true
        Status.Text = "on"
        Status.TextColor3 = Color3.new(0, 185, 0)
        
        -- เพิ่มลูป while นี้

while Clipon5 do
    ypcall(function()
        wait(0.5)
    sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", 10000)
    sethiddenproperty(game.Players.LocalPlayer, "MaxSimulationRadius", 1000)
    
    for _, d in pairs(game:GetService("Workspace"):GetDescendants()) do
        if d:IsA('Model') and d:FindFirstChildOfClass('Humanoid') and d.Name ~= player.Name then
            d:FindFirstChildOfClass('Humanoid').Health = -1
        end
    end

    wait(0.50) -- รอ 0.5 วินาที

    for _, d in pairs(game:GetService("Workspace"):GetDescendants()) do
        if d:IsA('Model') and d:FindFirstChildOfClass('Humanoid') and d.Name ~= player.Name then
            d:FindFirstChildOfClass('Humanoid').Health = 100
            local hitbox = Instance.new("Part")
            hitbox.Size = Vector3.new(0, 0, 0) -- ขนาดของ hitbox ของคุณ
            hitbox.Position = player.Character.HumanoidRootPart.Position -- ตำแหน่ง hitbox จะอยู่ที่ตัวละครของผู้เล่น
            hitbox.Anchored = true
            hitbox.CanCollide = false
            hitbox.Parent = game.Workspace
            
            -- ตั้งค่า hitbox ให้ทำลายอย่างเดียว
            hitbox.Touched:Connect(function(otherPart)
                local character = otherPart.Parent
                if character and character:FindFirstChild("Humanoid") and character.Name ~= player.Name then
                    character.Humanoid.Health = 0
                end
            end)
        end
    end
    end)
end
    else
        Clipon5 = false
        Status.Text = "off"
        Status.TextColor3 = Color3.new(170, 0, 0)
    end
end)
end)

btna:Button("sliem aim หยุดไม่ได้น่ะ แต่ดี ใช้ ได้ทักแมพ", function()
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local mouse = LocalPlayer:GetMouse()
local Camera = workspace.CurrentCamera
local Debris = game:GetService("Debris")
local UserInputService = game:GetService("UserInputService")
local target = nil
local RunService = game:GetService("RunService")

local features = {
    silentaim = true,
    fov = 500,
}

function getnearest()
    local nearestmagnitude = math.huge
    local nearestenemy = nil

    for i, v in pairs(Players:GetPlayers()) do
        if v ~= LocalPlayer and v.Character and v.Character:FindFirstChild("HumanoidRootPart") and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health > 0 then
            local vector, onScreen = Camera:WorldToScreenPoint(v.Character["HumanoidRootPart"].Position)

            if onScreen then
                local ray = Ray.new(
                    Camera.CFrame.Position,
                    (v.Character["Head"].Position - Camera.CFrame.Position).unit * 500
                )

                local ignore = {
                    LocalPlayer.Character,
                }

                local hit, position, normal = workspace:FindPartOnRayWithIgnoreList(ray, ignore)

                if hit and hit:FindFirstAncestorOfClass("Model") and Players:FindFirstChild(hit:FindFirstAncestorOfClass("Model").Name) then
                    local magnitude = (Vector2.new(mouse.X, mouse.Y) - Vector2.new(vector.X, vector.Y)).magnitude

                    if magnitude < nearestmagnitude and magnitude <= features["fov"] then
                        nearestenemy = v
                        nearestmagnitude = magnitude
                    end
                end
            end
        end
    end

    return nearestenemy
end

local meta = getrawmetatable(game)
setreadonly(meta, false)
local oldNamecall = meta.__namecall

meta.__namecall = newcclosure(function(...)
    local method = getnamecallmethod()
    local args = {...}

    if string.find(method,'Ray') then
        if target then
            args[2] = Ray.new(Camera.CFrame.Position, (target + Vector3.new(0, (Camera.CFrame.Position - target).Magnitude / 500, 0) - Camera.CFrame.Position).unit * 500)
        end
    end

    return oldNamecall(unpack(args))
end)

RunService:BindToRenderStep("silentaim", 1, function()
    if UserInputService:IsMouseButtonPressed(0) and features["silentaim"] and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") and LocalPlayer.Character.Humanoid.Health > 0 then
        local enemy = getnearest()

        if enemy and enemy.Character and enemy.Character:FindFirstChild("Humanoid") and enemy.Character.Humanoid.Health > 0 then
            local vector, onScreen = Camera:WorldToScreenPoint(enemy.Character["Head"].Position)
            local magnitude = (Vector2.new(mouse.X, mouse.Y) - Vector2.new(vector.X, vector.Y)).magnitude
            target = workspace[enemy.Name]["Head"].Position
        end
    else
        target = nil
    end
end)
end)

btna:Button("tween monster gui", function()
local Workspace = game:GetService("Workspace")
local CoreGui = game:GetService("CoreGui")
local Players = game:GetService("Players")
local Noclip = Instance.new("ScreenGui")
local BG = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Toggle = Instance.new("TextButton")
local StatusPF = Instance.new("TextLabel")
local Status = Instance.new("TextLabel")
local Credit = Instance.new("TextLabel")
local Plr = Players.LocalPlayer
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local Clipon4 = false
Cooldown4 = .0*.0*.0*.0

Noclip.Name = "stop monter Script"
Noclip.Parent = game.CoreGui

BG.Name = "BG"
BG.Parent = Noclip
BG.BackgroundColor3 = Color3.new(0.0980392, 0.0980392, 0.0980392)
BG.BorderColor3 = Color3.new(0.0588235, 0.0588235, 0.0588235)
BG.BorderSizePixel = 2
BG.Position = UDim2.new(0.149479166, 0, 0.82087779, 0)
BG.Size = UDim2.new(0, 210, 0, 127)
BG.Active = true
BG.Draggable = true

Title.Name = "Title"
Title.Parent = BG
Title.BackgroundColor3 = Color3.new(13, 105, 172)
Title.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Title.BorderSizePixel = 2
Title.Size = UDim2.new(0, 210, 0, 33)
Title.Font = Enum.Font.Highway
Title.Text = "tween monster out of range"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.FontSize = Enum.FontSize.Size32
Title.TextSize = 30
Title.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Title.TextStrokeTransparency = 0

Toggle.Parent = BG
Toggle.BackgroundColor3 = Color3.new(123, 182, 232)
Toggle.BorderColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.BorderSizePixel = 2
Toggle.Position = UDim2.new(0.152380958, 0, 0.374192119, 0)
Toggle.Size = UDim2.new(0, 146, 0, 36)
Toggle.Font = Enum.Font.Highway
Toggle.FontSize = Enum.FontSize.Size28
Toggle.Text = "stop toggle"
Toggle.TextColor3 = Color3.new(1, 1, 1)
Toggle.TextSize = 25
Toggle.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Toggle.TextStrokeTransparency = 0

StatusPF.Name = "StatusPF"
StatusPF.Parent = BG
StatusPF.BackgroundColor3 = Color3.new(1, 1, 1)
StatusPF.BackgroundTransparency = 1
StatusPF.Position = UDim2.new(0.314285725, 0, 0.708661377, 0)
StatusPF.Size = UDim2.new(0, 56, 0, 20)
StatusPF.Font = Enum.Font.Highway
StatusPF.FontSize = Enum.FontSize.Size24
StatusPF.Text = "Status:"
StatusPF.TextColor3 = Color3.new(1, 1, 1)
StatusPF.TextSize = 20
StatusPF.TextStrokeColor3 = Color3.new(0.333333, 0.333333, 0.333333)
StatusPF.TextStrokeTransparency = 0
StatusPF.TextWrapped = true

Status.Name = "Status"
Status.Parent = BG
Status.BackgroundColor3 = Color3.new(1, 1, 1)
Status.BackgroundTransparency = 1
Status.Position = UDim2.new(0.580952346, 0, 0.708661377, 0)
Status.Size = UDim2.new(0, 56, 0, 20)
Status.Font = Enum.Font.Highway
Status.FontSize = Enum.FontSize.Size14
Status.Text = "off"
Status.TextColor3 = Color3.new(0.666667, 0, 0)
Status.TextScaled = true
Status.TextSize = 14
Status.TextStrokeColor3 = Color3.new(0.180392, 0, 0.431373)
Status.TextWrapped = true
Status.TextXAlignment = Enum.TextXAlignment.Left

Credit.Name = "Credit"
Credit.Parent = BG
Credit.BackgroundColor3 = Color3.new(1, 1, 1)
Credit.BackgroundTransparency = 1
Credit.Position = UDim2.new(0.195238099, 0, 0.866141737, 0)
Credit.Size = UDim2.new(0, 128, 0, 17)
Credit.Font = Enum.Font.SourceSans
Credit.FontSize = Enum.FontSize.Size18
Credit.Text = "by sazx hub"
Credit.TextColor3 = Color3.new(1, 1, 1)
Credit.TextSize = 16
Credit.TextStrokeColor3 = Color3.new(0.196078, 0.196078, 0.196078)
Credit.TextStrokeTransparency = 0
Credit.TextWrapped = true
Toggle.MouseButton1Click:connect(function()
    if Status.Text == "off" then
        Clipon4 = true
        Status.Text = "on"
        Status.TextColor3 = Color3.new(0, 185, 0)
        
        -- เพิ่มลูป while นี้
local function handleTween(humanoidRootPart, endPosition)
    local humanoidRootPartTweenInfo = TweenInfo.new(1)
    local tween = TweenService:Create(humanoidRootPart, humanoidRootPartTweenInfo, {Position = endPosition})
    tween:Play()

    wait(0.5) -- รอ tween เริ่ม

    while humanoidRootPart.Position ~= endPosition do
        wait(0.1)
    end
end

RunService.RenderStepped:Connect(function()
    if Clipon4 then
        pcall(function()
            wait(Cooldown4)
            local player = game.Players.LocalPlayer
            local playerPos = player.Character and player.Character:FindFirstChild("HumanoidRootPart") and player.Character.HumanoidRootPart.Position

            if playerPos then
                local allPlayers = game.Players:GetPlayers()

                for _, v in pairs(game:GetService("Workspace"):GetDescendants()) do
                    if v:IsA("Model") and v:FindFirstChild("HumanoidRootPart") and not v:IsA("Player") then
                        local humanoidRootPart = v:FindFirstChild("HumanoidRootPart")
                        local mobPos = humanoidRootPart.Position

                        local isScriptRunner = v == player.Character
                        local isOtherPlayer = false

                        for _, otherPlayer in ipairs(allPlayers) do
                            if v == otherPlayer.Character then
                                isOtherPlayer = true
                                break
                            end
                        end

                        -- ตรวจสอบว่า v ไม่ใช่ตัวเอง และไม่ใช่ผู้เล่นคนอื่น
                        if mobPos and (playerPos - mobPos).Magnitude <= 25 and not isScriptRunner and not isOtherPlayer then
                            if (playerPos - mobPos).Magnitude <= 25 then
                                local direction = (mobPos - playerPos).Unit
                                local distance = 20

                                local endPosition = mobPos + direction * distance
                                handleTween(humanoidRootPart, endPosition)

                                if sethiddenproperty then
                                    sethiddenproperty(player, "SimulationRadius", math.huge)
                                    sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                                end
                            end
                        end
                    end
                end
            end
        end)
    end
end)
    else
        Clipon4 = false
        Status.Text = "off"
        Status.TextColor3 = Color3.new(170, 0, 0)
    end
end)
end)

local plr = game.Players.LocalPlayer

local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
    local p13 = CbFw2.activeController
    local ret = p13.blades[1]
    if not ret then return end
    while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
    return ret
end

function AttackNoCD() 
    local AC = CbFw2.activeController
    for i = 1, 1 do 
        local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
            plr.Character,
            {plr.Character.HumanoidRootPart},
            60
        )
        local cac = {}
        local hash = {}
        for k, v in pairs(bladehit) do
            if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
                table.insert(cac, v.Parent.HumanoidRootPart)
                hash[v.Parent] = true
            end
        end
        bladehit = cac
        if #bladehit > 0 then
            local u8 = debug.getupvalue(AC.attack, 5)
            local u9 = debug.getupvalue(AC.attack, 6)
            local u7 = debug.getupvalue(AC.attack, 4)
            local u10 = debug.getupvalue(AC.attack, 7)
            local u12 = (u8 * 798405 + u7 * 727595) % u9
            local u13 = u7 * 798405
            (function()
                u12 = (u12 * u9 + u13) % 1099511627776
                u8 = math.floor(u12 / u9)
                u7 = u12 - u8 * u9
            end)()
            u10 = u10 + 1
            debug.setupvalue(AC.attack, 5, u8)
            debug.setupvalue(AC.attack, 6, u9)
            debug.setupvalue(AC.attack, 4, u7)
            debug.setupvalue(AC.attack, 7, u10)
            pcall(function()
                for k, v in pairs(AC.animator.anims.basic) do
                    v:Play()
                end                  
            end)
            if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
                game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
            end
        end
    end
end
spawn(function()
    while wait(fast10) do
        if _G.FastAttack then
            pcall(function()
            repeat wait(_G.FastAttackDelay)                   
                AttackNoCD() 
                until not _G.FastAttack
            end)
        end
    end
end)

require(game.ReplicatedStorage.Util.CameraShaker):Stop()
             spawn(function()
                while wait() do
                    pcall(function()
                        if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
                        end
                    end)
                end
            end)
            
            
            spawn(function()
	game:GetService("RunService").Heartbeat:Connect(function()
		if _G.Auto_Farm_Level or _G.Auto_New_World or _G.TeleportIsland or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.Auto_Farm_Boss or _G.GunMastery or _G.Mastery or _G.AutoFarmFruitMastery or _G.AutoFarmGunMastery or _G.Auto_Elite_Hunter or _G.AutoFarmKenHaki or _G.AutoFactory or _G.AutoFarmSelectMonster or _G.Auto_Cake_Prince or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.d or _G.Auto_Rengoku or _G.Autotushita or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Mirage or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.AutoFarmMaterial or _G.autoraid or _G.Auto_Twin_Hook or AutoNextIsland or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.AutoObservationHakiV2 or _G.d or _G.Auto_Next_Island or _G.Auto_Farm_Sword or _G.MeleeFarm or _G.Auto_Kill_Law or _G.Auto_Raid then
			if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid") then
				setfflag("HumanoidParallelRemoveNoPhysics", "False")
				setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
				game:GetService("Players").LocalPlayer.Character.Humanoid:ChangeState(11)
			end
		end
	end)
end)

spawn(function()
    pcall(function()
       game:GetService("RunService").Heartbeat:Connect(function()
        if _G.Auto_Farm_Level or _G.Auto_New_World or _G.TeleportIsland or _G.Auto_Third_World or _G.Auto_Farm_Chest or _G.Auto_Farm_Boss or _G.GunMastery or _G.Mastery or _G.AutoFarmFruitMastery or _G.AutoFarmGunMastery or _G.Auto_Elite_Hunter or _G.AutoFarmKenHaki or _G.AutoFactory or _G.AutoFarmSelectMonster or _G.Auto_Cake_Prince or _G.Auto_Farm_All_Boss or _G.Auto_Saber or _G.Auto_Pole or _G.Auto_Farm_Scrap_and_Leather or _G.Auto_Farm_Angel_Wing or _G.Auto_Factory_Farm or _G.Auto_Farm_Ectoplasm or _G.Auto_Bartilo_Quest or _G.d or _G.Auto_Rengoku or _G.Autotushita or _G.Auto_Farm_Radioactive or _G.Auto_Farm_Vampire_Fang or _G.Auto_Farm_Mystic_Droplet or _G.Auto_Farm_GunPowder or _G.Auto_Farm_Dragon_Scales or _G.Auto_Evo_Race_V2 or _G.Auto_Swan_Glasses or _G.Auto_Dragon_Trident or _G.Auto_Soul_Reaper or _G.Auto_Farm_Fish_Tail or _G.Mirage or _G.Auto_Farm_Magma_Ore or _G.Auto_Farm_Bone or _G.Auto_Farm_Conjured_Cocoa or _G.Auto_Open_Dough_Dungeon or _G.Auto_Rainbow_Haki or _G.Auto_Musketeer_Hat or _G.Auto_Holy_Torch or _G.Auto_Canvander or _G.AutoFarmMaterial or _G.autoraid or _G.Auto_Twin_Hook or AutoNextIsland or _G.Auto_Serpent_Bow or _G.Auto_Fully_Death_Step or _G.Auto_Fully_SharkMan_Karate or _G.Teleport_to_Player or _G.Auto_Kill_Player_Melee or _G.Auto_Kill_Player_Gun or _G.Start_Tween_Island or _G.AutoObservationHakiV2 or _G.d or _G.Auto_Next_Island or _G.Auto_Farm_Sword or _G.MeleeFarm or _G.Auto_Kill_Law or _G.Auto_Raid then
          if not game:GetService("Workspace"):FindFirstChild("LOL") then
             local Paertaiteen = Instance.new("Part")
             Paertaiteen.Name = "LOL"
             Paertaiteen.Parent = game.Workspace
             Paertaiteen.Anchored = true
             Paertaiteen.Transparency = 0
             Paertaiteen.Size = Vector3.new(35,1,35,35)
             Paertaiteen.Material = "Neon"
             while true do 
                 wait(0.1) 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 155, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 255, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 255, 0)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 255, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(0, 155, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 255)}):Play() 
                 wait(.5)
 
                 game:GetService('TweenService'):Create(
                     Paertaiteen,TweenInfo.new(1,Enum.EasingStyle.Linear,Enum.EasingDirection.InOut),
                 {Color = Color3.fromRGB(255, 0, 155)}):Play() 
                 wait(.5)
             end 
         elseif game:GetService("Workspace"):FindFirstChild("LOL") then
             game.Workspace["LOL"].CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Y - 3.92,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
         end
     else
         if game:GetService("Workspace"):FindFirstChild("LOL") then
             game:GetService("Workspace"):FindFirstChild("LOL"):Destroy()
         end
        end
    end)
 end)
end)
            
