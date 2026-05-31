-- Menu Delta CDT V26 - Eclipse Edition (Criado por NOIA)
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local FrameCorner = Instance.new("UICorner")
local Title = Instance.new("TextLabel")
local TitleCorner = Instance.new("UICorner")
local Grav100 = Instance.new("TextButton")
local Grav80 = Instance.new("TextButton")
local Grav60 = Instance.new("TextButton")
local Grav20 = Instance.new("TextButton")
local GravNormal = Instance.new("TextButton")

-- Botão de Minimizar (Bolinha)
local ToggleBtn = Instance.new("TextButton")
local ToggleCorner = Instance.new("UICorner")

ScreenGui.Parent = game:GetService("CoreGui") or game.Players.LocalPlayer:WaitForChild("PlayerGui")
ScreenGui.ResetOnSpawn = false

-- INTERFACE V26: Eclipse Theme (Preto Fosco com Verde Limão Neon)
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(12, 12, 12)
Frame.Position = UDim2.new(0.15, 0, 0.25, 0)
Frame.Size = UDim2.new(0, 240, 0, 260)
Frame.Active = true
Frame.BorderSizePixel = 1
Frame.BorderColor3 = Color3.fromRGB(46, 204, 113) -- Verde Neon
Frame.Visible = true

-- CRIAÇÃO DA BOLINHA FLUTUANTE (Botão de Abrir/Fechar)
ToggleBtn.Parent = ScreenGui
ToggleBtn.Size = UDim2.new(0, 45, 0, 45)
ToggleBtn.Position = UDim2.new(0.05, 0, 0.25, 0)
ToggleBtn.BackgroundColor3 = Color3.fromRGB(46, 204, 113) -- Verde Neon (Menu Aberto)
ToggleBtn.Text = "⚡"
ToggleBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
ToggleBtn.TextSize = 18
ToggleBtn.Font = Enum.Font.GothamBold
ToggleBtn.Active = true

ToggleCorner.CornerRadius = UDim.new(1, 0)
ToggleCorner.Parent = ToggleBtn

-- Sistema de Arrastar Manual Otimizado
local UserInputService = game:GetService("UserInputService")

local function ConfigurarArrasto(guiElement)
    local dragging, dragInput, dragStart, startPos
    
    local function update(input)
        local delta = input.Position - dragStart
        guiElement.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end

    guiElement.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            dragging = true
            dragStart = input.Position
            startPos = guiElement.Position
            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)

    guiElement.InputChanged:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch then
            dragInput = input
        end
    end)

    UserInputService.InputChanged:Connect(function(input)
        if input == dragInput and dragging then
            update(input)
        end
    end)
end

ConfigurarArrasto(Frame)
ConfigurarArrasto(ToggleBtn)

-- LÓGICA DE ABRIR E FECHAR AO CLICAR NA BOLINHA
ToggleBtn.MouseButton1Click:Connect(function()
    if Frame.Visible then
        Frame.Visible = false
        ToggleBtn.BackgroundColor3 = Color3.fromRGB(28, 28, 30) -- Cinza Escuro (Menu Fechado)
        ToggleBtn.Text = "❌"
    else
        Frame.Visible = true
        ToggleBtn.BackgroundColor3 = Color3.fromRGB(46, 204, 113) -- Verde Neon (Menu Aberto)
        ToggleBtn.Text = "⚡"
    end
end)

FrameCorner.CornerRadius = UDim.new(0, 12)
FrameCorner.Parent = Frame

-- Barra de Título V26
Title.Parent = Frame
Title.Size = UDim2.new(1, 0, 0, 38)
Title.BackgroundColor3 = Color3.fromRGB(27, 38, 59) -- Azul Escuro Premium
Title.Text = "CDT PERFORMANCE | ⚡ NOIA ⚡"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 11
Title.Font = Enum.Font.GothamBold

TitleCorner.CornerRadius = UDim.new(0, 12)
TitleCorner.Parent = Title

-- Função para Estilizar Botões V26
local function criarBotaoV26(botaof, texto, posicao, cor)
    botaof.Parent = Frame
    botaof.Size = UDim2.new(0.9, 0, 0, 32)
    botaof.Position = posicao
    botaof.BackgroundColor3 = cor
    botaof.Text = texto
    botaof.TextColor3 = Color3.fromRGB(255, 255, 255)
    botaof.TextSize = 12
    botaof.Font = Enum.Font.GothamSemibold
    local btnCorner = Instance.new("UICorner")
    btnCorner.CornerRadius = UDim.new(0, 6)
    btnCorner.Parent = botaof
end

-- Botões Alinhados (Texto corrigido sem a palavra 'Rampa')
criarBotaoV26(Grav100, "Drift (Grav: 100)", UDim2.new(0.05, 0, 0.18, 0), Color3.fromRGB(28, 28, 30))
criarBotaoV26(Grav80, "Drift (Grav: 80)", UDim2.new(0.05, 0, 0.34, 0), Color3.fromRGB(28, 28, 30))
criarBotaoV26(Grav60, "Drift (Grav: 60)", UDim2.new(0.05, 0, 0.50, 0), Color3.fromRGB(28, 28, 30))
criarBotaoV26(Grav20, "Drift (Grav: 20)", UDim2.new(0.05, 0, 0.66, 0), Color3.fromRGB(28, 28, 30))
criarBotaoV26(GravNormal, "DESATIVAR MOD", UDim2.new(0.05, 0, 0.84, 0), Color3.fromRGB(46, 204, 113))

-- Lógica de Drift Universal Corrigida
local player = game.Players.LocalPlayer
local gravidadeAlvo = 196.2
local modAtivo = false

task.spawn(function()
    while true do
        if modAtivo then
            workspace.Gravity = gravidadeAlvo
            pcall(function()
                local char = player.Character
                if char and char:FindFirstChildOfClass("Humanoid") then
                    local seat = char.Humanoid.SeatPart
                    if seat and seat:IsA("VehicleSeat") then
                        local direcao = seat.SteerFloat
                        local velocidadeVelha = seat.AssemblyLinearVelocity
                        local direcaoOlhar = seat.CFrame.LookVector
                        local direcaoLado = seat.CFrame.RightVector
                        local velocidadeFrente = velocidadeVelha:Dot(direcaoOlhar)
                        
                        if math.abs(velocidadeFrente) > 10 then
                            if math.abs(direcao) > 0.1 then
                                local velocidadeLateralAtual = velocidadeVelha:Dot(direcaoLado)
                                local forcaLateral = direcaoLado * (direcao * math.abs(velocidadeFrente) * 0.22)
                                local forcaFrente = direcaoOlhar * velocityFrente
                                
                                seat.AssemblyLinearVelocity = Vector3.new(
                                    forcaFrente.X + (forcaLateral.X * 0.7),
                                    velocidadeVelha.Y,
                                    forcaFrente.Z + (forcaLateral.Z * 0.7)
                                )
                                
                                seat.AssemblyAngularVelocity = Vector3.new(
                                    seat.AssemblyAngularVelocity.X,
                                    -direcao * 1.8,
                                    seat.AssemblyAngularVelocity.Z
                                )
                            end
                        end
                        
                        -- TRAVA ANTI-FLING REALISTA
                        local angular = seat.AssemblyAngularVelocity
                        if math.abs(angular.X) > 6 or math.abs(angular.Z) > 6 then
                            seat.AssemblyAngularVelocity = Vector3.new(angular.X * 0.2, angular.Y, angular.Z * 0.2)
                        end
                    end
                end
            end)
        end
        task.wait(0.015)
    end
end)

-- Conexões dos Botões
local function ativarModV26(grav)
    gravidadeAlvo = grav
    modAtivo = true
end

Grav100.MouseButton1Click:Connect(function() ativarModV26(100) end)
Grav80.MouseButton1Click:Connect(function() ativarModV26(80) end)
Grav60.MouseButton1Click:Connect(function() ativarModV26(60) end)
Grav20.MouseButton1Click:Connect(function() ativarModV26(20) end)

GravNormal.MouseButton1Click:Connect(function()
    modAtivo = false
    workspace.Gravity = 196.2
end)
