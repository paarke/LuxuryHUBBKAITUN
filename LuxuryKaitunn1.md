getgenv().FixedFastAttackScript = true
getgenv().Team = "Pirates"
_G.Key = "LuxuryV2_15hz16cdxazfpa0ppamj"
_G.DiscordId = "1122795311874711604"
_G.KaitanMode = true
shared.Team = "Pirates"
getgenv().Configs = {
    FpsBoost = true,
    SkipFarm = true,
    HopIfCantKill = true,
    BlockAllHop = false,
    FastAttack = true,
    NewFastAttack = true,
    NoAttackAnimation = true,
    StartKaitun = true,
    AutoPole = true,
    AutoSaber = true,
    AutoSecondSea = true,
    AutoRengoku = true,
    AutoQuestFlower = true,
    AutoRaceV3 = false,
    AutoBartiloQuest = true,
    AutoCursedCaptain = true,
    AutoDarkbeard = true,
    AutoFactory = true,
    AutoThirdSea = true,
    SkipGetItemGuitar = true,
    AlliesFruit = {"Kitsune-Kitsune","Dragon-Dragon","Leopard-Leopard"}, -- Add Mammoth or whatever
    AutoHallowScythe = true,
    AutoBuddySword = true,
    AutoDoughKing = true,
    AutoSpikeyTrident = true,
    AutoTushita = true,
    AutoEliteHunter = true,
    AutoDarkDagger = true,
    AutoYama = true,
    AutoCanvander = true,
    AutoSoulGuitar = true, 
    AutoRainbowHaki = false,
    AutoCursedDualKatana = true,
    AutoGodHuman = true,
    AutoSuperhuman = true,
    AutoDeathStep = true,
    AutoSharkmanKarate = true,
    AutoElectricClaw = true,
    AutoDargonTalon = true,
    AutoDFMastery = true,
    SettingsSkill = {
        -- ["Z"] = 0.1,
        -- ["X"] = 0.1,
        -- ["C"] = 0.1,
        -- ["V"] = 0.1,
    },
    AutoSwordMastery = false,
    SelectRaritySword = {""},
    SelectRedeemCodeLevel = 1,
    SelectRateFruitRaid = 1000000,
    LimitFragmentsRaids = 100000,
    SelectMainDF = {""Dragon-Dragon","Spirit-Spirit","Venom-Venom","Dough-Dough"},
    SelectSubDF = {""Ice-Ice","Sand-Sand","Dark-Dark","Quake-Quake","Light-Light"},
    AllowEatDFInventory = false,
    StartSniper = true,
    RAMPort = 7963,
    RAMPassword = "",
    AutoDescription = false,
    StartWebhook = false,
    WebhookURL = "",
    WebhookSettings = "",
    LockFPS = 35,
    LockFPSNow = true,
    WhiteScreen = true
}
-- Prevent 20 Minutes AFK
local vu = game:service'VirtualUser'
game:service'Players'.LocalPlayer.Idled:connect(function()
    vu:CaptureController()
    vu:ClickButton2(Vector2.new())
end)

coroutine.wrap(function()
local StopCamera = require(game.ReplicatedStorage.Util.CameraShaker)StopCamera:Stop()
    for v,v in pairs(getreg()) do
        if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework then
             for v,v in pairs(debug.getupvalues(v)) do
                if typeof(v) == "table" then
                    spawn(function()
                        game:GetService("RunService").RenderStepped:Connect(function()
                            if getgenv().FixedFastAttackScript then
                                 pcall(function()
                                     v.activeController.timeToNextAttack = -(math.huge^math.huge^math.huge)
                                     v.activeController.attacking = false
                                     v.activeController.increment = 4
                                     v.activeController.blocking = false   
                                     v.activeController.hitboxMagnitude = 150
    		                         v.activeController.humanoid.AutoRotate = true
    	                      	     v.activeController.focusStart = 0
    	                      	     v.activeController.currentAttackTrack = 0
                                     sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRaxNerous", math.huge)
                                 end)
                             end
                         end)
                    end)
                end
            end
        end
    end
end)()

loadstring(game:HttpGet("https://raw.githubusercontent.com/NightsTimeZ/RoyryX/main/Loader.lua"))()
