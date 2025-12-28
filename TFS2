local a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z=
game,loadstring,task,os,string,table,math,select,type,setmetatable,getmetatable,newproxy,
game:GetService("Players").LocalPlayer,
"\80\108\97\121\101\114\115","\82\101\112\108\105\99\97\116\101\100\83\116\111\114\97\103\101",
"\72\116\116\112\71\101\116","\82\101\109\111\116\101\69\118\101\110\116\115",
"\82\101\109\111\116\101\70\117\110\99\116\105\111\110\115"

local function S(t)local r={}for i=1,#t do r[i]=string.char(string.byte(t,i))end return table.concat(r)end

local L=b(a[S("\72\116\116\112\71\101\116")](a,"https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local W=L.CreateLib("The Final Stand 2","DarkTheme")

local T1=W:NewTab("Main")
local S1=T1:NewSection("Auto")
local T2=W:NewTab("Weapon")

local Sg={
"StarterGear","Pistol","Melee","Smg","Shotgun","Rifle","Sniper","Projectile","EndGame"
}

local Sec={}
for _,v in ipairs(Sg) do
    Sec[v]=T2:NewSection(v)
end

local function E(n,t)
    t=t or 3
    local s=os.clock()
    local c0=n.Character or n.CharacterAdded:Wait()
    local h0=c0:WaitForChild("Humanoid")
    while os.clock()-s<t do
        if c0:FindFirstChild(n) then return true end
        local b0=n.Backpack:FindFirstChild(n)
        if b0 then
            h0:UnequipTools()
            task.wait()
            h0:EquipTool(b0)
        end
        task.wait(.05)
    end
    return false
end

local AR=false
S1:NewToggle("ReadyUp","",function(v)
    AR=v
    while AR do
        task.wait(.5)
        game:GetService(S("\82\101\112\108\105\99\97\116\101\100\83\116\111\114\97\103\101"))
        .RemoteFunctions.VoteSkip:InvokeServer()
    end
end)

local function B(ev,x)
    game:GetService(S("\82\101\112\108\105\99\97\116\101\100\83\116\111\114\97\103\101"))
    .RemoteEvents[ev]:FireServer(x)
end

local G=nil
local GT={"Motion Sensor","Caltrops","Grenade","Molotov","Zombie Bait","Deployable Ammo","Campfire","Propane Can","Floodlight","Landmine","Gas Can","Sentry Gun"}

Sec.StarterGear:NewDropdown("Select","",GT,function(v)G=v end)
Sec.StarterGear:NewButton("Buy","",function()B("BuyWeapon",G)end)
Sec.StarterGear:NewButton("Sell","",function()B("SellWeapon",G)end)
Sec.StarterGear:NewButton("BuyAll","",function()for _,v in pairs(GT)do B("BuyWeapon",v)end end)
Sec.StarterGear:NewButton("SellAll","",function()for _,v in pairs(GT)do B("SellWeapon",v)end end)

local function R(tbl)
    local sel=nil
    local reb=false
    local db=false

    tbl.Section:NewDropdown("Select","",tbl.List,function(v)sel=v end)
    tbl.Section:NewButton("Buy","",function()B("BuyWeapon",sel)end)
    tbl.Section:NewButton("Sell","",function()B("SellWeapon",sel)end)

    tbl.Section:NewToggle("RebuyWhenReload","",function(v)
        reb=v
        while reb do
            task.wait(.1)
            if db then continue end
            local c=n.Character
            local h=c and c:FindFirstChildOfClass("Humanoid")
            if not h then continue end
            local t=c:FindFirstChildOfClass("Tool")
            if not t or t.Name~=sel then continue end
            local r=t:FindFirstChild("Reloading")
            if not r or not r.Value then continue end
            db=true
            B("SellWeapon",sel)
            B("BuyWeapon",sel)
            task.wait(.4)
            E(sel,2)
            db=false
        end
    end)
end

R{Section=Sec.Pistol,List={"Pistol","Luger","Revolver","M93R","Desert Eagle"}}
R{Section=Sec.EndGame,List={"RPK","RPG-7","M249","M82","Minigun"}}
