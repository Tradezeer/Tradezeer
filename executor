local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")
local lp = Players.LocalPlayer

local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local TitleBar = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local EditorFrame = Instance.new("ScrollingFrame")
local TextBox = Instance.new("TextBox")
local ButtonHolder = Instance.new("Frame")

pcall(function()
    ScreenGui.Parent = CoreGui
end)
if not ScreenGui.Parent then
    ScreenGui.Parent = lp:WaitForChild("PlayerGui")
end

ScreenGui.Name = "DoSploit_UI"
ScreenGui.ResetOnSpawn = false

MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
MainFrame.Position = UDim2.new(0.5, -275, 0.5, -150)
MainFrame.Size = UDim2.new(0, 550, 0, 300)
MainFrame.BorderSizePixel = 1
MainFrame.BorderColor3 = Color3.fromRGB(0, 170, 255)
MainFrame.Active = true

TitleBar.Name = "TitleBar"
TitleBar.Parent = MainFrame
TitleBar.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
TitleBar.Size = UDim2.new(1, 0, 0, 25)
TitleBar.BorderSizePixel = 0

Title.Name = "Title"
Title.Parent = TitleBar
Title.BackgroundTransparency = 1
Title.Position = UDim2.new(0, 10, 0, 0)
Title.Size = UDim2.new(1, -10, 1, 0)
Title.Font = Enum.Font.Code
Title.Text = "DoSploit"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 14
Title.TextXAlignment = Enum.TextXAlignment.Left

EditorFrame.Name = "EditorFrame"
EditorFrame.Parent = MainFrame
EditorFrame.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
EditorFrame.Position = UDim2.new(0, 10, 0, 35)
EditorFrame.Size = UDim2.new(0, 420, 0, 220)
EditorFrame.BorderSizePixel = 1
EditorFrame.BorderColor3 = Color3.fromRGB(40, 40, 40)
EditorFrame.CanvasSize = UDim2.new(0, 0, 5, 0)

TextBox.Parent = EditorFrame
TextBox.Size = UDim2.new(1, 0, 1, 0)
TextBox.BackgroundTransparency = 1
TextBox.Text = ""
TextBox.TextColor3 = Color3.fromRGB(0, 170, 255)
TextBox.TextSize = 14
TextBox.ClearTextOnFocus = false
TextBox.MultiLine = true
TextBox.Font = Enum.Font.Code
TextBox.TextXAlignment = Enum.TextXAlignment.Left
TextBox.TextYAlignment = Enum.TextYAlignment.Top

ButtonHolder.Name = "ButtonHolder"
ButtonHolder.Parent = MainFrame
ButtonHolder.BackgroundTransparency = 1
ButtonHolder.Position = UDim2.new(0, 10, 0, 265)
ButtonHolder.Size = UDim2.new(0, 530, 0, 25)

local function AddButton(text, x_offset)
    local btn = Instance.new("TextButton")
    btn.Parent = ButtonHolder
    btn.Text = text
    btn.Size = UDim2.new(0, 80, 1, 0)
    btn.Position = UDim2.new(0, x_offset, 0, 0)
    btn.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
    btn.TextColor3 = Color3.fromRGB(255, 255, 255)
    btn.Font = Enum.Font.Code
    btn.TextSize = 12
    btn.BorderSizePixel = 1
    btn.BorderColor3 = Color3.fromRGB(0, 170, 255)
    return btn
end

local Exec = AddButton("Execute", 0)
local Clear = AddButton("Clear", 85)

Exec.MouseButton1Click:Connect(function()
    local func = loadstring(TextBox.Text)
    if func then
        task.spawn(func)
    end
end)

Clear.MouseButton1Click:Connect(function()
    TextBox.Text = ""
end)

local ScriptList = Instance.new("Frame")
ScriptList.Parent = MainFrame
ScriptList.BackgroundColor3 = Color3.fromRGB(15, 15, 15)
ScriptList.Position = UDim2.new(0, 440, 0, 35)
ScriptList.Size = UDim2.new(0, 100, 0, 220)
ScriptList.BorderSizePixel = 1
ScriptList.BorderColor3 = Color3.fromRGB(40, 40, 40)

local UserInputService = game:GetService("UserInputService")
local dragging, dragInput, dragStart, startPos

TitleBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true
        dragStart = input.Position
        startPos = MainFrame.Position
    end
end)

TitleBar.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = false
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        dragInput = input
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if dragging and input == dragInput then
        local delta = input.Position - dragStart
        MainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)
