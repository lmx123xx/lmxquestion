local Players = game:GetService("Players")
local Player = Players.LocalPlayer
local PlayerGui = Player:WaitForChild("PlayerGui")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local TweenService = game:GetService("TweenService")

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "TeleportGui"
ScreenGui.ResetOnSpawn = false

local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 200, 0, 220)
MainFrame.Position = UDim2.new(0.5, -100, 0.7, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
MainFrame.BackgroundTransparency = 0.2
MainFrame.BorderSizePixel = 0
MainFrame.ClipsDescendants = true

local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 10)
UICorner.Parent = MainFrame

local TitleBar = Instance.new("Frame")
TitleBar.Name = "TitleBar"
TitleBar.Size = UDim2.new(1, 0, 0, 30)
TitleBar.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
TitleBar.BorderSizePixel = 0

local TitleText = Instance.new("TextLabel")
TitleText.Name = "TitleText"
TitleText.Size = UDim2.new(1, -60, 1, 0)
TitleText.Position = UDim2.new(0, 10, 0, 0)
TitleText.BackgroundTransparency = 1
TitleText.Text = "传送系统"
TitleText.TextColor3 = Color3.fromRGB(255, 255, 255)
TitleText.TextSize = 16
TitleText.Font = Enum.Font.SourceSansBold
TitleText.TextXAlignment = Enum.TextXAlignment.Left

local MinimizeButton = Instance.new("TextButton")
MinimizeButton.Name = "MinimizeButton"
MinimizeButton.Size = UDim2.new(0, 50, 1, 0)
MinimizeButton.Position = UDim2.new(1, -50, 0, 0)
MinimizeButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
MinimizeButton.BorderSizePixel = 0
MinimizeButton.Text = "最小化"
MinimizeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
MinimizeButton.TextSize = 14

local CloseButton = Instance.new("TextButton")
CloseButton.Name = "CloseButton"
CloseButton.Size = UDim2.new(0, 30, 1, 0)
CloseButton.Position = UDim2.new(1, -80, 0, 0)
CloseButton.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
CloseButton.BorderSizePixel = 0
CloseButton.Text = "×"
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseButton.TextSize = 20
CloseButton.Visible = false

local ContentFrame = Instance.new("Frame")
ContentFrame.Name = "ContentFrame"
ContentFrame.Size = UDim2.new(1, 0, 1, -30)
ContentFrame.Position = UDim2.new(0, 0, 0, 30)
ContentFrame.BackgroundTransparency = 1

local StatusLabel = Instance.new("TextLabel")
StatusLabel.Name = "StatusLabel"
StatusLabel.Size = UDim2.new(1, -20, 0, 30)
StatusLabel.Position = UDim2.new(0, 10, 0, 10)
StatusLabel.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
StatusLabel.BackgroundTransparency = 0.5
StatusLabel.Text = "未设置传送点"
StatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
StatusLabel.TextSize = 14
StatusLabel.Font = Enum.Font.SourceSans

local UICorner2 = Instance.new("UICorner")
UICorner2.CornerRadius = UDim.new(0, 5)
UICorner2.Parent = StatusLabel

local PlaceButton = Instance.new("TextButton")
PlaceButton.Name = "PlaceButton"
PlaceButton.Size = UDim2.new(1, -20, 0, 40)
PlaceButton.Position = UDim2.new(0, 10, 0, 50)
PlaceButton.BackgroundColor3 = Color3.fromRGB(0, 120, 215)
PlaceButton.BorderSizePixel = 0
PlaceButton.Text = "放置传送点"
PlaceButton.TextColor3 = Color3.fromRGB(255, 255, 255)
PlaceButton.TextSize = 16
PlaceButton.Font = Enum.Font.SourceSansBold

local UICorner3 = Instance.new("UICorner")
UICorner3.CornerRadius = UDim.new(0, 8)
UICorner3.Parent = PlaceButton

local TeleportButton = Instance.new("TextButton")
TeleportButton.Name = "TeleportButton"
TeleportButton.Size = UDim2.new(1, -20, 0, 40)
TeleportButton.Position = UDim2.new(0, 10, 0, 100)
TeleportButton.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
TeleportButton.BorderSizePixel = 0
TeleportButton.Text = "传送"
TeleportButton.TextColor3 = Color3.fromRGB(255, 255, 255)
TeleportButton.TextSize = 16
TeleportButton.Font = Enum.Font.SourceSansBold

local UICorner4 = Instance.new("UICorner")
UICorner4.CornerRadius = UDim.new(0, 8)
UICorner4.Parent = TeleportButton

local ResetButton = Instance.new("TextButton")
ResetButton.Name = "ResetButton"
ResetButton.Size = UDim2.new(1, -20, 0, 40)
ResetButton.Position = UDim2.new(0, 10, 0, 150)
ResetButton.BackgroundColor3 = Color3.fromRGB(215, 60, 0)
ResetButton.BorderSizePixel = 0
ResetButton.Text = "重置传送点"
ResetButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ResetButton.TextSize = 16
ResetButton.Font = Enum.Font.SourceSansBold

local UICorner5 = Instance.new("UICorner")
UICorner5.CornerRadius = UDim.new(0, 8)
UICorner5.Parent = ResetButton

local MinimizedFrame = Instance.new("Frame")
MinimizedFrame.Name = "MinimizedFrame"
MinimizedFrame.Size = UDim2.new(0, 100, 0, 40)
MinimizedFrame.Position = UDim2.new(0.5, -50, 0.9, 0)
MinimizedFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
MinimizedFrame.BackgroundTransparency = 0.2
MinimizedFrame.BorderSizePixel = 0
MinimizedFrame.Visible = false

local UICorner6 = Instance.new("UICorner")
UICorner6.CornerRadius = UDim.new(0, 10)
UICorner6.Parent = MinimizedFrame

local ExpandButton = Instance.new("TextButton")
ExpandButton.Name = "ExpandButton"
ExpandButton.Size = UDim2.new(1, 0, 1, 0)
ExpandButton.BackgroundTransparency = 1
ExpandButton.Text = "展开传送"
ExpandButton.TextColor3 = Color3.fromRGB(255, 255, 255)
ExpandButton.TextSize = 14

TitleBar.Parent = MainFrame
TitleText.Parent = TitleBar
MinimizeButton.Parent = TitleBar
CloseButton.Parent = TitleBar
ContentFrame.Parent = MainFrame
StatusLabel.Parent = ContentFrame
PlaceButton.Parent = ContentFrame
TeleportButton.Parent = ContentFrame
ResetButton.Parent = ContentFrame
MinimizedFrame.Parent = ScreenGui
ExpandButton.Parent = MinimizedFrame
MainFrame.Parent = ScreenGui
ScreenGui.Parent = PlayerGui

local teleportPoint = nil
local isDragging = false
local dragStartPos = nil
local frameStartPos = nil
local isMinimized = false

local function updateStatus()
    if teleportPoint then
        StatusLabel.Text = "传送点已设置"
        StatusLabel.TextColor3 = Color3.fromRGB(0, 255, 0)
        TeleportButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
    else
        StatusLabel.Text = "未设置传送点"
        StatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
        TeleportButton.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
    end
end

local function createVisualMarker(position)
    if not workspace:FindFirstChild("TeleportMarkers") then
        local folder = Instance.new("Folder")
        folder.Name = "TeleportMarkers"
        folder.Parent = workspace
    end
    
    local marker = Instance.new("Part")
    marker.Name = Player.Name .. "_TeleportMarker"
    marker.Size = Vector3.new(2, 0.2, 2)
    marker.Position = position + Vector3.new(0, 0.1, 0)
    marker.Anchored = true
    marker.CanCollide = false
    marker.Transparency = 0.3
    marker.Color = Color3.fromRGB(0, 255, 255)
    marker.Material = Enum.Material.Neon
    
    local beam = Instance.new("Beam")
    beam.Attachment0 = Instance.new("Attachment")
    beam.Attachment0.Parent = marker
    beam.Attachment1 = Instance.new("Attachment")
    beam.Attachment1.Parent = marker
    beam.Attachment1.Position = Vector3.new(0, 5, 0)
    beam.Color = ColorSequence.new(Color3.fromRGB(0, 255, 255))
    beam.Width0 = 0.5
    beam.Width1 = 0.5
    beam.Parent = marker
    
    local light = Instance.new("PointLight")
    light.Parent = marker
    light.Color = Color3.fromRGB(0, 255, 255)
    light.Range = 10
    light.Brightness = 1
    
    marker.Parent = workspace.TeleportMarkers
    
    return marker
end

PlaceButton.MouseButton1Click:Connect(function()
    local character = Player.Character
    if character and character:FindFirstChild("HumanoidRootPart") then
        local hrp = character.HumanoidRootPart
        teleportPoint = hrp.Position
        
        if workspace:FindFirstChild("TeleportMarkers") then
            local oldMarker = workspace.TeleportMarkers:FindFirstChild(Player.Name .. "_TeleportMarker")
            if oldMarker then
                oldMarker:Destroy()
            end
        end
        
        createVisualMarker(teleportPoint)
        updateStatus()
    end
end)

TeleportButton.MouseButton1Click:Connect(function()
    if teleportPoint then
        local character = Player.Character
        if character and character:FindFirstChild("HumanoidRootPart") then
            local hrp = character.HumanoidRootPart
            hrp.CFrame = CFrame.new(teleportPoint)
        end
    end
end)

ResetButton.MouseButton1Click:Connect(function()
    teleportPoint = nil
    
    if workspace:FindFirstChild("TeleportMarkers") then
        local marker = workspace.TeleportMarkers:FindFirstChild(Player.Name .. "_TeleportMarker")
        if marker then
            marker:Destroy()
        end
    end
    
    updateStatus()
end)

MinimizeButton.MouseButton1Click:Connect(function()
    if not isMinimized then
        MainFrame.Visible = false
        MinimizedFrame.Visible = true
        isMinimized = true
        MinimizeButton.Text = "展开"
    else
        MainFrame.Visible = true
        MinimizedFrame.Visible = false
        isMinimized = false
        MinimizeButton.Text = "最小化"
    end
end)

ExpandButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = true
    MinimizedFrame.Visible = false
    isMinimized = false
    MinimizeButton.Text = "最小化"
end)

CloseButton.MouseButton1Click:Connect(function()
    ScreenGui.Enabled = false
end)

TitleBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
        isDragging = true
        dragStartPos = input.Position
        frameStartPos = MainFrame.Position
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if isDragging and (input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseMovement) then
        local delta = input.Position - dragStartPos
        MainFrame.Position = UDim2.new(
            frameStartPos.X.Scale,
            frameStartPos.X.Offset + delta.X,
            frameStartPos.Y.Scale,
            frameStartPos.Y.Offset + delta.Y
        )
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
        isDragging = false
    end
end)

MinimizedFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then
        isDragging = true
        dragStartPos = input.Position
        frameStartPos = MinimizedFrame.Position
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if isDragging and MinimizedFrame.Visible and (input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseMovement) then
        local delta = input.Position - dragStartPos
        MinimizedFrame.Position = UDim2.new(
            frameStartPos.X.Scale,
            frameStartPos.X.Offset + delta.X,
            frameStartPos.Y.Scale,
            frameStartPos.Y.Offset + delta.Y
        )
    end
end)

updateStatus()

Player.CharacterAdded:Connect(function()
    if teleportPoint then
