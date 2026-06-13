local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local CoreGui = game:GetService("CoreGui")
local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local LP = Players.LocalPlayer

----------------------------------------------------------------
-- الجزء الأول: واجهة الترحيب الدورية (تنزلق من الأعلى)
----------------------------------------------------------------
local function ShowWelcomeUI()
    local BLUE  = Color3.fromRGB(0, 190, 255)
    local BLACK = Color3.fromRGB(20, 20, 20)
    local WHITE = Color3.fromRGB(255, 255, 255)
    local TARGET_IMAGE_USER = "moila933" 
    local DEVELOPER_NAME = "moila933"

    pcall(function() CoreGui.WelcomeUI_NAH:Destroy() end)

    local ScreenGui = Instance.new("ScreenGui", CoreGui)
    ScreenGui.Name = "WelcomeUI_NAH"
    ScreenGui.IgnoreGuiInset = true

    local Main = Instance.new("Frame", ScreenGui)
    Main.Size = UDim2.new(0, 520, 0, 260)
    Main.Position = UDim2.new(0.5, -260, 0, -300)
    Main.BackgroundColor3 = Color3.fromRGB(10, 10, 15)
    Main.BorderSizePixel = 0
    Main.Active = true
    Main.Draggable = true
    Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 25)

    TweenService:Create(Main, TweenInfo.new(1.5, Enum.EasingStyle.Bounce, Enum.EasingDirection.Out), {Position = UDim2.new(0.5, -260, 0.5, -130)}):Play()

    local Title = Instance.new("TextLabel", Main)
    Title.Size = UDim2.new(1, 0, 0, 50)
    Title.Position = UDim2.new(0, 0, 0.05, 0)
    Title.BackgroundTransparency = 1
    Title.Text = "ARB CLAN"
    Title.Font = Enum.Font.GothamBlack
    Title.TextSize = 40
    Title.TextColor3 = WHITE
    Title.TextStrokeTransparency = 0.5

    task.spawn(function()
        while Main.Parent do
            TweenService:Create(Title, TweenInfo.new(1.2, Enum.EasingStyle.Sine), {TextColor3 = BLUE}):Play()
            task.wait(1.2)
            TweenService:Create(Title, TweenInfo.new(1.2, Enum.EasingStyle.Sine), {TextColor3 = WHITE}):Play()
            task.wait(1.2)
        end
    end)

    local CircleFrame = Instance.new("Frame", Main)
    CircleFrame.Size = UDim2.new(0, 150, 0, 150)
    CircleFrame.Position = UDim2.new(0.68, 0, 0.35, 0)
    CircleFrame.BackgroundColor3 = BLUE
    CircleFrame.ClipsDescendants = true 
    Instance.new("UICorner", CircleFrame).CornerRadius = UDim.new(1, 0)

    task.spawn(function()
        while Main.Parent do
            TweenService:Create(CircleFrame, TweenInfo.new(1.2, Enum.EasingStyle.Sine), {BackgroundColor3 = BLUE}):Play()
            task.wait(1.2)
            TweenService:Create(CircleFrame, TweenInfo.new(1.2, Enum.EasingStyle.Sine), {BackgroundColor3 = WHITE}):Play()
            task.wait(1.2)
        end
    end)

    local ImageFrame = Instance.new("ImageLabel", CircleFrame)
    ImageFrame.Size = UDim2.new(0.9, 0, 0.9, 0)
    ImageFrame.Position = UDim2.new(0.05, 0, 0.05, 0)
    ImageFrame.BackgroundTransparency = 1
    local userId = game.Players:GetUserIdFromNameAsync(TARGET_IMAGE_USER)
    ImageFrame.Image = "https://www.roblox.com/headshot-thumbnail/image?userId="..userId.."&width=420&height=420&format=png"
    Instance.new("UICorner", ImageFrame).CornerRadius = UDim.new(1, 0)

    local DescLabel = Instance.new("TextLabel", Main)
    DescLabel.Size = UDim2.new(0, 300, 0, 100)
    DescLabel.Position = UDim2.new(0.05, 0, 0.45, 0)
    DescLabel.BackgroundTransparency = 1
    DescLabel.TextXAlignment = Enum.TextXAlignment.Left
    DescLabel.TextYAlignment = Enum.TextYAlignment.Top
    DescLabel.Font = Enum.Font.GothamBold
    DescLabel.TextSize = 14
    DescLabel.Text = "مطور السكربت ومنشاءه ومبرمجه الاسم ("..DEVELOPER_NAME..")\n"..
        "وقائد الكلان (Ahmad_00435A)\n\n"..
        "وشكر خاص مني لاعضاء التيم ونائبين التيم"

    local OkBtn = Instance.new("TextButton", Main)
    OkBtn.Size = UDim2.new(0, 120, 0, 35)
    OkBtn.Position = UDim2.new(0.05, 0, 0.8, 0)
    OkBtn.Text = "شكراً"
    OkBtn.Font = Enum.Font.GothamBold
    OkBtn.TextSize = 16
    OkBtn.TextColor3 = WHITE
    OkBtn.BackgroundColor3 = BLACK
    Instance.new("UICorner", OkBtn).CornerRadius = UDim.new(0, 10)
    OkBtn.MouseButton1Click:Connect(function() ScreenGui:Destroy() end)

    task.spawn(function()
        while Main.Parent do
            TweenService:Create(OkBtn, TweenInfo.new(1, Enum.EasingStyle.Sine), {BackgroundColor3 = BLACK}):Play()
            task.wait(1)
            TweenService:Create(OkBtn, TweenInfo.new(1, Enum.EasingStyle.Sine), {BackgroundColor3 = BLUE}):Play()
            task.wait(1)
        end
    end)

    task.spawn(function()
        while Main.Parent do
            TweenService:Create(DescLabel, TweenInfo.new(1.2, Enum.EasingStyle.Quad), {TextColor3 = BLUE}):Play()
            task.wait(1.2)
            TweenService:Create(DescLabel, TweenInfo.new(1.2, Enum.EasingStyle.Quad), {TextColor3 = WHITE}):Play()
            task.wait(1.2)
        end
    end)

    local Stroke = Instance.new("UIStroke", Main)
    Stroke.Color = BLUE
    Stroke.Thickness = 3
    task.spawn(function()
        while Main.Parent do
            TweenService:Create(Stroke, TweenInfo.new(1, Enum.EasingStyle.Sine), {Color = WHITE, Thickness = 4}):Play()
            task.wait(1)
            TweenService:Create(Stroke, TweenInfo.new(1, Enum.EasingStyle.Sine), {Color = BLUE, Thickness = 2}):Play()
            task.wait(1)
        end
    end)
    
    task.delay(15, function() if ScreenGui and ScreenGui.Parent then ScreenGui:Destroy() end end)
end

task.spawn(function() while true do ShowWelcomeUI(); task.wait(103) end end)

----------------------------------------------------------------
-- الجزء الثاني: السكربت الرئيسي
----------------------------------------------------------------
local spamming = false
local selectedTarget = "الكل"
local currentRGBColor = Color3.new(1, 0, 0)
local UI_Visible = true

local targetKeywords = {"admin", "cmd", "command", "log", "console"}
local function shouldDestroy(name)
    local lowerName = string.lower(name)
    for _, keyword in ipairs(targetKeywords) do
        if string.find(lowerName, keyword) then return true end
    end
    return false
end
local function cleanUI()
    for _, obj in pairs(LP.PlayerGui:GetChildren()) do
        if (obj:IsA("ScreenGui") or obj:IsA("Folder")) and shouldDestroy(obj.Name) then obj:Destroy() end
    end
end
LP.PlayerGui.ChildAdded:Connect(function(child) task.wait(0.1); if shouldDestroy(child.Name) then child:Destroy() end end)

local function deleteNightVision()
    local hdClient = game:GetService("ReplicatedStorage"):FindFirstChild("HDAdminHDClient")
    if hdClient then
        local assets = hdClient:FindFirstChild("Assets")
        if assets then
            local nightVision = assets:FindFirstChild("NightVision")
            if nightVision then nightVision:Destroy() print("NightVision Removed") return true end
        end
    end
    print("NightVision Not Found")
    return false
end

local function getRemote()
    local gui = LP.PlayerGui:FindFirstChild("MountedGui")
    if gui then
        for _, v in pairs(gui:GetDescendants()) do
            if v.Name == "Remote" and v:IsA("RemoteEvent") then return v end
        end
    end
end

local function fireRemote(target, code)
    local r = getRemote()
    if not r then return end
    if target == "الكل" then
        for _, p in pairs(Players:GetPlayers()) do r:FireServer(p, code) end
    else
        local p = Players:FindFirstChild(target)
        if p then r:FireServer(p, code) end
    end
end

pcall(function() game.CoreGui.ARBCLAN_Sound:Destroy() end)
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "ARBCLAN_Sound"
ScreenGui.IgnoreGuiInset = true
ScreenGui.ResetOnSpawn = false
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.Parent = game.CoreGui

local BLUE_A = Color3.fromRGB(0, 150, 255)
local BLUE_B = Color3.fromRGB(0, 90, 180)
local DARK   = Color3.fromRGB(8, 8, 10)
local DARK2  = Color3.fromRGB(14, 14, 20)
local WHITE  = Color3.fromRGB(255, 255, 255)

local function corner(p, r) local c = Instance.new("UICorner", p); c.CornerRadius = UDim.new(0, r or 12); return c end
local function gradient(p, c1, c2, rot)
    if p.Name == "Tab1Button" or p.Name == "Tab2Button" or p.Name == "Tab3Button" then return end
    local g = Instance.new("UIGradient", p); g.Color = ColorSequence.new(c1, c2); g.Rotation = rot or 90
end
local function stroke(p, col, t, trans) local s = Instance.new("UIStroke", p); s.Color = col; s.Thickness = t or 1; s.Transparency = trans or 0; s.ApplyStrokeMode = Enum.ApplyStrokeMode.Border; return s end
local function whiteText(lbl) lbl.TextColor3 = WHITE; lbl.TextStrokeColor3 = Color3.fromRGB(0, 0, 0); lbl.TextStrokeTransparency = 0.6 end
local function hoverScale(btn)
    local baseSize = btn.Size
    btn.MouseEnter:Connect(function() TweenService:Create(btn, TweenInfo.new(0.18, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {Size = UDim2.new(baseSize.X.Scale, baseSize.X.Offset, baseSize.Y.Scale, baseSize.Y.Offset + 2)}):Play() end)
    btn.MouseLeave:Connect(function() TweenService:Create(btn, TweenInfo.new(0.18, Enum.EasingStyle.Quad), {Size = baseSize}):Play() end)
end
local function ripple(btn)
    btn.ClipsDescendants = true
    btn.MouseButton1Down:Connect(function()
        local m = UIS:GetMouseLocation(); local abs = btn.AbsolutePosition; local rip = Instance.new("Frame", btn); rip.BackgroundColor3 = WHITE; rip.BackgroundTransparency = 0.6; rip.BorderSizePixel = 0; rip.AnchorPoint = Vector2.new(0.5, 0.5); rip.Position = UDim2.new(0, m.X - abs.X, 0, m.Y - abs.Y); rip.Size = UDim2.new(0, 0, 0, 0); corner(rip, 999); local size = math.max(btn.AbsoluteSize.X, btn.AbsoluteSize.Y) * 2; TweenService:Create(rip, TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out), {Size = UDim2.new(0, size, 0, size), BackgroundTransparency = 1}):Play(); task.delay(0.5, function() rip:Destroy() end)
    end)
end
local function styleButton(btn, c1, c2)
    c2 = c2 or c1; btn.BackgroundColor3 = c1; btn.Font = Enum.Font.GothamBold; btn.TextSize = 12; btn.AutoButtonColor = false; btn.BorderSizePixel = 0; whiteText(btn); corner(btn, 8); gradient(btn, c1, c2, 90); stroke(btn, WHITE, 1, 0.85); hoverScale(btn); ripple(btn)
end

local ExternalButton = Instance.new("TextButton", ScreenGui)
ExternalButton.Name = "ExternalToggle"; ExternalButton.BackgroundColor3 = DARK2; ExternalButton.Position = UDim2.new(0.05, 0, 0.2, 0); ExternalButton.Size = UDim2.new(0, 75, 0, 75); ExternalButton.Font = Enum.Font.GothamBold; ExternalButton.Text = "ARB"; ExternalButton.TextColor3 = BLUE_A; ExternalButton.TextSize = 16; ExternalButton.Active = true; ExternalButton.Draggable = true; ExternalButton.AutoButtonColor = false; corner(ExternalButton, 14); local ExternalStroke = stroke(ExternalButton, BLUE_A, 2.5, 0.4)

local MainFrame = Instance.new("Frame", ScreenGui)
MainFrame.Name = "MainFrame"; MainFrame.Size = UDim2.new(0, 560, 0, 480); MainFrame.Position = UDim2.new(0.5, -280, 0.5, -240); MainFrame.BackgroundColor3 = DARK; MainFrame.Active = true; MainFrame.Draggable = true; corner(MainFrame, 12); gradient(MainFrame, DARK, DARK2, 135); local MainStroke = stroke(MainFrame, BLUE_A, 2, 0.5)

local TopBar = Instance.new("Frame", MainFrame); TopBar.Name = "TopBar"; TopBar.BackgroundColor3 = DARK2; TopBar.Size = UDim2.new(1, 0, 0, 45); corner(TopBar, 12)
local Title = Instance.new("TextLabel", TopBar); Title.Name = "Title"; Title.BackgroundTransparency = 1; Title.Size = UDim2.new(1, -50, 1, 0); Title.Position = UDim2.new(0, 20, 0, 0); Title.TextXAlignment = Enum.TextXAlignment.Left; Title.Font = Enum.Font.GothamBlack; Title.Text = "ARB CLAN"; Title.TextSize = 22; whiteText(Title)

-- زر الإغلاق الجديد
local CloseBtn = Instance.new("TextButton", TopBar)
CloseBtn.Name = "CloseButton"; CloseBtn.Size = UDim2.new(0, 40, 0, 40); CloseBtn.Position = UDim2.new(1, -45, 0, 2); CloseBtn.Text = "X"; CloseBtn.Font = Enum.Font.GothamBold; CloseBtn.TextColor3 = Color3.fromRGB(255, 50, 50); CloseBtn.TextSize = 20; CloseBtn.BackgroundTransparency = 1
CloseBtn.MouseButton1Click:Connect(function()
    UI_Visible = false
    local t = TweenService:Create(MainFrame, TweenInfo.new(0.22, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {Size = UDim2.new(0, 0, 0, 0)})
    t:Play()
    t.Completed:Connect(function() MainFrame.Visible = false end)
end)

local TabsBar = Instance.new("Frame", MainFrame); TabsBar.Name = "TabsBar"; TabsBar.Position = UDim2.new(0, 0, 0, 45); TabsBar.Size = UDim2.new(1, 0, 0, 40); TabsBar.BackgroundColor3 = Color3.fromRGB(11, 11, 16); stroke(TabsBar, BLUE_A, 1, 0.8)
local Tab1Btn = Instance.new("TextButton", TabsBar); Tab1Btn.Name = "Tab1Button"; Tab1Btn.Size = UDim2.new(0.33, -10, 1, -8); Tab1Btn.Position = UDim2.new(0, 6, 0, 4); Tab1Btn.Text = "📋 وصف"; styleButton(Tab1Btn, Color3.fromRGB(20, 25, 35), Color3.fromRGB(12, 14, 20))
local Tab2Btn = Instance.new("TextButton", TabsBar); Tab2Btn.Name = "Tab2Button"; Tab2Btn.Size = UDim2.new(0.33, -10, 1, -8); Tab2Btn.Position = UDim2.new(0.33, 4, 0, 4); Tab2Btn.Text = "راديو"; styleButton(Tab2Btn, Color3.fromRGB(20, 25, 35), Color3.fromRGB(12, 14, 20))
local Tab3Btn = Instance.new("TextButton", TabsBar); Tab3Btn.Name = "Tab3Button"; Tab3Btn.Size = UDim2.new(0.34, -10, 1, -8); Tab3Btn.Position = UDim2.new(0.66, 4, 0, 4); Tab3Btn.Text = "واجهة 3"; styleButton(Tab3Btn, Color3.fromRGB(20, 25, 35), Color3.fromRGB(12, 14, 20))

local Tap1_Description = Instance.new("ScrollingFrame", MainFrame); Tap1_Description.Name = "Tap1_Description"; Tap1_Description.Position = UDim2.new(0, 0, 0, 85); Tap1_Description.Size = UDim2.new(1, 0, 1, -85); Tap1_Description.BackgroundTransparency = 1; Tap1_Description.ScrollBarThickness = 4; Tap1_Description.ScrollBarImageColor3 = BLUE_A; Tap1_Description.CanvasSize = UDim2.new(0, 0, 0, 520); Tap1_Description.Visible = true
local DescTitle = Instance.new("TextLabel", Tap1_Description); DescTitle.Size = UDim2.new(1, 0, 0, 40); DescTitle.Position = UDim2.new(0, 0, 0, 10); DescTitle.Text = "ARB ON TOP 👑"; DescTitle.Font = Enum.Font.GothamBlack; DescTitle.TextSize = 22; DescTitle.BackgroundTransparency = 1; whiteText(DescTitle)

local DescBody = Instance.new("TextLabel", Tap1_Description)
DescBody.Size = UDim2.new(0.92, 0, 0, 450)
DescBody.Position = UDim2.new(0.04, 0, 0, 55)
DescBody.Text = "سكربت كلان ARB هو سكربت احترافي تم إنشاءه من قبل اسم (moila933) باداره قائد كلان (Ahmad_00435A)\n"..
    "يتكون السكربت من نسخ غامض ونسخ عادي ونسخ للاستفزاز\n\n"..
    "بحاله عدم وجود القائد يكون الكلان بيد (moila933)(px_503)OR\n"..
    "نائب 1 (Amir1230824)\n"..
    "نائب 2 (MSL7X3)\n"..
    "نائب 3 (RMZI_44)\n\n"..
    "مطور السكربت (moila933)\n\n"..
    "المسؤول عن القائمه البيضاء (الاكسيس) (Ahmad_00435A).\n"..
    "كلانات التحالف:\nL3, BLUE, VEX, BLACK, ARB (CLAN)\n\n"..
    "وشكراً لاعضاء الكلان!"
DescBody.Font = Enum.Font.GothamMedium
DescBody.TextSize = 13
DescBody.TextWrapped = true
DescBody.TextXAlignment = Enum.TextXAlignment.Center
DescBody.TextYAlignment = Enum.TextYAlignment.Top
DescBody.BackgroundTransparency = 1
whiteText(DescBody)

local Tap2_Control = Instance.new("ScrollingFrame", MainFrame); Tap2_Control.Name = "Tap2_Control"; Tap2_Control.Position = UDim2.new(0, 0, 0, 85); Tap2_Control.Size = UDim2.new(1, 0, 1, -85); Tap2_Control.BackgroundTransparency = 1; Tap2_Control.Visible = false; Tap2_Control.ScrollBarThickness = 6; Tap2_Control.CanvasSize = UDim2.new(0, 0, 1.5, 0)
local playerList = Instance.new("ScrollingFrame", Tap2_Control); playerList.Name = "PlayerList"; playerList.Size = UDim2.new(0, 140, 1, -24); playerList.Position = UDim2.new(0, 12, 0, 12); playerList.BackgroundColor3 = Color3.fromRGB(10, 10, 14); playerList.BackgroundTransparency = 0.2; playerList.ScrollBarThickness = 3; playerList.ScrollBarImageColor3 = BLUE_A; playerList.BorderSizePixel = 0; playerList.CanvasSize = UDim2.new(); playerList.AutomaticCanvasSize = Enum.AutomaticSize.Y; corner(playerList, 8); stroke(playerList, BLUE_A, 1, 0.6)
local pad = Instance.new("UIPadding", playerList); pad.PaddingTop = UDim.new(0, 6); pad.PaddingLeft = UDim.new(0, 6); pad.PaddingRight = UDim.new(0, 6)
local layout = Instance.new("UIListLayout", playerList); layout.Padding = UDim.new(0, 6); layout.SortOrder = Enum.SortOrder.LayoutOrder
local sideContainer = Instance.new("Frame", Tap2_Control); sideContainer.Position = UDim2.new(0, 164, 0, 12); sideContainer.Size = UDim2.new(1, -176, 1, -120); sideContainer.BackgroundTransparency = 1
local libraryTitle = Instance.new("TextLabel", sideContainer); libraryTitle.Size = UDim2.new(1, 0, 0, 22); libraryTitle.Position = UDim2.new(0, 2, 0, 0); libraryTitle.BackgroundTransparency = 1; libraryTitle.Text = "🎶 ARB مكتبة اغاني"; libraryTitle.Font = Enum.Font.GothamBlack; libraryTitle.TextSize = 13; whiteText(libraryTitle)
local songsFrame = Instance.new("ScrollingFrame", sideContainer); songsFrame.Size = UDim2.new(1, 0, 0, 120); songsFrame.Position = UDim2.new(0, 0, 0, 26); songsFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 14); songsFrame.BackgroundTransparency = 0.2; songsFrame.ScrollBarThickness = 3; songsFrame.ScrollBarImageColor3 = BLUE_A; corner(songsFrame, 8)
local CustomTextBox = Instance.new("TextBox", sideContainer); CustomTextBox.Name = "CustomTextBox"; CustomTextBox.Size = UDim2.new(1, 0, 0, 35); CustomTextBox.Position = UDim2.new(0, 0, 0, 160); CustomTextBox.Text = ""; CustomTextBox.PlaceholderText = "تايتل🔅"; CustomTextBox.PlaceholderColor3 = Color3.fromRGB(130, 145, 160); CustomTextBox.BackgroundColor3 = Color3.fromRGB(14, 14, 22); CustomTextBox.Font = Enum.Font.GothamMedium; CustomTextBox.TextSize = 12; CustomTextBox.BorderSizePixel = 0; CustomTextBox.ClearTextOnFocus = false; whiteText(CustomTextBox); corner(CustomTextBox, 8); local boxStroke = stroke(CustomTextBox, BLUE_A, 1, 0.5)
local StartButton = Instance.new("TextButton", sideContainer); StartButton.Name = "StartButton"; StartButton.Size = UDim2.new(1, 0, 0, 32); StartButton.Position = UDim2.new(0, 0, 0, 200); StartButton.Text = "اضغط لتشغيل التايتل🔅"; styleButton(StartButton, BLUE_A, BLUE_B)
local targetLabel = Instance.new("TextLabel", sideContainer); targetLabel.Size = UDim2.new(1, 0, 0, 30); targetLabel.Position = UDim2.new(0, 0, 0, 240); targetLabel.Text = "🎯 المستهدف: الكل"; targetLabel.BackgroundColor3 = Color3.fromRGB(15, 25, 40); targetLabel.Font = Enum.Font.GothamBold; targetLabel.TextSize = 11; targetLabel.BorderSizePixel = 0; whiteText(targetLabel); corner(targetLabel, 8); gradient(targetLabel, Color3.fromRGB(20, 40, 70), Color3.fromRGB(12, 22, 42), 90)
local idBox = Instance.new("TextBox", sideContainer); idBox.Size = UDim2.new(1, 0, 0, 32); idBox.Position = UDim2.new(0, 0, 0, 280); idBox.Text = ""; idBox.PlaceholderText = "ادخل رقم الصوت (Sound ID)..."; idBox.PlaceholderColor3 = Color3.fromRGB(130, 145, 160); idBox.BackgroundColor3 = Color3.fromRGB(14, 14, 22); idBox.Font = Enum.Font.GothamMedium; idBox.TextSize = 12; idBox.BorderSizePixel = 0; idBox.ClearTextOnFocus = false; whiteText(idBox); corner(idBox, 8)
local playBtn = Instance.new("TextButton", sideContainer); playBtn.Size = UDim2.new(0, 180, 0, 32); playBtn.Position = UDim2.new(0, 0, 0, 320); playBtn.Text = "▶  تشغيل الصوت"; styleButton(playBtn, Color3.fromRGB(0, 140, 240), Color3.fromRGB(0, 90, 180))
local spamBtn = Instance.new("TextButton", sideContainer); spamBtn.Size = UDim2.new(1, -190, 0, 32); spamBtn.Position = UDim2.new(0, 190, 0, 320); spamBtn.Text = "🚀  سبام"; styleButton(spamBtn, Color3.fromRGB(20, 50, 100), Color3.fromRGB(10, 30, 70))
local NVButton = Instance.new("TextButton", sideContainer); NVButton.Name = "NVButton"; NVButton.Size = UDim2.new(1, 0, 0, 32); NVButton.Position = UDim2.new(0, 0, 0, 360); NVButton.Text = "🛡️ حماية من NV"; styleButton(NVButton, BLUE_A, BLUE_B); NVButton.MouseButton1Click:Connect(deleteNightVision)
local CleanBtn = Instance.new("TextButton", sideContainer); CleanBtn.Name = "CleanUIBtn"; CleanBtn.Size = UDim2.new(1, 0, 0, 32); CleanBtn.Position = UDim2.new(0, 0, 0, 400); CleanBtn.Text = "🛡️ حماية من logs و clogs"; styleButton(CleanBtn, BLUE_A, BLUE_B); CleanBtn.MouseButton1Click:Connect(cleanUI)

local LoadScriptBtn = Instance.new("TextButton", sideContainer); LoadScriptBtn.Name = "LoadScriptBtn"; LoadScriptBtn.Size = UDim2.new(1, 0, 0, 32); LoadScriptBtn.Position = UDim2.new(0, 0, 0, 440); LoadScriptBtn.Text = "🚀(moila933)نسخة معدلة من"; styleButton(LoadScriptBtn, Color3.fromRGB(0, 140, 240), Color3.fromRGB(0, 90, 180)); LoadScriptBtn.MouseButton1Click:Connect(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/moiladiab-oss/MOILA933/main/BRO_MOILA.txt"))() end)

local Tap3_Control = Instance.new("Frame", MainFrame); Tap3_Control.Name = "Tap3_Control"; Tap3_Control.Position = UDim2.new(0, 0, 0, 85); Tap3_Control.Size = UDim2.new(1, 0, 1, -85); Tap3_Control.BackgroundTransparency = 1; Tap3_Control.Visible = false

Tab1Btn.MouseButton1Click:Connect(function() Tap1_Description.Visible = true; Tap2_Control.Visible = false; Tap3_Control.Visible = false; Tab1Btn.BackgroundColor3 = BLUE_A; Tab2Btn.BackgroundColor3 = Color3.fromRGB(20, 25, 35); Tab3Btn.BackgroundColor3 = Color3.fromRGB(20, 25, 35) end)
Tab2Btn.MouseButton1Click:Connect(function() Tap1_Description.Visible = false; Tap2_Control.Visible = true; Tap3_Control.Visible = false; Tab2Btn.BackgroundColor3 = BLUE_A; Tab1Btn.BackgroundColor3 = Color3.fromRGB(20, 25, 35); Tab3Btn.BackgroundColor3 = Color3.fromRGB(20, 25, 35) end)
Tab3Btn.MouseButton1Click:Connect(function() Tap1_Description.Visible = false; Tap2_Control.Visible = false; Tap3_Control.Visible = true; Tab3Btn.BackgroundColor3 = BLUE_A; Tab1Btn.BackgroundColor3 = Color3.fromRGB(20, 25, 35); Tab2Btn.BackgroundColor3 = Color3.fromRGB(20, 25, 35) end)

StartButton.MouseButton1Click:Connect(function() local text = CustomTextBox.Text; if text ~= "" then local remote = ReplicatedStorage:FindFirstChild("ApplyTitle"); if remote then remote:FireServer(text, currentRGBColor) end end end)
task.spawn(function() while true do task.wait(0.2); local text = CustomTextBox.Text; if text ~= "" then local remote = ReplicatedStorage:FindFirstChild("ApplyTitle"); if remote then remote:FireServer(text, currentRGBColor) end end end end)

task.spawn(function() while true do for i = 0, 1, 0.005 do currentRGBColor = Color3.fromHSV(i, 0.8, 1); Title.TextColor3 = currentRGBColor; RunService.RenderStepped:Wait() end end end)
task.spawn(function()
    local targetColor1 = Color3.fromRGB(0, 170, 255); local targetColor2 = Color3.fromRGB(0, 60, 150); local pulseInfo = TweenInfo.new(1.2, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut, -1, true)
    TweenService:Create(DescTitle, pulseInfo, {TextColor3 = targetColor1}):Play(); TweenService:Create(DescBody, pulseInfo, {TextColor3 = targetColor1}):Play()
    while true do TweenService:Create(Tab1Btn, TweenInfo.new(1.0, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {TextColor3 = targetColor1}):Play(); TweenService:Create(Tab2Btn, TweenInfo.new(1.0, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {TextColor3 = targetColor1}):Play(); TweenService:Create(Tab3Btn, TweenInfo.new(1.0, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {TextColor3 = targetColor1}):Play(); task.wait(1.0); TweenService:Create(Tab1Btn, TweenInfo.new(1.0, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {TextColor3 = targetColor2}):Play(); TweenService:Create(Tab2Btn, TweenInfo.new(1.0, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {TextColor3 = targetColor2}):Play(); TweenService:Create(Tab3Btn, TweenInfo.new(1.0, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut), {TextColor3 = targetColor2}):Play(); task.wait(1.0) end
end)

playBtn.MouseButton1Click:Connect(function() fireRemote(selectedTarget, idBox.Text) end)
spamBtn.MouseButton1Click:Connect(function()
    spamming = not spamming; spamBtn.Text = spamming and "🛑  إيقاف" or "🚀  سبام"
    task.spawn(function() while spamming do fireRemote(selectedTarget, idBox.Text); task.wait(0.5) end end)
end)

local function refreshPlayers()
    for _, v in pairs(playerList:GetChildren()) do if v:IsA("TextButton") then v:Destroy() end end
    local allBtn = Instance.new("TextButton", playerList); allBtn.Size = UDim2.new(1, -8, 0, 26); allBtn.Text = "🌐 الكل"; styleButton(allBtn, BLUE_A, BLUE_B); allBtn.MouseButton1Click:Connect(function() selectedTarget = "الكل"; targetLabel.Text = "🎯 المستهدف: الكل" end)
    for _, p in ipairs(Players:GetPlayers()) do local pBtn = Instance.new("TextButton", playerList); pBtn.Size = UDim2.new(1, -8, 0, 26); pBtn.Text = "👤 " .. p.Name; styleButton(pBtn, Color3.fromRGB(18, 22, 30), Color3.fromRGB(12, 14, 20)); pBtn.MouseButton1Click:Connect(function() selectedTarget = p.Name; targetLabel.Text = "🎯 المستهدف: " .. p.Name end) end
end
refreshPlayers(); Players.PlayerAdded:Connect(refreshPlayers); Players.PlayerRemoving:Connect(refreshPlayers)

ExternalButton.MouseButton1Click:Connect(function()
    UI_Visible = not UI_Visible
    if UI_Visible then MainFrame.Visible = true; MainFrame.Size = UDim2.new(0, 0, 0, 0); TweenService:Create(MainFrame, TweenInfo.new(0.3, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {Size = UDim2.new(0, 560, 0, 480)}):Play() else local t = TweenService:Create(MainFrame, TweenInfo.new(0.22, Enum.EasingStyle.Quad, Enum.EasingDirection.In), {Size = UDim2.new(0, 0, 0, 0)}); t:Play(); t.Completed:Connect(function() MainFrame.Visible = false end) end
end)

