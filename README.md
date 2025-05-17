local Players = game:GetService("Players")
local player = Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local TweenService = game:GetService("TweenService")

local ATTACK_DISTANCE = 30 -- distância máxima para atacar

local function getQuestInfo()
    local level = player.Data.Level.Value
    if level >= 1 and level <= 9 then
        return {
            npcName = "Pirate A",
            enemyName = "Pirate",
            questPosition = CFrame.new(-1164.25, 7.45, 1536.83),
            enemyPosition = CFrame.new(-1170.72, 7.45, 1537.17)
        }
    elseif level >= 10 and level <= 14 then
        return {
            npcName = "Bandit Leader",
            enemyName = "Bandit",
            questPosition = CFrame.new(1277.81, 7.45, -1280.57),
            enemyPosition = CFrame.new(1277.85, 7.45, -1270.55)
        }
    end
    return nil
end

local function moveToPosition(position)
    local distance = (humanoidRootPart.Position - position.Position).Magnitude
    local tweenInfo = TweenInfo.new(distance / 50)
    local tween = TweenService:Create(humanoidRootPart, tweenInfo, {CFrame = position})
    tween:Play()
    tween.Completed:Wait()
end

local function attackEnemy(enemy)
    while enemy and enemy.Parent and enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 do
        local distance = (humanoidRootPart.Position - enemy.HumanoidRootPart.Position).Magnitude
        if distance > ATTACK_DISTANCE then
            print("Inimigo muito longe, parando ataque.")
            break
        end
        ReplicatedStorage.Remotes.CommF_:InvokeServer("Attack", enemy)
        wait(0.5)
    end
end

while true do
    local quest = getQuestInfo()
    if not quest then
        print("Nível fora do range conhecido para farm.")
        break
    end

    moveToPosition(quest.questPosition)
    wait(1)

    ReplicatedStorage.Remotes.CommF_:InvokeServer("StartQuest", quest.npcName)
    wait(1)

    moveToPosition(quest.enemyPosition)
    wait(1)

    for _, enemy in pairs(workspace.Enemies:GetChildren()) do
        if enemy.Name == quest.enemyName and enemy:FindFirstChild("Humanoid") and enemy.Humanoid.Health > 0 then
            attackEnemy(enemy)
        end
    end

    wait(2)
end
