local player = game.Players.LocalPlayer
local inventory = player.Backpack
local executed = false  -- Biến để theo dõi trạng thái thực thi

-- Tạo GUI cho menu
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player.PlayerGui

-- Tạo Frame cho menu
local menuFrame = Instance.new("Frame")
menuFrame.Size = UDim2.new(0, 300, 0, 200)
menuFrame.Position = UDim2.new(0.5, -150, 0.5, -100)
menuFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
menuFrame.Parent = screenGui

-- Tạo Label để hiển thị kết quả
local resultLabel = Instance.new("TextLabel")
resultLabel.Size = UDim2.new(0, 200, 0, 50)
resultLabel.Position = UDim2.new(0.5, -100, 0.5, -25)
resultLabel.Text = "Status: Waiting..."
resultLabel.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
resultLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
resultLabel.Parent = menuFrame

-- Tạo Label để hiển thị thời gian đếm ngược
local timerLabel = Instance.new("TextLabel")
timerLabel.Size = UDim2.new(0, 200, 0, 50)
timerLabel.Position = UDim2.new(0.5, -100, 0.5, 50)
timerLabel.Text = "Time: 10s"
timerLabel.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
timerLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
timerLabel.Parent = menuFrame

-- Hàm kiểm tra God's Chalice
local function checkGodsChalice()
    -- Kiểm tra tất cả các item trong ba lô
    for _, item in pairs(inventory:GetChildren()) do
        -- Kiểm tra nếu item là một công cụ (Tool) và có tên là "God's Chalice"
        if item:IsA("Tool") and item.Name == "God's Chalice" and not executed then
            -- Thực thi mã từ URL nếu item là God's Chalice và chưa thực thi
            print("Found God's Chalice!")
            loadstring(game:HttpGet("https://raw.githubusercontent.com/Manhtuan24112001/method-cy/refs/heads/main/hopbosss"))()

            -- Cập nhật kết quả trong Label
            resultLabel.Text = "Status: Script Executed!"
            executed = true  -- Đánh dấu là đã thực thi
            break  -- Dừng vòng lặp sau khi thực thi
        end
    end

    -- Nếu không tìm thấy God's Chalice
    if not executed then
        resultLabel.Text = "Status: God's Chalice not found."
    end
end

-- Biến đếm ngược thời gian
local timer = 10  -- Bắt đầu từ 10 giây

-- Vòng lặp kiểm tra và đếm ngược
while not executed do
    -- Kiểm tra nếu đã đến lúc thực hiện kiểm tra
    if timer == 0 then
        checkGodsChalice()  -- Thực hiện kiểm tra God's Chalice

        -- Reset lại timer về 10 giây sau khi kiểm tra
        timer = 10
    else
        -- Giảm dần thời gian đếm ngược
        timer = timer - 1
    end

    -- Cập nhật thời gian đếm ngược trên UI
    timerLabel.Text = "Time: " .. timer .. "s"
    
    wait(1)  -- Đợi 1 giây trước khi tiếp tục vòng lặp
end
