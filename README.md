-- Auto Farm de Sia (Sea Event)
_G.SeaFarm = true

function FarmSeaEvent()
    while _G.SeaFarm do
        for _, entity in pairs(workspace.Enemies:GetChildren()) do
            if entity:FindFirstChild("Humanoid") and entity:FindFirstChild("HumanoidRootPart") then
                if entity.Name:find("Sea") or entity.Name:find("Shark") or entity.Name:find("Pirate") then
                    repeat
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =
                            entity.HumanoidRootPart.CFrame * CFrame.new(0, 20, 0)
                        wait(0.2)
                        game:GetService("VirtualInputManager"):SendKeyEvent(true, "Z", false, game)
                        wait(0.1)
                    until entity.Humanoid.Health <= 0 or not _G.SeaFarm
                end
            end
        end
        wait(1)
    end
end

spawn(FarmSeaEvent)
