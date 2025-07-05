

lastupdate = "GMT +0: 26.10.2024 17:43:33"



local asciiart = [[

 _   _                       _ _ _
| | | |_   _ _ __   ___ _ __| (_) |__
| |_| | | | | '_ \ / _ \ '__| | | '_ \
|  _  | |_| | |_) |  __/ |  | | | |_) |
|_| |_|\__, | .__/ \___|_|  |_|_|_.__/
       |___/|_|
]]
function bigRedItalicText(text)
    pcall(function()
        game:GetService("StarterGui"):SetCore("ChatMakeSystemMessage", {
            Text = text,
            Color = Color3.fromRGB(255, 0, 0), 
            Font = Enum.Font.SourceSansItalic,
            TextTransparency = 0,
            TextStrokeTransparency = 0,
            TextScaled = false,
            TextWrapped = false,
            TextXAlignment = Enum.TextXAlignment.Center,
            TextYAlignment = Enum.TextYAlignment.Center,
            TextStrokeColor3 = Color3.new(0, 0, 0),
            FontSize = Enum.FontSize.Size48,
        })
    end)

    pcall(function()
        game.TextChatService.TextChannels.RBXSystem:DisplaySystemMessage("<font color=\"rgb(255, 0, 0)\">" ..
        text .. "</font> ")
    end)
end

function getGUIs(parent)
    local guis = {}

    for _, gui in pairs(parent:GetChildren()) do
        if gui:IsA("GuiBase2d") or gui:IsA("BillboardGui") then
            table.insert(guis, gui)
        end
    end

    return guis
end

getgenv().coreGui = game:GetService("CoreGui")

function checkAndManageGUIs()
    local currentGUIs = getGUIs(coreGui)

    
    local newGUIs = {}
    for _, gui in pairs(currentGUIs) do
        if not table.find(previousGUIs, gui) then
            table.insert(newGUIs, gui)
        end
    end

    
    for _, gui in pairs(previousGUIs) do
        if not table.find(currentGUIs, gui) then
            print("Found new Guis")
            gui:Destroy() 
        end
    end

    
    for _, gui in pairs(newGUIs) do
        gui:Destroy() 
    end

    previousGUIs = currentGUIs 
end

function ManagerRefreshGuis()
    for gui, _ in pairs(guitrackedbyhyperlib) do
        if not table.find(currentGUIs, gui) then
            
            guitrackedbyhyperlib[gui][1]:RemoveLabel()
            guitrackedbyhyperlib[gui][2]:RemoveButton()
            guitrackedbyhyperlib[gui][6]:RemoveButton()
            
        end
        
        if ignoredguis[gui] == true then
            
            guitrackedbyhyperlib[gui][1]:RemoveLabel()
            guitrackedbyhyperlib[gui][2]:RemoveButton()
            guitrackedbyhyperlib[gui][6]:RemoveButton()
            
            guitrackedbyhyperlib[gui] = nil
        end
    end
end
function isMobile()
    local UserInputService = game:GetService("UserInputService")

    if UserInputService.TouchEnabled and not UserInputService.KeyboardEnabled then
        return true
    else
        return false
    end
end

if getgenv().hyperlibreload == nil then
    getgenv().hyperlibreload = false
end
if getgenv().serverhoptolow == nil then
    getgenv().serverhoptolow = false
end
if getgenv().hyperlibblock == nil then
    getgenv().hyperlibblock = true
else
    if getgenv().hyperlibblock == true then
        bigRedItalicText("Another Hyperlib instance is already running! Aborting...")
        return
    elseif getgenv().hyperlibblock == false then
        getgenv().hyperlibblock = true
    end
end

getgenv().gamecount = 0
getgenv().scriptcount = 0

getgenv().hubscripts = {
    allscripts = {}
}
getgenv().uniscripts = {
    allscripts = {}
}
version = "Hyperlib V.3.6.5 (Legacy)"
getgenv().statusdict = {}



function getLocalPlayerName()
    local player = game:GetService("Players").LocalPlayer
    return player.Name
end

function bigRedText(text)
    pcall(function()
        game:GetService("StarterGui"):SetCore("ChatMakeSystemMessage", {
            Text = text,
            Color = Color3.new(1, 0, 0),
            Font = Enum.Font.GothamBold,
            FontSize = Enum.FontSize.Size48,
        })
    end)
    pcall(function()
        game.TextChatService.TextChannels.RBXSystem:DisplaySystemMessage("<font color=\"rgb(255, 0, 0)\">" ..
        text .. "</font> ")
    end)
end
function bigGreenItalicText(text)
    pcall(function()
        game:GetService("StarterGui"):SetCore("ChatMakeSystemMessage", {
            Text = text,
            Color = Color3.fromRGB(0, 255, 0), 
            Font = Enum.Font.SourceSansItalic,
            TextTransparency = 0,
            TextStrokeTransparency = 0,
            TextScaled = false,
            TextWrapped = false,
            TextXAlignment = Enum.TextXAlignment.Center,
            TextYAlignment = Enum.TextYAlignment.Center,
            TextStrokeColor3 = Color3.new(0, 0, 0),
            FontSize = Enum.FontSize.Size48,
        })
    end)

    pcall(function()
        game.TextChatService.TextChannels.RBXSystem:DisplaySystemMessage("<font color=\"rgb(0, 255, 0)\">" ..
        text .. "</font> ")
    end)
end
function clearChat()
    local clearMessage = ""
    for i = 1, 20 do
        clearMessage = clearMessage .. " "
    end

    for i = 1, 30 do
        pcall(function()
            game:GetService("StarterGui"):SetCore("ChatMakeSystemMessage", {
                Text = clearMessage,
                Color = Color3.new(1, 1, 1), 
                Font = Enum.Font.SourceSans,
                FontSize = Enum.FontSize.Size18,
            })
        end)
        pcall(function()
            game.TextChatService.TextChannels.RBXSystem:DisplaySystemMessage("‎")
        end)
    end
end

function bigBlueItalicText(text)
    pcall(function()
        game:GetService("StarterGui"):SetCore("ChatMakeSystemMessage", {
            Text = text,
            Color = Color3.fromRGB(0, 162, 255), 
            Font = Enum.Font.SourceSansItalic,
            TextTransparency = 0,
            TextStrokeTransparency = 0,
            TextScaled = false,
            TextWrapped = false,
            TextXAlignment = Enum.TextXAlignment.Center,
            TextYAlignment = Enum.TextYAlignment.Center,
            TextStrokeColor3 = Color3.new(0, 0, 0),
            FontSize = Enum.FontSize.Size48,
        })
    end)

    pcall(function()
        game.TextChatService.TextChannels.RBXSystem:DisplaySystemMessage("<font color=\"rgb(0, 162, 255)\">" ..
        text .. "</font> ")
    end)
end
local function formatTimeForUser(lastupdate)
    local function parseDateTime(dateTimeStr)
        local gmtOffset, dateStr, timeStr = string.match(dateTimeStr, "GMT ([+-]%d+): (%d+%.%d+%.%d+) (%d+:%d+:%d+)")
        local day, month, year = string.match(dateStr, "(%d+)%.(%d+)%.(%d+)")
        local hour, minute, second = string.match(timeStr, "(%d+):(%d+):(%d+)")
        return os.time({
            year = tonumber(year),
            month = tonumber(month),
            day = tonumber(day),
            hour = tonumber(hour),
            min = tonumber(minute),
            sec = tonumber(second)
        }) - tonumber(gmtOffset) * 3600 
    end

    local function getTimezoneOffset()
        
        local utcTime = os.time(os.date("!*t"))

        
        local localTime = os.time()

        
        local offsetInSeconds = os.difftime(localTime, utcTime)

        
        local offsetInHours = offsetInSeconds / 3600

        return offsetInHours
    end

    local userTimezoneOffset = getTimezoneOffset()
    local parsedTime = parseDateTime(lastupdate)
    local userTimeInSeconds = parsedTime + userTimezoneOffset * 3600

    
    local formattedTime = os.date("%A, %B %d %H:%M:%S %Y", userTimeInSeconds)
    return formattedTime
end





function addscript(Place, Gamename, title, author, scriptlink, origin)
    getgenv().gamecount = getgenv().gamecount + 1
    getgenv().scriptcount = getgenv().scriptcount + 1

    if game.PlaceId == Place then
        getgenv().gamescripts = {
            place = Place,
            gamename = Gamename,
            allscripts = {}
        }
        local scriptdata = {
            title = title,
            author = author,
            scriptlink = scriptlink,
            origin = origin
        }
        table.insert(getgenv().gamescripts.allscripts, scriptdata)
    end
end

function addscriptexist(Place, title, author, scriptlink, origin)
    getgenv().scriptcount = getgenv().scriptcount + 1
    name = title

    if game.PlaceId == Place then
        local scriptdata = {
            title = title,
            author = author,
            scriptlink = scriptlink,
            origin = origin
        }
        table.insert(getgenv().gamescripts.allscripts, scriptdata)
    end
end

function addscriptuniversal(title, author, scriptlink, origin)
    getgenv().scriptcount = getgenv().scriptcount + 1
    local scriptdata = {
        title = title,
        author = author,
        scriptlink = scriptlink,
        origin = origin
    }
    table.insert(getgenv().uniscripts.allscripts, scriptdata)
end

function addhub(title, author, scriptlink, origin)
    getgenv().scriptcount = getgenv().scriptcount + 1
    local scriptdata = {
        title = title,
        author = author,
        scriptlink = scriptlink,
        origin = origin
    }
    table.insert(getgenv().hubscripts.allscripts, scriptdata)
end

function UpdateWindowTitle(title)
    getgenv().hyperlibguititle.Text = title
end

function DisplayWindowMessage(title)
    spawn(function()
        UpdateWindowTitle(title)
        wait(3)
        UpdateWindowTitle(version)
    end)
end

function sortHubs()
    table.sort(getgenv().hubscripts.allscripts, function(a, b)
        return a.title < b.title
    end)
end

function sortUni()
    table.sort(getgenv().uniscripts.allscripts, function(a, b)
        return a.title < b.title
    end)
end

function getCurrentPlayerCount()
    return #game.Players:GetPlayers()
end
function getMaxPlayerCount()
    return game.Players.MaxPlayers
end
function getClientPing()
    local ping = game:GetService("Stats").Network.ServerStatsItem["Data Ping"]:GetValue()
    return math.floor(ping + 0.5)
end

local fps = 0
local lastTick = tick()
game:GetService("RunService").Heartbeat:Connect(function()
    local currentTick = tick()
    fps = 1 / (currentTick - lastTick)
    lastTick = currentTick
end)

function getFPS()
    return math.floor(fps + 0.5)
end

function getPlaceID()
    return game.PlaceId
end

function getPlaceName()
    return game.Place.Name
end

function getServerID()
    return game.JobId
end
local function getClientUptime()
    return tick()
end


getgenv().HyperlibLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/Fantemil/Trenglehub/main/Library/kavo-ui.lua"))()
getgenv().Window = getgenv().HyperlibLibrary.CreateLib(version, "DarkTheme")
Window = getgenv().Window
getgenv().hyperlibgui.ZIndexBehavior = Enum.ZIndexBehavior.Global


repeat
    UpdateWindowTitle("Waiting for game to load.")
    wait(0.1)
    UpdateWindowTitle("Waiting for game to load..")
    wait(0.1)
    UpdateWindowTitle("Waiting for game to load...")
    wait(0.1)
until game:IsLoaded()
UpdateWindowTitle("Game is loaded!")


if game.PlaceId == 13772394625 then
    UpdateWindowTitle("Protecting against Blade Ball Anticheat...")
    for i, v in pairs(game.ReplicatedStorage:GetChildren()) do
        if v.Name == "Security" then
            for i, v in game.ReplicatedStorage.Security:GetChildren() do
                v:Destroy()
            end
            game.ReplicatedStorage.Security:Destroy()
        end
    end
    UpdateWindowTitle("Successfully protected against Blade Ball Anticheat!")
end
UpdateWindowTitle(version)
local Player = Window:NewTab("Toolbox")
local PlayerSection = Player:NewSection("Player")
local GeneralSection = Player:NewSection("General")

GeneralSection:NewButton("Rejoin", "Rejoins the game", function()
    getgenv().hyperlibblock = false
    game:GetService("TeleportService"):Teleport(game.PlaceId, game.Players.LocalPlayer)
end)
GeneralSection:NewButton("Exit Game", "Exits the game", function()
    getgenv().hyperlibblock = false
    game:Shutdown()
end)
GeneralSection:NewButton("Clear Chat", "Clears the chat", function()
    clearChat()
end)
getgenv().guireloader = GeneralSection:NewButton("Reload Hyperlib", "Reloads the Gui with the newest Version", function()
    spawn(function()
        guireloader:UpdateButton("Reloading in 3")
        wait(1)
        guireloader:UpdateButton("Reloading in 2")
        wait(1)
        guireloader:UpdateButton("Reloading in 1")
        wait(1)
        guireloader:UpdateButton("Reloading...")
        wait(1)
        getgenv().hyperlibgui:Destroy()
        
        getgenv().hyperlibreload = true
        getgenv().hyperlibblock = false
        pcall(function()
            getgenv().HyperlibMobileButtonGUI:Destroy()
        end)
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Fantemil/Hyperlib/main/trenglehub.lua"))()
    end)
end)

getgenv().hyperlibkill = GeneralSection:NewButton("Kill Hyperlib", "Kills the Hyperlib Gui", function()
    spawn(function()
        hyperlibkill:UpdateButton("Closing Hyperlib in 3")
        wait(1)
        hyperlibkill:UpdateButton("Closing Hyperlib in 2")
        wait(1)
        hyperlibkill:UpdateButton("Closing Hyperlib in 1")
        wait(1)
        hyperlibkill:UpdateButton("Goodbye!")
        wait(1)
        getgenv().hyperlibgui:Destroy()
        
        getgenv().hyperlibreload = false
        getgenv().hyperlibblock = false
        pcall(function()
            getgenv().HyperlibMobileButtonGUI:Destroy()
        end)
    end)
end)

getgenv().mobiletogglestate = false
getgenv().mobilebuttontoggle = GeneralSection:NewButton("Load Mobile GUI Toggle", "Enable/Disable the Mobile GUI Toggle", function()
    
    if getgenv().mobiletogglestate == false then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Fantemil/Hyperlib/refs/heads/main/Extensions/mobiletoggle.lua"))()
        getgenv().mobilebuttontoggle:UpdateButton("Unload Mobile GUI Toggle")
    else
        getgenv().HyperlibMobileButtonGUI:Destroy()
        mobiletogglestate = false
        getgenv().mobilebuttontoggle:UpdateButton("Load Mobile GUI Toggle")
        bigGreenItalicText("Unloading Mobile GUI Toggle!")
    end
end)

getgenv().serverhopper = GeneralSection:NewButton("Server Hop",
    "Hop to another random Server", function()

        local PlaceID = game.PlaceId
        local AllIDs = {}
        local foundAnything = ""
        local actualHour = os.date("!*t").hour
        
        function TPReturner()
            local sortOrder = math.random(1, 2) == 1 and "Asc" or "Desc"
            local Site
            if foundAnything == "" then
                Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' ..
                PlaceID .. '/servers/Public?sortOrder=' .. sortOrder .. '&limit=100&excludeFullGames=true'))
            else
                Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' ..
                PlaceID .. '/servers/Public?sortOrder=' .. sortOrder .. '&limit=100&cursor=' .. foundAnything .. '&excludeFullGames=true'))
            end
            if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
                foundAnything = Site.nextPageCursor
            end
        
            local serverList = {}
            for _, v in pairs(Site.data) do
                if tonumber(v.maxPlayers) > tonumber(v.playing) then
                    table.insert(serverList, tostring(v.id))
                end
            end
        
            if #serverList > 0 then
                local randomIndex = math.random(1, #serverList) 
                local randomServerID = serverList[randomIndex]
                table.insert(AllIDs, randomServerID)
        
                pcall(function()
                    bigGreenItalicText("Teleporting to a random server now!")
                    game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, randomServerID, game.Players.LocalPlayer)
                end)
            else
                if foundAnything ~= "" then
                    TPReturner()
                end
            end
        end
        
        function Teleport()
            while wait() do
                pcall(function()
                    TPReturner()
                end)
            end
        end
        
        spawn(function()
            while true do
                getgenv().serverhopper:UpdateButton("Teleporting")
                wait(0.1)
                getgenv().serverhopper:UpdateButton("Teleporting.")
                wait(0.1)
                getgenv().serverhopper:UpdateButton("Teleporting..")
                wait(0.1)
                getgenv().serverhopper:UpdateButton("Teleporting...")
                wait(0.1)
            end
        end)
        
        bigGreenItalicText("Teleporting to a random server...")
        Teleport()
end)
getgenv().serverhopperlower = GeneralSection:NewButton("Server Hop to emptiest Server",
    "Hop to another Server thats as empty as it can be", function()
    local PlaceID = game.PlaceId
    local AllIDs = {}
    local foundAnything = ""
    local actualHour = os.date("!*t").hour
    local Deleted = false

    function TPReturner()
        local Site;
        if foundAnything == "" then
            Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' ..
            PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
        else
            Site = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' ..
            PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. foundAnything))
        end
        local ID = ""
        if Site.nextPageCursor and Site.nextPageCursor ~= "null" and Site.nextPageCursor ~= nil then
            foundAnything = Site.nextPageCursor
        end
        local num = 0;
        for i, v in pairs(Site.data) do
            local Possible = true
            ID = tostring(v.id)
            if tonumber(v.maxPlayers) > tonumber(v.playing) then
                for _, Existing in pairs(AllIDs) do
                    if num ~= 0 then
                        if ID == tostring(Existing) then
                            Possible = false
                        end
                    else
                        if tonumber(actualHour) ~= tonumber(Existing) then
                            local delFile = pcall(function()
                                AllIDs = {}
                                table.insert(AllIDs, actualHour)
                            end)
                        end
                    end
                    num = num + 1
                end
                if Possible == true then
                    table.insert(AllIDs, ID)
                    wait()
                    pcall(function()
                        wait()
                        getgenv().serverhoptolow = true
                        bigGreenItalicText("Teleporting now!")
                        game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
                    end)
                    wait(4)
                end
            end
        end
    end

    function Teleport()
        while wait() do
            pcall(function()
                TPReturner()
                if foundAnything ~= "" then
                    TPReturner()
                end
            end)
        end
    end

    spawn(function()
        while true do
            getgenv().serverhopperlower:UpdateButton("Teleporting")
            wait(0.1)
            getgenv().serverhopperlower:UpdateButton("Teleporting.")
            wait(0.1)
            getgenv().serverhopperlower:UpdateButton("Teleporting..")
            wait(0.1)
            getgenv().serverhopperlower:UpdateButton("Teleporting...")
            wait(0.1)
        end
    end)
    bigGreenItalicText("Teleporting to a Server with the lowest amount of players...")
    Teleport()
end)
getgenv().serverhopperhigher = GeneralSection:NewButton("Server Hop to full Server",
"Hop to the fu
