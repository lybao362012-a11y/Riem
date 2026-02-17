local p=game:GetService("Players").LocalPlayer
repeat task.wait() until p

local g=Instance.new("ScreenGui")
g.Name="5 riêm"
g.Parent=p:WaitForChild("PlayerGui")

local f=Instance.new("Frame",g)
f.Size=UDim2.new(0,140,0,70)
f.Position=UDim2.new(0.5,-70,0.8,0)
f.BackgroundColor3=Color3.fromRGB(30,30,30)
f.Active=true
f.Draggable=true

local t=Instance.new("TextLabel",f)
t.Size=UDim2.new(1,0,0,20)
t.BackgroundColor3=Color3.fromRGB(45,45,45)
t.Text="5 riêm"
t.TextColor3=Color3.new(1,1,1)
t.TextScaled=true

local b=Instance.new("TextButton",f)
b.Size=UDim2.new(0.9,0,0,35)
b.Position=UDim2.new(0.05,0,0.45,0)
b.Text="OFF"
b.BackgroundColor3=Color3.fromRGB(255,0,0)
b.TextScaled=true

local a=false
local h

local function char(c)
	h=c:WaitForChild("Humanoid")
end

if p.Character then char(p.Character) end
p.CharacterAdded:Connect(char)

b.MouseButton1Click:Connect(function()
	a=not a
	if a then
		b.Text="ON"
		b.BackgroundColor3=Color3.fromRGB(0,255,0)
		task.spawn(function()
			while a do
				if h and h.Health>0 then
					h:ChangeState(Enum.HumanoidStateType.Jumping)
				end
				task.wait(0.1)
			end
		end)
	else
		b.Text="OFF"
		b.BackgroundColor3=Color3.fromRGB(255,0,0)
	end
end)g.Name=
