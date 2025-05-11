-- LocalScript dentro de ToggleUI

local player = game.Players.LocalPlayer
local gui = script.Parent -- ToggleUI

-- Referências aos elementos da interface
local mainFrame = gui:FindFirstChild("MainFrame")
local messageLabel = mainFrame and mainFrame:FindFirstChild("MessageLabel")
local toggleButton = mainFrame and mainFrame:FindFirstChild("ToggleButton")

-- Estado inicial
local isActive = false

-- Função para mostrar a mensagem por 3 segundos
function showMessage()
    if messageLabel then
        messageLabel.Visible = true
        task.wait(3) -- Mais seguro que wait() em LocalScripts
        messageLabel.Visible = false
    end
end

-- Conecta evento do botão
if toggleButton then
    toggleButton.MouseButton1Click:Connect(function()
        isActive = not isActive -- Alterna o estado

        if isActive then
            showMessage() -- Mostra a mensagem
        else
            print("Missão desativada.")
        end
    end)
end
