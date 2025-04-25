-- Script de Auto Treino para Dragon Ball Rage (Mobile)
-- Suporta Ki, Defesa e Ataque com ativação/desativação
-- Aviso: Use apenas em ambientes de teste. Automação pode violar os termos do Roblox.

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local VirtualInputManager = game:GetService("VirtualInputManager")

-- Configurações
local autoTrainKiEnabled = false
local autoTrainDefenseEnabled = false
local autoTrainAttackEnabled = false

local touchInterval = 0.5 -- Intervalo entre toques (em segundos)
local kiTouchPosition = Vector2.new(500, 500) -- Posição do botão de Ki (ajuste)
local defenseTouchPosition = Vector2.new(600, 500) -- Posição do botão de Defesa (ajuste)
local attackTouchPosition = Vector2.new(700, 500) -- Posição do botão de Ataque (ajuste)

-- Função para simular toque na tela
local function simulateTouch(position)
    VirtualInputManager:SendTouchEvent(true, position, 1)
    wait(0.1)
    VirtualInputManager:SendTouchEvent(false, position, 1)
end

-- Funções de auto treino
local function autoTrainKi()
    while autoTrainKiEnabled do
        if not LocalPlayer.Character or not LocalPlayer.Character.Humanoid then
            wait(1) -- Aguarda o personagem carregar
            continue
        end
        simulateTouch(kiTouchPosition)
        wait(touchInterval)
    end
end

local function autoTrainDefense()
    while autoTrainDefenseEnabled do
        if not LocalPlayer.Character or not LocalPlayer.Character.Humanoid then
            wait(1) -- Aguarda o personagem carregar
            continue
        end
        simulateTouch(defenseTouchPosition)
        wait(touchInterval)
    end
end

local function autoTrainAttack()
    while autoTrainAttackEnabled do
        if not LocalPlayer.Character or not LocalPlayer.Character.Humanoid then
            wait(1) -- Aguarda o personagem carregar
            continue
        end
        simulateTouch(attackTouchPosition)
        wait(touchInterval)
    end
end

-- Funções de ativação
local function enableAutoTrainKi()
    if not autoTrainKiEnabled then
        autoTrainKiEnabled = true
        print("Auto Treino de Ki: Ativado")
        spawn(autoTrainKi) -- Inicia o loop de Ki
    else
        print("Auto Treino de Ki: Já está ativado")
    end
end

local function enableAutoTrainDefense()
    if not autoTrainDefenseEnabled then
        autoTrainDefenseEnabled = true
        print("Auto Treino de Defesa: Ativado")
        spawn(autoTrainDefense) -- Inicia o loop de Defesa
    else
        print("Auto Treino de Defesa: Já está ativado")
    end
end

local function enableAutoTrainAttack()
    if not autoTrainAttackEnabled then
        autoTrainAttackEnabled = true
        print("Auto Treino de Ataque: Ativado")
        spawn(autoTrainAttack) -- Inicia o loop de Ataque
    else
        print("Auto Treino de Ataque: Já está ativado")
    end
end

-- Funções de desativação
local function disableAutoTrainKi()
    if autoTrainKiEnabled then
        autoTrainKiEnabled = false
        print("Auto Treino de Ki: Desativado")
    else
        print("Auto Treino de Ki: Já está desativado")
    end
end

local function disableAutoTrainDefense()
    if autoTrainDefenseEnabled then
        autoTrainDefenseEnabled = false
        print("Auto Treino de Defesa: Desativado")
    else
        print("Auto Treino de Defesa: Já está desativado")
    end
end

local function disableAutoTrainAttack()
    if autoTrainAttackEnabled then
        autoTrainAttackEnabled = false
        print("Auto Treino de Ataque: Desativado")
    else
        print("Auto Treino de Ataque: Já está desativado")
    end
end

-- Exemplo de uso via executor
print("Script de Auto Treino (Mobile) carregado.")
print("Comandos disponíveis no executor:")
print("enableAutoTrainKi() - Ativa treino de Ki")
print("disableAutoTrainKi() - Desativa treino de Ki")
print("enableAutoTrainDefense() - Ativa treino de Defesa")
print("disableAutoTrainDefense() - Desativa treino de Defesa")
print("enableAutoTrainAttack() - Ativa treino de Ataque")
print("disableAutoTrainAttack() - Desativa treino de Ataque")
