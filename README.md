
function CheckQuest()
    local player = game.Players.LocalPlayer
    if not player or not player:FindFirstChild("Data") or not player.Data:FindFirstChild("Level") then
        warn("Player ou dados de nível não encontrados.")
        return nil
    end

    local Level = player.Data.Level.Value
    local MyLevel = Level

    -- Verifica se está no World1 (assumindo que World1 é uma variável booleana definida em outro lugar)
    if not World1 then
        warn("World1 não está ativo.")
        return nil
    end

    local LevelFarm, NameQuest, QuestLv, CFrameQuestPos, CFrameMon

    if MyLevel >= 1 and MyLevel <= 9 then
        LevelFarm = "Bandit [Lv. 5]"
        NameQuest = "BanditQuest1"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(1060, 17, 1547)
        CFrameMon = CFrame.new(1199, 28, 1547)

    elseif MyLevel >= 10 and MyLevel <= 14 then
        LevelFarm = "Monkey [Lv. 14]"
        NameQuest = "JungleQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(-1602, 36, 153)
        CFrameMon = CFrame.new(-1448, 67, 40)

    elseif MyLevel >= 15 and MyLevel <= 29 then
        LevelFarm = "Gorilla [Lv. 20]"
        NameQuest = "JungleQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(-1602, 36, 153)
        CFrameMon = CFrame.new(-1237, 6, -486)

    elseif MyLevel >= 30 and MyLevel <= 39 then
        LevelFarm = "Pirate [Lv. 35]"
        NameQuest = "BuggyQuest1"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(-1141, 5, 3826)
        CFrameMon = CFrame.new(-1213, 44, 3893)

    elseif MyLevel >= 40 and MyLevel <= 59 then
        LevelFarm = "Brute [Lv. 45]"
        NameQuest = "BuggyQuest1"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(-1141, 5, 3826)
        CFrameMon = CFrame.new(-1088, 14, 4281)

    elseif MyLevel >= 60 and MyLevel <= 74 then
        LevelFarm = "Desert Bandit [Lv. 60]"
        NameQuest = "DesertQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(896, 7, 4483)
        CFrameMon = CFrame.new(928, 22, 4480)

    elseif MyLevel >= 75 and MyLevel <= 89 then
        LevelFarm = "Desert Officer [Lv. 70]"
        NameQuest = "DesertQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(896, 7, 4483)
        CFrameMon = CFrame.new(1572, 10, 4373)

    elseif MyLevel >= 90 and MyLevel <= 119 then
        LevelFarm = "Snow Bandit [Lv. 90]"
        NameQuest = "SnowQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(1386, 87, -1297)
        CFrameMon = CFrame.new(1355, 87, -1372)

    elseif MyLevel >= 120 and MyLevel <= 149 then
        LevelFarm = "Snowman [Lv. 100]"
        NameQuest = "SnowQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(1386, 87, -1297)
        CFrameMon = CFrame.new(1204, 144, -1451)

    elseif MyLevel >= 150 and MyLevel <= 174 then
        LevelFarm = "Chief Petty Officer [Lv. 120]"
        NameQuest = "MarineQuest2"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(-5033, 29, 4324)
        CFrameMon = CFrame.new(-4871, 64, 4493)

    elseif MyLevel >= 175 and MyLevel <= 189 then
        LevelFarm = "Sky Bandit [Lv. 150]"
        NameQuest = "SkyQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(-4842, 717, -2623)
        CFrameMon = CFrame.new(-4951, 365, -2890)

    elseif MyLevel >= 190 and MyLevel <= 209 then
        LevelFarm = "Dark Master [Lv. 175]"
        NameQuest = "SkyQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(-4842, 717, -2623)
        CFrameMon = CFrame.new(-5250, 389, -2272)

    elseif MyLevel >= 210 and MyLevel <= 249 then
        LevelFarm = "Prisoner [Lv. 190]"
        NameQuest = "PrisonerQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(5308, 2, 474)
        CFrameMon = CFrame.new(5411, 96, 744)

    elseif MyLevel >= 250 and MyLevel <= 274 then
        LevelFarm = "Dangerous Prisoner [Lv. 210]"
        NameQuest = "PrisonerQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(5308, 2, 474)
        CFrameMon = CFrame.new(4977, 69, 778)

    elseif MyLevel >= 275 and MyLevel <= 299 then
        LevelFarm = "Toga Warrior [Lv. 250]"
        NameQuest = "ColosseumQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(-1576, 8, -2985)
        CFrameMon = CFrame.new(-1871, 39, -2917)

    elseif MyLevel >= 300 and MyLevel <= 324 then
        LevelFarm = "Gladiator [Lv. 275]"
        NameQuest = "ColosseumQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(-1576, 8, -2985)
        CFrameMon = CFrame.new(-1294, 56, -3338)

    elseif MyLevel >= 325 and MyLevel <= 374 then
        LevelFarm = "Military Soldier [Lv. 300]"
        NameQuest = "MagmaQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(-5313, 12, 8516)
        CFrameMon = CFrame.new(-5483, 64, 8463)

    elseif MyLevel >= 375 and MyLevel <= 399 then
        LevelFarm = "Military Spy [Lv. 325]"
        NameQuest = "MagmaQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(-5313, 12, 8516)
        CFrameMon = CFrame.new(-5815, 84, 8820)

    elseif MyLevel >= 400 and MyLevel <= 449 then
        LevelFarm = "Fishman Warrior [Lv. 375]"
        NameQuest = "FishmanQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(61123, 19, 1569)
        CFrameMon = CFrame.new(60844, 80, 1297)

    elseif MyLevel >= 450 and MyLevel <= 474 then
        LevelFarm = "Fishman Commando [Lv. 400]"
        NameQuest = "FishmanQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(61123, 19, 1569)
        CFrameMon = CFrame.new(61891, 70, 1434)

    elseif MyLevel >= 475 and MyLevel <= 524 then
        LevelFarm = "God's Guard [Lv. 450]"
        NameQuest = "SkyExp1Quest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(-4721, 845, -1954)
        CFrameMon = CFrame.new(-4696, 845, -1925)

    elseif MyLevel >= 525 and MyLevel <= 549 then
        LevelFarm = "Shanda [Lv. 475]"
        NameQuest = "SkyExp1Quest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(-4721, 845, -1954)
        CFrameMon = CFrame.new(-7685, 5566, -502)

    elseif MyLevel >= 550 and MyLevel <= 624 then
        LevelFarm = "Royal Squad [Lv. 525]"
        NameQuest = "SkyExp2Quest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(-7904, 5546, -380)
        CFrameMon = CFrame.new(-7677, 5607, -1460)

    elseif MyLevel >= 625 and MyLevel <= 649 then
        LevelFarm = "Royal Soldier [Lv. 550]"
        NameQuest = "SkyExp2Quest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(-7904, 5546, -380)
        CFrameMon = CFrame.new(-7828, 5607, -1744)

    elseif MyLevel >= 650 and MyLevel <= 699 then
        LevelFarm = "Galley Pirate [Lv. 625]"
        NameQuest = "FountainQuest"
        QuestLv = 1
        CFrameQuestPos = CFrame.new(5256, 38, 4050)
        CFrameMon = CFrame.new(5553, 77, 3930)

    elseif MyLevel >= 700 then
        LevelFarm = "Galley Captain [Lv. 650]"
        NameQuest = "FountainQuest"
        QuestLv = 2
        CFrameQuestPos = CFrame.new(5256, 38, 4050)
        CFrameMon = CFrame.new(5710, 77, 3986)
    else
        warn("Nível fora do range previsto para farming.")
        return nil
    end

    return {
        LevelFarm = LevelFarm,
        NameQuest = NameQuest,
        QuestLv = QuestLv,
        CFrameQuestPos = CFrameQuestPos,
        CFrameMon = CFrameMon
    }
end
