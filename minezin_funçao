local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local localPlayer = Players.LocalPlayer

-- Cria ScreenGui
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "KillMenuGui"
screenGui.ResetOnSpawn = false
screenGui.Parent = game:GetService("CoreGui")

-- Função para criar botões arredondados e com hover
local function createButton(text, parent, position, size)
	local btn = Instance.new("TextButton")
	btn.Text = text
	btn.BackgroundColor3 = Color3.fromRGB(70, 45, 100)
	btn.TextColor3 = Color3.fromRGB(230, 230, 250)
	btn.Size = size
	btn.Position = position
	btn.BorderSizePixel = 0
	btn.Font = Enum.Font.GothamBold
	btn.TextScaled = true
	btn.AutoButtonColor = false
	btn.Parent = parent

	-- Arredondar cantos
	local corner = Instance.new("UICorner")
	corner.CornerRadius = UDim.new(0, 10)
	corner.Parent = btn

	-- Hover efeito
	btn.MouseEnter:Connect(function()
		btn.BackgroundColor3 = Color3.fromRGB(110, 75, 150)
	end)
	btn.MouseLeave:Connect(function()
		btn.BackgroundColor3 = Color3.fromRGB(70, 45, 100)
	end)

	return btn
end

-- Cria Frame principal arredondado
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 340, 0, 360)
frame.Position = UDim2.new(0.5, -170, 0.5, -180)
frame.BackgroundColor3 = Color3.fromRGB(25, 18, 45)
frame.BorderSizePixel = 0
frame.Parent = screenGui
frame.Active = true
frame.Draggable = true
frame.ClipsDescendants = true
frame.BackgroundTransparency = 1 -- começa invisível para animar

-- Arredondar cantos do frame
local frameCorner = Instance.new("UICorner")
frameCorner.CornerRadius = UDim.new(0, 16)
frameCorner.Parent = frame

-- Animação fade-in do frame
local TweenService = game:GetService("TweenService")
local tweenInfo = TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
local tween = TweenService:Create(frame, tweenInfo, {BackgroundTransparency = 0})
tween:Play()

-- Cabeçalho com arredondado em cima
local header = Instance.new("Frame")
header.Size = UDim2.new(1, 0, 0, 50)
header.BackgroundColor3 = Color3.fromRGB(45, 30, 85)
header.BorderSizePixel = 0
header.Parent = frame

local headerCorner = Instance.new("UICorner")
headerCorner.CornerRadius = UDim.new(0, 16)
headerCorner.Parent = header

-- Texto do título
local headerText = Instance.new("TextLabel")
headerText.Size = UDim2.new(1, -40, 1, 0)
headerText.Position = UDim2.new(0, 10, 0, 0)
headerText.BackgroundTransparency = 1
headerText.Text = "Minezin"
headerText.TextColor3 = Color3.fromRGB(235, 215, 255)
headerText.Font = Enum.Font.GothamBlack
headerText.TextSize = 40
headerText.TextXAlignment = Enum.TextXAlignment.Left
headerText.Parent = header

-- Botão fechar arredondado no topo direito
local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 30, 0, 30)
closeBtn.Position = UDim2.new(1, -40, 0, 10)
closeBtn.BackgroundColor3 = Color3.fromRGB(180, 30, 30)
closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
closeBtn.Font = Enum.Font.GothamBold
closeBtn.TextSize = 24
closeBtn.Text = "X"
closeBtn.AutoButtonColor = false
closeBtn.Parent = header

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(0, 6)
closeCorner.Parent = closeBtn

closeBtn.MouseEnter:Connect(function()
	closeBtn.BackgroundColor3 = Color3.fromRGB(230, 50, 50)
end)
closeBtn.MouseLeave:Connect(function()
	closeBtn.BackgroundColor3 = Color3.fromRGB(180, 30, 30)
end)
closeBtn.MouseButton1Click:Connect(function()
	screenGui:Destroy()
end)

-- TextBox para nome do player arredondado
local nameBox = Instance.new("TextBox")
nameBox.PlaceholderText = "Escreva aqui"
nameBox.Size = UDim2.new(1, -20, 0, 40)
nameBox.Position = UDim2.new(0, 10, 0, 70)
nameBox.BackgroundColor3 = Color3.fromRGB(40, 25, 75)
nameBox.TextColor3 = Color3.fromRGB(230, 230, 255)
nameBox.Font = Enum.Font.Gotham
nameBox.TextSize = 20
nameBox.ClearTextOnFocus = false
nameBox.Parent = frame
nameBox.TextStrokeTransparency = 0.7
nameBox.TextXAlignment = Enum.TextXAlignment.Left
nameBox.PlaceholderColor3 = Color3.fromRGB(180, 160, 200)

local nameBoxCorner = Instance.new("UICorner")
nameBoxCorner.CornerRadius = UDim.new(0, 10)
nameBoxCorner.Parent = nameBox

-- Botões arredondados
local killBtn = createButton("Kill Player Name", frame, UDim2.new(0, 10, 0, 130), UDim2.new(0, 150, 0, 40))
local killLoopBtn = createButton("Kill Player Name Loop: OFF", frame, UDim2.new(0, 180, 0, 130), UDim2.new(0, 150, 0, 40))
local killAllBtn = createButton("Kill All", frame, UDim2.new(0, 10, 0, 190), UDim2.new(0, 150, 0, 40))
local killAllLoopBtn = createButton("Kill All Loop: OFF", frame, UDim2.new(0, 180, 0, 190), UDim2.new(0, 150, 0, 40))

-- Função de KillPlayer
local function KillPlayer(targetPlayer)
	if not targetPlayer.Character then return end
	local humanoidRootPart = targetPlayer.Character:FindFirstChild("HumanoidRootPart")
	local localChar = localPlayer.Character
	if not humanoidRootPart or not localChar then return end
	local weapon = localChar:FindFirstChild("Glock")
	if not weapon then return end

	local args = {
		weapon,
		{
			["p"] = Vector3.new(-1934.757568359375, -73.66830444335938, -11445.2548828125),
			["pid"] = 1,
			["part"] = humanoidRootPart,
			["d"] = 0.2078668624162674,
			["maxDist"] = 0.2078594863414764,
			["h"] = targetPlayer.Character.Humanoid,
			["m"] = Enum.Material.Plastic,
			["sid"] = 1,
			["t"] = 0.011482002849878449,
			["n"] = Vector3.new(-0.9999971389770508, -0.0006082971813157201, 0.002314852550625801)
		}
	}

	ReplicatedStorage.WeaponsSystem.Network.WeaponHit:FireServer(unpack(args))
end

-- Botões eventos
killBtn.MouseButton1Click:Connect(function()
	local name = nameBox.Text
	local target = Players:FindFirstChild(name)
	if target and target ~= localPlayer then
		KillPlayer(target)
	end
end)

local killLoopEnabled = false
killLoopBtn.MouseButton1Click:Connect(function()
	killLoopEnabled = not killLoopEnabled
	killLoopBtn.Text = "Kill Player Name Loop: " .. (killLoopEnabled and "ON" or "OFF")
end)

killAllBtn.MouseButton1Click:Connect(function()
	for _, plr in pairs(Players:GetPlayers()) do
		if plr ~= localPlayer then
			KillPlayer(plr)
		end
	end
end)

local killAllLoopEnabled = false
killAllLoopBtn.MouseButton1Click:Connect(function()
	killAllLoopEnabled = not killAllLoopEnabled
	killAllLoopBtn.Text = "Kill All Loop: " .. (killAllLoopEnabled and "ON" or "OFF")
end)

-- Loop principal para kills em loop
spawn(function()
	while true do
		if killLoopEnabled then
			local name = nameBox.Text
			local target = Players:FindFirstChild(name)
			if target and target ~= localPlayer then
				KillPlayer(target)
			end
		end

		if killAllLoopEnabled then
			for _, plr in pairs(Players:GetPlayers()) do
				if plr ~= localPlayer then
					KillPlayer(plr)
				end
			end
		end

		task.wait(0.1)
	end
end)
