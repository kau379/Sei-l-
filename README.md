-- Função para listar todos os jogadores no servidor
function listarJogadores()
    for _, jogador in pairs(game.Players:GetPlayers()) do
        print("Jogador: " .. jogador.Name)
    end
end

-- Função para pegar abóboras do evento de Halloween
function pegarAboboras()
    for _, abobora in pairs(workspace:FindPartsInRegion3(workspace.CurrentCamera.CFrame, Vector3.new(50, 50, 50))) do
        if abobora.Name == "HalloweenPumpkin" then
            abobora:Destroy()
            print("Abóbora coletada!")
        end
    end
end

-- Função para remover o tempo de carregamento dos poderes
function removerTempoCarregamento()
    for _, jogador in pairs(game.Players:GetPlayers()) do
        jogador.Character.Humanoid.WalkSpeed = 50 -- Aumenta a velocidade de movimento
        jogador.Character.Humanoid.JumpPower = 100 -- Aumenta a potência do pulo
        -- Adicione outras modificações de poderes aqui
    end
end

-- Conectar as funções a eventos
game.Players.PlayerAdded:Connect(function(player)
    player.Chatted:Connect(function(msg)
        if msg == "!verJogadores" then
            listarJogadores()
        elseif msg == "!pegarAboboras" then
            pegarAboboras()
        elseif msg == "!removerTempoCarregamento" then
            removerTempoCarregamento()
        end
    end)
end)
