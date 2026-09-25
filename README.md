--[[
    WindUI Example 2
]]

local cloneref = (cloneref or clonereference or function(instance)
	return instance
end)
local ReplicatedStorage = cloneref(game:GetService("ReplicatedStorage"))
local RunService = cloneref(game:GetService("RunService"))

local WindUI

do
	local ok, result = pcall(function()
		return require("./src/Init")
	end)

	if ok then
		WindUI = result
	else
		if RunService:IsStudio() or not writefile then
			WindUI = require(ReplicatedStorage:WaitForChild("WindUI"):WaitForChild("Init"))
		else
			WindUI =
				loadstring(game:HttpGet("https://raw.githubusercontent.com/Footagesus/WindUI/main/dist/main.lua"))()
		end
	end
end

-- ===== Lucide 图标映射表 =====
local IconMap = { -- lucide
	Tab = "table-of-contents",
	Paragraph = "type",
	Button = "square-mouse-pointer",
	Toggle = "toggle-right",
	Slider = "sliders-horizontal",
	Keybind = "command",
	Input = "text-cursor-input",
	Dropdown = "chevrons-up-down",
	Code = "terminal",
	Colorpicker = "palette",
	ProgressBar = "chart-bar",
}
-- =================================

--WindUI.TransparencyValue = .9
local ThemeName = "Dark"

local Window = WindUI:CreateWindow({
	Title = "WindUI Library",
	Author = "by .ftgs",
	Icon = "solar:wind-bold",
	Theme = ThemeName,
	ToggleKey = Enum.KeyCode.F,

	KeySystem = {
		Title = "Key System",
		Description = "Enter the correct key to unlock the window",
		KeyValidator = function(key)
			return key == "zzcnb666"
		end,
	}
})

Window:Tag({
	Title = "v1.6.64-fix",
	Color = "ElementBackground",
})

-- ========== Main Tab（包含作者信息和QQ） ==========
local MainTab = Window:Tab({
	Title = "Main",
	Icon = "warehouse",
})

-- 作者信息段落（包含QQ）
MainTab:Paragraph({
	Title = "👤 作者信息",
	Desc = "WindUI Library 由 zzc 开发\n版本: v1.6.64-fix\nQQ: 320242164\n感谢使用！",
	Buttons = {
		{
			Title = "复制作者信息",
			Callback = function()
				setclipboard("WindUI Library by zzc | Version: v1.6.64-fix | QQ: 320242164")
				print("作者信息已复制到剪贴板！")
			end,
		},
		{
			Title = "复制QQ",
			Variant = "Secondary",
			Callback = function()
				setclipboard("320242164")
				print("QQ号已复制到剪贴板！")
			end,
		},
		{
			Title = "查看 GitHub",
			Variant = "Secondary",
			Callback = function()
				print("打开 GitHub 页面...")
				-- 可在此添加实际跳转逻辑
			end,
		},
	},
})

-- Silent Section
MainTab:Section({
	Title = "Silent",
})
-- =====================================================

-- ========== Exploits Tab ==========
local Tab1 = Window:Tab({
	Title = "Exploits",
	Icon = "terminal",
})
-- =================================

Window:Tab({
	Title = "Aimbot",
	Icon = "locate-fixed",
})

Window:Tab({
	Title = "ESP",
	Icon = "eye",
})

-- ========== Info Tab ==========
local InfoTab = Window:Tab({
	Title = "Info",
	Icon = "badge-info",
})

InfoTab:Paragraph({
	Title = "WindUI",
	Desc = "WindUI is a open source UI library for Roblox Script Hubs",
	Buttons = {
		{
			Title = "GitHub",
			Callback = function()
				print("GitHub Button Clicked")
			end,
		},
		{
			Title = "Documentation",
			Variant = "Secondary",
			Callback = function()
				print("Documentation Button Clicked")
			end,
		},
	},
})

local HStack1 = InfoTab:HStack()

local VStackLeft = HStack1:VStack()
local VStackRight = HStack1:VStack()

VStackLeft:Button({
	Title = "Reload UI",
	Justify = "Center",
	Icon = "refresh-ccw",
	IconAlign = "Left",
	Color = Color3.fromHex("#F44732"),
	Callback = function()
		print("Reloading UI...")
	end,
})

VStackRight:Button({
	Title = "Rejoin Place",
	Justify = "Center",
	Icon = "log-out",
	IconAlign = "Left",
	Color = Color3.fromHex("#f4b332"),
	Callback = function()
		print("Rejoining place...")
	end,
})
-- ===============================

-- ========== Section in Exploits Tab ==========
local Section = Tab1:Section({
	Title = "Hi1",
	Icon = "rbxassetid://77799629590713",
	IconThemed = true,
	Box = true,
	BoxBorder = true,
})

local Viewport = Section:Viewport({
	Object = Instance.new("Part"),
	Interactive = true,
})

Section:Input({
	Title = "Leave at Wave",
	Desc = "Enter a wave number to automatically leave the raid at that wave (0 = never leave)",
	Icon = "log-out",
	Type = "Default",
	Placeholder = "e.g. 50",
	Value = "0",
	Flag = "ninja_raid_leave_wave",
	Callback = function(text)
		-- 预留回调
	end,
})
-- ===============================================

-- ========== Empty Tab ==========
local EmptyTab = Window:Tab({
	Title = "Custom empty page tab",

	CustomEmptyPage = {
		Icon = "lucide:smile",
		Title = "This is a cool empty tab",
		Desc = "I like it. its so great tab with cool 'custom empty page'",
	},
})
-- ===============================

-- ========== DynamicShapeModule ==========
local Creator

local DynamicShapeModule = {
	New = nil,
	Init = nil,
	Shapes = {
		Circle = {
			Image = "rbxassetid://111665032676235",
			Rect = Rect.new(1024 / 2, 1024 / 2, 1024 / 2, 1024 / 2),
			Radius = 1024 / 2,
		},
		CircleOutline = {
			Image = "rbxassetid://108556680453287",
			Rect = Rect.new(1024 / 2, 1024 / 2, 1024 / 2, 1024 / 2),
			Radius = 1024 / 2,
		},
		CircleGlass = {
			Image = "rbxassetid://95600044758841",
			Rect = Rect.new(1024 / 2, 1024 / 2, 1024 / 2, 1024 / 2),
			Radius = 1024 /
