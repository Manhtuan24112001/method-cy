getgenv().Config = {
    ["Enable"] = true,
    ["Type"] = "RARE_BOSS", -- MIRAGE_ISLANDS / COMMON_BOSS / RARE_BOSS / FULL_MOONS / NEAR_MOONS / LENGEDARY_SWORDS
    ["Team"] = "Pirates", -- Pirates / Marines
    ["Server Find Age"] = 10, -- This is server age of server since found max 60s
    ["Lock Boss"] = {
        ["Rare Boss"] = {
            ["Enable"] = true, -- Enable = Auto lock find boss by name / Off = Random boss hop
            ["Boss"] = "Dough King" -- Darkbeard / rip_indra True Form / Dough King
        },
        ["Common Boss"] = {
            ["Enable"] = true, -- Enable = Auto lock find boss by name / Off = Random boss hop
            ["Boss"] = "Soul Reaper" -- Soul Reaper / Cursed Captain
        }
    }
}
loadstring(game:HttpGet("http://pluto-cheat.x10.mx/Lua/Finder.lua"))()
