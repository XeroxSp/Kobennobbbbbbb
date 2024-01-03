_G.KobenNoobFast2 = true
_G.KobenNoobFast = true
spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
		if _G.KobenNoobFast2 then
			pcall(function()
				game:GetService'VirtualUser':CaptureController()
				game:GetService'VirtualUser':Button1Down(Vector2.new(0,1,0,1))
			end)
		end
	end)
end)
spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
		if _G.KobenNoobFast2 then
			pcall(function()
				game:GetService'VirtualUser':CaptureController()
				game:GetService'VirtualUser':Button1Down(Vector2.new(0,1,0,1))
			end)
		end
	end)
end)
spawn(function()
	game:GetService("RunService").RenderStepped:Connect(function()
		if _G.KobenNoobFast2 then
			pcall(function()
				game:GetService'VirtualUser':CaptureController()
				game:GetService'VirtualUser':Button1Down(Vector2.new(0,1,0,1))
			end)
		end
	end)
end)
local CameraShaker = require(game.ReplicatedStorage.Util.CameraShaker)
CombatFrameworkR = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
y = debug.getupvalues(CombatFrameworkR)[2]
spawn(function()
    game:GetService("RunService").RenderStepped:Connect(function()
        if _G.KobenNoobFast then
            if typeof(Fast) == "table" then
                pcall(function()
                    CameraShaker:Stop()
                    Fast.activeController.timeToNextAttack = (math.huge^math.huge^math.huge)
                    Fast.activeController.timeToNextAttack = 0
                    Fast.activeController.hitboxMagnitude = 60
                    Fast.activeController.active = true
                    Fast.activeController.timeToNextBlock = 0
                    Fast.activeController.focusStart = 1655503339.0980349
                    Fast.activeController.increment = 1
                    Fast.activeController.blocking = true
                    Fast.activeController.attacking = true
                    Fast.activeController.humanoid.AutoRotate = true
                end)
            end
        end
    end)
end)
local CamShake = require(game.ReplicatedStorage.Util.CameraShaker)
CamShake:Stop()
function GetBladeHit()
    local CombatFrameworkLib = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework))
    local CmrFwLib = CombatFrameworkLib[2]
    local p13 = CmrFwLib.activeController
    local weapon = p13.blades[1]
    if not weapon then 
        return weapon
    end
    while weapon.Parent ~= game.Players.LocalPlayer.Character do
        weapon = weapon.Parent 
    end
    return weapon
end
function AttackHit()
    local CombatFrameworkLib = debug.getupvalues(require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework))
    local CmrFwLib = CombatFrameworkLib[2]
    local plr = game.Players.LocalPlayer
    for i = 1, 1 do
        local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(plr.Character,{plr.Character.HumanoidRootPart},60)
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
            pcall(function()
                CmrFwLib.activeController.timeToNextAttack = 1
                CmrFwLib.activeController.attacking = false
                CmrFwLib.activeController.blocking = false
                CmrFwLib.activeController.timeToNextBlock = 0
                CmrFwLib.activeController.increment = 2
                CmrFwLib.activeController.hitboxMagnitude = 80
                CmrFwLib.activeController.focusStart = 0
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetBladeHit()))
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "")
            end)
        end
    end
end
spawn(function()
    while wait(.1) do
        if _G.KobenNoobFast then
            pcall(function()
                repeat task.wait(0.1)
                    AttackHit()
                until not _G.KobenNoobFast
            end)
        end
    end
end)
