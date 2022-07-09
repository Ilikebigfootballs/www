local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

local Window = OrionLib:MakeWindow({Name = "Mine Aura Close Tab", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

Tab1 = Window:MakeTab({
	Name = "Mine Aura",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

Tab1:AddBind({
	Name = "Bind",
	Default = Enum.KeyCode.E,
	Hold = false,
	Callback = function()
		print("press")
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Axe") then
					function onTouched(part)       
						local h = part
						if h.Name == "Block" then
							game:GetService("Players").LocalPlayer.Backpack.Axe.RemoteEvent:FireServer(h)  
						end
					end
					Partz              = Instance.new("Part")
					Partz.Parent       = workspace
					Partz.Transparency = 1
					Partz.CanCollide   = false
					Partz.Massless     = true
					Partz.Position     = game.Players.LocalPlayer.Character.HumanoidRootPart.Position + Vector3.new(0,9,0)
					Partz.Size         = Vector3.new(15,20,15)

					local light         = Instance.new("SelectionBox")
					light.Adornee       = Partz
					light.LineThickness = 0.05
					light.Color3        = Color3.fromRGB(0, 255, 0)
					light.Parent        = Partz
					light.Name          = "SelectBox"

					local bruh = Partz.Touched:connect(onTouched)

					wait()
					bruh:Disconnect()
					Partz:Destroy()
				end
	end    
})
